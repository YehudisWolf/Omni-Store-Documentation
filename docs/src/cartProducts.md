# Cart Products

## Add Product to cart

### Query Parameters

| Parameter        | Required | Unique | Description                                   |
| ---------------- | -------- | ------ | --------------------------------------------- |
| cartToken        | false    | -      | Cart to add product to (creates one if empty) |
| customerToken    | false    | -      | Customer Token (creates a new one if empty)   |
| prodToken        | true     | -      | Variant Token                                 |
| cartProdQuantity | true     | -      | Quantity to add to cart                       |

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/cartprods/[cartToken] \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{ "cartProdQuantity" : "1", "prodToken" : "prod_nHc1b0iV8NsN2RGw" }'

```

> The above command returns JSON structured like this

```json
{
  "cartToken": "cart_33FkeUtvV7PXTwMOVCCcVa0S",
  "cartProdToken": "cp_lJgk0e8n8ZM7d2hJBTutM0R6",
  "cartProdQuantity": "1",
  "customerToken": "cust_111",
  "prodToken": "prod_oqOBvfghjNtO6Q",
  "cartAddedQuantity": "3",
  "status": "Prod Added"
}
```

> if Prod in cart already The above command returns JSON structured like this

```json
{
  "cartToken": "cart_340qwertyuCx46z",
  "prodToken": "prod_MMetyuiGWoF",
  "customerToken": "cs_123456",
  "cartProdQuantity": 23,
  "cartProdToken": "cp_GNly67fafffafI2aB0V",
  "cartAddedQuantity": "8",
  "status": "Prod Updated"
}
```

## Edit cart product

This endpoint Edits a product in cart

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/cartprods/{cartProdToken}`

### Query Parameters

| Parameter        | Required | Unique | Description             |
| ---------------- | -------- | ------ | ----------------------- |
| cartProdQuantity | true     | -      | Quantity to add to cart |
| customerToken    | true     | -      | Customer Token          |

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/cartprods/{cartProdToken} \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{ "cartProdQuantity" : "1" }'

```

> The above command returns JSON structured like this

```json
{
  "cartProdToken": "cp_Yrr8oQ2BiZMTcUllOqG83Drv",
  "cartProdQuantity": "50",
  "cartAddedQuantity": "",
  "prodToken": "prod_nHc1b0iV8NsN2RGw"
}
```

## Get A Cart Product

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/cartprods/[cartProdToken]`

### URL Parameters

| Parameter     | Required | Unique | Description                    |
| ------------- | -------- | ------ | ------------------------------ |
| cartProdToken | true     | -      | cart product Token to retreive |
| customerToken | true     | -      | customer token in header       |

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/cartprods/[cartProdToken] \
  --header 'token: 123'
  --header 'customerToken: cs_123456'
```

> The above command returns JSON structured like this:

```json
{
  "cartToken": "cart_NnUTURuJTwgoPjWTnU5Inei9",
  "cartProdToken": "cp_agb15oMDn46vxOyV0IbbT3h1",
  "cartProdQuantity": 12,
  "addOnToProdToken": "",
  "addOnProdTokens": null,
  "prodToken": "prod_3aiNdXcBQ2CPxPny",
  "deleted": 0,
  "createdAt": "2021-12-29 14:57:32",
  "editedAt": "2021-12-29 14:57:32",
  "companyToken": "comp_123456",
  "siteToken": "site_123",
  "customerToken": "cust_123456",
  "cartCreated": "1640789852",
  "cartLastTouched": "1640789852",
  "specialValues": [],
  "product": {},
  "addOnProducts": [],
  "pricing": {
    "total": 0
  },
  "shipping": {
    "totalWeight": 0
  }
}
```

This endpoint retrieves a cart products

## Delete a Product from cart

This endpoint deletes (archives) a cart product

### HTTP Request

`DELETE https://api.omnifront.cloudsnob.com/cartprods/{cartProdToken}`

### URL Parameters

| Parameter | Description                   |
| --------- | ----------------------------- |
| Token     | The Token of the cart product |

```shell
curl --request DELETE \
  --url https://api.omnifront.cloudsnob.com/cartprods/{cartProdToken} \
  --header 'content-type: application/json' \
  --header 'token: 123'
```

> The above command returns JSON structured like this:

```json
{
  "token": "cp_IB4kqwerty03Cb0QBz",
  "deleted": true
}
```

```

```
