# Settings


## GET settings 

### HTTP Request

`GET https://apistore.csomni.com/settings`

## Get A Specific Site

```shell
curl --request GET \
  --url https://apistore.csomni.com/sites/ \
  --header 'token: [site_token]'
```
Note: The response includes 2 positions:
1. 'settings' is pulling the response from 'settings' table which 
saves each setting in a separate row. This table is being phased out, but its data is included here until
its data is dynamically transfered to settingsSite/settingsCompany on migration
2. 'settingsSite' is pulling the response from 'settingsSite' table which uses one row per siteToken
This will be the table for all site based enquiries
> The above command returns JSON structured like this:

```json
{
    "settings": [
        {
            "settingCategory": "SITE",
            "settingType": "baseUrl",
            "setting": "https://opticsforce.com"
        },
        {
            "settingCategory": "SITE",
            "settingType": "collectionUrl",
            "setting": "[BASE_URL]/collections/[COLLECTION_SLUG]"
        },
        {
            "settingCategory": "SITE",
            "settingType": "productUrl",
            "setting": "[BASE_URL]/products/[PRODUCT_SLUG]"
        },
        {
            "settingCategory": "SITE",
            "settingType": "variantUrl",
            "setting": "[BASE_URL]/products/[PRODUCT_SLUG]?variant=[VARIANT_TOKEN]"
        },
        {
            "settingCategory": "COMPANY",
            "settingType": "fs1GetToken",
            "setting": "123456"
        },
        {
            "settingCategory": "SITE",
            "settingType": "cartQuantityCombine",
            "setting": "1"
        },
        {
            "settingCategory": "SITE",
            "settingType": "googleSheetId",
            "setting": "1Jl81_123456"
        }
    ],
    "settingssite": {
        "settingToken": "stngSite_123456",
        "companyToken": "comp_123456",
        "siteToken": "site_123456",
        "baseUrl": "https://optics.evelt.dev/",
        "cartQuantityCombine": 1,
        "collectionUrl": "",
        "googleSheetId": "",
        "productUrl": "",
        "sendOrderEmail": 1,
        "sendWelcomeEmail": 0,
        "signupStatus": null,
        "smtpEmail": "",
        "smtpHost": "",
        "smtpPassword": "",
        "taxByState": 0,
        "taxOutOfState": "1",
        "taxRate": 8.75,
        "variantUrl": "",
        "deleted": 0,
        "dateCreated": "0000-00-00 00:00:00",
        "dateUpdated": "2022-11-20 22:08:55",
        "deleteSessionsRuleInDays": 40,
        "sendPendingAccountEmail": 0,
        "quotesEnabled": 1
    }
}
```
