# QUOTES
## Feature explained:
1. Customer submits 'Create quote' containing quote details - variants, quantities, shipping address, contact details etc
2. Admin views quote and adds shipping options
3. Customer views quote, chooses a shipping method and Saves quote
Pricing: 
1. A quote has pricing related to the variants, the shipping choice and the tax for both variants and shipping charges.
2. Tables 'quotes' and 'quoteVariant' both store pricing details. See the table below to explain the use of each type

## Quotes Status's options:

| Status Types        |
| ---------           |
| quoted              | 
| adminDeclined       |
| cancelledByCustomer |
| waiting-response    |
| approvedByCustomer  |



### TABLE: variantQuotes 
(not complete list of table - more is shown in further down this page as updates to quote are made)

| column name   | Description                               | Default
| -----------   | -------------------------------           | --------- |
| quoteToken    | Quotes unique id                          |           |
| variantToken  | Variant to be quoted                      |           |
| quantity      | Quantity of variantToken required         |           |
| itemPrice     | Individual Single variant price           | 0         |
| itemTax       | Tax calculated according to the Sites tax settings for this individual single variant   | NULL   |
| lineTotal     | Adds together columns 'itemPrice' and 'itemTax', then multiplies by column 'quantity'     |  NULL  |
   
### TABLE: QUOTES 
(not complete list of table)

| column name   | Description                               | Value set 
| -----------   | -------------------------------           | --------- |
| quoteToken    | Quotes unique id                     |      When quote is created     |
| variantsTotal | Adds 'itemPrice * quantity' from every record in table 'quoteVariants' saved against the above variant Token. Does NOT include the tax for the variant      |     When quote is created      |
| shippingTotal | Set according to the shipping choice chosen by customer. Does NOT include the tax due against the shipping charge           | When customer confirms shipping option         |
| taxTotal      | Adds 'itemTax * quantity' from every record in table 'quoteVariants' saved against the above quoteToken. It then adds the shipping tax for the final value.   | When customer confirms shipping option   |
| combinedTotal | Adds together above columns 'variantsTotal' and 'shippingTotal' and 'taxTotal' to provide the final 'combinedTotal' column     |  When customer confirms shipping option  |
   



## Create a quote by customer

### HTTP Request

`POST https://apistore.csomni.com/quotes`

### Data Parameters

| Parameter   | Description                     | Required
| ----------- | ------------------------------- | ------------------------------- |
| quoteItems | Object of variants within quote | true |
| quoteItems: variantToken | variantToken of product. |true |
| quoteItems: quantity | Quantity of product |true |
| shippingAddress | address token associated with customer |true |
| contactDetails: Name | receiver contact name |true |
| contactDetails: Email | receiver contact email |true |
| contactDetails: Phone | receiver contact phone |true |
| contactDetails: Company | areceiver contact company |false |


```shell
curl --request POST \
  --url https://apistore.csomni.com/quotes \
  --header 'token: site_Token'
  --header 'customerToken: cs_123456' \
  --data '{
        "quoteItems": [
               {
                   "variantToken" : "vrnt_123456",
                   "quantity" : 2
               },
               {
                   "variantToken" : "vrnt_123456",
                   "quantity" : 1
               }
           ],
           "shippingAddress" : "adrs_123456",
           "contactDetails" : {
               "firstName" : "Sarah",
               "lastName" : "Jones",
               "email" : "sjones@gmail.com",
               "phoneNumber" : "987657489",
               "companyName" : "Tyrell Corp"
           }
}'
```

Response:

```json
{
    "quoteToken": "quote_123456",
    "customerToken": "cs_123456",
    "companyToken": "comp_123456",
    "quoteFiles": "",
    "status": "waiting-response",
    "deleted": 0,
    "dateCreated": "2023-01-03 12:53:02",
    "dateUpdated": "2023-01-03 11:53:02",
    "variantsTotal": 360.39,
    "shippingTotal": 0,
    "taxTotal": 0,
    "combinedTotal": null,
 "quoteNumber": 50004,
    "variantDetails": [
        {
            "quote_variantsToken": "quoteVariant_123456",
            "variantToken": "vrnt_123456",
            "quantity": 2,
            "itemPrice": 0.2,
            "itemTax": 0.02,
            "lineTotal": 0.44,
            "fullDetails": {
                "prodToken": "prod_123456",
                "variantToken": "vrnt_123456",
                "companyToken": "comp_123456",
                "variantName": "Vortex Optics Kaibab 18x56 HD Binocular",
                "variantImage": {
                    "file": "6-27-2018/1530121117199__32308__5618.jpg"
                },
                "variantImages": [
                    {
                        "file": "6-27-2018/1530121126552__29522__56181.jpg",
                        "name": "56181"
                    },
                    {
                        "file": "6-27-2018/1530121135284__30461__56182.jpg",
                        "name": "56182"
                    },
                    {
                        "file": "6-27-2018/1530121143009__29290__56183.jpg",
                        "name": "56183"
                    }
                ],
                "variantWeight": "4.4",
                "variantDimW": "8",
                "variantDimL": "4.25",
                "variantDimH": "13",
                "variantUpc": "8.76E+11",
                "variantNumber": "KAI-5618",
                "manufacturerPartNumber": "",
                "variantPrice": 0.2,
                "variantMapPrice": 0,
                "variantMsrpPrice": 0,
                "variantDisplayPrice": 0,
                "variantDescription": "KAIBAB® HD 18X56 BINOCULAR\nThe Kaibab HD 18x56 is the ultimate long-distance western-hunting binocular series. When serious patience and superior optics are required to locate trophy animals at extreme distances, the Kaibab HD delivers the premium-quality, high-magnification optical performance you need to get the job done. Intended to be used with a tripod for extended, comfortable, rock-steady viewing. Ultracomfortable twist-up eyecups are perfect for long glassing sessions. Visually tear apart open landscapes in pursuit of tough-to-locate trophy big game with the Kaibab HD.\n\n\n\nVIP Warranty HD Premium APO XRPlus Coatings ArmorTek Argon Purged Waterproof\nMagnification\t18 x\nObjective Lens Diameter\t56 mm\nEye Relief\t16.4 mm\nExit Pupil\t3.1 mm\nLinear Field of View\t194 feet/1000 yards\nClose Focus\t23 feet\nInterpupillary Distance\t60-76 mm\nHeight\t7.7 inches\nWidth\t5.7 inches\nWeight\t43.5 ounces",
                "variantAlert": "",
                "variantLowlevel": "",
                "variantSlug": "vortex-optics-kaibab-18x56-hd-binocular",
                "variantVisible": 1,
                "taxType": "",
                "hideGoogleData": 0,
                "google_variantCategory": null,
                "google_variantType": null,
                "google_variantCondition": null,
                "taxable": 1,
                "variantAllowCheckout": 0,
                "variantCheckInvetory": 0,
                "variantTrackInventory": 0,
                "inventoryCount": -18,
                "shippingProduct": 1,
                "variantMetaTitle": "",
                "variantMetaDescription": "",
                "variantBrand": "",
                "sortOrder": 0,
                "dateCreated": "",
                "deleted": 0,
                "backOrderWarning": 0,
                "createdAt": "2021-12-15 13:23:54",
                "editedAt": "2023-01-03 11:08:21",
                "variantInStock": true
            }
        },
        {
            "quote_variantsToken": "quoteVariant_123456",
            "variantToken": "vrnt_123456",
            "quantity": 1,
            "itemPrice": 359.99,
            "itemTax": 32.4,
            "lineTotal": 392.39,
            "fullDetails": {
                "prodToken": "prod_123456",
                "variantToken": "vrnt_123456",
                "companyToken": "comp_123456",
                "variantName": "Vortex Optics Diamondback HP 4-16x42  BDC Riflescopes",
                "variantImage": {
                    "file": "6-27-2018/1530121344004__33909__10019.jpg"
                },
                "variantImages": [
                    {
                        "file": "6-27-2018/1530121353525__35090__100191.jpg",
                        "name": "100191"
                    },
                    {
                        "file": "6-27-2018/1530121379690__53555__100192.jpg",
                        "name": "100192"
                    },
                    {
                        "file": "6-27-2018/1530121387810__31428__100193.jpg",
                        "name": "100193"
                    }
                ],
                "variantWeight": "2.05",
                "variantDimW": "3.25",
                "variantDimL": "5",
                "variantDimH": "16.75",
                "variantUpc": "8.76E+11",
                "variantNumber": "DBK-10019",
                "manufacturerPartNumber": "",
                "variantPrice": 359.99,
                "variantMapPrice": 0,
                "variantMsrpPrice": 0,
                "variantDisplayPrice": 0,
                "variantDescription": "Build Your Own Custom Turret\nDIAMONDBACK® HP 4-16X42 RIFLESCOPE\nThe Diamondback® HP (High Performance) riflescope offers a full-on array of features that discerning hunters are sure to appreciate. Optically, these scopes hit the proverbial mark. XD extra-low dispersion glass increases resolution and color fidelity while XR fully multi-coated lenses maximize every minute of shooting light. The side focus/parallax adjustment is easily accessible while keeping a trim profile and allowing optimal mounting height. And, with a 4x zoom range, the Diamondback® HP offers highly versatile magnification.\n\nDual use for Shooting Tactical / Hunting\n\n\n\nVIP Warranty XD Lens Elements XR Coatings Argon Purged Waterproof\nMagnification\t4-16 x\nObjective Lens Diameter\t42 mm\nEye Relief\t4.0 inches\nField of View\t23.8-6.1 feet/100 yards\nTube Size\t1-inch\nTurret Style\tCapped\nAdjustment Graduation\t1/4 MOA\nTravel per Rotation\t15 MOA\nMax Elevation Adjustment\t80 MOA\nMax Windage Adjustment\t80 MOA\nParallax Setting\t30 yards to infinity\nLength\t12.5 inches\nWeight\t18 ounces\nOptically, these scopes deliver unparalleled image quality. Our proprietary ALO automated laser optical alignment process forges a new paradigm in the sport optics industry, resulting in the most forgiving, comfortable, and highest quality images possible. The APO objective lens system uses index-matched lenses to correct color across the entire visual spectrum. HD premium extra-low dispersion glass delivers the ultimate in resolution and color fidelity, resulting in High Definition images. XR™ Plus premium fully multi-coated lenses increase light transmission for optimum brightness. ArmorTek® protects exterior lenses from scratches, oil and dirt.\n\n\nDual use for Shooting Tactical / Hunting • UA Patent 7,937,879, US Patent 7,958,665, US Patent 8,166,696 B2\n\n\nVIP Warranty HD Premium APO XRPlus Coatings ArmorTek Argon Purged Waterproof\nMagnification\t6-24 x\nObjective Lens Diameter\t50 mm\nEye Relief\t3.6 inches\nField of View\t20.4-5.1 feet/100 yards\nTube Size\t30 mm\nTurret Style\tL-Tec\nAdjustment Graduation\t0.1\nTravel per Rotation\t10 MRAD\nMax Elevation Adjustment\t27.5 MRAD (See Features Tab)\nMax Windage Adjustment\t10 MRAD (See Features Tab)\nParallax Setting\t25 to Infinity\nLength\t15.2 inches\nWeight\t28.8 oz",
                "variantAlert": "",
                "variantLowlevel": "",
                "variantSlug": "diamondback-hp-4-16x42-bdc-riflescopes",
                "variantVisible": 1,
                "taxType": "",
                "hideGoogleData": 0,
                "google_variantCategory": null,
                "google_variantType": null,
                "google_variantCondition": null,
                "taxable": 1,
                "variantAllowCheckout": 0,
                "variantCheckInvetory": 0,
                "variantTrackInventory": 0,
                "inventoryCount": -9,
                "shippingProduct": 1,
                "variantMetaTitle": "",
                "variantMetaDescription": "",
                "variantBrand": "",
                "sortOrder": 0,
                "dateCreated": "",
                "deleted": 0,
                "backOrderWarning": 0,
                "createdAt": "2021-12-15 13:23:54",
                "editedAt": "2023-01-03 11:08:21",
                "variantInStock": true
            }
        }
    ],
    "shippingAddress": {
        "addressToken": "adrs_123456",
        "addressLabel": "",
        "address": "12354 Main Street",
        "address2": "",
        "addressCity": "Monsey",
        "addressState": "NY",
        "addressZip": "10952",
        "addressFirstName": "Sarah",
        "addressLastName": "Jones",
        "phoneNumber": "",
        "mobileNumber": "",
        "addressCountry": "United States",
        "addressDefault": 0,
        "customerToken": "cust_123456",
        "createdAt": "2023-01-03 11:30:56",
        "editedAt": "2023-01-03 11:30:56",
        "specialValues": []
    },
    "contactDetails": {
        "quote_ContactToken": "quoteContact_123456",
        "firstName": "Sarah",
        "lastName": "Jones",123456
        "email": "sjones1@gmail.com",
        "phoneNumber": "987657489",
        "companyName": "Tyrell Corp"
    },
    "shippingQuote": []
}
```

## Choose a shipping option and approve a quote

### HTTP Request

`POST https://apistore.csomni.com/quotes/[shippingQuotesToken]/approve-shipping `

### Data Parameters

| Parameter   | Description                     | Required
| ----------- | ------------------------------- | ------------------------------- |
| approved    | bool true/false. default null   | true                            |
| approvedBy  | Name of person approving        | true                            |

```shell
curl --request POST \
  --url https://apistore.csomni.com/quotes/[shippingQuotesToken]/approve-shipping \
  --header 'token: site_Token'
  --header 'customerToken: cs_123456' \
  --data '{
        "approved": true,
        "approvedBy": "[name]"
        }'
```

Response:

```json
{
    "quote": "quote_123456",
    "shipQuote": "shippingQuoteToken_123456",
    "approved": true
}
```

## Get All Quotes by Customer

### HTTP Request

`GET https://apistore.csomni.com/quotes`

```shell
curl --request GET \
  --url https://apistore.csomni.com/quotes \
  --header 'token: 123'
  --header 'customerToken: cs_123456' \
```

Response:

```json
[
    {
        "quoteToken": "quote_123456",
        "customerToken": "cs_123456",
        "companyToken": "comp_123456",
        "quoteFiles": "",
        "status": "waiting-response",
        "deleted": 0,
        "dateCreated": "2023-01-03 12:38:09",
        "dateUpdated": "2023-01-03 11:38:09",
        "variantsTotal": 360.39,
        "shippingTotal": 0,
        "taxTotal": 0,
        "combinedTotal": null,
"quoteNumber": 50005,
        "variantDetails": [
            {
                "quote_variantsToken": "quoteVariant_123456",
                "variantToken": "vrnt_123456",
                "quantity": 2,
                "itemPrice": 0.2,
                "itemTax": 0.02,
                "lineTotal": 0.44,
                "fullDetails": {
                    "prodToken": "prod_123456",
                    "variantToken": "vrnt_123456",
                    "companyToken": "comp_123456",
                    "variantName": "Vortex Optics Kaibab 18x56 HD Binocular",
                    "variantImage": {
                        "file": "6-27-2018/1530121117199__32308__5618.jpg"
                    },
                    "variantImages": [
                        {
                            "file": "6-27-2018/1530121126552__29522__56181.jpg",
                            "name": "56181"
                        },
                        {
                            "file": "6-27-2018/1530121135284__30461__56182.jpg",
                            "name": "56182"
                        },
                        {
                            "file": "6-27-2018/1530121143009__29290__56183.jpg",
                            "name": "56183"
                        }
                    ],
                    "variantWeight": "4.4",
                    "variantDimW": "8",
                    "variantDimL": "4.25",
                    "variantDimH": "13",
                    "variantUpc": "8.76E+11",
                    "variantNumber": "KAI-5618",
                    "manufacturerPartNumber": "",
                    "variantPrice": 0.2,
                    "variantMapPrice": 0,
                    "variantMsrpPrice": 0,
                    "variantDisplayPrice": 0,
                    "variantDescription": "KAIBAB® HD 18X56 BINOCULAR\nThe Kaibab HD 18x56 is the ultimate long-distance western-hunting binocular series. When serious patience and superior optics are required to locate trophy animals at extreme distances, the Kaibab HD delivers the premium-quality, high-magnification optical performance you need to get the job done. Intended to be used with a tripod for extended, comfortable, rock-steady viewing. Ultracomfortable twist-up eyecups are perfect for long glassing sessions. Visually tear apart open landscapes in pursuit of tough-to-locate trophy big game with the Kaibab HD.\n\n\n\nVIP Warranty HD Premium APO XRPlus Coatings ArmorTek Argon Purged Waterproof\nMagnification\t18 x\nObjective Lens Diameter\t56 mm\nEye Relief\t16.4 mm\nExit Pupil\t3.1 mm\nLinear Field of View\t194 feet/1000 yards\nClose Focus\t23 feet\nInterpupillary Distance\t60-76 mm\nHeight\t7.7 inches\nWidth\t5.7 inches\nWeight\t43.5 ounces",
                    "variantAlert": "",
                    "variantLowlevel": "",
                    "variantSlug": "vortex-optics-kaibab-18x56-hd-binocular",
                    "variantVisible": 1,
                    "taxType": "",
                    "hideGoogleData": 0,
                    "google_variantCategory": null,
                    "google_variantType": null,
                    "google_variantCondition": null,
                    "taxable": 1,
                    "variantAllowCheckout": 0,
                    "variantCheckInvetory": 0,
                    "variantTrackInventory": 0,
                    "inventoryCount": -18,
                    "shippingProduct": 1,
                    "variantMetaTitle": "",
                    "variantMetaDescription": "",
                    "variantBrand": "",
                    "sortOrder": 0,
                    "dateCreated": "",
                    "deleted": 0,
                    "backOrderWarning": 0,
                    "createdAt": "2021-12-15 13:23:54",
                    "editedAt": "2023-01-03 11:08:21",
                    "variantInStock": true
                }
            },
            {
                "quote_variantsToken": "quoteVariant_123456",
                "variantToken": "vrnt_123456",
                "quantity": 1,
                "itemPrice": 359.99,
                "itemTax": 32.4,
                "lineTotal": 392.39,
                "fullDetails": {
                    "prodToken": "prod_123456",
                    "variantToken": "vrnt_123456",
                    "companyToken": "comp_123456",
                    "variantName": "Vortex Optics Diamondback HP 4-16x42  BDC Riflescopes",
                    "variantImage": {
                        "file": "6-27-2018/1530121344004__33909__10019.jpg"
                    },
                    "variantImages": [
                        {
                            "file": "6-27-2018/1530121353525__35090__100191.jpg",
                            "name": "100191"
                        },
                        {
                            "file": "6-27-2018/1530121379690__53555__100192.jpg",
                            "name": "100192"
                        },
                        {
                            "file": "6-27-2018/1530121387810__31428__100193.jpg",
                            "name": "100193"
                        }
                    ],
                    "variantWeight": "2.05",
                    "variantDimW": "3.25",
                    "variantDimL": "5",
                    "variantDimH": "16.75",
                    "variantUpc": "8.76E+11",
                    "variantNumber": "DBK-10019",
                    "manufacturerPartNumber": "",
                    "variantPrice": 359.99,
                    "variantMapPrice": 0,
                    "variantMsrpPrice": 0,
                    "variantDisplayPrice": 0,
                    "variantDescription": "Build Your Own Custom Turret\nDIAMONDBACK® HP 4-16X42 RIFLESCOPE\nThe Diamondback® HP (High Performance) riflescope offers a full-on array of features that discerning hunters are sure to appreciate. Optically, these scopes hit the proverbial mark. XD extra-low dispersion glass increases resolution and color fidelity while XR fully multi-coated lenses maximize every minute of shooting light. The side focus/parallax adjustment is easily accessible while keeping a trim profile and allowing optimal mounting height. And, with a 4x zoom range, the Diamondback® HP offers highly versatile magnification.\n\nDual use for Shooting Tactical / Hunting\n\n\n\nVIP Warranty XD Lens Elements XR Coatings Argon Purged Waterproof\nMagnification\t4-16 x\nObjective Lens Diameter\t42 mm\nEye Relief\t4.0 inches\nField of View\t23.8-6.1 feet/100 yards\nTube Size\t1-inch\nTurret Style\tCapped\nAdjustment Graduation\t1/4 MOA\nTravel per Rotation\t15 MOA\nMax Elevation Adjustment\t80 MOA\nMax Windage Adjustment\t80 MOA\nParallax Setting\t30 yards to infinity\nLength\t12.5 inches\nWeight\t18 ounces\nOptically, these scopes deliver unparalleled image quality. Our proprietary ALO automated laser optical alignment process forges a new paradigm in the sport optics industry, resulting in the most forgiving, comfortable, and highest quality images possible. The APO objective lens system uses index-matched lenses to correct color across the entire visual spectrum. HD premium extra-low dispersion glass delivers the ultimate in resolution and color fidelity, resulting in High Definition images. XR™ Plus premium fully multi-coated lenses increase light transmission for optimum brightness. ArmorTek® protects exterior lenses from scratches, oil and dirt.\n\n\nDual use for Shooting Tactical / Hunting • UA Patent 7,937,879, US Patent 7,958,665, US Patent 8,166,696 B2\n\n\nVIP Warranty HD Premium APO XRPlus Coatings ArmorTek Argon Purged Waterproof\nMagnification\t6-24 x\nObjective Lens Diameter\t50 mm\nEye Relief\t3.6 inches\nField of View\t20.4-5.1 feet/100 yards\nTube Size\t30 mm\nTurret Style\tL-Tec\nAdjustment Graduation\t0.1\nTravel per Rotation\t10 MRAD\nMax Elevation Adjustment\t27.5 MRAD (See Features Tab)\nMax Windage Adjustment\t10 MRAD (See Features Tab)\nParallax Setting\t25 to Infinity\nLength\t15.2 inches\nWeight\t28.8 oz",
                    "variantAlert": "",
                    "variantLowlevel": "",
                    "variantSlug": "diamondback-hp-4-16x42-bdc-riflescopes",
                    "variantVisible": 1,
                    "taxType": "",
                    "hideGoogleData": 0,
                    "google_variantCategory": null,
                    "google_variantType": null,
                    "google_variantCondition": null,
                    "taxable": 1,
                    "variantAllowCheckout": 0,
                    "variantCheckInvetory": 0,
                    "variantTrackInventory": 0,
                    "inventoryCount": -9,
                    "shippingProduct": 1,
                    "variantMetaTitle": "",
                    "variantMetaDescription": "",
                    "variantBrand": "",
                    "sortOrder": 0,
                    "dateCreated": "",
                    "deleted": 0,
                    "backOrderWarning": 0,
                    "createdAt": "2021-12-15 13:23:54",
                    "editedAt": "2023-01-03 11:08:21",
                    "variantInStock": true
                }
            }
        ],
        "shippingAddress": {
            "addressToken": "adrs_123456",
            "addressLabel": "",
            "address": "12354 Main Street",
            "address2": "",
            "addressCity": "Monsey",
            "addressState": "NY",
            "addressZip": "10952",
            "addressFirstName": "Sarah",
            "addressLastName": "Jones",
            "phoneNumber": "",
            "mobileNumber": "",
            "addressCountry": "United States",
            "addressDefault": 0,
            "customerToken": "cust_123456",
            "createdAt": "2023-01-03 11:30:56",
            "editedAt": "2023-01-03 11:30:56",
            "specialValues": []
        },
        "contactDetails": {
            "quote_ContactToken": "quoteContact_123456",123456
            "firstName": "Sarah",
            "lastName": "Jones",
            "email": "sjones1@gmail.com",
            "phoneNumber": "987657489",
            "companyName": "Tyrell Corp"
        },
        "shippingQuote": []
    },
    {
        "quoteToken": "quote_123456",
        "customerToken": "cs_123456",
        "companyToken": "comp_123456",
        "quoteFiles": "",
        "status": "approvedByCustomer",
        "deleted": 0,
        "dateCreated": "2023-01-03 12:30:59",
        "dateUpdated": "2023-01-03 11:31:14",
        "variantsTotal": 360.39,
        "shippingTotal": 10,
        "taxTotal": 33.32,
        "combinedTotal": "403.71",
"quoteNumber": 5000425,
        "variantDetails": [
            {
                "quote_variantsToken": "quoteVariant_123456",123456
                "variantToken": "vrnt_123456",
                "quantity": 2,
                "itemPrice": 0.2,
                "itemTax": 0.02,
                "lineTotal": 0.44,
                "fullDetails": {
                    "prodToken": "prod_123456",123456
                    "variantToken": "vrnt_123456",
                    "companyToken": "comp_123456",
                    "variantName": "Vortex Optics Kaibab 18x56 HD Binocular",
                    "variantImage": {
                        "file": "6-27-2018/1530121117199__32308__5618.jpg"
                    },
                    "variantImages": [
                        {
                            "file": "6-27-2018/1530121126552__29522__56181.jpg",
                            "name": "56181"
                        },
                        {
                            "file": "6-27-2018/1530121135284__30461__56182.jpg",
                            "name": "56182"
                        },
                        {
                            "file": "6-27-2018/1530121143009__29290__56183.jpg",
                            "name": "56183"
                        }
                    ],
                    "variantWeight": "4.4",
                    "variantDimW": "8",
                    "variantDimL": "4.25",
                    "variantDimH": "13",
                    "variantUpc": "8.76E+11",
                    "variantNumber": "KAI-5618",
                    "manufacturerPartNumber": "",
                    "variantPrice": 0.2,
                    "variantMapPrice": 0,
                    "variantMsrpPrice": 0,
                    "variantDisplayPrice": 0,
                    "variantDescription": "KAIBAB® HD 18X56 BINOCULAR\nThe Kaibab HD 18x56 is the ultimate long-distance western-hunting binocular series. When serious patience and superior optics are required to locate trophy animals at extreme distances, the Kaibab HD delivers the premium-quality, high-magnification optical performance you need to get the job done. Intended to be used with a tripod for extended, comfortable, rock-steady viewing. Ultracomfortable twist-up eyecups are perfect for long glassing sessions. Visually tear apart open landscapes in pursuit of tough-to-locate trophy big game with the Kaibab HD.\n\n\n\nVIP Warranty HD Premium APO XRPlus Coatings ArmorTek Argon Purged Waterproof\nMagnification\t18 x\nObjective Lens Diameter\t56 mm\nEye Relief\t16.4 mm\nExit Pupil\t3.1 mm\nLinear Field of View\t194 feet/1000 yards\nClose Focus\t23 feet\nInterpupillary Distance\t60-76 mm\nHeight\t7.7 inches\nWidth\t5.7 inches\nWeight\t43.5 ounces",
                    "variantAlert": "",
                    "variantLowlevel": "",
                    "variantSlug": "vortex-optics-kaibab-18x56-hd-binocular",
                    "variantVisible": 1,
                    "taxType": "",
                    "hideGoogleData": 0,
                    "google_variantCategory": null,
                    "google_variantType": null,
                    "google_variantCondition": null,
                    "taxable": 1,
                    "variantAllowCheckout": 0,
                    "variantCheckInvetory": 0,
                    "variantTrackInventory": 0,
                    "inventoryCount": -18,
                    "shippingProduct": 1,
                    "variantMetaTitle": "",
                    "variantMetaDescription": "",
                    "variantBrand": "",
                    "sortOrder": 0,
                    "dateCreated": "",
                    "deleted": 0,
                    "backOrderWarning": 0,
                    "createdAt": "2021-12-15 13:23:54",
                    "editedAt": "2023-01-03 11:08:21",
                    "variantInStock": true
                }
            },
            {
                "quote_variantsToken": "quoteVariant_JDlatoUBnean",
                "variantToken": "vrnt_123456",
                "quantity": 1,
                "itemPrice": 359.99,
                "itemTax": 32.4,
                "lineTotal": 392.39,
                "fullDetails": {
                    "prodToken": "prod_123456",
                    "variantToken": "vrnt_123456",123456
                    "companyToken": "comp_123456",
                    "variantName": "Vortex Optics Diamondback HP 4-16x42  BDC Riflescopes",
                    "variantImage": {
                        "file": "6-27-2018/1530121344004__33909__10019.jpg"
                    },
                    "variantImages": [
                        {
                            "file": "6-27-2018/1530121353525__35090__100191.jpg",
                            "name": "100191"
                        },
                        {
                            "file": "6-27-2018/1530121379690__53555__100192.jpg",
                            "name": "100192"
                        },
                        {
                            "file": "6-27-2018/1530121387810__31428__100193.jpg",
                            "name": "100193"
                        }
                    ],
                    "variantWeight": "2.05",
                    "variantDimW": "3.25",
                    "variantDimL": "5",
                    "variantDimH": "16.75",
                    "variantUpc": "8.76E+11",
                    "variantNumber": "DBK-10019",
                    "manufacturerPartNumber": "",
                    "variantPrice": 359.99,
                    "variantMapPrice": 0,
                    "variantMsrpPrice": 0,
                    "variantDisplayPrice": 0,
                    "variantDescription": "Build Your Own Custom Turret\nDIAMONDBACK® HP 4-16X42 RIFLESCOPE\nThe Diamondback® HP (High Performance) riflescope offers a full-on array of features that discerning hunters are sure to appreciate. Optically, these scopes hit the proverbial mark. XD extra-low dispersion glass increases resolution and color fidelity while XR fully multi-coated lenses maximize every minute of shooting light. The side focus/parallax adjustment is easily accessible while keeping a trim profile and allowing optimal mounting height. And, with a 4x zoom range, the Diamondback® HP offers highly versatile magnification.\n\nDual use for Shooting Tactical / Hunting\n\n\n\nVIP Warranty XD Lens Elements XR Coatings Argon Purged Waterproof\nMagnification\t4-16 x\nObjective Lens Diameter\t42 mm\nEye Relief\t4.0 inches\nField of View\t23.8-6.1 feet/100 yards\nTube Size\t1-inch\nTurret Style\tCapped\nAdjustment Graduation\t1/4 MOA\nTravel per Rotation\t15 MOA\nMax Elevation Adjustment\t80 MOA\nMax Windage Adjustment\t80 MOA\nParallax Setting\t30 yards to infinity\nLength\t12.5 inches\nWeight\t18 ounces\nOptically, these scopes deliver unparalleled image quality. Our proprietary ALO automated laser optical alignment process forges a new paradigm in the sport optics industry, resulting in the most forgiving, comfortable, and highest quality images possible. The APO objective lens system uses index-matched lenses to correct color across the entire visual spectrum. HD premium extra-low dispersion glass delivers the ultimate in resolution and color fidelity, resulting in High Definition images. XR™ Plus premium fully multi-coated lenses increase light transmission for optimum brightness. ArmorTek® protects exterior lenses from scratches, oil and dirt.\n\n\nDual use for Shooting Tactical / Hunting • UA Patent 7,937,879, US Patent 7,958,665, US Patent 8,166,696 B2\n\n\nVIP Warranty HD Premium APO XRPlus Coatings ArmorTek Argon Purged Waterproof\nMagnification\t6-24 x\nObjective Lens Diameter\t50 mm\nEye Relief\t3.6 inches\nField of View\t20.4-5.1 feet/100 yards\nTube Size\t30 mm\nTurret Style\tL-Tec\nAdjustment Graduation\t0.1\nTravel per Rotation\t10 MRAD\nMax Elevation Adjustment\t27.5 MRAD (See Features Tab)\nMax Windage Adjustment\t10 MRAD (See Features Tab)\nParallax Setting\t25 to Infinity\nLength\t15.2 inches\nWeight\t28.8 oz",
                    "variantAlert": "",
                    "variantLowlevel": "",
                    "variantSlug": "diamondback-hp-4-16x42-bdc-riflescopes",
                    "variantVisible": 1,
                    "taxType": "",
                    "hideGoogleData": 0,
                    "google_variantCategory": null,
                    "google_variantType": null,
                    "google_variantCondition": null,
                    "taxable": 1,
                    "variantAllowCheckout": 0,
                    "variantCheckInvetory": 0,
                    "variantTrackInventory": 0,
                    "inventoryCount": -9,
                    "shippingProduct": 1,
                    "variantMetaTitle": "",
                    "variantMetaDescription": "",
                    "variantBrand": "",
                    "sortOrder": 0,
                    "dateCreated": "",
                    "deleted": 0,
                    "backOrderWarning": 0,
                    "createdAt": "2021-12-15 13:23:54",
                    "editedAt": "2023-01-03 11:08:21",
                    "variantInStock": true
                }
            }
        ],
        "shippingAddress": {
            "addressToken": "adrs_123456",
            "addressLabel": "",
            "address": "12354 Main Street",
            "address2": "",
            "addressCity": "Monsey",
            "addressState": "NY",
            "addressZip": "10952",
            "addressFirstName": "Sarah",
            "addressLastName": "Jones",
            "phoneNumber": "",
            "mobileNumber": "",
            "addressCountry": "United States",
            "addressDefault": 0,
            "customerToken": "cust_123456",
            "createdAt": "2023-01-03 11:30:56",
            "editedAt": "2023-01-03 11:30:56",
            "specialValues": []
        },
        "contactDetails": {
            "quote_ContactToken": "quoteContact_123456",
            "firstName": "Sarah",
            "lastName": "Jones",
            "email": "sjones1@gmail.com",
            "phoneNumber": "123456789",
            "companyName": "Tyrell Corp"
        },
        "shippingQuote": [
            {
                "quote_shippingQuoteToken": "shippingQuoteToken_123456",
                "carrier": "UPS",
                "methodName": "Next Day Air",
                "origRate": null,
                "rate": "10",
                "deliveryDateTime": null,
                "deliveryDays": "1",
                "description": null,
                "approved": 1,
                "approvedBy": "Fernando Mills"
            },
            {
                "quote_shippingQuoteToken": "shippingQuoteToken_123456",
                "carrier": "Fedex",
                "methodName": "Ground Express",
                "origRate": null,
                "rate": "15",
                "deliveryDateTime": null,
                "deliveryDays": "2",
                "description": null,
                "approved": null,
                "approvedBy": null
            }
        ]
    }
]
```

## Get a quote by Quote Token

### HTTP Request

`GET https://apistore.csomni.com/quotes/{quoteToken}`

### URL Parameters

| Parameter   | Description                     |
| ----------- | ------------------------------- |
| Quote Token | Token of the Quote to retrieve. |

```shell
curl --request GET \
  --url https://apistore.csomni.com/quotes/{quoteToken} \
   --header 'token: 123'
  --header 'customerToken: cs_123456' \
```

Response:

```json
{
    "quoteToken": "quote_123456123456",
    "customerToken": "cs_123456",
    "companyToken": "comp_123456",
    "quoteFiles": "",
    "status": "approvedByCustomer",
    "deleted": 0,
    "dateCreated": "2023-01-03 13:20:15",
    "dateUpdated": "2023-01-03 12:20:35",
    "variantsTotal": 360.39,
    "shippingTotal": 10,
    "taxTotal": 33.32,
    "combinedTotal": "403.71",
"quoteNumber": 5007404,
    "variantDetails": [
        {
            "quote_variantsToken": "quoteVariant_123456",
            "variantToken": "vrnt_123456",
            "quantity": 2,
            "itemPrice": 0.2,
            "itemTax": 0.02,
            "lineTotal": 0.44,
            "fullDetails": {
                "prodToken": "prod_123456",
                "variantToken": "vrnt_123456",123456
                "companyToken": "comp_123456",
                "variantName": "Vortex Optics Kaibab 18x56 HD Binocular",
                "variantImage": {
                    "file": "6-27-2018/1530121117199__32308__5618.jpg"
                },
                "variantImages": [
                    {
                        "file": "6-27-2018/1530121126552__29522__56181.jpg",
                        "name": "56181"
                    },
                    {
                        "file": "6-27-2018/1530121135284__30461__56182.jpg",
                        "name": "56182"
                    },
                    {
                        "file": "6-27-2018/1530121143009__29290__56183.jpg",
                        "name": "56183"
                    }
                ],
                "variantWeight": "4.4",
                "variantDimW": "8",
                "variantDimL": "4.25",
                "variantDimH": "13",
                "variantUpc": "8.76E+11",
                "variantNumber": "KAI-5618",
                "manufacturerPartNumber": "",
                "variantPrice": 0.2,
                "variantMapPrice": 0,
                "variantMsrpPrice": 0,
                "variantDisplayPrice": 0,
                "variantDescription": "KAIBAB® HD 18X56 BINOCULAR\nThe Kaibab HD 18x56 is the ultimate long-distance western-hunting binocular series. When serious patience and superior optics are required to locate trophy animals at extreme distances, the Kaibab HD delivers the premium-quality, high-magnification optical performance you need to get the job done. Intended to be used with a tripod for extended, comfortable, rock-steady viewing. Ultracomfortable twist-up eyecups are perfect for long glassing sessions. Visually tear apart open landscapes in pursuit of tough-to-locate trophy big game with the Kaibab HD.\n\n\n\nVIP Warranty HD Premium APO XRPlus Coatings ArmorTek Argon Purged Waterproof\nMagnification\t18 x\nObjective Lens Diameter\t56 mm\nEye Relief\t16.4 mm\nExit Pupil\t3.1 mm\nLinear Field of View\t194 feet/1000 yards\nClose Focus\t23 feet\nInterpupillary Distance\t60-76 mm\nHeight\t7.7 inches\nWidth\t5.7 inches\nWeight\t43.5 ounces",
                "variantAlert": "",
                "variantLowlevel": "",
                "variantSlug": "vortex-optics-kaibab-18x56-hd-binocular",
                "variantVisible": 1,
                "taxType": "",
                "hideGoogleData": 0,
                "google_variantCategory": null,
                "google_variantType": null,
                "google_variantCondition": null,
                "taxable": 1,
                "variantAllowCheckout": 0,
                "variantCheckInvetory": 0,
                "variantTrackInventory": 0,
                "inventoryCount": -18,
                "shippingProduct": 1,
                "variantMetaTitle": "",
                "variantMetaDescription": "",
                "variantBrand": "",
                "sortOrder": 0,
                "dateCreated": "",
                "deleted": 0,
                "backOrderWarning": 0,
                "createdAt": "2021-12-15 13:23:54",
                "editedAt": "2023-01-03 11:08:21",
                "variantInStock": true
            }
        },
        {
            "quote_variantsToken": "quoteVariant_123456",
            "variantToken": "vrnt_123456",
            "quantity": 1,
            "itemPrice": 359.99,
            "itemTax": 32.4,
            "lineTotal": 392.39,
            "fullDetails": {
                "prodToken": "prod_123456",
                "variantToken": "vrnt_123456",123456
                "companyToken": "comp_123456",
                "variantName": "Vortex Optics Diamondback HP 4-16x42  BDC Riflescopes",
                "variantImage": {
                    "file": "6-27-2018/1530121344004__33909__10019.jpg"
                },
                "variantImages": [
                    {
                        "file": "6-27-2018/1530121353525__35090__100191.jpg",
                        "name": "100191"
                    },
                    {
                        "file": "6-27-2018/1530121379690__53555__100192.jpg",
                        "name": "100192"
                    },
                    {
                        "file": "6-27-2018/1530121387810__31428__100193.jpg",
                        "name": "100193"
                    }
                ],
                "variantWeight": "2.05",
                "variantDimW": "3.25",
                "variantDimL": "5",
                "variantDimH": "16.75",
                "variantUpc": "8.76E+11",
                "variantNumber": "DBK-10019",
                "manufacturerPartNumber": "",
                "variantPrice": 359.99,
                "variantMapPrice": 0,
                "variantMsrpPrice": 0,
                "variantDisplayPrice": 0,
                "variantDescription": "Build Your Own Custom Turret\nDIAMONDBACK® HP 4-16X42 RIFLESCOPE\nThe Diamondback® HP (High Performance) riflescope offers a full-on array of features that discerning hunters are sure to appreciate. Optically, these scopes hit the proverbial mark. XD extra-low dispersion glass increases resolution and color fidelity while XR fully multi-coated lenses maximize every minute of shooting light. The side focus/parallax adjustment is easily accessible while keeping a trim profile and allowing optimal mounting height. And, with a 4x zoom range, the Diamondback® HP offers highly versatile magnification.\n\nDual use for Shooting Tactical / Hunting\n\n\n\nVIP Warranty XD Lens Elements XR Coatings Argon Purged Waterproof\nMagnification\t4-16 x\nObjective Lens Diameter\t42 mm\nEye Relief\t4.0 inches\nField of View\t23.8-6.1 feet/100 yards\nTube Size\t1-inch\nTurret Style\tCapped\nAdjustment Graduation\t1/4 MOA\nTravel per Rotation\t15 MOA\nMax Elevation Adjustment\t80 MOA\nMax Windage Adjustment\t80 MOA\nParallax Setting\t30 yards to infinity\nLength\t12.5 inches\nWeight\t18 ounces\nOptically, these scopes deliver unparalleled image quality. Our proprietary ALO automated laser optical alignment process forges a new paradigm in the sport optics industry, resulting in the most forgiving, comfortable, and highest quality images possible. The APO objective lens system uses index-matched lenses to correct color across the entire visual spectrum. HD premium extra-low dispersion glass delivers the ultimate in resolution and color fidelity, resulting in High Definition images. XR™ Plus premium fully multi-coated lenses increase light transmission for optimum brightness. ArmorTek® protects exterior lenses from scratches, oil and dirt.\n\n\nDual use for Shooting Tactical / Hunting • UA Patent 7,937,879, US Patent 7,958,665, US Patent 8,166,696 B2\n\n\nVIP Warranty HD Premium APO XRPlus Coatings ArmorTek Argon Purged Waterproof\nMagnification\t6-24 x\nObjective Lens Diameter\t50 mm\nEye Relief\t3.6 inches\nField of View\t20.4-5.1 feet/100 yards\nTube Size\t30 mm\nTurret Style\tL-Tec\nAdjustment Graduation\t0.1\nTravel per Rotation\t10 MRAD\nMax Elevation Adjustment\t27.5 MRAD (See Features Tab)\nMax Windage Adjustment\t10 MRAD (See Features Tab)\nParallax Setting\t25 to Infinity\nLength\t15.2 inches\nWeight\t28.8 oz",
                "variantAlert": "",
                "variantLowlevel": "",
                "variantSlug": "diamondback-hp-4-16x42-bdc-riflescopes",
                "variantVisible": 1,
                "taxType": "",
                "hideGoogleData": 0,
                "google_variantCategory": null,
                "google_variantType": null,
                "google_variantCondition": null,
                "taxable": 1,
                "variantAllowCheckout": 0,
                "variantCheckInvetory": 0,
                "variantTrackInventory": 0,
                "inventoryCount": -9,
                "shippingProduct": 1,
                "variantMetaTitle": "",
                "variantMetaDescription": "",
                "variantBrand": "",
                "sortOrder": 0,
                "dateCreated": "",
                "deleted": 0,
                "backOrderWarning": 0,
                "createdAt": "2021-12-15 13:23:54",
                "editedAt": "2023-01-03 11:08:21",
                "variantInStock": true
            }
        }
    ],
    "shippingAddress": {
        "addressToken": "adrs_123456",
        "addressLabel": "",
        "address": "12354 Main Street",
        "address2": "",
        "addressCity": "Monsey",
        "addressState": "NY",
        "addressZip": "10952",
        "addressFirstName": "Sarah",
        "addressLastName": "Jones",
        "phoneNumber": "",
        "mobileNumber": "",
        "addressCountry": "United States",
        "addressDefault": 0,
        "customerToken": "cust_123456",
        "createdAt": "2023-01-03 12:20:12",
        "editedAt": "2023-01-03 12:20:12",
        "specialValues": []
    },
    "contactDetails": {
        "quote_ContactToken": "quoteContact_123456",
        "firstName": "Sarah",
        "lastName": "Jones",
        "email": "sjones1@gmail.com",
        "phoneNumber": "123456789",
        "companyName": "Tyrell Corp"
    },
    "shippingQuote": [
        {
            "quote_shippingQuoteToken": "shippingQuoteToken_123456",
            "carrier": "UPS",
            "methodName": "Next Day Air",
            "origRate": null,
            "rate": "10",
            "deliveryDateTime": null,
            "deliveryDays": "1",
            "description": null,
            "approved": 1,
            "approvedBy": "John Smith"
        },
        {
            "quote_shippingQuoteToken": "shippingQuoteToken_123456",
            "carrier": "Fedex",
            "methodName": "Ground Express",
            "origRate": null,
            "rate": "15",
            "deliveryDateTime": null,
            "deliveryDays": "2",
            "description": null,
            "approved": null,
            "approvedBy": null
        }
    ]
}
```

## Get a quote by Status

### HTTP Request

`GET https://apistore.csomni.com/quotes/{status}`

### URL Parameters

| Parameter | Description                                                           |
| --------- | --------------------------------------------------------------------- |
| Status    | can be either of 'waiting-response', 'denied', 'cancelledByCustomer', 'approvedByCustomer' |

```shell
curl --request GET \
  --url https://apistore.csomni.com/quotes/status \
    --header 'token: 123'
  --header 'customerToken: cs_123456' \
```

Response:

```json
[
  {
    "name": "",
    "quoteToken": "cc_123456",
    "customerToken": "cust_123456",
    "companyToken": "comp_123456",
    "quoteItems": null,
    "quoteFiles": "",
    "dateSubmitted": "2021-12-01 20:47:19",
    "status": "Approved",
    "deleted": 0,
    "dateCreated": "2021-07-07 06:16:01",
    "dateUpdated": "2021-12-01 20:47:19"
  },
  {
    "name": "",
    "quoteToken": "sadasdasdasds",
    "customerToken": "cust_123456",
    "companyToken": "comp_123456",
    "quoteItems": [
      {
        "prodToken": "prod_123456",
        "variantToken": "vrnt_123456",
        "companyToken": "comp_123456",
        "variantName": "",
        "variantImage": "",
        "variantImages": "[]",
        "variantWeight": "",
        "variantDimW": "",
        "variantDimL": "",
        "variantDimH": "",
        "variantUpc": "",
        "variantNumber": "",
        "variantPrice": "1.01",
        "variantCostPrice": "",
        "variantDescription": "",
        "variantAlert": "",
        "variantLowlevel": "null",
        "variantSlug": "",
        "variantVisible": "1",
        "variantAllowCheckout": "0",
        "variantCheckInvetory": "1",
        "variantTrackInventory": "0",
        "inventoryCount": 25,
        "shippingProduct": 0,
        "dateCreated": "1536270703",
        "deleted": "0",
        "varinatImages": null,
        "variantOptions": {
          "optn_123456": "Var 1"
        },
        "prodName": "widget",
        "prodImage": "9-6-2018/1536271360573__14511__yb.jpg",
        "quantity": 2
      }
    ],
    "quoteFiles": "",
    "dateSubmitted": "2021-12-01 20:38:27",
    "status": "Approved",
    "deleted": 0,
    "dateCreated": "2021-07-07 04:29:09",
    "dateUpdated": "2021-12-01 20:38:27"
  }
]
```

## Update Quote status : only allowed to update status to 'cancelled'. NO other edits allowed at this point

### HTTP Request

`POST https://apistore.csomni.com/quotes/{quoteToken}/cancel`


### URL Parameters

| Parameter   | Description                   |
| ----------- | ----------------------------- |
| Quote Token | Token of the Quote to update. |

### QUERY Parameters

| Parameter                | Required | Description            |
| -------------            | -------- | ---------------------- |
| token (header)           | true     | siteToken              |
| customerToken (header)    | true     | cs loginToken          |

```shell
curl --request POST \
  --url https://apistore.csomni.com/quotes/[quoteToken]/cancel \
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
   --header 'token: 123'\
  --header 'customerToken: cs_123456' \
  --data ''
}'

```

Response:

```json
{
    "quoteToken": "quote_123456",
    "customerToken": "cust_123456",
    "companyToken": "comp_123456",
    "quoteFiles": "",
    "status": "cancelled",
    "deleted": 0,
    "dateCreated": "2022-11-20 12:20:15",
    "dateUpdated": "2022-11-20 21:06:05",
    "variantDetails": [
        {
            "quote_variantsToken": "quoteVariant_123456",
            "variantToken": "vrnt_123456",
            "quantity": 1,
            "fullDetails": {
                "prodToken": "prod_123456",
                "variantToken": "vrnt_123456",
                "companyToken": "comp_123456",
                "variantName": "Vortex Optics Diamondback HP 4-16x42  BDC Riflescopes",
                "variantImage": {
                    "file": "6-27-2018/1530121344004__33909__10019.jpg"
                },
                "variantImages": [
                    {
                        "file": "6-27-2018/1530121353525__35090__100191.jpg",
                        "name": "100191"
                    },
                    {
                        "file": "6-27-2018/1530121379690__53555__100192.jpg",
                        "name": "100192"
                    },
                    {
                        "file": "6-27-2018/1530121387810__31428__100193.jpg",
                        "name": "100193"
                    }
                ],
                "variantWeight": "2.05",
                "variantDimW": "3.25",
                "variantDimL": "5",
                "variantDimH": "16.75",
                "variantUpc": "8.76E+11",
                "variantNumber": "DBK-10019",
                "manufacturerPartNumber": "",
                "variantPrice": 359.99,
                "variantMapPrice": 0,
                "variantMsrpPrice": 0,
                "variantDisplayPrice": 0,
                "variantDescription": "Build Your Own Custom Turret\nDIAMONDBACK® HP 4-16X42 RIFLESCOPE\nThe Diamondback® HP (High Performance) riflescope offers a full-on array of features that discerning hunters are sure to appreciate. Optically, these scopes hit the proverbial mark. XD extra-low dispersion glass increases resolution and color fidelity while XR fully multi-coated lenses maximize every minute of shooting light. The side focus/parallax adjustment is easily accessible while keeping a trim profile and allowing optimal mounting height. And, with a 4x zoom range, the Diamondback® HP offers highly versatile magnification.\n\nDual use for Shooting Tactical / Hunting\n\n\n\nVIP Warranty XD Lens Elements XR Coatings Argon Purged Waterproof\nMagnification\t4-16 x\nObjective Lens Diameter\t42 mm\nEye Relief\t4.0 inches\nField of View\t23.8-6.1 feet/100 yards\nTube Size\t1-inch\nTurret Style\tCapped\nAdjustment Graduation\t1/4 MOA\nTravel per Rotation\t15 MOA\nMax Elevation Adjustment\t80 MOA\nMax Windage Adjustment\t80 MOA\nParallax Setting\t30 yards to infinity\nLength\t12.5 inches\nWeight\t18 ounces\nOptically, these scopes deliver unparalleled image quality. Our proprietary ALO automated laser optical alignment process forges a new paradigm in the sport optics industry, resulting in the most forgiving, comfortable, and highest quality images possible. The APO objective lens system uses index-matched lenses to correct color across the entire visual spectrum. HD premium extra-low dispersion glass delivers the ultimate in resolution and color fidelity, resulting in High Definition images. XR™ Plus premium fully multi-coated lenses increase light transmission for optimum brightness. ArmorTek® protects exterior lenses from scratches, oil and dirt.\n\n\nDual use for Shooting Tactical / Hunting • UA Patent 7,937,879, US Patent 7,958,665, US Patent 8,166,696 B2\n\n\nVIP Warranty HD Premium APO XRPlus Coatings ArmorTek Argon Purged Waterproof\nMagnification\t6-24 x\nObjective Lens Diameter\t50 mm\nEye Relief\t3.6 inches\nField of View\t20.4-5.1 feet/100 yards\nTube Size\t30 mm\nTurret Style\tL-Tec\nAdjustment Graduation\t0.1\nTravel per Rotation\t10 MRAD\nMax Elevation Adjustment\t27.5 MRAD (See Features Tab)\nMax Windage Adjustment\t10 MRAD (See Features Tab)\nParallax Setting\t25 to Infinity\nLength\t15.2 inches\nWeight\t28.8 oz",
                "variantAlert": "",
                "variantLowlevel": "",
                "variantSlug": "diamondback-hp-4-16x42-bdc-riflescopes",
                "variantVisible": 1,
                "taxType": "",
                "hideGoogleData": 0,
                "google_variantCategory": null,
                "google_variantType": null,
                "google_variantCondition": null,
                "taxable": 1,
                "variantAllowCheckout": 0,
                "variantCheckInvetory": 0,
                "variantTrackInventory": 0,
                "inventoryCount": 0,
                "shippingProduct": 0,
                "variantMetaTitle": "",
                "variantMetaDescription": "",
                "variantBrand": "",
                "sortOrder": 0,
                "dateCreated": "",
                "deleted": 0,
                "backOrderWarning": 0,
                "createdAt": "2021-12-15 13:23:54",
                "editedAt": "2021-12-15 13:23:54",
                "variantInStock": true
            }
        },
        {
            "quote_variantsToken": "quoteVariant_123456",
            "variantToken": "vrnt_123456",
            "quantity": 1,
            "fullDetails": {
                "prodToken": "prod_123456",
                "variantToken": "vrnt_123456",
                "companyToken": "comp_123456",
                "variantName": "Vortex Optics Diamondback HP 4-16x42  BDC Riflescopes",
                "variantImage": {
                    "file": "6-27-2018/1530121344004__33909__10019.jpg"
                },
                "variantImages": [
                    {
                        "file": "6-27-2018/1530121353525__35090__100191.jpg",
                        "name": "100191"
                    },
                    {
                        "file": "6-27-2018/1530121379690__53555__100192.jpg",
                        "name": "100192"
                    },
                    {
                        "file": "6-27-2018/1530121387810__31428__100193.jpg",
                        "name": "100193"
                    }
                ],
                "variantWeight": "2.05",
                "variantDimW": "3.25",
                "variantDimL": "5",
                "variantDimH": "16.75",
                "variantUpc": "8.76E+11",
                "variantNumber": "DBK-10019",
                "manufacturerPartNumber": "",
                "variantPrice": 359.99,
                "variantMapPrice": 0,
                "variantMsrpPrice": 0,
                "variantDisplayPrice": 0,
                "variantDescription": "Build Your Own Custom Turret\nDIAMONDBACK® HP 4-16X42 RIFLESCOPE\nThe Diamondback® HP (High Performance) riflescope offers a full-on array of features that discerning hunters are sure to appreciate. Optically, these scopes hit the proverbial mark. XD extra-low dispersion glass increases resolution and color fidelity while XR fully multi-coated lenses maximize every minute of shooting light. The side focus/parallax adjustment is easily accessible while keeping a trim profile and allowing optimal mounting height. And, with a 4x zoom range, the Diamondback® HP offers highly versatile magnification.\n\nDual use for Shooting Tactical / Hunting\n\n\n\nVIP Warranty XD Lens Elements XR Coatings Argon Purged Waterproof\nMagnification\t4-16 x\nObjective Lens Diameter\t42 mm\nEye Relief\t4.0 inches\nField of View\t23.8-6.1 feet/100 yards\nTube Size\t1-inch\nTurret Style\tCapped\nAdjustment Graduation\t1/4 MOA\nTravel per Rotation\t15 MOA\nMax Elevation Adjustment\t80 MOA\nMax Windage Adjustment\t80 MOA\nParallax Setting\t30 yards to infinity\nLength\t12.5 inches\nWeight\t18 ounces\nOptically, these scopes deliver unparalleled image quality. Our proprietary ALO automated laser optical alignment process forges a new paradigm in the sport optics industry, resulting in the most forgiving, comfortable, and highest quality images possible. The APO objective lens system uses index-matched lenses to correct color across the entire visual spectrum. HD premium extra-low dispersion glass delivers the ultimate in resolution and color fidelity, resulting in High Definition images. XR™ Plus premium fully multi-coated lenses increase light transmission for optimum brightness. ArmorTek® protects exterior lenses from scratches, oil and dirt.\n\n\nDual use for Shooting Tactical / Hunting • UA Patent 7,937,879, US Patent 7,958,665, US Patent 8,166,696 B2\n\n\nVIP Warranty HD Premium APO XRPlus Coatings ArmorTek Argon Purged Waterproof\nMagnification\t6-24 x\nObjective Lens Diameter\t50 mm\nEye Relief\t3.6 inches\nField of View\t20.4-5.1 feet/100 yards\nTube Size\t30 mm\nTurret Style\tL-Tec\nAdjustment Graduation\t0.1\nTravel per Rotation\t10 MRAD\nMax Elevation Adjustment\t27.5 MRAD (See Features Tab)\nMax Windage Adjustment\t10 MRAD (See Features Tab)\nParallax Setting\t25 to Infinity\nLength\t15.2 inches\nWeight\t28.8 oz",
                "variantAlert": "",
                "variantLowlevel": "",
                "variantSlug": "diamondback-hp-4-16x42-bdc-riflescopes",
                "variantVisible": 1,
                "taxType": "",
                "hideGoogleData": 0,
                "google_variantCategory": null,
                "google_variantType": null,
                "google_variantCondition": null,
                "taxable": 1,
                "variantAllowCheckout": 0,
                "variantCheckInvetory": 0,
                "variantTrackInventory": 0,
                "inventoryCount": 0,
                "shippingProduct": 0,
                "variantMetaTitle": "",
                "variantMetaDescription": "",
                "variantBrand": "",
                "sortOrder": 0,
                "dateCreated": "",
                "deleted": 0,
                "backOrderWarning": 0,
                "createdAt": "2021-12-15 13:23:54",
                "editedAt": "2021-12-15 13:23:54",
                "variantInStock": true
            }
        }
    ],
    "shippingAddress": {
        "quote_ShippingAddressToken": "quoteShippingAdrs_123456",
        "address1": "3 peek aboo",
        "address2": null,
        "city": "Brooklyn",
        "state": "NY",
        "zip": "130245",
        "country": "US",
        "receiverContactName": "John",
        "receiverContactNumber": "123456"
    },
    "contactDetails": {
        "quote_ContactToken": "quoteContact_123456",
        "name": "Sarah Jones",
        "email": "sjones1@gmail.com",
        "phoneNumber": "123456789",
        "companyName": "Tyrell Corp"
    },
    "shippingQuote": null
}
```


## Delete a Specific quote

### HTTP Request

`DELETE https://apistore.csomni.com/quotes/{quoteToken}`

```shell
curl --request DELETE \
  --url https://apistore.csomni.com/quotes/{quoteToken} \
  --header 'content-type: application/json' \
    --header 'token: 123'\
  --header 'customerToken: cs_123456' \
```

Response:

```json
{
  "token": "quote_SCOBBRFrfpXV",
  "deleted": "true"
}
```
## Delete all quotes by customer

### HTTP Request
`DELETE https://apistore.csomni.com/quotes/all`

```shell
curl --request DELETE \
  --url https://apistore.csomni.com/quotes/all \
  --header 'content-type: application/json' \
    --header 'token: 123'\
  --header 'customerToken: cs_123456' \
```

Response:

```json
{
    "customertoken": "cs_123456",
    "quotes": "all",
    "deleted": "true"
}
