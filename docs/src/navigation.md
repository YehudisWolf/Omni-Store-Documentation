# Navigations

## Get a Navigation

This endpoint retrieves a full poulated navigation

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/navigations/[navigationToken/navigationSlug]`

### URL Parameters

| Parameter       | Description                                |
| --------------- | ------------------------------------------ |
| navigationToken | The token of the navigation to retreive OR |
| navigationSlug  | The slug of the navigation to retreive     |

### Response Data (Add as GET param ?responeData) comma dilimited

| Option            | Description                                     |
| ----------------- | ----------------------------------------------- |
| fullProducts      | Return the full product (Product with variants) |
| variantAggregates | Return the variant aggregates on each variant   |

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/navigations/[navigationToken/navigationSlug] \
  --header 'token: 123'
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "companyToken": "comp_123456",
  "navigationToken": "nav_0hunlFryeREclg9f",
  "name": "My Nav",
  "slug": "my-nav-slug",
  "navigationImage": "",
  "items": [
    {
      "id": 4,
      "navigationToken": "nav_0hunlFryeREclg9f",
      "navigationItemToken": "navI_tpvH1PyuWr2ewnOJ",
      "itemType": "product",
      "itemToken": "prod_dO3DKC6pXBKiPSYX",
      "sort": "1",
      "link": "",
      "fullItem": {
        "prodToken": "prod_dO3DKC6pXBKiPSYX",
        "companyToken": "comp_123456",
        "prodName": "A. Saks Expandable 26\" Soft Duffel Bag Black",
        "prodImage": {
          "file": "5-31-2021/1622471456251__6160299__jonah-brown-veEPQ7aOx8w-unsplash.jpg",
          "name": "",
          "type": ""
        },
        "prodImages": [
          {
            "file": "3-8-2021/1615234536845__119807__Quotes.png",
            "type": ""
          }
        ],
        "prodWeight": "",
        "prodDimW": "",
        "prodDimL": "",
        "prodDimH": "",
        "prodUpc": "",
        "prodNumber": "AS-AE26",
        "prodPrice": "175",
        "prodDescription": "",
        "prodHighlights": "",
        "prodAlert": "",
        "prodLowlevel": "",
        "prodSlug": "",
        "prodVisible": "1",
        "prodAllowCheckout": "0",
        "prodCheckInvetory": "0",
        "prodTrackInventory": "0",
        "inventoryCount": 0,
        "shippingProduct": 1,
        "prodMetaTitle": "",
        "prodMetaDescription": "",
        "prodBrand": "brnd_Ft1tM2ZaEZHPz4CkY6TQ",
        "prodType": "",
        "prodTemplate": "",
        "prodAccessories": [],
        "google_prodCategory": "",
        "google_prodType": "",
        "google_prodCondition": "",
        "backOrderWarning": 0,
        "prodCollections": [
          "clcs_pZYTDuzGLEQjvvlW",
          "clcs_pZYTDuzGLEQjvvlW",
          "clcs_vFPTXp7oQu0XcV7S",
          ""
        ],
        "variantInfo": {
          "priceTo": 123,
          "priceFrom": 0,
          "variantCount": 7
        },
        "prodOptions": [
          {
            "optionToken": "optn_wiHwKikSFxOEUK9q4slU",
            "optionName": "color",
            "optionOrder": "0"
          },
          {
            "optionToken": "optn_6agmbVov1dTdSsproX3o",
            "optionName": "size",
            "optionOrder": "2"
          },
          {
            "optionToken": "optn_4iBOdZ385V8shWA6IW1v",
            "optionName": "Another option",
            "optionOrder": "1"
          }
        ]
      }
    },

    {
      "id": 6,
      "navigationToken": "nav_0hunlFryeREclg9f",
      "navigationItemToken": "navI_NaLimtVSEvvLgGlq",
      "itemType": "search",
      "itemToken": "",
      "sort": "2",
      "link": "searchlink.com"
    },
    {
      "id": 5,
      "navigationToken": "nav_0hunlFryeREclg9f",
      "navigationItemToken": "navI_PPQRJ7H4Y63V1Djf",
      "itemType": "collection",
      "itemToken": "clcs_e49y9ZuhyE6E9wuz",
      "sort": "3",
      "link": "",
      "fullItem": [
        {
          "collectionToken": "clcs_e49y9ZuhyE6E9wuz",
          "companyToken": "comp_123456",
          "collectionName": "Luggage & Bags",
          "collectionDefaultSort": "",
          "collectionSlug": "luggage-bags",
          "collectionDescription": "",
          "collectionImage": "6-7-2018/1528384139619__144078__luggage-bags.jpg",
          "archived": "0"
        }
      ]
    }
  ]
}
```
