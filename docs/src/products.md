# Products

## Get a Specific Product

```shell
curl --request GET \
  --url https://apistore.csomni.com/products/[prodToken||slug] \
  --header 'token: 123'
```

> The above command returns JSON structured like this:

```json
{
  "prodToken": "prod_123456",
  "companyToken": "comp_123456",
  "prodName": "No moref",
  "prodImage": {
    "file": "11-24-2020/1606237454516__1133421__1605838189835__12153371__ad_-_11X17_-_Copy.jpg"
  },
  "prodImages": [],
  "prodWeight": "",
  "prodDimW": "",
  "prodDimL": "",
  "prodDimH": "",
  "prodUpc": "",
  "prodNumber": "",
  "prodPrice": 0,
  "prodDescription": "<p>asdf</p>",
  "prodHighlights": "<p>adsfadsf</p>",
  "prodAlert": "",
  "prodLowlevel": "",
  "prodSlug": "fffff",
  "prodVisible": 1,
  "prodAllowCheckout": 0,
  "prodCheckInvetory": 0,
  "prodTrackInventory": 0,
  "inventoryCount": "0",
  "shippingProduct": 0,
  "prodMetaTitle": "",
  "prodMetaDescription": "",
  "prodBrand": "brnd_123456",
  "prodType": "",
  "prodTemplate": "fdsa",
  "prodAccessories": [
    "prod_123456",
    "prod_123456"
  ],
  "google_prodCategory": "",
  "google_prodType": "",
  "google_prodCondition": "",
  "backOrderWarning": 0,
  "prodCollections": [
    "clcs_123456",
    "clcs_123456",
    "clcs_123456",
    "clcs_123456"
  ],
  "variantInfo": {
    "priceTo": 0,
    "priceFrom": 0,
    "variantCount": 4
  },
  "prodOptions": [
    {
      "optionToken": "optn_123456",
      "optionName": "size",
      "optionOrder": ""
    },
    {
      "optionToken": "optn_123456",
      "optionName": "color",
      "optionOrder": "1"
    }
  ]
}
```

This endpoint retrieves a Specific Product.

### HTTP Request

`GET https://apistore.csomni.com/products/[prodToken||slug]`

### URL Parameters

| Parameter     | Description                       |
| ------------- | --------------------------------- |
| Product Token | Token of the Product to retrieve. |
| Slug          | OR a slug of the product          |

## Get a Full Product (options,variants)

```shell
curl --request GET \
  --url https://apistore.csomni.com/products/[prodToken||slug]/full \
  --header 'token: 123'
```

> The above command returns JSON structured like this:

```json
       {
  "prodToken": "prod_123456",
  "companyToken": "comp_123456",
  "prodName": "No moref",
  "prodImage": {
    "file": "11-24-2020/1606237454516__1133421__1605838189835__12153371__ad_-_11X17_-_Copy.jpg"
  },
  "prodImages": [],
  "prodWeight": "",
  "prodDimW": "",
  "prodDimL": "",
  "prodDimH": "",
  "prodUpc": "",
  "prodNumber": "",
  "prodPrice": 0,
  "prodDescription": "<p>asdf</p>",
  "prodHighlights": "<p>adsfadsf</p>",
  "prodAlert": "",
  "prodLowlevel": "",
  "prodSlug": "fffff",
  "prodVisible": 1,
  "prodAllowCheckout": 0,
  "prodCheckInvetory": 0,
  "prodTrackInventory": 0,
  "inventoryCount": "0",
  "shippingProduct": 0,
  "prodMetaTitle": "",
  "prodMetaDescription": "",
  "prodBrand": "brnd_123456",
  "prodType": "",
  "prodTemplate": "fdsa",
  "prodAccessories": [
    "prod_123456",
    "prod_123456"
  ],
  "google_prodCategory": "",
  "google_prodType": "",
  "google_prodCondition": "",
  "backOrderWarning": 0,
  "prodCollections": [
    "clcs_123456",
    "clcs_123456",
    "clcs_123456",
    "clcs_123456"
  ],
  "variantInfo": {
    "priceTo": 0,
    "priceFrom": 0,
    "variantCount": 4
  },
  "prodOptions": [
    {
      "optionToken": "optn_123456",
      "optionName": "size",
      "optionOrder": "",
      "values": [
        "lg",
        "sm"
      ]
    },
    {
      "optionToken": "optn_123456",
      "optionName": "color",
      "optionOrder": "1",
      "values": [
        "red"
      ]
    }
  ],
  "variants": [
    {
      "prodToken": "prod_123456",
      "variantToken": "vrnt_123456",
      "companyToken": "comp_123456",
      "variantName": "ffffff",
      "variantImage": {
        "file": ""
      },
      "variantImages": [
        {
          "file": "11-24-2020/1606237454516__1133421__1605838189835__12153371__ad_-_11X17_-_Copy.jpg"
        }
      ],
      "variantWeight": "1",
      "variantDimW": "0",
      "variantDimL": "0",
      "variantDimH": "0",
      "variantUpc": "",
      "variantNumber": "pppppppppppppppppppppppppppppppppppppppppp",
      "manufacturerPartNumber": "",
      "variantPrice": 0,
      "variantMapPrice": 0,
      "variantMsrpPrice": 0,
      "variantDisplayPrice": 0,
      "variantDescription": "",
      "variantAlert": "",
      "variantLowlevel": "",
      "variantSlug": "ffffff",
      "variantVisible": 1,
      "variantAllowCheckout": 0,
      "variantCheckInvetory": 0,
      "variantTrackInventory": 0,
      "taxType": "",
      "taxable": 1,
      "inventoryCount": "8",
      "shippingProduct": 1,
      "variantMetaTitle": "",
      "variantMetaDescription": "",
      "variantBrand": "",
      "google_variantCategory": "",
      "google_variantType": "",
      "google_variantCondition": "",
      "hideGoogleData": 0,
      "sortOrder": 0,
      "dateCreated": "1610566995",
      "deleted": 0,
      "backOrderWarning": 0,
      "variantInStock": true,
      "variantOptions": [
        {
          "optionToken": "optn_123456",
          "optionValue": "sm",
          "optionName": "size"
        },
        {
          "optionToken": "optn_123456",
          "optionValue": "red",
          "optionName": "color"
        }
      ]
    },
    {
      "prodToken": "prod_123456",
      "variantToken": "vrnt_123456",
      "companyToken": "comp_123456",
      "variantName": "ffffff",
      "variantImage": {
        "file": ""
      },
      "variantImages": [
        {
          "file": "11-24-2020/1606237454516__1133421__1605838189835__12153371__ad_-_11X17_-_Copy.jpg"
        }
      ],
      "variantWeight": "1",
      "variantDimW": "0",
      "variantDimL": "0",
      "variantDimH": "0",
      "variantUpc": "",
      "variantNumber": "pppppppppppppppppppppppppppppppppppppppppp",
      "manufacturerPartNumber": "",
      "variantPrice": 0,
      "variantMapPrice": 0,
      "variantMsrpPrice": 0,
      "variantDisplayPrice": 0,
      "variantDescription": "",
      "variantAlert": "",
      "variantLowlevel": "",
      "variantSlug": "ffffff",
      "variantVisible": 1,
      "variantAllowCheckout": 0,
      "variantCheckInvetory": 0,
      "variantTrackInventory": 0,
      "taxType": "",
      "taxable": 1,
      "inventoryCount": "9",
      "shippingProduct": 1,
      "variantMetaTitle": "",
      "variantMetaDescription": "",
      "variantBrand": "",
      "google_variantCategory": "",
      "google_variantType": "",
      "google_variantCondition": "",
      "hideGoogleData": 0,
      "sortOrder": 0,
      "dateCreated": "1610566995",
      "deleted": 0,
      "backOrderWarning": 0,
      "variantInStock": true,
      "variantOptions": [
        {
          "optionToken": "optn_123456",
          "optionValue": "lg",
          "optionName": "size"
        },
        {
          "optionToken": "optn_123456",
          "optionValue": "red",
          "optionName": "color"
        }
      ]
    },
    {
      "prodToken": "prod_123456",
      "variantToken": "vrnt_123456",
      "companyToken": "comp_123456",
      "variantName": "",
      "variantImage": {
        "file": ""
      },
      "variantImages": [],
      "variantWeight": "0",
      "variantDimW": "0",
      "variantDimL": "0",
      "variantDimH": "0",
      "variantUpc": "",
      "variantNumber": "asdf;a",
      "manufacturerPartNumber": "",
      "variantPrice": 0,
      "variantMapPrice": 0,
      "variantMsrpPrice": 0,
      "variantDisplayPrice": 0,
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
      "inventoryCount": "0",
      "shippingProduct": 0,
      "variantMetaTitle": "",
      "variantMetaDescription": "",
      "variantBrand": "",
      "google_variantCategory": "",
      "google_variantType": "",
      "google_variantCondition": "",
      "hideGoogleData": 0,
      "sortOrder": 2,
      "dateCreated": "1622563231",
      "deleted": 0,
      "backOrderWarning": 0,
      "variantInStock": true
    },
    {
      "prodToken": "prod_123456",
      "variantToken": "vrnt_123456",
      "companyToken": "comp_123456",
      "variantName": "",
      "variantImage": {
        "file": ""
      },
      "variantImages": [],
      "variantWeight": "0",
      "variantDimW": "0",
      "variantDimL": "0",
      "variantDimH": "0",
      "variantUpc": "",
      "variantNumber": "",
      "manufacturerPartNumber": "",
      "variantPrice": 0,
      "variantMapPrice": 0,
      "variantMsrpPrice": 0,
      "variantDisplayPrice": 0,
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
      "inventoryCount": "0",
      "shippingProduct": 0,
      "variantMetaTitle": "",
      "variantMetaDescription": "",
      "variantBrand": "",
      "google_variantCategory": "",
      "google_variantType": "",
      "google_variantCondition": "",
      "hideGoogleData": 0,
      "sortOrder": 4,
      "dateCreated": "1622563296",
      "deleted": 0,
      "backOrderWarning": 0,
      "variantInStock": true
    }
  ]
}  
```

This endpoint retrieves a Specific Product And all its information.

### HTTP Request

`GET https://apistore.csomni.com/products/[prodToken||slug]/full`

### URL Parameters

| Parameter     | Description                                                                                                     |
| ------------- | --------------------------------------------------------------------------------------------------------------- |
| Product Token | Token of the Product to retrieve.                                                                               |
| Slug          | OR a slug of the product                                                                                        |
| full          | To get the whole product and all its variants and options                                                       |
| responseData  | comma dilimited list of response data (full,fullAccessories,specailValues,specs,firstVariant) |

### Response Data Options

| Parameter         | Description                                                   |
| ----------------- | ------------------------------------------------------------- |
| full              | Returns All variants on the product                           |
| specs             | Returns Specs on the product and variant                      |
| specialValues     | Returns Special Values on the product and variant             |
| firstVariant      | Returns only the first variant on the product (as an object)  |
| fullAccessories   | Returns array of accessory products                           |

## Get All Products

This endpoint retrieves all products

### HTTP Request

`GET https://apistore.csomni.com/products`

### Query Parameters

| Parameter                                                                                                                                                                                                 | Required | Default | Description                                                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| q                                                                                                                                                                                                         | false    | -       | If empty will bring in all values (basic syntax is {"fieldname":"value"} for example to search product name do q={"prodName":"mo"}  |
| parsedQ                                                                                                                                                                                                   | false    | -       | If empty will bring in all values this will                                                                                         |
| do a search in catch all and in prodNumber and prodUpc if itll match upc or prodNumber fully it'll return those items first else it'll only check in catchAll for partial matches. Example: parsedQ=hello |
| start                                                                                                                                                                                                     | false    | 0       | At which field to start                                                                                                             |
| rows                                                                                                                                                                                                      | false    | 10      | Amount of rows to returns                                                                                                           |
| sort                                                                                                                                                                                                      | false    | -       | Any field to sort by                                                                                                                |
| sortOrder                                                                                                                                                                                                 | false    | asc     | asc (ascending) or desc (descending)                                                                                                |
| responseData                                                                                                                                                                                              | false    | -       | comma dilimited list of response data (full,variantAggregates,specs,specialValues,firstAggregate)                                   |
| fq                                                                                                                                                                                                        | false    | -       | A list of filters (for example if you want to show items from specific collection put fq={"prodCollectionSlugs":"collection-name"}) |
| facets                                                                                                                                                                                                    | false    | -       | put the value 1 if you want to get facets for the results.                                                                          |

when user selects a Facet. Let's say brand:brnd_123, add it to the filter query JSON object. To search by multiptple
brands,put an array, do like this: fq={"prodCollectionSlugs":["brnd_1","brnd_2"]} to search for range do fq={"
variantPrice":"[* TO 500]"} where \* is anything.

### Response Data Options

| Parameter         | Description                                                   |
| ----------------- | ------------------------------------------------------------- |
| full              | Returns All variants on the product                           |
| variantAggregates | Returns the varinat count, highest and lowest priced variants |
| specs             | Returns Specs on the product and variant                      |
| specialValues     | Returns Special Values on the product and variant             |
| firstVariant      | Returns only the first variant on the product (as an object)  |
| fullAccessories   | Returns array of accessory products                           |

```shell
curl --request GET \
  --url https://apistore.csomni.com/products \
  --header 'token: 123'
```

> The above command returns JSON structured like this:

```json
[
  {
    "prodToken": "prod_abcdefgABCDEFG123",
    "companyToken": "comp_123456",
    "prodName": "Not a Highlander",
    "prodImage": {
      "file": "12-17-2020/1608227079221__15192__image.png",
      "name": "main-image-item",
      "type": ""
    },
    "prodImages": [
      {
        "file": "9-14-2021/1631634128386__40977__gabe-rebra-j7b8-kN3Dgc-unsplash.jpg",
        "name": "front",
        "type": ""
      },
      {
        "file": "Xjv2-F6Quls",
        "name": "back",
        "type": "youtube"
      },
      {
        "file": "sO65YihyZac",
        "name": "close-up",
        "type": "youtube"
      }
    ],
    "prodWeight": "",
    "prodDimW": "",
    "prodDimL": "",
    "prodDimH": "",
    "prodUpc": "",
    "prodNumber": "",
    "prodPrice": 0,
    "prodDescription": "",
    "prodHighlights": "",
    "prodAlert": "",
    "prodLowlevel": "",
    "prodSlug": "not-a-highlander",
    "prodVisible": 1,
    "prodAllowCheckout": 0,
    "prodCheckInvetory": 0,
    "prodTrackInventory": 0,
    "shippingProduct": 0,
    "prodMetaTitle": "",
    "prodMetaDescription": "",
    "prodBrand": "brnd_123456",
    "prodType": "",
    "prodTemplate": "",
    "prodAccessories": [
      "prod_123456",
      "prod_123456",
      "prod_123456"
    ],
    "google_prodCategory": "",
    "google_prodType": "",
    "google_prodCondition": "",
    "backOrderWarning": 0,
    "prodCollections": [
      "clcs_123456",
      "clcs_123456"
    ],
    "prodOptions": [
      {
        "optionToken": "optn_123456",
        "optionName": "size",
        "optionOrder": "0"
      },
      {
        "optionToken": "optn_123456",
        "optionName": "material",
        "optionOrder": "1"
      },
      {
        "optionToken": "optn_123456",
        "optionName": "color",
        "optionOrder": "blue"
      }
    ]
  },
  {
    "prodToken": "prod_123456",
    "companyToken": "comp_123456",
    "prodName": "Not a Highlander",
    "prodImage": {
      "file": "12-17-2020/1608227079221__15192__image.png",
      "name": "main-image-item",
      "type": ""
    },
    "prodImages": [
      {
        "file": "9-14-2021/1631634128386__40977__gabe-rebra-j7b8-kN3Dgc-unsplash.jpg",
        "name": "front",
        "type": ""
      },
      {
        "file": "Xjv2-F6Quls",
        "name": "back",
        "type": "youtube"
      },
      {
        "file": "sO65YihyZac",
        "name": "close-up",
        "type": "youtube"
      }
    ],
    "prodWeight": "",
    "prodDimW": "",
    "prodDimL": "",
    "prodDimH": "",
    "prodUpc": "",
    "prodNumber": "",
    "prodPrice": 0,
    "prodDescription": "",
    "prodHighlights": "",
    "prodAlert": "",
    "prodLowlevel": "",
    "prodSlug": "not-a-highlander",
    "prodVisible": 1,
    "prodAllowCheckout": 0,
    "prodCheckInvetory": 0,
    "prodTrackInventory": 0,
    "shippingProduct": 0,
    "prodMetaTitle": "",
    "prodMetaDescription": "",
    "prodBrand": "brnd_123456",
    "prodType": "",
    "prodTemplate": "",
    "prodAccessories": [
      "prod_123456",
      "prod_123456",
      "prod_123456"
    ],
    "google_prodCategory": "",
    "google_prodType": "",
    "google_prodCondition": "",
    "backOrderWarning": 0,
    "prodCollections": [
      "clcs_123456",
      "clcs_123456"
    ],
    "prodOptions": [
      {
        "optionToken": "optn_123456",
        "optionName": "size",
        "optionOrder": "0"
      },
      {
        "optionToken": "optn_123456",
        "optionName": "material",
        "optionOrder": "1"
      },
      {
        "optionToken": "optn_123456",
        "optionName": "color",
        "optionOrder": "blue"
      }
    ]
  },
  {
    "prodToken": "prod_abcdefgABCDEFG123",
    "companyToken": "comp_abcdefgABCDEFG123",
    "prodName": "Not a Highlander",
    "prodImage": {
      "file": "12-17-2020/1608227079221__15192__image.png",
      "name": "main-image-item",
      "type": ""
    },
    "prodImages": [
      {
        "file": "9-14-2021/1631634128386__40977__gabe-rebra-j7b8-kN3Dgc-unsplash.jpg",
        "name": "front",
        "type": ""
      },
      {
        "file": "Xjv2-F6Quls",
        "name": "back",
        "type": "youtube"
      },
      {123456
        "file": "sO65YihyZac",
        "name": "close-up",
        "type": "youtube"
      }
    ],
    "prodWeight": "",
    "prodDimW": "",
    "prodDimL": "",
    "prodDimH": "",
    "prodUpc": "",
    "prodNumber": "",
    "prodPrice": 0,
    "prodDescription": "",
    "prodHighlights": "",
    "prodAlert": "",
    "prodLowlevel": "",
    "prodSlug": "not-a-highlander",
    "prodVisible": 1,
    "prodAllowCheckout": 0,
    "prodCheckInvetory": 0,
    "prodTrackInventory": 0,
    "shippingProduct": 0,
    "prodMetaTitle": "",
    "prodMetaDescription": "",
    "prodBrand": "brnd_123456",
    "prodType": "",
    "prodTemplate": "",
    "prodAccessories": [
      "prod_123456",
      "prod_123456",
      "prod_123456"
    ],
    "google_prodCategory": "",
    "google_prodType": "",
    "google_prodCondition": "",
    "backOrderWarning": 0,
    "prodCollections": [
      "clcs_123456",
      "clcs_123456"
    ],
    "prodOptions": [
      {
        "optionToken": "optn_123456",
        "optionName": "size",
        "optionOrder": "0"
      },
      {
        "optionToken": "optn_123456",
        "optionName": "material",
        "optionOrder": "1"
      },
      {
        "optionToken": "optn_123456",
        "optionName": "color",
        "optionOrder": "blue"
      }
    ]
  }
]
```

## Update Inventory Count

### HTTP Request

`POST https://apistore.csomni.com/products/{token}`

### QUERY Parameters

| Parameter     | Required | Description            |
| ------------- | -------- | ---------------------- |
| count | true     | count of product     |

```shell
curl --request POST \
  --url https://apistore.csomni.com/products/{token} \
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
    --header 'token: 123'\
  --header 'customerToken: cs_123456' \
  --data '{ "count" :3"  }'

```

Response:

```json
{
  "status": "success",
  "count": 2
}
```
