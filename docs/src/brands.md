# Brands

## Get All Brands

This endpoint retrieves all brands

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/brands`

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/brands \
  --header 'token: 123'
```

> The above command returns JSON structured like this:

```json
[
  {
    "companyToken": "comp_123456",
    "brandToken": "brnd_ICuB6izokMOcVps1c8I0",
    "brandName": "aaaaaaaaaa",
    "brandImage": "",
    "createdAt": "2021-12-16 18:45:21",
    "editedAt": "2021-12-16 18:45:21"
  },
  {
    "companyToken": "comp_123456",
    "brandToken": "brnd_IFQDSodUJWQMZapLUtXr",
    "brandName": "Second brand test",
    "brandImage": "",
    "createdAt": "2021-12-16 18:45:21",
    "editedAt": "2021-12-16 18:45:21"
  },
  {
    "companyToken": "comp_123456",
    "brandToken": "brnd_nsFrcZ5A4AEavqcYSKfO",
    "brandName": "newbrnaad",
    "brandImage": "",
    "createdAt": "2021-12-16 18:45:21",
    "editedAt": "2021-12-16 18:45:21"
  }
]
```

## Get a Specific Brand

This endpoint retrieves a Specific brand.

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/brands/[brandToken]`

### URL Parameters

| Parameter  | Description        |
| ---------- | ------------------ |
| brandToken | Token of the Brand |

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/brands/[brandToken] \
  --header 'token: 123'
```

> The above command returns JSON structured like this:

```json
{
  "companyToken": "comp_123456",
  "brandToken": "brnd_nsFrcZ5A4AEavqcYSKfO",
  "brandName": "newbrnaad",
  "brandImage": "",
  "createdAt": "2021-12-16 18:45:21",
  "editedAt": "2021-12-16 18:45:21"
}
```
