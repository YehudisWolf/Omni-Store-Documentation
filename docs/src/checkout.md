# Checkout

## Chekout Step 1 (email,address)

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/checkout/info \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{"contactEmail" : "mschwartz@test.com","addressToken" : "adrs_xipKF02Td5eJ66IoEyzHdXUM","contactFirstName":"Moises","contactLastName","Scheiyz"}'

```

> The above command returns JSON structured like this

```json
{
  "id": 821,
  "cartToken": "cart_ChXDOtbOnQSZRtH4LoKkfDFU",
  "customerToken": "cs_BXW5tm36lo2QHdAs634YYwAj6o4xItx3lbIK",
  "couponCodes": null,
  "addressToken": "adrs_xipKF02Td5eJ66IoEyzHdXUM",
  "shippingMethod": null,
  "shippingMethodId": "",
  "shippingAddressLabel": "",
  "shippingAddress": {
    "address": "abc",
    "address2": "",
    "city": "New York",
    "state": "New York",
    "zip": "71005",
    "country": "",
    "phone": "",
    "mobile": "",
    "specialValues": []
  },
  "contactEmail": "ha.haseeb29@gmail.com",
  "contactFirstName": "Haseeb",
  "contactLastName": "Ali",
  "companyName": "",
  "contactPhone": "1233333",
  "shippingMethodsJson": [
    {
      "carrier": "freeshipping",
      "description": "",
      "deliveryDateTime": null,
      "deliveryDays": null,
      "origRate": 0,
      "rate": 0,
      "id": "uC6tjBvFKAlrzb5Rh21nVmkG",
      "methodName": "freeshipping"
    }
  ],
  "pricing": {
    "productsTotal": 9,
    "origTotal": 9,
    "subTotal": 9,
    "tax": 0.9,
    "totalCouponDiscount": 0,
    "totalAfterCoupon": 9.9,
    "total": 9.9
  },
  "couponCodesInfo": []
}
```

This endpoint starts a checkout (returns all avail shipping methods if address token is set)

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/checkout/info`

### Query Parameters

| Parameter        | Required                                                        | Unique | Description                                                 |
| ---------------- | --------------------------------------------------------------- | ------ | ----------------------------------------------------------- |
| addressToken     | true (possible to post this in a other call then contact email) | -      | Customer Address                                            |
| contactEmail     | true (possible to post this in a other call then address token) |        | Customer Email (Gets filled automaticlly if not set)        |
| contactPhone     | true (possible to post this in a other call then address token) |        | Customer Phone (Gets filled automaticlly if not set)        |
| contactFirstName | false                                                           | false  | Customer First Name (Gets filled automaticlly if not set)   |
| contactLastName  | false                                                           | false  | Customer Last Name (Gets filled automaticlly if not set)    |
| companyName      | false                                                           | false  | Customer Company Name (Gets filled automaticlly if not set) |

## Chekout Step 2 (Choose shipping method)

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/checkout/shippingmethod \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{"shippingMethodId" : "123456789"}'

```

> The above command returns JSON structured like this

```json
{
  "id": 821,
  "cartToken": "cart_ChXDOtbOnQSZRtH4LoKkfDFU",
  "customerToken": "cs_BXW5tm36lo2QHdAs634YYwAj6o4xItx3lbIK",
  "couponCodes": null,
  "addressToken": "adrs_xipKF02Td5eJ66IoEyzHdXUM",
  "shippingMethod": null,
  "shippingMethodId": "",
  "shippingAddressLabel": "",
  "shippingAddress": {
    "address": "abc",
    "address2": "",
    "city": "New York",
    "state": "New York",
    "zip": "71005",
    "country": "",
    "phone": "",
    "mobile": "",
    "specialValues": []
  },
  "contactEmail": "ha.haseeb29@gmail.com",
  "contactFirstName": "Haseeb",
  "contactLastName": "Ali",
  "companyName": "",
  "contactPhone": "1233333",
  "shippingMethodsJson": [
    {
      "carrier": "freeshipping",
      "description": "",
      "deliveryDateTime": null,
      "deliveryDays": null,
      "origRate": 0,
      "rate": 0,
      "id": "uC6tjBvFKAlrzb5Rh21nVmkG",
      "methodName": "freeshipping"
    }
  ],
  "pricing": {
    "productsTotal": 9,
    "origTotal": 9,
    "subTotal": 9,
    "tax": 0.9,
    "totalCouponDiscount": 0,
    "totalAfterCoupon": 9.9,
    "total": 9.9
  },
  "couponCodesInfo": []
}
```

This endpoint selects a shipping method id (returned with each method) and returns the new total

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/checkout/info`

### Query Parameters

| Parameter        | Required | Description        |
| ---------------- | -------- | ------------------ |
| shippingMethodId | true     | Shipping method Id |
| cartToken        | true     | Cart Token         |
| po               | false    | -                  |

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/checkout/payment`

## Chekout Step 3 OPTION 1: Payment

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/checkout/payment \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{"cardNumbers" : "4242424242424242", "expMonth" : "12", "expYear" : "2025", "cvv" : "123", "amount" : "333", "po" : "PO-123456", "nameOnCard": "testChayelle BillingName", "billingPhone": "8455225252","billingAddress": "117 Maple Ave Bill","billingCity": "Bala Cynwyd Bill", "billingState": "Pennsylvania Bill", "billingZip": "19004", "orderNotePublic" :"this is a note submitted by the customer at payment" }'

```

> The above command returns JSON structured like this

```json
{
  "status": "success",
  "order": {
    "orderProducts": [
      {
        "cartToken": "cart_ChXDOtbOnQSZRtH4LoKkfDFU",
        "cartProdToken": "cp_79ZYOHiz6ZWmpIXlIxYAvEB8",
        "addOnToProdToken": "",
        "cartProdQuantity": 1,
        "addOnProdTokens": null,
        "prodToken": "vrnt_fwSP2CWn0v72Ag0c",
        "deleted": 0,
        "companyToken": "comp_sfgb50s0dsdgsfh5g",
        "siteToken": "site_dg30sdfsgdsgsvv",
        "customerToken": "cust_mKlmFU2BuyLg59nwVHToivs3",
        "cartCreated": "1638443146",
        "cartLastTouched": "1638443146",
        "prodStaticCollections": ["clcs_pZYTDuzGLEQjvvlW"],
        "specialValues": [],
        "product": {
          "prodToken": "prod_2zza34TZ9v6Aidya",
          "variantToken": "vrnt_fwSP2CWn0v72Ag0c",
          "companyToken": "comp_sfgb50s0dsdgsfh5g",
          "variantName": "Placeat aut consequ",
          "variantImage": {
            "file": "[]"
          },
          "variantImages": [],
          "variantWeight": "55",
          "variantDimW": "76",
          "variantDimL": "3",
          "variantDimH": "4",
          "variantUpc": "Tempora voluptatem u",
          "variantNumber": "Ut eaque dolor conse",
          "manufacturerPartNumber": "Veritatis labore lau",
          "variantPrice": 9,
          "variantMapPrice": 0,
          "variantMsrpPrice": 0,
          "variantDisplayPrice": 21,
          "variantDescription": "",
          "variantAlert": "",
          "variantLowlevel": "46",
          "variantSlug": "placeat-aut-consequ",
          "variantVisible": 1,
          "variantAllowCheckout": 0,
          "variantCheckInvetory": 0,
          "variantTrackInventory": 0,
          "taxType": "",
          "taxable": 1,
          "inventoryCount": "4",
          "shippingProduct": 0,
          "variantMetaTitle": "",
          "variantMetaDescription": "",
          "variantBrand": "",
          "google_variantCategory": "",
          "google_variantType": "",
          "google_variantCondition": "",
          "hideGoogleData": 0,
          "sortOrder": 0,
          "dateCreated": "1620318552",
          "deleted": 0,
          "backOrderWarning": 0,
          "variantInStock": true,
          "prodName": "Voluptate totam anim",
          "prodImage": {
            "file": ""
          }
        },
        "addOnProducts": [],
        "pricing": {
          "total": 9
        },
        "shipping": {
          "totalWeight": 55
        }
      }
    ],
    "orderEmail": "ha.haseeb29@gmail.com",
    "orderShippingMethod": {
      "carrier": "freeshipping",
      "description": "",
      "deliveryDateTime": null,
      "deliveryDays": null,
      "origRate": 0,
      "rate": 0,
      "id": "uC6tjBvFKAlrzb5Rh21nVmkG",
      "methodName": "freeshipping"
    },
    "orderTotal": 9.9,
    "orderTax": 0.9,
    "orderShipping": 0,
    "orderWeight": 55,
    "orderShippingAddress": "{\"address\":\"abc\",\"address2\":\"\",\"city\":\"New York\",\"state\":\"New York\",\"zip\":\"71005\",\"country\":\"\",\"phone\":\"\",\"mobile\":\"\",\"specialValues\":[]}",
    "orderPaymentMethod": {
      "xResult": "A",
      "xStatus": "Approved",
      "xError": "",
      "xErrorCode": "00000",
      "xRefNum": "554234277",
      "xExp": "0123",
      "xAuthCode": "27119A",
      "xBatch": "5150840",
      "xAvsResultCode": "NNN",
      "xAvsResult": "Address: No Match & 5 Digit Zip: No Match",
      "xCvvResultCode": "",
      "xCvvResult": "No CVV data available",
      "xAuthAmount": "9.90",
      "xMaskedCardNumber": "4xxxxxxxxxxx4242",
      "xCardType": "Visa",
      "xName": "Haseeb Ali",
      "xToken": "724h3q7h9n07n792m9pmppmp1q02nmhn",
      "xMID": "xxxxxxxxxx9999",
      "xTID": "xxxxx6789",
      "xCurrency": "USD",
      "xDate": "12/2/2021 6:19:14 AM",
      "xEntryMethod": "Keyed",
      "cardToken": "cc_OJctC8FyAXnk"
    },
    "contactLastName": "Ali",
    "contactFirstName": "Haseeb",
    "orderProdQuantity": 1,
    "paymentObject": "{\"xResult\":\"A\",\"xStatus\":\"Approved\",\"xError\":\"\",\"xErrorCode\":\"00000\",\"xRefNum\":\"554234277\",\"xExp\":\"0123\",\"xAuthCode\":\"27119A\",\"xBatch\":\"5150840\",\"xAvsResultCode\":\"NNN\",\"xAvsResult\":\"Address: No Match & 5 Digit Zip: No Match\",\"xCvvResultCode\":\"\",\"xCvvResult\":\"No CVV data available\",\"xAuthAmount\":\"9.90\",\"xMaskedCardNumber\":\"4xxxxxxxxxxx4242\",\"xCardType\":\"Visa\",\"xName\":\"Haseeb Ali\",\"xToken\":\"724h3q7h9n07n792m9pmppmp1q02nmhn\",\"xMID\":\"xxxxxxxxxx9999\",\"xTID\":\"xxxxx6789\",\"xCurrency\":\"USD\",\"xDate\":\"12\\/2\\/2021 6:19:14 AM\",\"xEntryMethod\":\"Keyed\",\"cardToken\":\"cc_OJctC8FyAXnk\"}",
    "cardToken": "cc_OJctC8FyAXnk",
    "orderIP": "103.151.236.50",
    "cartToken": "cart_ChXDOtbOnQSZRtH4LoKkfDFU",
    "po": "",
    "BillToName": "Haseeb Ali",
    "BillToAddress": "{\"name\":\"Haseeb Ali\",\"address\":\"abc\",\"address2\":\"\",\"zip\":\"71005\",\"city\":\"New York\",\"state\":\"New York\",\"country\":\"\",\"mobile\":\"\",\"phone\":\"\"}",
    "orderNotePublic": "",
    "siteToken": "site_dg30sdfsgdsgsvv",
    "companyToken": "comp_sfgb50s0dsdgsfh5g",
    "customerToken": "cust_mKlmFU2BuyLg59nwVHToivs3",
    "orderToken": "ordr_Bv0Opb8czca0o03czpwXz8Wj",
    "orderNumber": 117,
    "orderStatus": "os_awaiting_fulfillment",
    "checkoutObject": "{\"id\":821,\"cartToken\":\"cart_ChXDOtbOnQSZRtH4LoKkfDFU\",\"customerToken\":\"cs_BXW5tm36lo2QHdAs634YYwAj6o4xItx3lbIK\",\"couponCodes\":null,\"addressToken\":\"adrs_xipKF02Td5eJ66IoEyzHdXUM\",\"shippingMethod\":{\"carrier\":\"freeshipping\",\"description\":\"\",\"deliveryDateTime\":null,\"deliveryDays\":null,\"origRate\":0,\"rate\":0,\"id\":\"uC6tjBvFKAlrzb5Rh21nVmkG\",\"methodName\":\"freeshipping\"},\"shippingMethodId\":\"uC6tjBvFKAlrzb5Rh21nVmkG\",\"shippingAddressLabel\":\"\",\"shippingAddress\":{\"address\":\"abc\",\"address2\":\"\",\"city\":\"New York\",\"state\":\"New York\",\"zip\":\"71005\",\"country\":\"\",\"phone\":\"\",\"mobile\":\"\",\"specialValues\":[]},\"contactEmail\":\"ha.haseeb29@gmail.com\",\"contactFirstName\":\"Haseeb\",\"contactLastName\":\"Ali\",\"companyName\":\"\",\"contactPhone\":\"1233333\",\"shippingMethodsJson\":[{\"carrier\":\"freeshipping\",\"description\":\"\",\"deliveryDateTime\":null,\"deliveryDays\":null,\"origRate\":0,\"rate\":0,\"id\":\"uC6tjBvFKAlrzb5Rh21nVmkG\",\"methodName\":\"freeshipping\"}],\"pricing\":{\"productsTotal\":9,\"origTotal\":9,\"subTotal\":9,\"tax\":0.9,\"totalCouponDiscount\":0,\"totalAfterCoupon\":9.9,\"total\":9.9},\"couponCodesInfo\":[]}",
    "customerObject": "{\"id\":0,\"customerFirstName\":\"Haseeb \",\"customerLastName\":\"Ali\",\"customerEmail\":\"ha.haseeb29@gmail.com\",\"customerPhone\":\"0313445214\",\"customerCompanyName\":\"abcd\",\"dateCreated\":\"1635837718\",\"customerStatus\":\"\",\"customerTypes\":null,\"customerGroups\":null,\"isLoggedIn\":0,\"customerDocs\":null,\"taxExempt\":null,\"taxExemptID\":null,\"createdAt\":\"2021-11-02 07:21:58\",\"editedAt\":\"2021-11-02 12:04:02\"}"
  }
}
```

This endpoint pays the checkout and creates an order

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/checkout/payment`

### Query Parameters

| Parameter           | Required             | Unique | Description                                                                                                                                                                                         |
| ------------------- | -------------------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| cardNumbers         | true(if no token)    | false  | Card Numbers                                                                                                                                                                                        |
| expMonth            | true (if no token)   | false  | Card Exp Month                                                                                                                                                                                      |
| expYear             | true (if no token)   | false  | Card Exp Year                                                                                                                                                                                       |
| cvv                 | true (if no token)   | false  | Card CVV                                                                                                                                                                                            |
| cardToken           | true (if no numbers) | false  | cardToken. if card has billing address, and you do not send sameAsShipping: false, it will take shipping address for billing address                                                                |
| billingAddressLine2 | false                | false  | Billing Address Line 2                                                                                                                                                                              |
| billingZip          | false                | false  | Billing Address Zip                                                                                                                                                                                 |
| billingAddress      | false                | false  | Billing Address                                                                                                                                                                                     |
| billingCity         | false                | false  | Billing Address City                                                                                                                                                                                |
| billingState        | false                | false  | Billing Address State                                                                                                                                                                               |
| billingName         | false                | false  | Billing Address Name                                                                                                                                                                                |
| billingPhone        | false                | false  | Billing Phone Number                                                                                                                                                                                |
| billingMobile       | false                | false  | Billing Mobile Number                                                                                                                                                                               |
| billingCountry      | false                | false  | Billing Address Country                                                                                                                                                                             |
| sameAsShipping      | true                 | false  | Will set billing address same as shipping even if cardToken is provided (see above)                                                                                                                 |
| billingAddressToken | false                | false  | Billing Address Token                                                                                                                                                                               |
| PO                  | false                | fasle  | Identifying Purchase Order number. Can include digits, letters (which will be converted to upper case), dashes and dots. All other characters will not be procesed and will return an error message |
| orderNotePublic     | false                | fasle  | Order Note Public                                                                                                                                                                                   |


## Checkout Step 3 OPTION 2: Process as a PO

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/checkout/po \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: user_token' \
  --header '{
               "po": "123-P9ojd",
               "billingName": "431 Systems LLC",
                "billingAddress": "10 Eros Drive",
                "billingCity": "Airmont",
                "billingState": "NY",
                "billingZip": "10952",
                "billingCountry": "United States",
                "billingPhone": "000000",
                "orderNotePublic": "order paid through PO pathway"
            }'
```

> The above command returns JSON structured like this

```json
{
    "status": "success",
    "order": {
        "orderProducts": [
            {
                "cartToken": "cart_8II78afqDL1NC9pvEagHwlTB",
                "cartProdToken": "cp_N0HqKE2o0NPgKCiUiA6nhHoL",
                "cartProdQuantity": 1,
                "addOnToProdToken": "",
                "addOnProdTokens": null,
                "prodToken": "vrnt_Mt75VgrGixqkYsOB",
                "deleted": 0,
                "createdAt": "2022-12-08 12:34:27",
                "editedAt": "2022-12-08 12:34:27",
                "companyToken": "comp_dft6yhzjkli",
                "siteToken": "site_Dpawt345k2m4",
                "customerToken": "cust_PGenT8ngCNC4J5FyvAh4Jc3z",
                "cartCreated": "1670502867",
                "cartLastTouched": "1670502867",
                "prodStaticCollections": [],
                "specialValues": [],
                "product": {
                    "prodToken": "prod_6jy8JYtQ3FfKh4th",
                    "variantToken": "vrnt_Mt75VgrGixqkYsOB",
                    "companyToken": "comp_dft6yhzjkli",
                    "variantName": "viral",
                    "variantImage": [],
                    "variantImages": [],
                    "variantWeight": "",
                    "variantDimW": "",
                    "variantDimL": "",
                    "variantDimH": "",
                    "variantUpc": "",
                    "variantNumber": "",
                    "manufacturerPartNumber": "",
                    "variantPrice": 0.1,
                    "variantMapPrice": 0,
                    "variantMsrpPrice": 0,
                    "variantDisplayPrice": 0,
                    "variantDescription": "",
                    "variantAlert": "",
                    "variantLowlevel": "",
                    "variantSlug": "",
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
                    "inventoryCount": -2,
                    "shippingProduct": 0,
                    "variantMetaTitle": "",
                    "variantMetaDescription": "",
                    "variantBrand": "",
                    "sortOrder": 0,
                    "dateCreated": "1667771464",
                    "deleted": 0,
                    "backOrderWarning": 0,
                    "createdAt": "2022-11-06 21:51:04",
                    "editedAt": "2022-12-08 11:43:32",
                    "variantInStock": true,
                    "prodName": "Practical Soft Cheese redundant",
                    "prodImage": {
                        "file": "magni-quaerat-et"
                    }
                },
                "addOnProducts": [],
                "pricing": {
                    "total": 0.1
                },
                "shipping": {
                    "totalWeight": 0
                }
            }
        ],
        "orderEmail": "chayelle+102Shaylee@evelt.com",
        "orderShippingMethod": {
            "carrier": "freeshipping",
            "description": "",
            "deliveryDateTime": null,
            "deliveryDays": null,
            "origRate": 0,
            "rate": 0,
            "id": "BQRJmVECcNaT37w5Aq8h2fot",
            "methodName": ""
        },
        "orderTotal": 0.1,
        "orderTotalPaid": 0,
        "orderTax": 0,
        "orderShipping": 0,
        "orderWeight": 0,
        "orderShippingAddress": "{\"address\":\"12354 Main Street\",\"address2\":\"\",\"city\":\"Monsey\",\"state\":\"NY\",\"zip\":\"10952\",\"country\":\"\",\"phone\":\"\",\"mobile\":\"\",\"specialValues\":[]}",
        "orderPaymentMethod": null,
        "contactLastName": "Green - shippingName",
        "contactFirstName": "John - shippingName",
        "orderProdQuantity": 1,
        "paymentObject": null,
        "cardToken": null,
        "orderIP": "86.183.104.179",
        "cartToken": "cart_8II78afqDL1NC9pvEagHwlTB",
        "PO": "123-P9ojd",
        "BillToName": "John - shippingName Green - shippingName",
        "BillToAddress": "{\"name\":\"John - shippingName Green - shippingName\",\"address\":\"12354 Main Street\",\"address2\":\"\",\"zip\":\"10952\",\"city\":\"Monsey\",\"state\":\"NY\",\"country\":\"\",\"mobile\":\"\",\"phone\":\"\"}",
        "orderNotePublic": "order paid through PO pathway",
        "siteToken": "site_Dpawt345k2m4",
        "companyToken": "comp_dft6yhzjkli",
        "customerToken": "cust_PGenT8ngCNC4J5FyvAh4Jc3z",
        "orderToken": "ordr_dgzABf0dod39Bdtno5zwkfIe",
        "orderNumber": 200606,
        "orderStatus": "os_awaiting_fulfillment",
        "checkoutObject": "{\"id\":30557,\"cartToken\":\"cart_8II78afqDL1NC9pvEagHwlTB\",\"customerToken\":\"cs_3PheG4dLHNvWxlWYvPJunkyXPsGp9qn4vdmD\",\"couponCodes\":null,\"addressToken\":\"adrs_8yY55uZos2WfmnqUhfnBsuU1\",\"shippingMethod\":{\"carrier\":\"freeshipping\",\"description\":\"\",\"deliveryDateTime\":null,\"deliveryDays\":null,\"origRate\":0,\"rate\":0,\"id\":\"BQRJmVECcNaT37w5Aq8h2fot\",\"methodName\":\"\"},\"shippingMethodId\":\"BQRJmVECcNaT37w5Aq8h2fot\",\"shippingAddressLabel\":\"\",\"shippingAddress\":{\"address\":\"12354 Main Street\",\"address2\":\"\",\"city\":\"Monsey\",\"state\":\"NY\",\"zip\":\"10952\",\"country\":\"\",\"phone\":\"\",\"mobile\":\"\",\"specialValues\":[]},\"contactEmail\":\"chayelle+102Shaylee@evelt.com\",\"contactPhone\":\"925-755-7647\",\"shippingMethodsJson\":[{\"carrier\":\"freeshipping\",\"description\":\"\",\"deliveryDateTime\":null,\"deliveryDays\":null,\"origRate\":0,\"rate\":0,\"id\":\"BQRJmVECcNaT37w5Aq8h2fot\",\"methodName\":\"\"}],\"contactFirstName\":\"John - shippingName\",\"contactLastName\":\"Green - shippingName\",\"companyName\":\"Steuber, Schamberger and Leffler\",\"createdAt\":\"2022-12-08 12:34:38\",\"editedAt\":\"2022-12-08 12:34:46\",\"pricing\":{\"productsTotal\":0.1,\"origTotal\":0.1,\"subTotal\":0.1,\"tax\":0,\"totalCouponDiscount\":0,\"totalAfterCoupon\":0.1,\"total\":0.1},\"couponCodesInfo\":[]}",
        "customerObject": "{\"id\":53237,\"customerFirstName\":\"Zula\",\"customerLastName\":\"Gottlieb\",\"customerEmail\":\"chayelle+102Shaylee@evelt.com\",\"customerPhone\":\"925-755-7647\",\"customerCompanyName\":\"Steuber, Schamberger and Leffler\",\"dateCreated\":\"1670502805\",\"customerStatus\":\"cs_approved\",\"customerTypes\":null,\"customerGroups\":null,\"isLoggedIn\":1,\"customerDocs\":null,\"taxExempt\":null,\"taxExemptID\":null,\"createdAt\":\"2022-12-08 12:33:25\",\"editedAt\":\"2022-12-08 12:34:55\"}",
        "dateCreated": 1670502895
    }
}
```

This endpoint pays the checkout and creates an order

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/checkout/po`

### Query Parameters

| Parameter           | Required             | Unique | Description                                                                                                                                                                                         |
| ------------------- | -------------------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| billingAddressLine2 | true                | false  | Billing Address Line 2                                                                                                                                                                              |
| billingZip          | true                | false  | Billing Address Zip                                                                                                                                                                                 |
| billingAddress      | true                | false  | Billing Address                                                                                                                                                                                     |
| billingCity         | true                | false  | Billing Address City                                                                                                                                                                                |
| billingState        | true                | false  | Billing Address State                                                                                                                                                                               |
| nameOnCard         | true                | false  | Billing Address Name                                                                                                                                                                                |
| billingPhone        | true                | false  | Billing Phone Number                                                                                                                                                                                |
| billingMobile       | true                | false  | Billing Mobile Number                                                                                                                                                                               |
| billingCountry      | true                | false  | Billing Address Country                                                                                                                                                                             |
| PO                  | true            |false       | Identifying Purchase Order number. Can include digits, letters (which will be converted to upper case), dashes and dots. All other characters will not be procesed and will return an error message |
| orderNotePublic     | false                | fasle  | Order Note Public    

## Checkout Apply Coupon

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/checkout/applycoupon \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{"couponCode" : "SUMMER20"}'

```

> The above command returns JSON structured like this

```json
{
  "id": "117",
  "cartToken": "cart_E4uK4GcsbriLcQdangGrvYSq",
  "customerToken": "cust_HgjzzebMZgssVUqv2aCYbBUk",
  "couponCodes": ["SUMMER50"],
  "addressToken": "",
  "shippingMethod": "",
  "shippingMethodId": "",
  "shippingAddress": "",
  "shippingAddress2": "",
  "shippingZip": "",
  "shippingState": "",
  "shippingCity": "",
  "contactEmail": "",
  "contactFirstName": "",
  "contactLastName": "",
  "companyName": "",
  "contactPhone": "",
  "shippingMethodsJson": "",
  "pricing": {
    "productsTotal": 329.95,
    "origTotal": 329.95,
    "totalCouponDiscount": 164.975,
    "totalAfterCoupon": 164.98,
    "tax": 0,
    "subTotal": 164.98,
    "total": 164.98
  },
  "couponCodesInfo": [
    {
      "name": "SUMMER50",
      "msg": "Sucssecfully applied",
      "status": "valid"
    }
  ]
}
```

This endpoint applies a coupon code to a cart

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/checkout/applycoupon`

### Query Parameters

| Parameter  | Required | Unique | Description     |
| ---------- | -------- | ------ | --------------- |
| couponCode | true     | -      | The Coupon Code |

##Checkout Remove Coupon

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/checkout/removecoupon \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{"couponCode" : "SUMMER20"}'

```

> The above command returns JSON structured like this

```json
{
  "id": "117",
  "cartToken": "cart_E4uK4GcsbriLcQdangGrvYSq",
  "customerToken": "cust_HgjzzebMZgssVUqv2aCYbBUk",
  "couponCodes": [],
  "addressToken": "",
  "shippingMethod": "",
  "shippingMethodId": "",
  "shippingAddress": "",
  "shippingAddress2": "",
  "shippingZip": "",
  "shippingState": "",
  "shippingCity": "",
  "contactEmail": "",
  "contactFirstName": "",
  "contactLastName": "",
  "companyName": "",
  "contactPhone": "",
  "shippingMethodsJson": "",
  "pricing": {
    "productsTotal": 329.95,
    "origTotal": 329.95,
    "totalCouponDiscount": null,
    "totalAfterCoupon": 329.95,
    "tax": 0,
    "subTotal": 329.95,
    "total": 329.95
  },
  "couponCodesInfo": []
}
```

This endpoint removes a coupon code from a cart

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/checkout/removecoupon`

### Query Parameters

| Parameter  | Required | Unique | Description     |
| ---------- | -------- | ------ | --------------- |
| couponCode | true     | -      | The Coupon Code |
