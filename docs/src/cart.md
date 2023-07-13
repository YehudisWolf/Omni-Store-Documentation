# Cart

## New Cart

This endpoint creates a cart

### HTTP Request

`POST https://apistore.csomni.com/cart`

### Query Parameters

| Parameter     | Required | Unique | Description                                 |
| ------------- | -------- | ------ | ------------------------------------------- |
| customerToken | false    | -      | Customer Token (creates a new one if empty) |

```shell
curl --request POST \
  --url https://apistore.csomni.com/cart/ \
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
  --header 'token: 123' \
  --data '{"customerToken" : "cusst444"}'

```

> The above command returns JSON structured like this

```json
{
  "cartToken": "cart_123456",
  "companyToken": "comp_123456",
  "siteToken": "site_123",
  "customerToken": "cust_123456",
  "status": "cart created"
}
```

## Get A Cart

This endpoint retrieves a cart by cart token or customer token

### HTTP Request

`GET https://apistore.csomni.com/cart`

### URL Parameters

| Parameter     | Required | Unique | Description                           |
| ------------- | -------- | ------ | ------------------------------------- |
| customerToken | true     | -      | Customer Token for this cart (header) |

```shell
curl --request GET \
  --url https://apistore.csomni.com/cart \
  --header 'token: 123'
  --header 'customerToken: cs_123456'

```

> The above command returns JSON structured like this:

```json
{
  "companyToken": "comp_123456",
  "siteToken": "site_123456",
  "cartToken": "cart_123456",
  "customerToken": "cust_123456",
  "cartCreated": "1637945854",
  "cartLastTouched": "1637945854",
  "deleted": 0,
  "createdAt": "2021-12-17 15:37:57",
  "editedAt": "2021-12-17 15:37:57",
  "pricing": {
    "total": 34
  },
  "itemsInCart": 1,
  "cartWeight": 0,
  "cartProds": [
    {
      "cartToken": "cart_123456",
      "cartProdToken": "cp_123456",
      "addOnToProdToken": "",
      "cartProdQuantity": 1,
      "addOnProdTokens": null,
      "prodToken": "vrnt_123456",
      "deleted": 0,
      "companyToken": "comp_123456",
      "siteToken": "site_123456",
      "customerToken": "cust_123456",
      "cartCreated": "1637945854",
      "cartLastTouched": "1637945854",
      "prodStaticCollections": [
        "clcs_123456",
        "clcs_123456",
        "clcs_123456",
        ""
      ],
      "specialValues": [],
      "product": {
        "prodToken": "prod_123456",
        "variantToken": "vrnt_123456",
        "companyToken": "comp_123456",
        "variantName": "",
        "variantImage": {
          "file": "10-13-2021/1634136843403__65263__aron-yigin-epjvM-Ql5-Y-unsplash.jpg",
          "type": "",
          "id": "lwigs97k",
          "status": "poolImages"
        },
        "variantImages": [],
        "variantWeight": "0",
        "variantDimW": "0",
        "variantDimL": "0",
        "variantDimH": "0",
        "variantUpc": "",
        "variantNumber": "",
        "manufacturerPartNumber": "",
        "variantPrice": 34,
        "variantMapPrice": 0,
        "variantMsrpPrice": 0,
        "variantDisplayPrice": 32,
        "variantDescription": "",
        "variantAlert": "",
        "variantLowlevel": "",
        "variantSlug": "",
        "variantVisible": 1,
        "variantAllowCheckout": 0,
        "variantCheckInvetory": 0,
        "variantTrackInventory": 0,
        "taxType": "",
        "taxable": 1,
        "shippingProduct": 0,
        "variantMetaTitle": "",
        "variantMetaDescription": "",
        "variantBrand": "",
        "google_variantCategory": "",
        "google_variantType": "",
        "google_variantCondition": "",
        "hideGoogleData": 0,
        "sortOrder": 0,
        "dateCreated": "1634137246",
        "deleted": 0,
        "backOrderWarning": 0,
        "variantInStock": true,
        "variantOptions": [
          {
            "optionToken": "optn_123456",
            "optionValue": "dsasda",
            "optionName": "color"
          },
          {
            "optionToken": "optn_123456",
            "optionValue": "f",
            "optionName": "size"
          }
        ],
        "prodName": "dsadsadsads",
        "prodImage": {
          "file": "5-31-2021/1622471456251__6160299__jonah-brown-veEPQ7aOx8w-unsplash.jpg",
          "name": "",
          "type": ""
        }
      },
      "addOnProducts": [],
      "pricing": {
        "total": 34
      },
      "shipping": {
        "totalWeight": 0
      }
    }
  ]
}
```

## Add cart to customer

This endpoint Adds a user to a cart

### HTTP Request

`POST https://apistore.csomni.com/cart/combine/[cartToken]/[customerToken cs_]/`

### URL Parameters

| Parameter | Required | Unique | Description        |
| --------- | -------- | ------ | ------------------ |
| combine   | true     | -      | To combine 2 carts |
| cartToken | true     | -      | Cart to transfer   |

```shell
curl --request POST \
  --url https://apistore.csomni.com/cart/combine/[cartToken]/[customerToken cs_] \
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
  --header 'token: 123, customertoken : cs_123' \
```

Another example:

```shell
curl --request POST \
  --url 'https://apistore.csomni.com/cart/combine/cart_123456/cs_123456' \
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
  --header 'token: 123, customertoken : cs_123456' \
```

> The above command returns JSON structured like this

```json
{
  "companyToken": "comp_123456",
  "siteToken": "site_123",
  "cartToken": "cart_123456",
  "customerToken": "cust_123456",
  "cartCreated": "1638346960",
  "cartLastTouched": "1638346960",
  "deleted": 0,
  "pricing": {
    "total": 12
  },
  "itemsInCart": 4,
  "cartWeight": 4,
  "cartProds": [
    {
      "cartToken": "cart_123456",
      "cartProdToken": "cp_123456",
      "addOnToProdToken": "",
      "cartProdQuantity": 4,
      "addOnProdTokens": null,
      "prodToken": "vrnt_123456",
      "deleted": 0,
      "companyToken": "comp_123456",
      "siteToken": "site_123",
      "customerToken": "cust_123456",
      "cartCreated": "1638346960",
      "cartLastTouched": "1638346960",
      "prodStaticCollections": [],
      "specialValues": [],
      "product": {
        "prodToken": "prod_123456",
        "variantToken": "vrnt_123456",
        "companyToken": "comp_123456",
        "variantName": "",
        "variantImage": {
          "file": ""
        },
        "variantImages": [],
        "variantWeight": "1",
        "variantDimW": "0",
        "variantDimL": "0",
        "variantDimH": "0",
        "variantUpc": "",
        "variantNumber": "",
        "manufacturerPartNumber": "",
        "variantPrice": 3,
        "variantMapPrice": 0,
        "variantMsrpPrice": 0,
        "variantDisplayPrice": 0,
        "variantDescription": "",
        "variantAlert": "",
        "variantLowlevel": "",
        "variantSlug": "",
        "variantVisible": 1,
        "variantAllowCheckout": 1,
        "variantCheckInvetory": 1,
        "variantTrackInventory": 0,
        "taxType": "",
        "taxable": 1,
        "shippingProduct": 1,
        "variantMetaTitle": "",
        "variantMetaDescription": "",
        "variantBrand": "",
        "google_variantCategory": null,
        "google_variantType": null,
        "google_variantCondition": null,
        "hideGoogleData": 1,
        "sortOrder": 0,
        "dateCreated": "1606236358",
        "deleted": 0,
        "backOrderWarning": 0,
        "variantInStock": true,
        "prodName": "Yes",
        "prodImage": {
          "file": "11-24-2020/1606236354284__36278__GUEST_1e09d33a-dc4e-4ff2-8640-7540993a94ae.jpg"
        }
      },
      "addOnProducts": [],
      "pricing": {
        "total": 12
      },
      "shipping": {
        "totalWeight": 4
      }
    }
  ]
}
```

This endpoint Adds a user to a cart

### HTTP Request

`POST https://apistore.csomni.com/cart/combine/[cartToken]/[customerToken]`

### URL Parameters

| Parameter             | Required | Unique | Description                                                                                    |
| --------------------- | -------- | ------ | ---------------------------------------------------------------------------------------------- |
| combine               | true     | -      | To combine 2 carts                                                                             |
| cartToken             | true     | -      | Cart to transfer                                                                               |
| customerToken         | true     | -      | Customer login Token associated with the previously used cartToken                             |
| HEADER: customerToken | true     | -      | Customer Login Token of account you would like to send the cart content in Http request URL to |
