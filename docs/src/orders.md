# Orders

## Get all orders by customer

This endpoint retrieves orders for a specified customer


#### HTTP Request
`GET https://apistore.csomni.com/orders`

### Header Requirements

| Parameter   | Description                     |
| ----------- | ------------------------------- |
| customerToken | Login token associated with customer |
| token        | Site token |


```shell
curl --request GET \
  --url https://apistore.csomni.com/orders \
  --header 'token: usr_token'\
  --header 'token: site_token
```

> The above command returns JSON structured like this:

```json
[
    {
        "orderToken": "ordr_123456",
        "orderNumber": 200349,
        "companyToken": "comp_123456",
        "PO": "",
        "siteToken": "site_123456",
        "customerToken": "cust_123456",
        "orderProducts": [
            {
                "cartToken": "cart_123456",
                "cartProdToken": "cp_123456",
                "cartProdQuantity": 1,
                "addOnToProdToken": "",
                "addOnProdTokens": null,
                "prodToken": "vrnt_123456",
                "deleted": 0,
                "createdAt": "2022-11-27 22:34:02",
                "editedAt": "2022-11-27 22:34:02",
                "companyToken": "comp_123456",
                "siteToken": "site_123456",
                "customerToken": "cust_123456",
                "cartCreated": "1669588442",
                "cartLastTouched": "1669588442",
                "prodStaticCollections": [],
                "specialValues": [],
                "product": {
                    "prodToken": "prod_123456",
                    "variantToken": "vrnt_123456",
                    "companyToken": "comp_123456",
                    "variantName": "Ameliorated",
                    "variantImage": [],
                    "variantImages": [],
                    "variantWeight": "1",
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
                    "inventoryCount": 78,
                    "shippingProduct": 0,
                    "variantMetaTitle": "",
                    "variantMetaDescription": "",
                    "variantBrand": "",
                    "sortOrder": 2,
                    "dateCreated": "1668684651",
                    "deleted": 0,
                    "backOrderWarning": 0,
                    "createdAt": "2022-11-17 11:30:51",
                    "editedAt": "2022-11-27 22:32:33",
                    "variantInStock": true,
                    "prodName": "Tasty Concrete ChipsBacon",
                    "prodImage": {
                        "file": ""
                    }
                },
                "addOnProducts": [],
                "pricing": {
                    "total": 0.1
                },
                "shipping": {
                    "totalWeight": 1
                }
            }
        ],
        "BillToName": "Sarah - shippingName Jones - shippingName",
        "BillToAddress": "{\"name\":\"Sarah - shippingName Jones - shippingName\",\"address\":\"12354 Main Street\",\"address2\":\"\",\"zip\":\"10952\",\"city\":\"Monsey\",\"state\":\"NY\",\"country\":\"\",\"mobile\":\"\",\"phone\":\"\"}",
        "orderShippingMethod": {
            "carrier": "freeshipping",
            "description": "",
            "deliveryDateTime": null,
            "deliveryDays": null,
            "origRate": 0,
            "rate": 0,
            "id": "123456",
            "methodName": ""
        },
        "orderShippingAddress": {
            "address": "12354 Main Street",
            "address2": "",
            "city": "Monsey",
            "state": "NY",
            "zip": "10952",
            "country": "",
            "phone": "",
            "mobile": "",
            "specialValues": []
        },
        "orderTotal": "0.1",
        "orderTax": "0",
        "orderTotalPaid": null,
        "orderShipping": "0",
        "orderStatus": "os_awaiting_fulfillment",
        "customerObject": {
            "id": 52806,
            "customerFirstName": "Sarah",
            "customerLastName": "Jones",
            "customerEmail": "sjones1.com",
            "customerPhone": "123-456-7890",
            "customerCompanyName": "Tyrell Corp",
            "dateCreated": "1669588428",
            "customerStatus": "cs_reg_customer",
            "customerTypes": null,
            "customerGroups": null,
            "isLoggedIn": 1,
            "customerDocs": null,
            "taxExempt": null,
            "taxExemptID": null,
            "createdAt": "2022-11-27 22:33:48",
            "editedAt": "2022-11-27 22:33:48"
        },
        "orderWeight": 1,
        "contactFirstName": "Sarah - shippingName",
        "contactLastName": "Jones - shippingName",
        "orderEmail": "sjones1@gmail.com",
        "orderNotePublic": "this is a public note I wrote and submited through payment checkout api call",
        "cartToken": "cart_123456",
        "orderPaymentMethod": {
            "xResult": "A",
            "xStatus": "Approved",
            "xError": "",
            "xErrorCode": "00000",
            "xRefNum": "760465207",
            "xExp": "0325",
            "xDate": "11/27/2022 5:34:39 PM",
            "xAuthCode": "678485",
            "xBatch": "100202",
            "xAvsResultCode": "YYY",
            "xAvsResult": "Address: Match & 5 Digit Zip: Match",
            "xCvvResultCode": "",
            "xCvvResult": "No CVV data available",
            "xAuthAmount": "0.10",
            "xToken": "1234567890",
            "xMaskedCardNumber": "5xxxxxxxxxxx0666",
            "xCardType": "MasterCard",
            "xName": "Sarah - shippingName Jones - shippingName",
            "cardToken": "cc_123456"
        },
        "checkoutObject": {
            "id": 30450,
            "cartToken": "cart_123456",
            "customerToken": "cs_123456",
            "couponCodes": null,
            "addressToken": "adrs_123456",
            "shippingMethod": {
                "carrier": "freeshipping",
                "description": "",
                "deliveryDateTime": null,
                "deliveryDays": null,
                "origRate": 0,
                "rate": 0,
                "id": "123456",
                "methodName": ""
            },
            "shippingMethodId": "123456",
            "shippingAddressLabel": "",
            "shippingAddress": {
                "address": "12354 Main Street",
                "address2": "",
                "city": "Monsey",
                "state": "NY",
                "zip": "10952",
                "country": "",
                "phone": "",
                "mobile": "",
                "specialValues": []
            },
            "contactEmail": "sjones1@gmail.com",
            "contactPhone": "123-456-7890",
            "shippingMethodsJson": [
                {
                    "carrier": "freeshipping",
                    "description": "",
                    "deliveryDateTime": null,
                    "deliveryDays": null,
                    "origRate": 0,
                    "rate": 0,
                    "id": "123456",
                    "methodName": ""
                },
                {
                    "desc": "UPS Ground",
                    "rate": 13.164000000000001,
                    "currency": "USD",
                    "service_code": "03",
                    "est_delivery_time": "2022-11-29T23:00:00-00:00",
                    "delivery_days": 1,
                    "package_type": "02",
                    "rate_detail": [
                        {
                            "amount": 10.97,
                            "currency": "USD",
                            "type": "TransportationCharges"
                        },
                        {
                            "amount": 0,
                            "currency": "USD",
                            "type": "376"
                        },
                        {
                            "amount": 1.61,
                            "currency": "USD",
                            "type": "375"
                        },
                        {
                            "amount": 9.36,
                            "currency": "USD",
                            "type": "BaseServiceCharge"
                        }
                    ],
                    "billing_weight": 1,
                    "carrier": "ups",
                    "description": "UPS Ground",
                    "deliveryDateTime": "2022-11-29T23:00:00-00:00",
                    "deliveryDays": 1,
                    "origRate": 10.97,
                    "id": "123456",
                    "methodName": ""
                },
                {
                    "desc": "UPS 3 Day Select",
                    "rate": 19.416,
                    "currency": "USD",
                    "service_code": "12",
                    "est_delivery_time": "2022-12-01T23:00:00-00:00",
                    "delivery_days": 3,
                    "package_type": "02",
                    "rate_detail": [
                        {
                            "amount": 16.18,
                            "currency": "USD",
                            "type": "TransportationCharges"
                        },
                        {
                            "amount": 0,
                            "currency": "USD",
                            "type": "376"
                        },
                        {
                            "amount": 2.61,
                            "currency": "USD",
                            "type": "375"
                        },
                        {
                            "amount": 13.57,
                            "currency": "USD",
                            "type": "BaseServiceCharge"
                        }
                    ],
                    "billing_weight": 1,
                    "carrier": "ups",
                    "description": "UPS 3 Day Select",
                    "deliveryDateTime": "2022-12-01T23:00:00-00:00",
                    "deliveryDays": 3,
                    "origRate": 16.18,
                    "id": "123456",
                    "methodName": ""
                },
                {
                    "desc": "Priority Mail Large Flat Rate Box",
                    "rate": 27.45,
                    "currency": "USD",
                    "service_code": "22",
                    "est_delivery_time": "2022-11-30",
                    "package_type": "",
                    "rate_detail": null,
                    "guaranteed": false,
                    "zone": "1",
                    "carrier": "usps",
                    "description": "Priority Mail Large Flat Rate Box",
                    "deliveryDateTime": "2022-11-30",
                    "deliveryDays": "",
                    "origRate": 22.45,
                    "id": "123456",
                    "methodName": ""
                },
                {
                    "desc": "UPS 2nd Day Air",
                    "rate": 30.384,
                    "currency": "USD",
                    "service_code": "02",
                    "est_delivery_time": "2022-11-30T23:00:00-00:00",
                    "delivery_days": 2,
                    "package_type": "02",
                    "rate_detail": [
                        {
                            "amount": 25.32,
                            "currency": "USD",
                            "type": "TransportationCharges"
                        },
                        {
                            "amount": 4.09,
                            "currency": "USD",
                            "type": "375"
                        },
                        {
                            "amount": 21.23,
                            "currency": "USD",
                            "type": "BaseServiceCharge"
                        },
                        {
                            "amount": 0,
                            "currency": "USD",
                            "type": "376"
                        }
                    ],
                    "billing_weight": 1,
                    "carrier": "ups",
                    "description": "UPS 2nd Day Air",
                    "deliveryDateTime": "2022-11-30T23:00:00-00:00",
                    "deliveryDays": 2,
                    "origRate": 25.32,
                    "id": "123456",
                    "methodName": ""
                },
                {
                    "desc": "UPS Second Day Air AM",
                    "rate": 33.096,
                    "currency": "USD",
                    "service_code": "59",
                    "est_delivery_time": "2022-11-30T23:00:00-00:00",
                    "delivery_days": 2,
                    "package_type": "02",
                    "rate_detail": [
                        {
                            "amount": 27.58,
                            "currency": "USD",
                            "type": "TransportationCharges"
                        },
                        {
                            "amount": 0,
                            "currency": "USD",
                            "type": "376"
                        },
                        {
                            "amount": 4.45,
                            "currency": "USD",
                            "type": "375"
                        },
                        {
                            "amount": 23.13,
                            "currency": "USD",
                            "type": "BaseServiceCharge"
                        }
                    ],
                    "billing_weight": 1,
                    "carrier": "ups",
                    "description": "UPS Second Day Air AM",
                    "deliveryDateTime": "2022-11-30T23:00:00-00:00",
                    "deliveryDays": 2,
                    "origRate": 27.58,
                    "id": "123456",
                    "methodName": ""
                },
                {
                    "desc": "UPS Next Day Air Saver",
                    "rate": 45.132,
                    "currency": "USD",
                    "service_code": "13",
                    "est_delivery_time": "2022-11-29T23:00:00-00:00",
                    "delivery_days": 1,
                    "package_type": "02",
                    "rate_detail": [
                        {
                            "amount": 37.61,
                            "currency": "USD",
                            "type": "TransportationCharges"
                        },
                        {
                            "amount": 6.07,
                            "currency": "USD",
                            "type": "375"
                        },
                        {
                            "amount": 31.54,
                            "currency": "USD",
                            "type": "BaseServiceCharge"
                        },
                        {
                            "amount": 0,
                            "currency": "USD",
                            "type": "376"
                        }
                    ],
                    "billing_weight": 1,
                    "carrier": "ups",
                    "description": "UPS Next Day Air Saver",
                    "deliveryDateTime": "2022-11-29T23:00:00-00:00",
                    "deliveryDays": 1,
                    "origRate": 37.61,
                    "id": "123456",
                    "methodName": ""
                },
                {
                    "desc": "UPS Next Day Air",
                    "rate": 49.368,
                    "currency": "USD",
                    "service_code": "01",
                    "est_delivery_time": "2022-11-29T15:00:00-00:00",
                    "delivery_days": 1,
                    "package_type": "02",
                    "rate_detail": [
                        {
                            "amount": 41.14,
                            "currency": "USD",
                            "type": "TransportationCharges"
                        },
                        {
                            "amount": 0,
                            "currency": "USD",
                            "type": "376"
                        },
                        {
                            "amount": 6.64,
                            "currency": "USD",
                            "type": "375"
                        },
                        {
                            "amount": 34.5,
                            "currency": "USD",
                            "type": "BaseServiceCharge"
                        }
                    ],
                    "billing_weight": 1,
                    "carrier": "ups",
                    "description": "UPS Next Day Air",
                    "deliveryDateTime": "2022-11-29T15:00:00-00:00",
                    "deliveryDays": 1,
                    "origRate": 41.14,
                    "id": "123456",
                    "methodName": ""
                },
                {
                    "desc": "UPS Next Day Air Early AM",
                    "rate": 92.304,
                    "currency": "USD",
                    "service_code": "14",
                    "est_delivery_time": "2022-11-29T10:00:00-00:00",
                    "delivery_days": 1,
                    "package_type": "02",
                    "rate_detail": [
                        {
                            "amount": 76.92,
                            "currency": "USD",
                            "type": "TransportationCharges"
                        },
                        {
                            "amount": 12.42,
                            "currency": "USD",
                            "type": "375"
                        },
                        {
                            "amount": 64.5,
                            "currency": "USD",
                            "type": "BaseServiceCharge"
                        },
                        {
                            "amount": 0,
                            "currency": "USD",
                            "type": "376"
                        }
                    ],
                    "billing_weight": 1,
                    "carrier": "ups",
                    "description": "UPS Next Day Air Early AM",
                    "deliveryDateTime": "2022-11-29T10:00:00-00:00",
                    "deliveryDays": 1,
                    "origRate": 76.92,
                    "id": "123456",
                    "methodName": ""
                }
            ],
            "contactFirstName": "Sarah - shippingName",
            "contactLastName": "Jones - shippingName",
            "companyName": "Tyrell Corp",
            "createdAt": "2022-11-27 22:34:13",
            "editedAt": "2022-11-27 22:34:18",
            "pricing": {
                "productsTotal": 0.1,
                "origTotal": 0.1,
                "subTotal": 0.1,
                "tax": 0,
                "totalCouponDiscount": 0,
                "totalAfterCoupon": 0.1,
                "total": 0.1
            },
            "couponCodesInfo": []
        },
        "orderProdQuantity": "1",
        "paymentObject": {
            "xResult": "A",
            "xStatus": "Approved",
            "xError": "",
            "xErrorCode": "00000",
            "xRefNum": "760465207",
            "xExp": "0325",
            "xDate": "11/27/2022 5:34:39 PM",
            "xAuthCode": "678485",
            "xBatch": "100202",
            "xAvsResultCode": "YYY",
            "xAvsResult": "Address: Match & 5 Digit Zip: Match",
            "xCvvResultCode": "",
            "xCvvResult": "No CVV data available",
            "xAuthAmount": "0.10",
            "xToken": "1234567890",
            "xMaskedCardNumber": "5xxxxxxxxxxx0666",
            "xCardType": "MasterCard",
            "xName": "Sarah - shippingName Jones - shippingName",
            "cardToken": "cc_123456"
        },
        "cardToken": "cc_123456",
        "orderIP": "::1",
        "dateCreated": "1669588464",
        "deleted": "",
        "numberOfPackages": 0,
        "createdAt": "2022-11-27 22:34:24",
        "editedAt": "2022-11-27 22:34:24",
        "orderStatusValue": {
            "id": "os_awaiting_fulfillment",
            "name": "Awaiting Fulfillment",
            "color": "#ffc107"
        },
        "statusAndTerms": {
            "processingStatus": "Awaiting Fulfillment",
            "shippingStatus": "Pending",
            "paymentStatus": "Closed",
            "orderStatus": "Open",
            "paymentTerms": "Website Payment Transaction",
            "postPaymentStatus": "NULL"
        },
        "paymentHistory": [
            {
                "paymentHistoryToken": "pmth_123456",
                "orderToken": "ordr_123456",
                "amount": "0.1",
                "action": "charge",
                "dateTime": "1669588465",
                "paymentObject": "{\"xResult\":\"A\",\"xStatus\":\"Approved\",\"xError\":\"\",\"xErrorCode\":\"00000\",\"xRefNum\":\"760465207\",\"xExp\":\"0325\",\"xDate\":\"11\\/27\\/2022 5:34:39 PM\",\"xAuthCode\":\"678485\",\"xBatch\":\"100202\",\"xAvsResultCode\":\"YYY\",\"xAvsResult\":\"Address: Match & 5 Digit Zip: Match\",\"xCvvResultCode\":\"\",\"xCvvResult\":\"No CVV data available\",\"xAuthAmount\":\"0.10\",\"xToken\":\"1234567890\",\"xMaskedCardNumber\":\"5xxxxxxxxxxx0666\",\"xCardType\":\"MasterCard\",\"xName\":\"Sarah - shippingName Jones - shippingName\",\"cardToken\":\"cc_123456\"}",
                "cardToken": "cc_123456",
                "userToken": "omni",
                "createdAt": "2022-11-27 22:34:25",
                "editedAt": "2022-11-27 22:34:25"
            }
        ]
    }
]
```




## Get a specific order

This endpoint retrieves a specific order


### HTTP Request

`GET https://apistore.csomni.com/orders/[orderToken]`

### Header Requirements

| Parameter   | Description                     |
| ----------- | ------------------------------- |
| customerToken | Login token associated with customer |
| token        | Site token |

### URL Parameters

| Parameter   | Description                     |
| ----------- | ------------------------------- |
| Order Token | Token of the Order to retrieve. |

```shell
curl --request GET \
  --url https://apistore.csomni.com/orders/[orderToken] \
  --header 'token: 123'/
  --header 'customerToken: loginToken123'
```

> The above command returns JSON structured like this:

```json
{
    "orderToken": "ordr_123456",
    "orderNumber": 200349,
    "companyToken": "comp_123456",
    "PO": "",
    "siteToken": "site_123456",
    "customerToken": "cust_123456",
    "orderProducts": [
        {
            "cartToken": "cart_123456",
            "cartProdToken": "cp_123456",
            "cartProdQuantity": 1,
            "addOnToProdToken": "",
            "addOnProdTokens": null,
            "prodToken": "vrnt_123456",
            "deleted": 0,
            "createdAt": "2022-11-27 22:34:02",
            "editedAt": "2022-11-27 22:34:02",
            "companyToken": "comp_123456",
            "siteToken": "site_123456",
            "customerToken": "cust_123456",
            "cartCreated": "1669588442",
            "cartLastTouched": "1669588442",
            "prodStaticCollections": [],
            "specialValues": [],
            "product": {
                "prodToken": "prod_l123456",
                "variantToken": "vrnt_123456",
                "companyToken": "comp_123456",
                "variantName": "Ameliorated",
                "variantImage": [],
                "variantImages": [],
                "variantWeight": "1",
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
                "inventoryCount": 78,
                "shippingProduct": 0,
                "variantMetaTitle": "",
                "variantMetaDescription": "",
                "variantBrand": "",
                "sortOrder": 2,
                "dateCreated": "1668684651",
                "deleted": 0,
                "backOrderWarning": 0,
                "createdAt": "2022-11-17 11:30:51",
                "editedAt": "2022-11-27 22:32:33",
                "variantInStock": true,
                "prodName": "Tasty Concrete ChipsBacon",
                "prodImage": {
                    "file": ""
                }
            },
            "addOnProducts": [],
            "pricing": {
                "total": 0.1
            },
            "shipping": {
                "totalWeight": 1
            }
        }
    ],
    "BillToName": "Sarah - shippingName Jones - shippingName",
    "BillToAddress": "{\"name\":\"Sarah - shippingName Jones - shippingName\",\"address\":\"12354 Main Street\",\"address2\":\"\",\"zip\":\"10952\",\"city\":\"Monsey\",\"state\":\"NY\",\"country\":\"\",\"mobile\":\"\",\"phone\":\"\"}",
    "orderShippingMethod": {
        "carrier": "freeshipping",
        "description": "",
        "deliveryDateTime": null,
        "deliveryDays": null,
        "origRate": 0,
        "rate": 0,
        "id": "123456",
        "methodName": ""
    },
    "orderShippingAddress": {
        "address": "12354 Main Street",
        "address2": "",
        "city": "Monsey",
        "state": "NY",
        "zip": "10952",
        "country": "",
        "phone": "",
        "mobile": "",
        "specialValues": []
    },
    "orderTotal": "0.1",
    "orderTax": "0",
    "orderTotalPaid": null,
    "orderShipping": "0",
    "orderStatus": "os_awaiting_fulfillment",
    "customerObject": {
        "id": 52806,
        "customerFirstName": "Sarah",
        "customerLastName": "Jones",
        "customerEmail": "sjones1@gmail.com",
        "customerPhone": "123-456-7890",
        "customerCompanyName": "Tyrell Corp",
        "dateCreated": "1669588428",
        "customerStatus": "cs_reg_customer",
        "customerTypes": null,
        "customerGroups": null,
        "isLoggedIn": 1,
        "customerDocs": null,
        "taxExempt": null,
        "taxExemptID": null,
        "createdAt": "2022-11-27 22:33:48",
        "editedAt": "2022-11-27 22:33:48"
    },
    "orderWeight": 1,
    "contactFirstName": "Sarah - shippingName",
    "contactLastName": "Jones - shippingName",
    "orderEmail": "sjones1@gmail.com",
    "orderNotePublic": "this is a public note I wrote and submited through payment checkout api call",
    "cartToken": "cart_123456",
    "orderPaymentMethod": {
        "xResult": "A",
        "xStatus": "Approved",
        "xError": "",
        "xErrorCode": "00000",
        "xRefNum": "760465207",
        "xExp": "0325",
        "xDate": "11/27/2022 5:34:39 PM",
        "xAuthCode": "678485",
        "xBatch": "100202",
        "xAvsResultCode": "YYY",
        "xAvsResult": "Address: Match & 5 Digit Zip: Match",
        "xCvvResultCode": "",
        "xCvvResult": "No CVV data available",
        "xAuthAmount": "0.10",
        "xToken": "1234567890",
        "xMaskedCardNumber": "5xxxxxxxxxxx0666",
        "xCardType": "MasterCard",
        "xName": "Sarah - shippingName Jones - shippingName",
        "cardToken": "cc_123456"
    },
    "checkoutObject": {
        "id": 30450,
        "cartToken": "cart_123456",
        "customerToken": "cs_123456",
        "couponCodes": null,
        "addressToken": "adrs_123456",
        "shippingMethod": {
            "carrier": "freeshipping",
            "description": "",
            "deliveryDateTime": null,
            "deliveryDays": null,
            "origRate": 0,
            "rate": 0,
            "id": "123456",
            "methodName": ""
        },
        "shippingMethodId": "123456",
        "shippingAddressLabel": "",
        "shippingAddress": {
            "address": "12354 Main Street",
            "address2": "",
            "city": "Monsey",
            "state": "NY",
            "zip": "10952",
            "country": "",
            "phone": "",
            "mobile": "",
            "specialValues": []
        },
        "contactEmail": "sjones1@gmail.com",
        "contactPhone": "123-456-7890",
        "shippingMethodsJson": [
            {
                "carrier": "freeshipping",
                "description": "",
                "deliveryDateTime": null,
                "deliveryDays": null,
                "origRate": 0,
                "rate": 0,
                "id": "123456",
                "methodName": ""
            },
            {
                "desc": "UPS Ground",
                "rate": 13.164000000000001,
                "currency": "USD",
                "service_code": "03",
                "est_delivery_time": "2022-11-29T23:00:00-00:00",
                "delivery_days": 1,
                "package_type": "02",
                "rate_detail": [
                    {
                        "amount": 10.97,
                        "currency": "USD",
                        "type": "TransportationCharges"
                    },
                    {
                        "amount": 0,
                        "currency": "USD",
                        "type": "376"
                    },
                    {
                        "amount": 1.61,
                        "currency": "USD",
                        "type": "375"
                    },
                    {
                        "amount": 9.36,
                        "currency": "USD",
                        "type": "BaseServiceCharge"
                    }
                ],
                "billing_weight": 1,
                "carrier": "ups",
                "description": "UPS Ground",
                "deliveryDateTime": "2022-11-29T23:00:00-00:00",
                "deliveryDays": 1,
                "origRate": 10.97,
                "id": "123456",
                "methodName": ""
            },
            {
                "desc": "UPS 3 Day Select",
                "rate": 19.416,
                "currency": "USD",
                "service_code": "12",
                "est_delivery_time": "2022-12-01T23:00:00-00:00",
                "delivery_days": 3,
                "package_type": "02",
                "rate_detail": [
                    {
                        "amount": 16.18,
                        "currency": "USD",
                        "type": "TransportationCharges"
                    },
                    {
                        "amount": 0,
                        "currency": "USD",
                        "type": "376"
                    },
                    {
                        "amount": 2.61,
                        "currency": "USD",
                        "type": "375"
                    },
                    {
                        "amount": 13.57,
                        "currency": "USD",
                        "type": "BaseServiceCharge"
                    }
                ],
                "billing_weight": 1,
                "carrier": "ups",
                "description": "UPS 3 Day Select",
                "deliveryDateTime": "2022-12-01T23:00:00-00:00",
                "deliveryDays": 3,
                "origRate": 16.18,
                "id": "123456",
                "methodName": ""
            },
            {
                "desc": "Priority Mail Large Flat Rate Box",
                "rate": 27.45,
                "currency": "USD",
                "service_code": "22",
                "est_delivery_time": "2022-11-30",
                "package_type": "",
                "rate_detail": null,
                "guaranteed": false,
                "zone": "1",
                "carrier": "usps",
                "description": "Priority Mail Large Flat Rate Box",
                "deliveryDateTime": "2022-11-30",
                "deliveryDays": "",
                "origRate": 22.45,
                "id": "123456",
                "methodName": ""
            },123456
            {
                "desc": "UPS 2nd Day Air",
                "rate": 30.384,
                "currency": "USD",
                "service_code": "02",
                "est_delivery_time": "2022-11-30T23:00:00-00:00",
                "delivery_days": 2,
                "package_type": "02",
                "rate_detail": [
                    {
                        "amount": 25.32,
                        "currency": "USD",
                        "type": "TransportationCharges"
                    },
                    {
                        "amount": 4.09,
                        "currency": "USD",
                        "type": "375"
                    },
                    {
                        "amount": 21.23,
                        "currency": "USD",
                        "type": "BaseServiceCharge"
                    },
                    {
                        "amount": 0,
                        "currency": "USD",
                        "type": "376"
                    }
                ],
                "billing_weight": 1,
                "carrier": "ups",
                "description": "UPS 2nd Day Air",
                "deliveryDateTime": "2022-11-30T23:00:00-00:00",
                "deliveryDays": 2,
                "origRate": 25.32,
                "id": "123456",
                "methodName": ""
            },
            {
                "desc": "UPS Second Day Air AM",
                "rate": 33.096,
                "currency": "USD",
                "service_code": "59",
                "est_delivery_time": "2022-11-30T23:00:00-00:00",
                "delivery_days": 2,
                "package_type": "02",
                "rate_detail": [
                    {
                        "amount": 27.58,
                        "currency": "USD",
                        "type": "TransportationCharges"
                    },
                    {
                        "amount": 0,
                        "currency": "USD",
                        "type": "376"
                    },
                    {
                        "amount": 4.45,
                        "currency": "USD",
                        "type": "375"
                    },
                    {
                        "amount": 23.13,
                        "currency": "USD",
                        "type": "BaseServiceCharge"
                    }
                ],
                "billing_weight": 1,
                "carrier": "ups",
                "description": "UPS Second Day Air AM",
                "deliveryDateTime": "2022-11-30T23:00:00-00:00",
                "deliveryDays": 2,
                "origRate": 27.58,
                "id": "KYUDVCnc0tPa1qxTwumZr8FE",
                "methodName": ""
            },
            {
                "desc": "UPS Next Day Air Saver",
                "rate": 45.132,
                "currency": "USD",
                "service_code": "13",
                "est_delivery_time": "2022-11-29T23:00:00-00:00",
                "delivery_days": 1,
                "package_type": "02",
                "rate_detail": [
                    {
                        "amount": 37.61,
                        "currency": "USD",
                        "type": "TransportationCharges"
                    },
                    {
                        "amount": 6.07,
                        "currency": "USD",
                        "type": "375"
                    },
                    {
                        "amount": 31.54,
                        "currency": "USD",
                        "type": "BaseServiceCharge"
                    },
                    {
                        "amount": 0,
                        "currency": "USD",
                        "type": "376"
                    }
                ],
                "billing_weight": 1,
                "carrier": "ups",
                "description": "UPS Next Day Air Saver",
                "deliveryDateTime": "2022-11-29T23:00:00-00:00",
                "deliveryDays": 1,
                "origRate": 37.61,
                "id": "123456",
                "methodName": ""
            },
            {
                "desc": "UPS Next Day Air",
                "rate": 49.368,
                "currency": "USD",
                "service_code": "01",
                "est_delivery_time": "2022-11-29T15:00:00-00:00",
                "delivery_days": 1,
                "package_type": "02",
                "rate_detail": [
                    {
                        "amount": 41.14,
                        "currency": "USD",
                        "type": "TransportationCharges"
                    },
                    {
                        "amount": 0,
                        "currency": "USD",
                        "type": "376"
                    },
                    {
                        "amount": 6.64,
                        "currency": "USD",
                        "type": "375"
                    },
                    {
                        "amount": 34.5,
                        "currency": "USD",
                        "type": "BaseServiceCharge"
                    }
                ],
                "billing_weight": 1,
                "carrier": "ups",
                "description": "UPS Next Day Air",
                "deliveryDateTime": "2022-11-29T15:00:00-00:00",
                "deliveryDays": 1,
                "origRate": 41.14,
                "id": "123456",
                "methodName": ""
            },
            {
                "desc": "UPS Next Day Air Early AM",
                "rate": 92.304,
                "currency": "USD",
                "service_code": "14",
                "est_delivery_time": "2022-11-29T10:00:00-00:00",
                "delivery_days": 1,
                "package_type": "02",
                "rate_detail": [
                    {
                        "amount": 76.92,
                        "currency": "USD",
                        "type": "TransportationCharges"
                    },
                    {
                        "amount": 12.42,
                        "currency": "USD",
                        "type": "375"
                    },
                    {
                        "amount": 64.5,
                        "currency": "USD",
                        "type": "BaseServiceCharge"
                    },
                    {
                        "amount": 0,
                        "currency": "USD",
                        "type": "376"
                    }
                ],
                "billing_weight": 1,
                "carrier": "ups",
                "description": "UPS Next Day Air Early AM",
                "deliveryDateTime": "2022-11-29T10:00:00-00:00",
                "deliveryDays": 1,
                "origRate": 76.92,
                "id": "123456",
                "methodName": ""
            }
        ],
        "contactFirstName": "Sarah - shippingName",
        "contactLastName": "Jones - shippingName",
        "companyName": "Tyrell Corp",
        "createdAt": "2022-11-27 22:34:13",
        "editedAt": "2022-11-27 22:34:18",
        "pricing": {
            "productsTotal": 0.1,
            "origTotal": 0.1,
            "subTotal": 0.1,
            "tax": 0,
            "totalCouponDiscount": 0,
            "totalAfterCoupon": 0.1,
            "total": 0.1
        },
        "couponCodesInfo": []
    },
    "orderProdQuantity": "1",
    "paymentObject": {
        "xResult": "A",
        "xStatus": "Approved",
        "xError": "",
        "xErrorCode": "00000",
        "xRefNum": "760465207",
        "xExp": "0325",
        "xDate": "11/27/2022 5:34:39 PM",
        "xAuthCode": "678485",
        "xBatch": "100202",
        "xAvsResultCode": "YYY",
        "xAvsResult": "Address: Match & 5 Digit Zip: Match",
        "xCvvResultCode": "",
        "xCvvResult": "No CVV data available",
        "xAuthAmount": "0.10",
        "xToken": "1234567890",
        "xMaskedCardNumber": "5xxxxxxxxxxx0666",
        "xCardType": "MasterCard",
        "xName": "Sarah - shippingName Jones - shippingName",
        "cardToken": "cc_123456"
    },
    "cardToken": "cc_123456",
    "orderIP": "::1",
    "dateCreated": "1669588464",
    "deleted": "",
    "numberOfPackages": 0,
    "createdAt": "2022-11-27 22:34:24",
    "editedAt": "2022-11-27 22:34:24",
    "orderStatusValue": {
        "id": "os_awaiting_fulfillment",
        "name": "Awaiting Fulfillment",
        "color": "#ffc107"
    },
    "statusAndTerms": {
        "processingStatus": "Awaiting Fulfillment",
        "shippingStatus": "Pending",
        "paymentStatus": "Closed",
        "orderStatus": "Open",
        "paymentTerms": "Website Payment Transaction",
        "postPaymentStatus": "NULL"
    },
    "paymentHistory": [
        {
            "paymentHistoryToken": "pmth_123456123456",
            "orderToken": "ordr_123456123456",
            "amount": "0.1",
            "action": "charge",
            "dateTime": "1669588465",
            "paymentObject": "{\"xResult\":\"A\",\"xStatus\":\"Approved\",\"xError\":\"\",\"xErrorCode\":\"00000\",\"xRefNum\":\"760465207\",\"xExp\":\"0325\",\"xDate\":\"11\\/27\\/2022 5:34:39 PM\",\"xAuthCode\":\"678485\",\"xBatch\":\"100202\",\"xAvsResultCode\":\"YYY\",\"xAvsResult\":\"Address: Match & 5 Digit Zip: Match\",\"xCvvResultCode\":\"\",\"xCvvResult\":\"No CVV data available\",\"xAuthAmount\":\"0.10\",\"xToken\":\"1234567890\",\"xMaskedCardNumber\":\"5xxxxxxxxxxx0666\",\"xCardType\":\"MasterCard\",\"xName\":\"Sarah - shippingName Jones - shippingName\",\"cardToken\":\"cc_123456\"}",
            "cardToken": "cc_123456",
            "userToken": "omni",
            "createdAt": "2022-11-27 22:34:25",
            "editedAt": "2022-11-27 22:34:25"
        }
    ]
}


## CREATE ORDER NOT AVAILABLE TO USE, USE CHECKOUT INSTEAD.

<!-- ## Create Order

### HTTP Request

`POST https://apistore.csomni.com/orders`

### QUERY Parameters

| Parameter            | Required | Description                                                                                                                                                                                         |
| -------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerToken        | true     | The Customer Token                                                                                                                                                                                  |
| companyToken         | false    | The Company Token                                                                                                                                                                                   |
| orderProducts        | true     | Products inside the order                                                                                                                                                                           |
| orderEmail           | true     | Email for Order                                                                                                                                                                                     |
| orderTotal           | false    | orderTotal                                                                                                                                                                                          |
| customerObject       | false    | customerObject                                                                                                                                                                                      |
| cartToken            | false    | cartToken                                                                                                                                                                                           |
| orderShippingMethod  | false    | orderShippingMethod                                                                                                                                                                                 |
| siteToken            | false    | The SITE Token                                                                                                                                                                                      |
| orderShippingAddress | false    | orderShippingAddress                                                                                                                                                                                |
| orderPaymentMethod   | false    | orderPaymentMethod                                                                                                                                                                                  |
| orderTax             | false    | orderTax                                                                                                                                                                                            |
| orderShipping        | false    | orderShipping                                                                                                                                                                                       |
| contactLastName      | false    | contactLastName                                                                                                                                                                                     |
| contactFirstName     | false    | contactFirstName                                                                                                                                                                                    |
| checkoutObject       | false    | checkoutObject                                                                                                                                                                                      |
| orderProdQuantity    | false    | orderProdQuantity                                                                                                                                                                                   |
| paymentObject        | false    | paymentObject                                                                                                                                                                                       |
| cardToken            | false    | Token of card                                                                                                                                                                                       |
| orderWeight          | false    | orderWeight                                                                                                                                                                                         |
| BillToName           | true     | Name to Bill                                                                                                                                                                                        |
| BillToAddress        | true     | Address to send bill                                                                                                                                                                                |
| avsMatched           | false    | avsMatched                                                                                                                                                                                          |
| zipMatched           | false    | zipMatched                                                                                                                                                                                          |
| orderIP              | false    | orderIP                                                                                                                                                                                             |
| orderNotePrivate     | false    | orderNotePrivate - Admin note private to only admin - is not returned in order object. Its created by the admin at checkout and submited with an order.                                             |
| orderNotePublic      | false    | Note written by customer to the site at checkout to be saved with the order                                                                                                                         |
| po                   | false    | Identifying Purchase Order number. Can include digits, letters (which will be converted to upper case), dashes and dots. All other characters will not be procesed and will return an error message |

```shell
curl --request POST \
  --url https://apistore.csomni.com/orders \
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
  --header 'token: 123' \
  --data '{ "customerToken" : "cs_123456", "orderProducts" : [array of products],"BillToName":"myName","BillToAddress":"myAddress", "orderEmail" : "abc@gmail.com" }'

```

Response:

```json
{
  "orderToken": "ordr_123456",
  "companyToken": "comp_123456",
  "siteToken": "site_123",
  "customerToken": "cust_123456",
  "orderProducts": [
    {
      "cartToken": "cart_123456",
      "cartProdToken": "cp_123456",
      "cartProdQuantity": 2,123456
      "prodToken": "prod_123456",
      "deleted": "0",
      "product": {
        "prodToken": "prod_123456",
        "companyToken": "comp_123456",
        "prodName": "Flat Wire for Lightning iPhone, iPad, iPod Sync and Charge Cable",
        "prodImage": "5-31-2018/1527796147164__187422__ZF-ZFACUSBFWIP5.jpg",
        "prodImages": [],
        "prodWeight": "5",
        "prodDimW": "",
        "prodDimL": "",
        "prodDimH": "",
        "prodUpc": "850067005100",
        "prodNumber": "ZF-ZFACUSBFWIP5zzz",
        "prodPrice": "100",
        "prodCostPrice": "",
        "prodDescription": "",
        "prodAlert": "",
        "prodLowlevel": "",
        "prodSlug": "flat-wire-for-lightning-iphone-ipad-ipod-sync-and-charge-cable",
        "prodVisible": "1",
        "prodAllowCheckout": "0",
        "prodCheckInvetory": "0",
        "prodTrackInventory": "0",
        "inventoryCount": "5",
        "prodCollections": ["clcs_123456"]
      },
      "pricing": {
        "total": 200
      },
      "shipping": {
        "totalWeight": 10
      }
    }
  ],
  "orderShippingMethod": {
    "desc": "Priority Mail 3-Day Window Flat Rate Envelope",
    "rate": 18.7,
    "currency": "USD",
    "service_code": "40",
    "est_delivery_time": "2018-06-28",
    "package_type": "",
    "rate_detail": null,
    "guaranteed": false,
    "carrier": "usps",
    "origRate": 6.7,
    "id": "123456"
  },
  "orderTotal": "218.7",
  "orderStatus": "1",
  "customerObject": "",
  "orderEmail": "sjones1@gmail.com",
  "orderNotePublic": "This is orderNotePublic",
  "cartToken": "",
  "orderPaymentMethod": {
    "id": "ch_123456",
    "object": "charge",
    "amount": 2187,
    "amount_refunded": 0,
    "application": null,
    "application_fee": null,
    "balance_transaction": "txn_123456",
    "captured": true,
    "created": 1530131498,
    "currency": "usd",
    "customer": null,
    "description": "Sarahs charge",
    "destination": null,
    "dispute": null,
    "failure_code": null,
    "failure_message": null,
    "fraud_details": [],
    "invoice": null,
    "livemode": false,
    "metadata": [],
    "on_behalf_of": null,
    "order": null,
    "outcome": {
      "network_status": "approved_by_network",
      "reason": null,
      "risk_level": "normal",
      "seller_message": "Payment complete.",
      "type": "authorized"
    },
    "paid": true,
    "receipt_email": null,
    "receipt_number": null,
    "refunded": false,
    "refunds": {
      "object": "list",
      "data": [],
      "has_more": false,
      "total_count": 0,
      "url": "/v1/charges/ch_123456/refunds"
    },
    "review": null,
    "shipping": null,
    "source": {
      "id": "card_123456",
      "object": "card",
      "address_city": null,
      "address_country": null,
      "address_line1": null,
      "address_line1_check": null,
      "address_line2": null,
      "address_state": null,
      "address_zip": null,
      "address_zip_check": null,
      "brand": "Visa",
      "country": "US",
      "customer": null,
      "cvc_check": "pass",
      "dynamic_last4": null,
      "exp_month": 12,
      "exp_year": 2020,
      "fingerprint": "123456",
      "funding": "credit",
      "last4": "4242",
      "metadata": [],
      "name": null,
      "tokenization_method": null
    },
    "source_transfer": null,
    "statement_descriptor": null,
    "status": "succeeded",
    "transfer_group": null
  },
  "dateCreated": "",
  "deleted": ""
}
``` -->

## Delete a cart Order 

This endpoint deletes (soft deletes) an address

### HTTP Request

`DELETE https://apistore.csomni.com/orders/[cartToken]`

### Header Parameters

| Parameter | Description              |
| --------- | ------------------------ |
| customerToken     | Login token associated with the address to be deleted |

### URL Parameters

| Parameter | Description              |
| --------- | ------------------------ |
| Token     | The cart Token to delete |

```shell
curl --request DELETE \
  --url https://apistore.csomni.com/orders/[cartToken] \
  --header 'content-type: application/json' \
  --header 'token: 123'/
  --header 'customerToken: loginToken123'
```

> The above command returns JSON structured like this:

```json
{
  "token": "cart_token",
  "deleted": true
}
```


