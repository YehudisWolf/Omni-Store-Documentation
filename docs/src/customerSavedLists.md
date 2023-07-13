# Customer Saved List


## Create New List

### HTTP Request

`POST https://apistore.csomni.com/customeritemlist`

### Header Requirements

| Parameter     | Required | Unique | Description |
| ------------- | -------- | ------ | ----------- |
| token         | true     | true   | siteToken   |
| customerToken | true     | true   | loginToken  |


&nbsp;

Sample in Shell:

```shell
curl --request POST \
  --url https://apistore.csomni.com/customeritemlist \
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
  --header 'token: site_123', 'customerToken: cs_123' \
  --data   '{
               "listReadableName":"{{$randomAdjective}}",
               "sortOrder" : 0
           }'

```

Response:

```json
{
    "listToken": "custList_123456",
    "listReadableName": "wireless"
}
```

## Add items to List (Not for editing)

### HTTP Request

`POST https://apistore.csomni.com/customeritemlist/[custListToken]`

### Header Requirements

| Parameter     | Required | Unique | Description |
| ------------- | -------- | ------ | ----------- |
| token         | true     | true   | siteToken   |
| customerToken | true     | true   | loginToken  |

### Data Requirements

Expects an array of objects. 'listItems' includes multiple objects, each representing a list item to be added to the list. Requirements for list objects:

| Parameter     | Required | Unique | Description |
| ------------- | -------- | ------ | ----------- |
| listItem:variantToken  | true     | true   | variantToken   |
| listItem:quantity | true     | false   | quantity for variant  |
| listItem:sortOrder | true     | false   | Order in which this list item should appear  |

&nbsp;

Sample in Shell:

```shell
curl --request POST \
  --url https://apistore.csomni.com/customeritemlist/{custListToken}
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
  --header 'token: site_123', 'customerToken: cs_123' \
  --data '{
            "listItems": [
                {
                    "variantToken": "vrnt_123456",
                    "quantity": 1,
                    "sortOrder": 0
                },
                {
                    "variantToken": "vrnt_123456",
                    "quantity": 2,
                    "sortOrder": 1
                }
            ],
          }'

```

Response:

```json
{
    "listToken": "custList_123456",
    "listReadableName": "haptic",
    "sortOrder": 0,
    "listItems": [
        {
            "variantToken": "vrnt_123456",
            "quantity": 1,
            "sortOrder": 0,
            "variantDetails": {
                "prodToken": "prod_123456",
                "variantToken": "vrnt_123456",
                "companyToken": "comp_123456",
                "variantName": "Vortex Optics Raptor 8.5x32 Binocular",
                "variantImage": {
                    "file": "11-7-2021/1636320272462__115916__vtx_bin_raptor_32_f_w.jpg"
                },
                "variantImages": [
                    {
                        "file": "11-7-2021/1636320332525__115691__vtx_bin_raptor_32_b_w.jpg"
                    },
                    {
                        "file": "11-7-2021/1636320336111__89446__vtx_bin_raptor_32_fl_w.jpg"
                    },
                    {
                        "file": "11-7-2021/1636320339109__92611__vtx_bin_raptor_32_fr_w.jpg"
                    }
                ],
                "variantWeight": "2",
                "variantDimW": "10",
                "variantDimL": "8",
                "variantDimH": "3",
                "variantUpc": "875874001862",
                "variantNumber": "VXR385",
                "manufacturerPartNumber": "R385",
                "variantPrice": 0.1,
                "variantMapPrice": 0,
                "variantMsrpPrice": 0,
                "variantDisplayPrice": 129,
                "variantDescription": "<p>Porro prism performance in a mid-size, wide-angle design, Raptor binoculars offer bright, crisp images with excellent color fidelity, even in low-light conditions. The design accommodates a wide range of interpupillary distances to fit everyone in the family.</p><p><strong>Included in the Box</strong></p><ul><li>Rainguard Eyepiece Cover</li><li>Tethered objective lens covers</li><li>Comfort neck strapSoft carry case</li></ul>",
                "variantAlert": "1",
                "variantLowlevel": "0",
                "variantSlug": "vortex-optics-raptor-8-5x32-binocular",
                "variantVisible": 1,
                "taxType": "",
                "hideGoogleData": 0,
                "google_variantCategory": null,
                "google_variantType": null,
                "google_variantCondition": null,
                "taxable": 1,
                "variantAllowCheckout": 1,
                "variantCheckInvetory": 1,
                "variantTrackInventory": 0,
                "inventoryCount": 20000,
                "shippingProduct": 1,
                "variantMetaTitle": "",
                "variantMetaDescription": "",
                "variantBrand": "",
                "sortOrder": 0,
                "dateCreated": "1636320488",
                "deleted": 0,
                "backOrderWarning": 0,
                "createdAt": "2021-12-15 13:23:54",
                "editedAt": "2022-07-04 21:51:14",
                "variantInStock": true
            }
        },
        {
            "variantToken": "vrnt_123456",
            "quantity": 2,
            "sortOrder": 1,
            "variantDetails": null
        }
    ],
    "totalItemsCount": 3
}
```


## Edit List Name or Sort Order

### HTTP Request

`PUT https://apistore.csomni.com/customeritemlist/[custListToken]`

### Header Requirements

| Parameter     | Required | Unique | Description |
| ------------- | -------- | ------ | ----------- |
| token         | true     | true   | siteToken   |
| customerToken | true     | true   | loginToken  |

### Data 

| Parameter              | Required | Unique  | Description |
| -------------          | -------  | ------  | ----------- |
| sortOrder              | false    | false   | The sort order for the entire list   |
| listReadableName       | false    | false   | The name of the list  |

```shell
curl --request PUT \
  --url https://apistore.csomni.com/customeritemlist/[custListToken] \
  --header 'customerToken: [cs_token]'\
  --data-raw '{
    "sortOrder": 0,
    "listReadableName": "test 1",
    "listItems": [
        {
            "variantToken": "vrnt_123456",
            "quantity": 1
        }
    ]
}'
```
Response:

```json
{
    "listToken": "custList_123456",
    "sortOrder": 1,
    "listReadableName": "fjyyds",
    "listItems": [
        {
            "itemToken": "listItem_123456",
            "variantToken": "vrnt_123456",
            "quantity": 5,
            "sortOrder": 0
        }
    ],
    "totalItemsCount": 5
}
```

## Edit List Item 

### HTTP Request

`PUT https://apistore.csomni.com/customeritemlist/[custListToken]/[listItem]`

### Header Requirements

| Parameter     | Required | Unique | Description |
| ------------- | -------- | ------ | ----------- |
| token         | true     | true   | siteToken   |
| customerToken | true     | true   | loginToken  |

### Data 

| Parameter              | Required | Unique  | Description |
| -------------          | -------  | ------  | ----------- |
| sortOrder              | false    | false   | The sort order for the entire list   |
| listReadableName       | false    | false   | The name of the list  |

```shell
curl --request PUT \
  --url https://apistore.csomni.com/customeritemlist/[custListToken] \
  --header 'token: site_########' \
  --header 'customerToken: cs_#########' \
  --header 'Content-Type: application/json' \
  --data-raw '{
      "sortOrder" : 1,
      "variantToken": "vrnt_########",
      "quantity" : 2
  }'
```
Response:

```json
{
    "listToken": "custList_123456",
    "sortOrder": 1,
    "listReadableName": "fjyyds",
    "listItems": [
        {
            "itemToken": "listItem_123456",
            "variantToken": "vrnt_123456",
            "quantity": 2,
            "sortOrder": 1
        }
    ],
    "totalItemsCount": 2
}
```


## Get A specific list

### HTTP Request

`GET https://apistore.csomni.com/customeritemlist/[custListToken]`

| Parameter     | Required | Unique | Description |
| ------------- | -------- | ------ | ----------- |
| token         | true     | true   | siteToken   |
| customerToken | true     | true   | loginToken  |

Response:

```json
[
    {
        "listToken": "custList_123456",
        "sortOrder": 0,
        "listReadableName": "haptic",
        "listItems": [
            {
                "variantToken": "vrnt_123456",
                "quantity": 1,
                "sortOrder": 0,
                "variantDetails": {
                    "prodToken": "prod_123456",
                    "variantToken": "vrnt_123456",123456123456
                    "companyToken": "comp_123456",
                    "variantName": "Vortex Optics Raptor 8.5x32 Binocular",
                    "variantImage": {
                        "file": "11-7-2021/1636320272462__115916__vtx_bin_raptor_32_f_w.jpg"
                    },
                    "variantImages": [
                        {
                            "file": "11-7-2021/1636320332525__115691__vtx_bin_raptor_32_b_w.jpg"
                        },
                        {
                            "file": "11-7-2021/1636320336111__89446__vtx_bin_raptor_32_fl_w.jpg"
                        },
                        {
                            "file": "11-7-2021/1636320339109__92611__vtx_bin_raptor_32_fr_w.jpg"
                        }
                    ],
                    "variantWeight": "2",
                    "variantDimW": "10",
                    "variantDimL": "8",
                    "variantDimH": "3",
                    "variantUpc": "875874001862",
                    "variantNumber": "VXR385",
                    "manufacturerPartNumber": "R385",
                    "variantPrice": 0.1,
                    "variantMapPrice": 0,
                    "variantMsrpPrice": 0,
                    "variantDisplayPrice": 129,
                    "variantDescription": "<p>Porro prism performance in a mid-size, wide-angle design, Raptor binoculars offer bright, crisp images with excellent color fidelity, even in low-light conditions. The design accommodates a wide range of interpupillary distances to fit everyone in the family.</p><p><strong>Included in the Box</strong></p><ul><li>Rainguard Eyepiece Cover</li><li>Tethered objective lens covers</li><li>Comfort neck strapSoft carry case</li></ul>",
                    "variantAlert": "1",
                    "variantLowlevel": "0",
                    "variantSlug": "vortex-optics-raptor-8-5x32-binocular",
                    "variantVisible": 1,
                    "taxType": "",
                    "hideGoogleData": 0,
                    "google_variantCategory": null,
                    "google_variantType": null,
                    "google_variantCondition": null,
                    "taxable": 1,
                    "variantAllowCheckout": 1,
                    "variantCheckInvetory": 1,
                    "variantTrackInventory": 0,
                    "inventoryCount": 20000,
                    "shippingProduct": 1,
                    "variantMetaTitle": "",
                    "variantMetaDescription": "",
                    "variantBrand": "",
                    "sortOrder": 0,
                    "dateCreated": "1636320488",
                    "deleted": 0,
                    "backOrderWarning": 0,
                    "createdAt": "2021-12-15 13:23:54",
                    "editedAt": "2022-07-04 21:51:14",
                    "variantInStock": true
                }
            },
            {
                "variantToken": "vrnt_123456123456",
                "quantity": 2,
                "sortOrder": 1,
                "variantDetails": null
            }
        ],
        "createdAt": "2022-07-05 11:47:37",
        "editedAt": "2022-07-05 12:01:13",
        "totalItemsCount": 3
    }
]
```

## Get Lists by customer

### HTTP Request

### Header Requirements


`GET https://apistore.csomni.com/customeritemlist/`

| Parameter     | Required | Unique | Description |
| ------------- | -------- | ------ | ----------- |
| token         | true     | true   | siteToken   |
| customerToken | true     | true   | loginToken  |

&nbsp;

Sample in Shell:

```shell
curl --request GET \
  --url https://apistore.csomni.com/customeritemlist/ \
   --header 'token: site_123', 'customerToken: cs_123' \
```

Response:

```json
[
    {
        "ID": 7,
        "listToken": "custList_123456123456",
        "sortOrder": 0,
        "customerToken": "cust_123456",
        "companyToken": "comp_123456",
        "listReadableName": "digital",
        "listItems": []
    },
    {
        "ID": 4,
        "listToken": "custList_123456123456",
        "sortOrder": 0,
        "customerToken": "cust_123456123456",
        "companyToken": "comp_123456",
        "listReadableName": "solid state",
        "listItems": [
            {
                "itemToken": "listItem_123456123456",
                "variantToken": "vrnt_123456123456",
                "quantity": 5,
                "sortOrder": 0
            },
            {
                "itemToken": "listItem_123456",
                "variantToken": "vrnt_123456",
                "quantity": 5,
                "sortOrder": 0
            }
        ]
    },
    {
        "ID": 9,
        "listToken": "custList_123456",
        "sortOrder": 0,
        "customerToken": "cust_123456",
        "companyToken": "comp_123456",
        "listReadableName": "bluetooth",
        "listItems": []
    },
    {
        "ID": 10,
        "listToken": "custList_123456",
        "sortOrder": 0,
        "customerToken": "cust_123456",
        "companyToken": "comp_123456",
        "listReadableName": "bluetooth",
        "listItems": []
    },
    {
        "ID": 11,
        "listToken": "custList_123456",
        "sortOrder": 0,
        "customerToken": "cust_123456",
        "companyToken": "comp_123456",
        "listReadableName": "primary",
        "listItems": []
    },
    {
        "ID": 12,
        "listToken": "custList_123456",
        "sortOrder": 0,
        "customerToken": "cust_123456",
        "companyToken": "comp_123456",
        "listReadableName": "1080p",
        "listItems": []
    },
    {
        "ID": 8,
        "listToken": "custList_123456",
        "sortOrder": 1,
        "customerToken": "cust_123456",
        "companyToken": "comp_123456",
        "listReadableName": "fds",
        "listItems": [
            {
                "itemToken": "listItem_123456",
                "variantToken": "vrnt_123456",
                "quantity": 5,
                "sortOrder": 0
            }
        ]
    },
    {
        "ID": 13,
        "listToken": "custList_123456",123456
        "sortOrder": 1,
        "customerToken": "cust_123456",
        "companyToken": "comp_123456",
        "listReadableName": "fjyyds",
        "listItems": [
            {
                "itemToken": "listItem_123456",
                "variantToken": "vrnt_123456",
                "quantity": 2,
                "sortOrder": 1
            }
        ]
    }
]
```

## Delete a Full List (List and its List Items)

### HTTP Request

`DELETE https://apistore.csomni.com/customeritemlist/[listToken]`

| Parameter     | Required | Unique | Description |
| ------------- | -------- | ------ | ----------- |
| token         | true     | true   | siteToken   |
| customerToken | true     | true   | loginToken  |

&nbsp;

Sample in Shell:

```shell
curl --request DELETE \
  --url https://apistore.csomni.com/customeritemlist/[listToken] \
  --header 'content-type: application/json' \
  --header 'token: 123', 'customerToken: cs_123'
```

Respose:

```json
{
  "Deleted": true
}
```

## Delete a Full List (List and its List Items)

### HTTP Request

`DELETE https://apistore.csomni.com/customeritemlist/[listToken]/[listItemToken]`

| Parameter     | Required | Unique | Description |
| ------------- | -------- | ------ | ----------- |
| token         | true     | true   | siteToken   |
| customerToken | true     | true   | loginToken  |

&nbsp;

Sample in Shell:

```shell
curl --request DELETE \
  --url https://apistore.csomni.com/customeritemlist/[listToken]/[listItemToken] \
  --header 'content-type: application/json' \
  --header 'token: 123', 'customerToken: cs_123'
```

Respose:

```json
{
  "Deleted": true
}
```
