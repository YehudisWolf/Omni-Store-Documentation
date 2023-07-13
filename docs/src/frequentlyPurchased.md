# Frequently Purchased

## Get Frequently Purchased List by Site  - if cached data is >24 hours old cached data is returned. Else: fresh data pull is created and returned

### HTTP Request

`GET https://apistore.csomni.com/frequentlyPurchased`

| Parameter | Required | Unique | Description                                                     |
| --------- | -------- | ------ | --------------------------------------------------------------- |
| token     | true     | -      | Token of the site to retreive the frequently purchased list for |

```shell
curl --request GET \
  --url https://apistore.csomni.com/frequentlyPurchased \
  --header 'token: site_dg30sdfsgdsgsvv'
```

Response:

```json
[
  {
    "variantToken": "vrnt_123456",
    "quantity": 145,
    "price": 3.5,
    "variantImage": {
      "file": "9-14-2021/1631634128386__40977__gabe-rebra-j7b8-kN3Dgc-unsplash.jpg",
      "id": "ast20tjq",
      "status": "poolImages"
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 134,
    "price": "",
    "variantImage": "",
    "productToken": ""
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 31,
    "price": "",
    "variantImage": "",
    "productToken": ""
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 17,
    "price": 0.29,
    "variantImage": {
      "file": "[]"
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 6,
    "price": 0.49,
    "variantImage": {
      "file": "[]"
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 5,
    "price": 1,
    "variantImage": {
      "file": "3-8-2021/1615263242853__786458__image_2020-04-27_18-51-09.png"
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 5,123456
    "price": 43.54,
    "variantImage": {
      "file": "1-19-2021/1611091609025__507613__2021_volkswagen_tiguan_hybrid_1.jpg"
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 4,
    "price": 10,
    "variantImage": {
      "file": "6-10-2021/1623352409463__31430__vbjr_.jpg",
      "id": "eotyi9x3",
      "status": "poolImages"
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 3,
    "price": "",
    "variantImage": "",
    "productToken": ""
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 2,
    "price": "",
    "variantImage": "",
    "productToken": ""
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 2,
    "price": "",
    "variantImage": "",
    "productToken": ""
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 2,
    "price": 15,
    "variantImage": {
      "file": "4-18-2021/1618739190948__90034__binary-1695475__340.webp"
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 1,
    "price": "",
    "variantImage": {
      "file": ""
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",123456123456
    "quantity": 1,
    "price": 5,
    "variantImage": {
      "file": "[]"
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 1,
    "price": 1.1,
    "variantImage": {
      "file": ""
    },
    "productToken": "prod_123456123456"
  }
]
```

## Get Frequently Purchased by siteToken FORCE FRESH DATA PULL

### HTTP Request

`GET https://apistore.csomni.com/frequentlyPurchased/forceRefresh`

| Parameter | Required | Unique | Description                                                     |
| --------- | -------- | ------ | --------------------------------------------------------------- |
| token     | true     | -      | Token of the site to retreive the frequently purchased list for |

```shell
curl --request GET \
  --url https://apistore.csomni.com/frequentlyPurchased/forceRefresh \
  --header 'token: site_123456123456'
```

Response:

```json
[
  {
    "variantToken": "vrnt_123456123456",
    "quantity": 145,
    "price": 3.5,
    "variantImage": {
      "file": ""
    },
    "productToken": "prod_123456123456"
  },
  {
    "variantToken": "vrnt_123456123456",
    "quantity": 134,
    "price": "",
    "variantImage": "",
    "productToken": ""
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 31,
    "price": "",
    "variantImage": "",
    "productToken": ""
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 17,
    "price": 0.29,
    "variantImage": {
      "file": "[]"
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 6,
    "price": 0.49,
    "variantImage": {
      "file": "[]"
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 5,
    "price": 1,
    "variantImage": {
      "file": "3-8-2021/1615263242853__786458__image_2020-04-27_18-51-09.png"
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 5,
    "price": 43.54,
    "variantImage": {
      "file": "1-19-2021/1611091609025__507613__2021_volkswagen_tiguan_hybrid_1.jpg"123456
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 4,
    "price": 10,
    "variantImage": "",
    "productToken": "prod_123456"
  },123456
  {
    "variantToken": "vrnt_123456",
    "quantity": 3,
    "price": "",
    "variantImage": "",
    "productToken": ""
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 2,
    "price": "",
    "variantImage": "",
    "productToken": ""
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 2,
    "price": "",
    "variantImage": "",
    "productToken": ""
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 2,
    "price": 15,
    "variantImage": {
      "file": "4-18-2021/1618739190948__90034__binary-1695475__340.webp"
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 1,
    "price": "",
    "variantImage": {
      "file": ""
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "vrnt_123456",
    "quantity": 1,
    "price": 5,
    "variantImage": {
      "file": "[]"
    },
    "productToken": "prod_123456"
  },
  {
    "variantToken": "123456",
    "quantity": 1,
    "price": 1.1,
    "variantImage": {
      "file": ""
    },
    "productToken": "123456"
  }
]
```

## GET frequently purchased by customer
Follow instructions above, and add optional customerToken header:

| Parameter | Required | Description                                                     |
| --------- | --------  | --------------------------------------------------------------- |
| customerToken     | false  | Token of the customer to retreive the frequently purchased list for |

--header 'customerToken: cs_123456'
