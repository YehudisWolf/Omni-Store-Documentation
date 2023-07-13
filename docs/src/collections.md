# Collections (static)

## Get All Collections

This endpoint retrieves all collections

### HTTP Request

`GET https://apistore.csomni.com/collections`

```shell
curl --request GET \
  --url https://apistore.csomni.com/collections \
  --header 'token: 123'
```

> The above command returns JSON structured like this:

```json
[
  {
    "collectionToken": "clcs_123456",
    "companyToken": "comp_123456",
    "collectionName": "c 1d23",
    "collectionDefaultSort": "b",
    "collectionSlug": "d",
    "collectionDescription": "",
    "collectionImage": "",
    "archived": "0",
    "collectionMetaTitle": "",
    "collectionMetaDescription": "",
    "collectionBrand": "",
    "createdAt": "2021-12-15 13:23:54",
    "editedAt": "2021-12-15 13:23:54",
    "products": []
  },
  {
    "collectionToken": "clcs_123456",
    "companyToken": "comp_123456",
    "collectionName": "NAME",
    "collectionDefaultSort": "b",
    "collectionSlug": "SLUG",
    "collectionDescription": "desc",
    "collectionImage": "url.url.com",
    "archived": "0",
    "collectionMetaTitle": "",
    "collectionMetaDescription": "",
    "collectionBrand": "",
    "collectionSortOrder": 0,
    "products": []
  }
]
```

## Get a Specific Collection

This endpoint retrieves a Specific Collecdtion and its products.

### HTTP Request

`GET https://apistore.csomni.com/collections/[collectiontoken||collectionSlug]`

### URL Parameters

| Parameter      | Description                 |
| -------------- | --------------------------- |
| collectionTken | Token of the Collection, Or |
| collectionSlug | Slug of the collection      |

```shell
curl --request GET \
  --url https://apistore.csomni.com/collections/[collectiontoken||collectionSlug] \
  --header 'token: 123'
```

> The above command returns JSON structured like this:

```json
{
  "collectionToken": "clcs_123456",
  "companyToken": "comp_123456",
  "collectionName": "c 1d23",
  "collectionDefaultSort": "b",
  "collectionSlug": "d",
  "collectionDescription": "",
  "collectionImage": "",
  "archived": "0",
  "collectionMetaTitle": "",
  "collectionMetaDescription": "",
  "collectionBrand": "",
  "createdAt": "2021-12-15 13:23:54",
  "editedAt": "2021-12-15 13:23:54",
  "products": [
    {
      "id": "4",
      "prodToken": "prod_123456",
      "collectionToken": "clcs_123456",
      "sortOrder": null,
      "companyToken": "comp_123456",
      "prodName": "brgtbr",
      "prodImage": "",
      "prodImages": "",
      "prodWeight": "",
      "prodDimW": "",
      "prodDimL": "",
      "prodDimH": "",
      "prodUpc": "rbr",
      "prodNumber": "",
      "prodPrice": "",
      "prodCostPrice": "",
      "prodDescription": "",
      "prodHighlights": "",
      "prodAlert": "",
      "prodLowlevel": "",
      "prodSlug": "",
      "prodVisible": "1",
      "prodAllowCheckout": 0,
      "prodCheckInvetory": 0,
      "prodTrackInventory": 0,
      "inventoryCount": "",
      "archived": "1",
      "shippingProduct": 0,
      "prodMetaTitle": "",
      "prodMetaDescription": "",
      "prodBrand": "",
      "prodType": "",
      "prodTemplate": "",
      "prodAccessories": "[]",
      "google_prodCategory": "",
      "google_prodType": "",
      "google_prodCondition": "",
      "backOrderWarning": 0,
      "variants": [
        {
          "prodToken": "prod_123456",
          "variantToken": "vrnt_123456",
          "companyToken": "comp_123456",
          "variantName": "Plvbnt dvbvt cghbvu",
          "variantImage": {
            "file": "[]"
          },
          "variantImages": [],
          "variantWeight": "55",
          "variantDimW": "76",
          "variantDimL": "3",
          "variantDimH": "4",
          "variantUpc": "Terrrrrrrrrra vdfgbvcxdrm u",
          "variantNumber": "Ut evbn dolor cgbnm se",
          "manufacturerPartNumber": "Vefghjmnis labore lau",
          "variantPrice": 9,
          "variantMapPrice": 0,
          "variantMsrpPrice": 0,
          "variantDisplayPrice": 21,
          "variantDescription": "",
          "variantAlert": "",
          "variantLowlevel": "46",
          "variantSlug": "plfgnm-aut-consequ",
          "variantVisible": 1,
          "variantAllowCheckout": 0,
          "variantCheckInvetory": 0,
          "variantTrackInventory": 0,
          "taxType": "",
          "taxable": 1,
          "inventoryCount": "1",
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
          "variantInStock": true
        }
      ],
      "variantInfo": {
        "priceTo": 9,
        "priceFrom": 9,
        "variantCount": 1
      }
    },
    {
      "id": "4",
      "prodToken": "prod_123456",
      "collectionToken": "clcs_123456",
      "sortOrder": null,
      "companyToken": "comp_123456",
      "prodName": "brgtbr",
      "prodImage": "",
      "prodImages": "",
      "prodWeight": "",
      "prodDimW": "",
      "prodDimL": "",
      "prodDimH": "",
      "prodUpc": "rbr",
      "prodNumber": "",
      "prodPrice": "",
      "prodCostPrice": "",
      "prodDescription": "",
      "prodHighlights": "",
      "prodAlert": "",
      "prodLowlevel": "",
      "prodSlug": "",
      "prodVisible": "1",
      "prodAllowCheckout": 0,
      "prodCheckInvetory": 0,
      "prodTrackInventory": 0,
      "inventoryCount": "",
      "archived": "1",
      "shippingProduct": 0,
      "prodMetaTitle": "",
      "prodMetaDescription": "",
      "prodBrand": "",
      "prodType": "",
      "prodTemplate": "",
      "prodAccessories": "[]",
      "google_prodCategory": "",
      "google_prodType": "",
      "google_prodCondition": "",
      "backOrderWarning": 0,
      "variants": [
        {
          "prodToken": "prod_123456",
          "variantToken": "vrnt_123456",
          "companyToken": "comp_123456",
          "variantName": "Placeat aut consequ",
          "variantImage": {
            "file": "[]"
          },
          "variantImages": [],
          "variantWeight": "55",
          "variantDimW": "76",
          "variantDimL": "3",
          "variantDimH": "4",
          "variantUpc": "qwerty voluptatem u",
          "variantNumber": "Ut ertyu erthj conse",
          "manufacturerPartNumber": "Verthjkkiuuuu labore lau",
          "variantPrice": 9,
          "variantMapPrice": 0,
          "variantMsrpPrice": 0,
          "variantDisplayPrice": 21,
          "variantDescription": "",
          "variantAlert": "",
          "variantLowlevel": "46",
          "variantSlug": "plertyut-aut-certyhjku",
          "variantVisible": 1,
          "variantAllowCheckout": 0,
          "variantCheckInvetory": 0,
          "variantTrackInventory": 0,
          "taxType": "",
          "taxable": 1,
          "inventoryCount": "1",
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
          "variantInStock": true
        }
      ],
      "variantInfo": {
        "priceTo": 9,
        "priceFrom": 9,
        "variantCount": 1
      }
    }
  ]
}
```
