# These instructions are for all DB related issues

### NOTE: 
1.  Before you start, please alert the Omni team that you are begining this process. During this process you will be changing the DB definition within the code base and thefore all work/api calls/tests on the dev site should be paused during this work.
2.  Visit https://evelt.atlassian.net/browse/MN-40 for instructions that include images
## This guide includes:

## 1. Create new DB
a) Right click in SCHEMAS section 
   
b) Select ‘create new schema' 
   
c) Enter DB name

d) select 'apply'

## 2. Export omni_PRODUCTION Schema:
a) Select ‘Data Export’ from the ‘Server’ menu option at the top of the application window

b) In the left hand side table titled ‘‘Tables to Export’, tick the schema named ‘cloudsno_omniPRODUCTION ’ (or whatever name the live production DB is called).

c) In the drop down beneath the right hand side table select ‘Dump Structure Only’

d)   In the ‘Export Options’ section, choose the ‘Export to Self-Contained Filed’ option and click the '…' button to name the file that will be created by this export and the place where it will be saved
   
e) Select ‘Start Export’ to start the process.


## 3. Import omniPROD schema to new DB:

a) Select ‘Server’ > 'Data Import from top menu

b) Choose the option ‘Import fron Self-containted File’, click the '…' button to select the file you exported in step #2

c) Choose your newly created DB from the drop down title ‘Default Targe Schema’

d) Towards the bottom of the page, choose ‘Dump Data Only’ 

e) Select ‘start import’ to begin the import process

## 4. Export Non-associative Omni data
a) The Api you will call in this step is hardcoded to point to cloudsno_omniPRODUCTION (current live DB). This means the exports will contain the most upto date data. The hardcoded DB may be changed incase the production DB name changes. The file in question is ‘…V1.10-DEV/adming/api/actions/fetchData.php’. The highlighted code in the image below represents the code that creates the DB connection.  The DB name is represented as the last value passing through the ‘real_connect’ function.
   
    $database->connection->real_connect(DB_SERVER, DB_USER, DB_PASS, 'cloudsno_omniPRODUCTION');

b) Open up Postman desktop app

c) Select ‘Import’ > ‘Raw text’ and paste this api call in the text box

    curl --location --request GET 'https://dev.api.omni.cloudsnob.com/V1.10/fetchData/123!' \
    --header 'token: usr_gb67jkKjgT'
    
d) Note:
  This call should ONLY be called in its format above where it calls the dev environment. Do not direct it to ‘…//api.omni …’
  
e) The last part of url represents the security token required for this call as it circomvents the regular security checks. 
 
f) The ‘token’ must be any existing user token

g) The call provided here points to the dev repo as our PROD db is empty with no users avl yet. Once a user is avl, the ‘dev.’ part of the URL may be removed if you wish to you use the PROD environment to power the call.

h) Select ‘Continue’ and then ‘Import’.

i) Click the ‘Send Button’ to run the api call

j) The results of this api call are saved on the new server at this location: '/var/www/html/omni-commerce/V1.10-DEV/admin/api/database/backup' and will be title: ‘db_backup_for_non_associated_tables_1658998738.sql’ where the digits represent the timestamp the call was made.

k) Sort by date to make it easier to locate the new file. This folder should be emptied regularly to avoid buildup of heavy files on the server. 

l) Download the newly created file

m) Do not attempt to copy and past the returned code in postman instead of downloading the file because the raw code in postman is not formatted to be imported to a DB.

## 5. Export Associative data (data for specific company)

a) Copy and paste this api call below into postman (Import > Raw text > Continue > Import)

    curl --location --request GET 'https://dev.api.omni.cloudsnob.com/V1.10/fetchData/companyToken/123!' \
    --header 'token: usr_gb67jkKjgT'

b) Edit the url ‘companyToken’ to the company token of the company you want the data of. eg ### ##### = ‘comp_123456’ :

    curl --location --request GET 'https://dev.api.omni.cloudsnob.com/V1.10/fetchData/comp_DUKNlH2doBNtlKrq/123!' \
    --header 'token: usr_gb67jkKjgT' 

c) The Api call you will call in the next few steps will be automatically pull data from the production DB: ‘cloudsno_omniPRODUCTION’. ( Note: production used to be cloudsno_omniPROD, but was changed. FYI in case of inconsistencies in name etc.)

d) Send the api by clicking ‘Send’ in postman. Expect this process to take about 10 mins. Postman will display a ‘504 Gateway Time-out', ignore it as the process is continuing just find on the server.

e) Find the exported file on the server in the same location as the last file and download it. The file name will start with ‘db_backup_comp_’ , followed by the company name and timestamp it was created at.

## 6. Run DDL migration file to update the new DB’s schema

a) Open server files using WinSCP and download the file at location /var/www/html/omni-commerce/V1.10-DEV/admin/api/includes/config.php

b) Comment out the line that defines CONST ‘DB’ as our DEV db:

c) Copy and paste the commented code to the line below, change the second value within the brackets to point to your NEWLY created db eg  . define("DB_NAME", "new_database"); as seen here: 

d) Save the changes (CNTRL S) to the server.

e) Log into the new omni server (ip: 172-31-38-139). Navigate to the server ‘api’ folder:

f) run this cmd: ‘php database/migration_cron.php'. This call will update your new DB’s schema (table/column structure) so that is upto date with the latest version of Omni.

g) Expect multiple record to be created. Make sure there are no errors in the above call, ask for help if there are errors.

## 7. Run DDL seeder file to update your new DB to include vital data

a) Confirm config.php is pointing to your new db

b) In the server, in the ‘api’ folder, run the DDL seeder cmd : 

    php database/seeder_cron.php

   Expect to see many records created. If there are any errors, ask for help.
   
## 8. Import Non-associative data to new DB

a) Navigate back to MySQL Workbench.

b) Select ‘Server’ > ‘data import’.

c) You may have to select the tab title ‘Import from Disk’ if the Import opens on a different tab.

d) Select the file by the ‘Import from Self-Contained File’ section.

e) Check that the ‘Default Target Schema' is set to the new DB

f) Check that ‘Dump Data Only’ is selected in the lower drop down, or change it if is not

g) Start Import.

## 9. Import Associative Data to new DB

a) In MySQL Workbench, go to ‘Server’ > ‘Import Data’, check you are on the tab titled ‘Import from Disk’, choose ‘Import from Self-Contained File’, select the newly downloaded/saved file.

b) Choose the new DB in the ‘Default Target Schema’ dropdown.

c) Choose ‘Dump Data only' in the lower drop down.

d) Start Import


---
You should now have a DB that contains all the non-associative data and data associated with the company you specified in the ‘fetchData’ by company call.

## To import another company into this DB:
1. Run ‘fetchData by company’ : Make sure the ‘fecthData’ by company is called on the production DB (be very careful with changing the CONST value of DB).
2. Download and import into the new db.



