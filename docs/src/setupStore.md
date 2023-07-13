# Setup Store

### This api is only available for use by an Evelt employee. This Api utilizes a different set of securities



## Setup a new store

This endpoint expects to receive site/company details and settings specifications. The database will be prepared for querying by this new store and return all relevant tokens that are required for the store front. There are 2 calls below that need to be triggered. Copy and paste them into postman, fill in the required details as explained below.

NOTE: This shippingSetting call must include a 'ups' and 'freeshipping' record. 'ups' record must include a working credential value. Note, all variants must have a weight of at least 1 to create label/check out and sites must have an address and phone number


### CALL 1: Company/site/settings

### HTTP Request

`POST https://apistore.csomni.com/V1.10/setupStore/`

### Headers
| Parameter   | Required | Unique | Description   | Default |
| security    | true     | false  | security token required, contact chayelle@evelt.com for details  |  none   |

### Query (Data) Parameters

| Parameter              | Required | Unique | Description                                                         | Default |
| ----------------       | -------- | ------ | ------------------------------------------------------------------- | ------- |
| company: companyName   | true     | true   | company name                                                        |         |
| company: companyEmail  | true     |true   | company email                                                        |         |
| company: companyPhone  | false    | false  | company phone number                                                |         |
| company: fs1Token      | false    | true   | fs1Token token                                                      |         |
| company: fs1GetToken   | false    | true   | fs1GetToken                                                         |         |
| company: cardknoxToken | false    | true   | cardnox token for payment purposes                                  |         |
| site: siteName         | true     | true   | Name for site - may be different to company name                    |         |
| site: Address1         | true     | false  | Registered address: first line                                      |         |
| site: Address2         | false    | false  | Registered address: second line                                     | US      |
| site: city             | true     | false  | Registered address: city                                            |         |
| site: state            | true     | false  | Registered address: state                                           |         |
| site: zipcode          | true     | false  | Registered address: zip code                                        |         |
| site: country          | true     | false  | Registered address: country (default is US)                         |         |
| site: logo             | false    | false  | Logo for site                                                       |         |
| site: phoneNumber      | true     | false  | Contact number for store                                            |         |
| site: lastOrderNumber  | true     | true   | The orderNumbers should start from this number. Each order will increase the number by 1    |         |
| user: name             | true     | false  | Name of specific user. More users may be added later                |         |
| user: password         | true     | false  | Password user will use for security specifically for Omni Admin     |         |
| user: role             | true     | false  | Role representing permissions allowed, default 3                    |         |
| user: email            | true     | true   | Email address for user - is used for signing into Omni Admin account|         |
| user: phone             | false    | false  | Users contact number                                               |         |
| additCompInfo: resetLink | false | false  | Link for the reset password Store webpage. Sent to customer to reset their account password |null
| additCompInfo: supportEmailAddress | false | false  | Email address for support |null
| additCompInfo: salesEmailAddress   | false  | false  | Email for sales dept.                                     | null    |
| settings: baseUrl                  | true   | false  | Base url for store                                        | null    |
| settings: cartQuantityCombine      | true   | false  | Bool, when guest cart combines with signed in cart. ie should the products in the guest cart be added to the signed in cart when a person signs in in the middle of a session                        |         |
| settings: collectionUrl            | true  | false  | CollectionUrl                                              | Null    |
| settings: googleSheetId            | true  | false  | Google sheet id                                            | Null    |
| settings: productUrl               | true  | false  | ProductUrl                                                 | Null    |
| settings: sendOrderEmail           | true  | false  | Bool - send order email                                    | 0       |
| settings: sendWelcomeEmail         | true  | false  | Bool - send welcome email when customer signs up to store  | 0       |
| settings: signupStatus             | true  | false  | Signup status                                              | Null    |
| settings: smtpEmail                | true  | false  | smtpEmail                                                  | NN      |
| settings: smtpHost                 | true  | false  | smtpHost                                                   | NN      |
| settings: smtpPassword             | true  | false  | smtpPassword                                               | NN      |
| settings: taxByState               | true  | false  | Bool - if tax by state feature is on or off                | 0       |
| settings: taxOutOfState            | true  | false  | Bool - tax out of state                                    | 0       |
| settings: taxRate                  | true  | false  | State tax if 'taxOutOfState' is set to true                | 0       |
| settings: variantUrl               | true  | false  | variant url                                                |         |
| settings: deleteSessionsRuleInDays | true  | false  | Custom delete sessions amount in days eg 10                | 30      |

## Example 

```shell
curl --location --request POST 'https://apistore.csomni.com/V1.10/setupStore/' \
--header 'Content-Type: application/json' \
--header 'securty: [contact chayelle@evelt.com]'

--data-raw '{
    "company": {
        "companyName": "This is the company name 338index",
        "companyEmail": "123456@gmail.com",
        "companyPhone": "1234567890",
        "fs1Token": "",
        "fs1GetToken": "",
        "cardknoxToken": "123456"
    },
    "site": {
        "siteName": "Tyrell Corp",
        "address1": "",
        "address2": "",
        "city": "",
        "state": "",
        "zipCode": "",
        "country": "",
        "logo": "",
        "phoneNumber": ""
    },
    "user": {
        "name": "Sarah Jones",
        "password": "passwordForUser",
        "role": 3,
        "email": "sjones1@gmail.com",
        "phone": ""
    },
    "additCompInfo": {
        "resetLink": "",
        "supportEmailAddress": "",
        "salesEmailAddress": "",
    },
    "settings": {
        "baseUrl": "",
        "cartQuantityCombine": 1,
        "collectionUrl": "",
        "googleSheetId": "",
        "productUrl": "",
        "sendOrderEmail": 1,
        "sendWelcomeEmail": 1,
        "signupStatus": "",
        "smtpEmail": "",
        "smtpHost": "",
        "smtpPassword": "",
        "taxByState": 1,
        "taxOutOfState": "",
        "taxRate": 0.8,
        "variantUrl": "",
        "deleteSessionsRuleInDays": 40
    }
}'
```

> The above command returns JSON structured like this
```json
    "company": {
        "companyName": "This is the company name 672copy",
        "companyEmail": "123456@hotmail.com",
        "companyPhone": "1234567890",
        "fs1Token": "",
        "fs1GetToken": "",
        "cardknoxToken": "123456",
        "companyToken": "comp_123456"
    },
    "site": {
        "siteName": "Tyrell Corp",
        "address1": "",
        "address2": "",
        "city": "",
        "state": "",
        "zipCode": "",
        "country": "",
        "logo": "",
        "phoneNumber": "",
        "lastOrderNumber": 1004534,
        "companyToken": "comp_123456",
        "siteToken": "site_123456"
    },
    "user": {
        "name": "Sarah Jones",
        "password": "passwordForUser",
        "role": 3,
        "email": "sjones1@gmail.com",
        "phone": "",
        "companyToken": "comp_123456",
        "siteToken": "site_123456",
        "userToken": "user_123456"
    },
    "additionalCompanyInfo": {
        "resetLink": "",
        "supportEmailAddress": "",
        "salesEmailAddress": "",
        "companyToken": "comp_123456",
        "siteToken": "site_123456"
    },
    "settings": {
        "company": {
            "fs1GetToken": "",
            "companyToken": "comp_123456",
            "siteToken": "site_123456",
            "companySettingToken": "stngComp_123456"
        },
        "site": {
            "baseUrl": "",
            "cartQuantityCombine": 1,
            "collectionUrl": "",
            "googleSheetId": "",
            "productUrl": "",
            "sendOrderEmail": 1,
            "sendWelcomeEmail": 1,
            "signupStatus": "",
            "smtpEmail": "",
            "smtpHost": "",
            "smtpPassword": "",
            "taxByState": 1,
            "taxOutOfState": "",
            "taxRate": 0.8,
            "variantUrl": "",
            "deleteSessionsRuleInDays": 40,
            "companyToken": "comp_123456",
            "siteToken": "site_123456",
            "settingsSiteToken": "stngSite_123456"
        }
    }
```

## Get all tokens/details by site token

This endpoint will return all tokens associated to the site token required.

### HTTP Request

`GET https://apistore.csomni.com/V1.10/setupStore`


```shell
curl --request GET \
  --url https://apistore.csomni.com/V1.10/setupStore \
  --header 'token: site_123456'
  --header 'security: [contact chayelle@evelt.com]'
```

> The above command returns JSON structured like this:

```json
    "site": {
        "id": 3,
        "siteToken": "site_123456",
        "companyToken": "comp_123456",
        "siteName": "123456.com",
        "archived": 0,
        "address1": "57 Bewick Road",
        "address2": "Apt. 4",
        "city": "Brooklyn",
        "state": "NY",
        "zipCode": "11206",
        "country": "US",
        "logo": "https://opticsforce.com/img/logo%20(3).png",
        "phoneNumber": "",
        "lastOrderNumber": 1004534,
        "createdAt": "2021-12-15 13:23:53",
        "editedAt": "2022-06-23 11:02:28"
    },
    "company": {
        "id": 2,
        "companyToken": "comp_123456",
        "companyEmail": "",
        "companyPhone": "",
        "comapnyName": "Tyrell Corp",
        "companyDomain": "",
        "fs1Token": "123456",
        "fs1GetToken": "123456",
        "urlIdentifier": "",
        "orderNumber": 0,
        "stripeTokenSecret": "",
        "stripeTokenPublic": "",
        "cardknoxToken": "123456",
        "dateCreated": "",
        "archived": 0,
        "createdAt": "2021-12-15 13:23:49",
        "editedAt": "2021-12-15 13:23:49"
    },
    "user": [
        {
            "id": 151,
            "userToken": "usr_123456",
            "companyToken": "comp_123456",
            "name": "Sarah Jones",
            "email": "sjones1@gmail.com",
            "phone": "1234567890",
            "role": 1,
            "createdOn": "1505148766",
            "lastLogin": "1657789823",
            "createdAt": "2021-12-15 13:23:54",
            "editedAt": "2022-07-14 09:10:23"
        },
        {
            "id": 163,
            "userToken": "user_123456",
            "companyToken": "comp_123456",
            "name": "",
            "email": "123456@gmail.com",
            "phone": "",
            "role": 1,
            "createdOn": "1641334157",
            "lastLogin": "1658091001",
            "createdAt": "2022-01-04 22:09:17",
            "editedAt": "2022-07-17 20:50:01"
        },
        {
            "id": 164,
            "userToken": "user_123456",
            "companyToken": "comp_123456",
            "name": "",
            "email": "sjones1@gmail.com",
            "phone": "",
            "role": 1,
            "createdOn": "1653599015",
            "lastLogin": "1653599162",
            "createdAt": "2022-05-26 21:03:35",
            "editedAt": "2022-05-26 21:06:02"
        },
        {
            "id": 188,
            "userToken": "user_123456",
            "companyToken": "comp_123456",
            "name": "",
            "email": "sjones1@gmail.com",
            "phone": "",
            "role": 0,
            "createdOn": "1657487951",
            "lastLogin": "",
            "createdAt": "2022-07-10 21:19:11",
            "editedAt": "2022-07-10 21:19:11"
        },
        {
            "id": 187,
            "userToken": "user_123456",
            "companyToken": "comp_123456",
            "name": "",
            "email": "sjones1@gmail.com",
            "phone": "",
            "role": 0,
            "createdOn": "1657487252",
            "lastLogin": "",
            "createdAt": "2022-07-10 21:07:32",
            "editedAt": "2022-07-10 21:17:59"
        },
        {
            "id": 184,
            "userToken": "user_123456",
            "companyToken": "comp_123456",
            "name": "",
            "email": "sjones1@gmail.com",
            "phone": "",
            "role": 0,
            "createdOn": "1657486361",
            "lastLogin": "1657486558",
            "createdAt": "2022-07-10 20:52:41",
            "editedAt": "2022-07-10 20:55:58"
        },
        {
            "id": 183,
            "userToken": "user_123456",
            "companyToken": "comp_123456",
            "name": "",
            "email": "sjones1@gmail.com",
            "phone": "",
            "role": 0,
            "createdOn": "1657486244",
            "lastLogin": "",
            "createdAt": "2022-07-10 20:50:44",
            "editedAt": "2022-07-10 20:50:44"
        }
    ],
    "settings": {
        "companySettings": {
            "settingToken": "stngComp_123456",
            "companyToken": "comp_123456",
            "siteToken": "site_123456",
            "fs1GetToken": "987",
            "deleted": 0,
            "dateCreated": "2022-07-17 20:27:26",
            "dateUpdated": "2022-07-17 20:27:27"
        },
        "siteSettings": {
            "settingToken": "stng_123456",
            "companyToken": "comp_123456",
            "siteToken": "site_123456",
            "baseUrl": null,
            "cartQuantityCombine": null,
            "collectionUrl": null,
            "googleSheetId": null,
            "productUrl": null,
            "sendOrderEmail": null,
            "sendWelcomeEmail": 1,
            "signupStatus": null,
            "smtpEmail": null,
            "smtpHost": null,
            "smtpPassword": null,
            "taxByState": 0,
            "taxOutOfState": null,
            "taxRate": null,
            "variantUrl": null,
            "deleted": 0,
            "dateCreated": "2022-06-21 09:25:50",
            "dateUpdated": "2022-06-21 09:25:50",
            "deleteSessionsRuleInDays": 0
        }
    }
```


### CALL 2: shipping setup:
### HTTP Request

`POST https://apistore.csomni.com/V1.10/shippingmethods/`

### Query (Data) Parameters

| Parameter              | Required | Unique | Description                                                         | Default |
| ----------------       | -------- | ------ | ------------------------------------------------------------------- | ------- |
| methodId               | true     | true   | the name the method is reffered to in the cod                       |         |
| zoneStates : US        | false    | false  | Specify which state zones are included in this shipping options (leave empty if all states are incl)                                                                                                   |         |
| zoneZipCodes           | false     |false   | Specify which zipcode zones are included in this shipping options (leave empty if all zips are incl)                                                                                                 |         |
| minOrder               | false    | false  | If a minimun order is required, specify as a number                 |   0     |
| stopIfAvail            | false    | false  | not sure!                                                           |    0    |
| active                 | false    | false  | Specify that shipping method is active or not                       |     0   |
| activeInAdmin          | false    | false  | Specify that shipping method is active in the admin panel for user to choose to create a label with                                                                                                |    0    |
| markup                 | false    | false  | a set value that all orders choosing this shipping method will increase the total to pay by                                                                                                             |    0    |
| markupType             | true if markup is specified    | false  | 'fixed' or 'percent'                          |         |
| maxOrder               | false    | false  | Specify a value until which this shipping option can be usednumber  |         |
| zoneRadius : pointer, radius, radiousUnit | false  | false  |                                                    |         |

## Example 

```shell
curl --location --request POST 'https://apistore.csomni.com/V1.10/shippingmethods/' \
--header 'token: user_123456' \
--header 'Content-Type: application/json' \
--data-raw '{
    "ups": {
        "methodId": "ups",
        "zoneStates": [],
        "zoneZipCodes": [],
        "minOrder": 0,
        "stopIfAvail": true,
        "sortOrder": 1,
        "active": true,
        "activeInAdmin": true,
        "markup": 5,
        "markupType": "percent",
        "zoneRadius": [
            {
                "pointer": "11",
                "radius": "12",
                "radiusUnit": "m"
            }
        ],
        "credentials": {
            "key": "123456",
            "account": "123456",
            "username": "SarahJones",
            "password": "#####"
        }
    },
    "freeshipping": {
        "methodId": "freeshipping",
        "zoneStates": [
            {
                "US": [
                    "AL",
                    "WY",
                    "WI",
                    "WV",
                    "WA",
                    "VA",
                    "VI",
                    "VT",
                    "UT",
                    "TX",
                    "TN",
                    "SD",
                    "SC",
                    "RI",
                    "PA",
                    "OR",
                    "OK",
                    "OH",
                    "ND",
                    "NC",
                    "NY",
                    "NM",
                    "NJ",
                    "NH",
                    "NV",
                    "NE",
                    "MT",
                    "MO",
                    "MS",
                    "MN",
                    "MI",
                    "MA",
                    "MD",
                    "ME",
                    "LA",
                    "KY",
                    "KS",
                    "IA",
                    "IN",
                    "IL",
                    "ID",
                    "GA",
                    "FL",
                    "DC",
                    "DE",
                    "CT",
                    "CO",
                    "CA",
                    "AR",
                    "AZ"
                ]
            }
        ],
        "zoneZipCodes": [],
        "minOrder": 0,
        "stopIfAvail": true,
        "sortOrder": 1,
        "active": true,
        "activeInAdmin": true,
        "markup": 0,
        "markupType": "",
        "zoneRadius": [
            
        ]
    }
}'
```

> The above command returns JSON structured like this
```json
   {
    "ups": {
        "methodId": "ups",
        "zoneStates": [],
        "zoneZipCodes": [],
        "minOrder": 0,
        "stopIfAvail": true,
        "sortOrder": 1,
        "active": true,
        "activeInAdmin": true,
        "markup": 5,
        "markupType": "percent",
        "zoneRadius": [
            {
                "pointer": "11",
                "radius": "12",
                "radiusUnit": "m"
            }
        ],
        "credentials": {
            "key": "123456",
            "account": "123456",
            "username": "SarahJones",
            "password": "#####"
        }
    },
    "freeshipping": {
        "methodId": "freeshipping",
        "zoneStates": [
            {
                "US": [
                    "AL",
                    "WY",
                    "WI",
                    "WV",
                    "WA",
                    "VA",
                    "VI",
                    "VT",
                    "UT",
                    "TX",
                    "TN",
                    "SD",
                    "SC",
                    "RI",
                    "PA",
                    "OR",
                    "OK",
                    "OH",
                    "ND",
                    "NC",
                    "NY",
                    "NM",
                    "NJ",
                    "NH",
                    "NV",
                    "NE",
                    "MT",
                    "MO",
                    "MS",
                    "MN",
                    "MI",
                    "MA",
                    "MD",
                    "ME",
                    "LA",
                    "KY",
                    "KS",
                    "IA",
                    "IN",
                    "IL",
                    "ID",
                    "GA",
                    "FL",
                    "DC",
                    "DE",
                    "CT",
                    "CO",
                    "CA",
                    "AR",
                    "AZ"
                ]
            }
        ],
        "zoneZipCodes": [],
        "minOrder": 0,
        "stopIfAvail": true,
        "sortOrder": 1,
        "active": true,
        "activeInAdmin": true,
        "markup": 0,
        "markupType": "",
        "zoneRadius": []
    }
}
```
## Edit SetupStore data

### HTTP Request

`PUT https://apistore.csomni.com/V1.10/setupStore/[companyToken]`

### Headers
| Parameter   | Required | Unique | Description                                                      | Default |
| security    | true     | false  | security token required, contact chayelle@evelt.com for details  |  none   |
| token       | true     | true   | site token required                                              |  none   |
| userToken   | true     | true   | userToken                                                        |  none   |

### Query (Data) Parameters

| Parameter              | Required | Unique | Description                                                         | Default |
| ----------------       | -------- | ------ | ------------------------------------------------------------------- | ------- |
| company: companyName   | true     | true   | company name                                                        |         |
| company: companyEmail  | true     |true   | company email                                                        |         |
| company: companyPhone  | false    | false  | company phone number                                                |         |
| company: fs1Token      | false    | true   | fs1Token token                                                      |         |
| company: fs1GetToken   | false    | true   | fs1GetToken                                                         |         |
| company: cardknoxToken | false    | true   | cardnox token for payment purposes                                  |         |
| site: siteName         | true     | true   | Name for site - may be different to company name                    |         |
| site: Address1         | true     | false  | Registered address: first line                                      |         |
| site: Address2         | false    | false  | Registered address: second line                                     | US      |
| site: city             | true     | false  | Registered address: city                                            |         |
| site: state            | true     | false  | Registered address: state                                           |         |
| site: zipcode          | true     | false  | Registered address: zip code                                        |         |
| site: country          | true     | false  | Registered address: country (default is US)                         |         |
| site: logo             | false    | false  | Logo for site                                                       |         |
| site: phoneNumber      | true     | false  | Contact number for store                                            |         |
| site: lastOrderNumber  | true     | false  | lastOrderNumber to be used                                          |         |
| user: name             | true     | false  | Name of specific user. More users may be added later                |         |
| user: password         | true     | false  | Password user will use for security specifically for Omni Admin     |         |
| user: role             | true     | false  | Role representing permissions allowed, default 3                    |         |
| user: email            | true     | true   | Email address for user - is used for signing into Omni Admin account|         |
| user: phone             | false    | false  | Users contact number                                               |         |
| additCompInfo: resetLink | false | false  | Link for the reset password Store webpage. Sent to customer to reset their account password |null
| additCompInfo: supportEmailAddress | false | false  | Email address for support |null
| additCompInfo: salesEmailAddress   | false  | false  | Email for sales dept.                                     | null    |
| settings: baseUrl                  | true   | false  | Base url for store                                        | null    |
| settings: cartQuantityCombine      | true   | false  | Bool, when guest cart combines with signed in cart. ie should the products in the guest cart be added to the signed in cart when a person signs in in the middle of a session                        |         |
| settings: collectionUrl            | true  | false  | CollectionUrl                                              | Null    |
| settings: googleSheetId            | true  | false  | Google sheet id                                            | Null    |
| settings: productUrl               | true  | false  | ProductUrl                                                 | Null    |
| settings: sendOrderEmail           | true  | false  | Bool - send order email                                    | 0       |
| settings: sendWelcomeEmail         | true  | false  | Bool - send welcome email when customer signs up to store  | 0       |
| settings: signupStatus             | true  | false  | Signup status                                              | Null    |
| settings: smtpEmail                | true  | false  | smtpEmail                                                  | NN      |
| settings: smtpHost                 | true  | false  | smtpHost                                                   | NN      |
| settings: smtpPassword             | true  | false  | smtpPassword                                               | NN      |
| settings: taxByState               | true  | false  | Bool - if tax by state feature is on or off                | 0       |
| settings: taxOutOfState            | true  | false  | Bool - tax out of state                                    | 0       |
| settings: taxRate                  | true  | false  | State tax if 'taxOutOfState' is set to true                | 0       |
| settings: variantUrl               | true  | false  | variant url                                                |         |
| settings: deleteSessionsRuleInDays | true  | false  | Custom delete sessions amount in days eg 10                | 30      |

## Example 
### Includes only a few possible editable fields. Note: See above table for more fields that may be edited through the below example

```shell
    curl --location --request PUT 'https://apistore.csomni.com/V1.10/setupStore/comp_123456' \
--header 'security: [contact evelt]' \
--header 'token: site_123456' \
--header 'userToken: user_123456' \
--header 'Content-Type: application/json' \
--data-raw '{
    "company": {
        "companyName": "Edited Company Name",
        "fs1GetToken": "jjj"
    },
    "site": {
        "siteName": "Edited Site Name",
        "lastOrderNumbe": 99
    },
    "user" : {
        "password": "jkl",
        "name": "updated"
    },
    "additCompInfo": {
        "resetLink": "123"
     },
     "settings": {
        "deleteSessionsRuleInDays": 10
    }
}'
```

The above example returns a json object that looks like this:

```json
{
    "company": {
        "id": 127,
        "companyToken": "comp_123456",
        "companyEmail": "123456@yahoo.com",
        "companyPhone": "1234567890",
        "comapnyName": "edited company name",
        "companyDomain": "",
        "fs1Token": "ABCDEFGH",
        "fs1GetToken": "jjj",
        "urlIdentifier": "",
        "orderNumber": 0,
        "stripeTokenSecret": "",
        "stripeTokenPublic": "",
        "cardknoxToken": "",
        "dateCreated": "",
        "archived": 0,
        "createdAt": "2022-09-11 11:36:46",
        "editedAt": "2022-09-11 22:13:43"
    },
    "site": {
        "id": 99,
        "siteToken": "site_123456",
        "companyToken": "comp_123456",
        "siteName": "edited site name",
        "archived": 0,
        "address1": "",
        "address2": "",
        "city": "",
        "state": "",
        "zipCode": "",
        "country": "",
        "logo": "",
        "phoneNumber": "",
        "lastOrderNumber": 99,
        "createdAt": "2022-09-11 11:36:46",
        "editedAt": "2022-09-11 21:19:07"
    },
    "user": {
        "id": 246,
        "userToken": "user_123456",
        "companyToken": "comp_123456",
        "name": "updated",
        "email": "123456@hotmail.com",
        "phone": "",
        "password": "jkl",
        "role": 3,
        "createdOn": "",
        "lastLogin": "",
        "archived": 0,
        "createdAt": "2022-09-11 11:36:46",
        "editedAt": "2022-09-11 22:53:03"
    },
    "additionalCompanyInfo": null,
    "settings": {
        "settingsSite": {
            "settingToken": "stngSite_123456",
            "companyToken": "comp_123456",
            "siteToken": "site_123456",
            "baseUrl": "",
            "cartQuantityCombine": 1,
            "collectionUrl": "",
            "googleSheetId": "",
            "productUrl": "",
            "sendOrderEmail": 1,
            "sendWelcomeEmail": 1,
            "signupStatus": "",
            "smtpEmail": "",
            "smtpHost": "",
            "smtpPassword": "",
            "taxByState": 1,
            "taxOutOfState": "",
            "taxRate": 0.8,
            "variantUrl": "",
            "deleted": 0,
            "dateCreated": "2022-09-11 11:36:46",
            "dateUpdated": "2022-09-11 22:26:31",
            "deleteSessionsRuleInDays": 10
        },
        "company": null
    }
} 
```

