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
    "name": "",
    "quoteToken": "cc_123456",
    "customerToken": "cust_123456",
    "companyToken": "",
    "quoteItems": null,
    "quoteFiles": "",
    "dateSubmitted": "2021-12-01 20:39:47",
    "status": "Waiting response",
    "deleted": 0,
    "dateCreated": "2021-07-07 06:11:46",
    "dateUpdated": "2021-12-01 20:39:47"
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
          "optn_OYTQkGqr39CvOopfJPi7": "Var 1"
        },
        "prodName": "Moishes Test",
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

## Get a quote by Quote Token

### HTTP Request

`GET https://apistore.csomni.com/quotes/{quoteToken}`

### URL Parameters

| Parameter   | Description                     |
| ----------- | ------------------------------- |
| Quote Token | Token of the Quote to retrieve. |

```shell
curl --request GET \
  --url https://apistore.csomni.com/quotes/quoteToken \
   --header 'token: 123'
  --header 'customerToken: cs_123456' \
```

Response:

```json
[
  {
    "name": "",
    "quoteToken": "quote_123456",
    "customerToken": "cust_123456",
    "companyToken": "comp_123456",
    "quoteItems": null,
    "quoteFiles": "",
    "dateSubmitted": "2021-12-01 20:43:38",
    "status": "Waiting response",
    "deleted": 0,
    "dateCreated": "2021-08-26 03:19:54",
    "dateUpdated": "2021-12-01 20:43:38"
  }
]
```

## Get a quote by Status

### HTTP Request

`GET https://apistore.csomni.com/quotes/{status}`

### URL Parameters

| Parameter | Description                                                           |
| --------- | --------------------------------------------------------------------- |
| Status    | can be either of 'Waiting response', 'Denied', 'Canceled', 'Approved' |

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
        "prodName": "Moishes Test",
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

## Get Opened quotes

### HTTP Request

`GET https://apistore.csomni.com/quotes/open`

### URL Parameters

| Parameter | Description                |
| --------- | -------------------------- |
| Open      | if submitted or not or not |

```shell
curl --request GET \
  --url https://apistore.csomni.com/quotes/open \
    --header 'token: 123'
  --header 'customerToken: cs_123456' \
```

Response:

```json
[
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
          "optn_OYTQkGqr39CvOopfJPi7": "Var 1"
        },
        "prodName": "Moishes Test",
        "prodImage": "9-6-2018/1536271360573__14511__yb.jpg",
        "quantity": 2
      }
    ],
    "quoteFiles": "",
    "dateSubmitted": "0000-00-00 00:00:00",
    "status": "Approved",
    "deleted": 0,
    "dateCreated": "2021-07-07 04:29:09",
    "dateUpdated": "2021-12-01 20:49:09"
  }
]
```

## Get Submitted quotes

### HTTP Request

`GET https://apistore.csomni.com/quotes/submitted`

### URL Parameters

| Parameter | Description                |
| --------- | -------------------------- |
| submitted | if submitted or not or not |

```shell
curl --request GET \
  --url https://apistore.csomni.com/quotes/submitted \
  --header 'token: 123'\
  --header 'customerToken: cs_123456' \
```

Response:

```json
[
  {
    "name": "",
    "quoteToken": "quote_123456",
    "customerToken": "cust_123456",
    "companyToken": "comp_123456",
    "quoteItems": null,
    "quoteFiles": "",
    "dateSubmitted": "2021-12-01 20:43:38",
    "status": "Waiting response",
    "deleted": 0,
    "dateCreated": "2021-08-26 03:19:54",
    "dateUpdated": "2021-12-01 20:43:38"
  },
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
    "quoteToken": "cc_123456",
    "customerToken": "cust_123456",
    "companyToken": "",
    "quoteItems": null,
    "quoteFiles": "",
    "dateSubmitted": "2021-12-01 20:39:47",
    "status": "Waiting response",
    "deleted": 0,
    "dateCreated": "2021-07-07 06:11:46",
    "dateUpdated": "2021-12-01 20:39:47"
  }
]
```

## Create and just Save Quote

### HTTP Request

`POST https://apistore.csomni.com/quotes`

### QUERY Parameters

| Parameter     | Required | Description            |
| ------------- | -------- | ---------------------- |
| customerToken ( Header)  | true     | Login Token            |
| quoteItems    | true     | Quote Items            |
| quoteFiles    | false    | Quote File(s) as a url |

```shell
curl --request POST \
  --url https://apistore.csomni.com/quotes \
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
    --header 'token: 123'\
  --header 'customerToken: cs_123456' \
  --data '{"quoteItems" : "lll", "quoteFiles" : "111111" }'

```

Response:

```json
{
  "name": "",
  "quoteToken": "quote_123456",
  "customerToken": "cust_123456",
  "companyToken": "comp_123456",
  "quoteItems": "lll",
  "quoteFiles": "",
  "dateSubmitted": null,
  "status": "Waiting response",
  "deleted": 0,
  "dateCreated": "2021-08-25 15:20:20",
  "dateUpdated": "2021-08-25 15:20:20"
}
```

## Create and Submit Quote

### HTTP Request

`POST https://apistore.csomni.com/quotes/submit`

### QUERY Parameters

| Parameter     | Required | Description            |
| ------------- | -------- | ---------------------- |
| customerToken (header)| true     | Login token            |
| quoteItems    | true     | Quote Items            |
| quoteFiles    | false    | Quote File(s) as a url |

```shell
curl --request POST \
  --url https://apistore.csomni.com/quotes/submit \
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
    --header 'token: 123'\
  --header 'customerToken: cs_123456' \
  --data '{ "quoteItems" : "lll", "quoteFiles" : "111111" }'

```

Response:

```json
{
  "name": "",
  "quoteToken": "quote_123456",
  "customerToken": "cust_123456",
  "companyToken": "comp_123456",
  "quoteItems": "lll",
  "quoteFiles": "111111",
  "dateSubmitted": "2021-12-01 17:00:25",
  "status": "Waiting response",
  "deleted": 0,
  "dateCreated": "2021-12-01 21:00:25",
  "dateUpdated": "2021-12-01 21:00:25"
}
```

## Update Quote status

### HTTP Request

`POST https://apistore.csomni.com/quotes/{quoteToken}`

### URL Parameters

| Parameter   | Description                   |
| ----------- | ----------------------------- |
| Quote Token | Token of the Quote to update. |

### QUERY Parameters

| Parameter     | Required | Description            |
| ------------- | -------- | ---------------------- |
| customerToken (header) | true     | TLogin Token           |
| quoteItems    | true     | Quote Items            |
| quoteFiles    | false    | Quote File(s) as a url |

```shell
curl --request POST \
  --url https://apistore.csomni.com/quotes \
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
   --header 'token: 123'\
  --header 'customerToken: cs_123456' \
  --data '{ "quoteItems" : "lll", "quoteFiles" : "111111" }'

```

Response:

```json
{
  "name": "",
  "quoteToken": "quote_123456",
  "customerToken": "cust_123456",
  "companyToken": "comp_123456",
  "quoteItems": "lllss",
  "quoteFiles": "111111",
  "dateSubmitted": "2021-12-01 21:01:42",
  "status": "Waiting response",
  "deleted": 0,
  "dateCreated": "2021-12-01 21:00:25",
  "dateUpdated": "2021-12-01 21:01:42"
}
```

## Update and submit Quote status

### HTTP Request

`POST https://apistore.csomni.com/quotes/submit/{quoteToken}`

### URL Parameters

| Parameter   | Description                   |
| ----------- | ----------------------------- |
| Quote Token | Token of the Quote to update. |

### QUERY Parameters

| Parameter     | Required | Description            |
| ------------- | -------- | ---------------------- |
| customerToken (header) | true     | Login token     |
| quoteItems    | true     | Quote Items            |
| quoteFiles    | false    | Quote File(s) as a url |

```shell
curl --request POST \
  --url https://apistore.csomni.com/quotes/submit/quoteToken \
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
    --header 'token: 123'\
  --header 'customerToken: cs_123456' \
  --data '{"quoteItems" : "lll", "quoteFiles" : "111111" }'

```

Response:

```json
{
  "name": "",
  "quoteToken": "cc_123456",
  "customerToken": "cust_123456",
  "companyToken": "comp_123456",
  "quoteItems": "lll",
  "quoteFiles": "",
  "dateSubmitted": "2020-02-02 04:04:45",
  "status": "Approved",
  "deleted": 0,
  "dateCreated": "2021-07-06 18:16:01",
  "dateUpdated": "2021-07-06 18:16:01"
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
  "token": "quote_123456",
  "deleted": "true"
}
```
