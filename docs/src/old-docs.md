---
title: Omni-Store Front API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - php

#toc_footers:
# - <a href='#'>Sign Up for a Developer Key</a>
#  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - bleemen/errors

search: true
---

# Introduction

Welcome to the Omni-Store end, this API is for the Omni Store Front side.

We have language bindings in Shell, and PHP! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
  --header 'token: 123'
```

```php
  <?php
 $request->setHeaders(array(
  'token' => '123'
  ));
  ?>
```

> Make sure to replace `123` with your API key.

Omni Store Front uses API Token to allow access to the API.

Omni Store Front expects for the API Token to be included in all API requests that need authentication to the server in a header that looks like the following:

`header 'token: 123'`

<aside class="notice">
You must replace <code>123</code> with your personal API key.
</aside>

# Products

## Get a Specific Product

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/products/[prodToken/slug] \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/products/[prodToken/slug]",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
  "prodName": "This is name",
  "prodNumber": "123",
  "prodUpc": "123456",
  "prodDescription": "This is a description",
  "prodAlert": true,
  "prodLowlevel": "3",
  "prodImage": {
    "file": "5-16-2019/1558035336341__607069__Imperial-Berkey-System-NMCL-E-Commerce-1.jpg"
  },
  "prodImages": ["w", "d"],
  "prodWeight": "34 LB",
  "prodDimW": 1,
  "prodDimL": 2,
  "prodDimH": 5,
  "inventoryCount": "200",
  "prodToken": "prod_vSk8g0uY4gz8gjOQ",
  "prodSlug": "niceslug",
  "prodCllections": ["clcs_2", "clcs_1e"],
  "variantInfo": {
    "varaintCount": 10,
    "priceTo": 67,
    "priceFrom": 2
  }
}
```

This endpoint retrieves a Specific Product.

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/products/[prodToken/slug]`

### URL Parameters

| Parameter     | Description                       |
| ------------- | --------------------------------- |
| Product Token | Token of the Product to retrieve. |
| Slug          | OR a slug of the product          |

## Get a Full Product (options,variants)

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/products/[prodToken/slug]/full \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/products/[prodToken/slug]/full",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
    "prodToken": "prod_123",
    "companyToken": "comp_3fgfgNjMfe5Bcst7",
    "prodName": "Base test",
     "prodImage": {
        "file": "5-16-2019/1558035336341__607069__Imperial-Berkey-System-NMCL-E-Commerce-1.jpg"
    },
    "prodImages": null,
    "prodWeight": "",
    "prodDimW": "",
    "prodDimL": "",
    "prodDimH": "",
    "prodUpc": "",
    "prodNumber": "",
    "prodPrice": "",
    "prodCostPrice": "",
    "prodDescription": "",
    "prodAlert": "",
    "prodLowlevel": "",
    "prodSlug": "",
    "prodVisible": "1",
    "prodAllowCheckout": "0",
    "prodCheckInvetory": "0",
    "prodTrackInventory": "0",
    "inventoryCount": 0,
    "shippingProduct": 0,
    "prodCollections": [],
    "variants": [
        {
            "prodToken": "prod_123",
            "variantToken": "vnt_r7ALexrjmZjsGYY3",
            "companyToken": "comp_3fgfgNjMfe5Bcst7",
            "variantName": "Moishe fVar",
            "variantImage": "",
            "variantImages": [
                {
                    "file": "5-29-2019/1559148025321__3937__mglass.png"
                }
            "variantWeight": "",
            "variantDimW": "",
            "variantDimL": "",
            "variantDimH": "",
            "variantUpc": "",
            "variantNumber": "",
            "variantPrice": ".00",
            "variantCostPrice": "",
            "variantDescription": "",
            "variantAlert": "",
            "variantLowlevel": "",
            "variantSlug": "",
            "variantVisible": "1",
            "variantAllowCheckout": "0",
            "variantCheckInvetory": "0",
            "variantTrackInventory": "0",
            "inventoryCount": 0,
            "shippingProduct": 0,
            "dateCreated": "1532094878",
            "varinatImages": null,
            "variantOptions": {
                "optn_456": "w",
                "optn_123": "value1"
            }
        },
        {
            "prodToken": "prod_123",
            "variantToken": "vrnt_4fRjcxwep6p80Jut",
            "companyToken": "comp_3fgfgNjMfe5Bcst7",
            "variantName": "Moishe fVar",
            "variantImage": "",
            "variantImages": [
                {
                    "file": "5-29-2019/1559148025321__3937__mglass.png"
                }
            "variantWeight": "",
            "variantDimW": "",
            "variantDimL": "",
            "variantDimH": "",
            "variantUpc": "",
            "variantNumber": "",
            "variantPrice": ".00",
            "variantCostPrice": "",
            "variantDescription": "",
            "variantAlert": "",
            "variantLowlevel": "",
            "variantSlug": "",
            "variantVisible": "1",
            "variantAllowCheckout": "0",
            "variantCheckInvetory": "0",
            "variantTrackInventory": "0",
            "inventoryCount": 0,
            "shippingProduct": 0,
            "dateCreated": "1532097163",
            "varinatImages": null,
            "variantOptions": {
                "optn_123": "value1",
                "optn_456": "valuex2"
            }
        }
    ],
     "prodOptions": [
        {
            "optionToken": "optn_eo6iih3bpIX2aeOS3bno",
            "optionName": "Size",
            "optionOrder": "",
            "values": [
                "Blue",
                "Green"
            ]
        },
        {
            "optionToken": "optn_hExz1WLP8oye5ZXOOtFW",
            "optionName": "Color",
            "optionOrder": "",
            "values": [
                "Large",
                "Small"
            ]
        }
    ],
       "variantInfo": {
        "varaintCount": 10,
        "priceTo": 67,
        "priceFrom": 2
    }
}
```

This endpoint retrieves a Specific Product And all its information.

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/products/[prodToken/slug]/full`

### URL Parameters

| Parameter     | Description                                                                                                     |
| ------------- | --------------------------------------------------------------------------------------------------------------- |
| Product TOken | Token of the Product to retrieve.                                                                               |
| Slug          | OR a slug of the product                                                                                        |
| full          | To get the whole product and all its variants and options                                                       |
| responseData  | comma dilimited list of response data (full,fullAccessories,variantAggregates,specailValues,specs,firstVariant) |

### Response Data Options
| Parameter         | Description                                                   |
| ----------------- | ------------------------------------------------------------- |
| full              | Returns All variants on the product                           |
| variantAggregates | Returns the varinat count, highest and lowest priced variants |
| specs             | Returns Specs on the product and variant                      |
| specialValues     | Returns Special Values on the product and variant             |
| firstVariant      | Returns only the first variant on the product (as an object)  |
| fullAccessories   | Returns array of accessory products                           |

<!--


## Get a Specific Product by Slug



```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/products/prodSlug \
  --header 'token: 123'
```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/products/prodSlug",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
    "prodName": "This is name",
    "prodNumber": "123",
    "prodUpc" : "123456",
    "prodDescription": "This is a description",
    "prodAlert": true,
    "prodLowlevel": "3",
    "prodImage": "123",
    "prodImages": [
        "w",
        "d"
    ],
    "prodWeight": "34 LB",
    "prodDimW": 1,
    "prodDimL": 2,
    "prodDimH": 5,
    "inventoryCount": "200",
    "prodToken": "prod_vSk8g0uY4gz8gjOQ",
    "prodSlug" : "niceslug"
}
```

This endpoint retrieves a Specific Product.



### HTTP Request

`GET https://api.omnifront.cloudsnob.com/products/prodSlug`




### URL Parameters

| Parameter    | Description                              |
| ------------ | ---------------------------------------- |
| Product Slug | Product Slug of the Product to retrieve. |

 -->

## Get All Products

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/products \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/products",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
[
  {
    "prodToken": "prod_BqrDoFZe1Nf04wXr",
    "prodName": "This is name",
    "prodNumber": "123",
    "prodDescription": "This is a description",
    "prodAlert": "1",
    "prodLowlevel": "3",
    "inventoryCount": "",
    "prodImage": {
      "file": "5-16-2019/1558035336341__607069__Imperial-Berkey-System-NMCL-E-Commerce-1.jpg"
    }
  },
  {
    "prodToken": "prod_e3AOqsnwC4AYihts",
    "prodName": "This is name",
    "prodNumber": "123",
    "prodDescription": "This is a description",
    "prodAlert": "1",
    "prodLowlevel": "3",
    "inventoryCount": "200",
    "prodImage": {
      "file": "5-16-2019/1558035336341__607069__Imperial-Berkey-System-NMCL-E-Commerce-1.jpg"
    }
  },
  {
    "prodToken": "prod_vSk8g0uY4gz8gjOQ",
    "prodName": "This is name",
    "prodNumber": "123",
    "prodDescription": "This is a description",
    "prodAlert": "1",
    "prodLowlevel": "3",
    "inventoryCount": "200",
    "prodImage": {
      "file": "5-16-2019/1558035336341__607069__Imperial-Berkey-System-NMCL-E-Commerce-1.jpg"
    }
  }
]
```

This endpoint retrieves all products

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/products`

### Query Parameters
| Parameter                                                                                                                                                                         | Required | Default | Description                                                                                                            |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | ------- | ---------------------------------------------------------------------------------------------------------------------- |
| q                                                                                                                                                                                 | false    | -       | If empty will bring in all values (basic syntax is fieldname:value for example to search product name do q=prodName:mo |
| parsedQ                                                                                                                                                                           | false    | -       | If empty will bring in all values  this will                                                                           |
| do a search in catch all and in prodNumber and prodUpc if itll match upc or prodNumber fully it'll return those items first else it'll only check in catchAll for partial matches |
| start                                                                                                                                                                             | false    | 0       | At which field to start                                                                                                |
| rows                                                                                                                                                                              | false    | 10      | Amount of rows to returns                                                                                              |
| sort                                                                                                                                                                              | false    | -       | Any field to sort by                                                                                                   |
| sortOrder                                                                                                                                                                         | false    | asc     | asc (ascending) or desc (descending)                                                                                   |
| responseData                                                                                                                                                                      | false    | -       | comma dilimited list of response data (full,variantAggregates,specs,specialValues,firstAggregate)                      |
| fq                                                                                                                                                                                | false    | -       | A list of filters (for example if you want to show items from specific collection put prodCollections:collectionToken) |

### Response Data Options
| Parameter         | Description                                                   |
| ----------------- | ------------------------------------------------------------- |
| full              | Returns All variants on the product                           |
| variantAggregates | Returns the varinat count, highest and lowest priced variants |
| specs             | Returns Specs on the product and variant                      |
| specialValues     | Returns Special Values on the product and variant             |
| firstVariant      | Returns only the first variant on the product (as an object)  |
| fullAccessories   | Returns array of accessory products                           |


# Collections (static)

## Get All Collections

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/collections \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/collections",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
[
  {
    "collectionToken": "clcs_5KHj1s7ZluZ9yKFy",
    "companyToken": "comp_3fgfgNjMfe5Bcst7",
    "collectionName": "c 1d23",
    "collectionDefaultSort": "b",
    "collectionSlug": "d",
    "collectionDescription": "",
    "collectionImage": "",
    "archived": "0"
  },
  {
    "collectionToken": "clcs_EoexlRSAdfrkH37d",
    "companyToken": "comp_3fgfgNjMfe5Bcst7",
    "collectionName": "NAME",
    "collectionDefaultSort": "b",
    "collectionSlug": "SLUG",
    "collectionDescription": "desc",
    "collectionImage": "url.url.com",
    "archived": "0"
  }
]
```

This endpoint retrieves all collections

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/collections`

## Get a Specific Collection

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/collections/[collectiontoken,collectionSlug] \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/collections/[collectiontoken,collectionSlug]",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
  "collectionToken": "clcs_5KHj1s7ZluZ9yKFy",
  "companyToken": "comp_3fgfgNjMfe5Bcst7",
  "collectionName": "c 1d23",
  "collectionDefaultSort": "b",
  "collectionSlug": "d",
  "collectionDescription": "",
  "collectionImage": "",
  "archived": "0",
  "products": [
    {
      "id": "1",
      "productToken": "prod_BqrDoFZe1Nf04wXr",
      "collectionToken": "clcs_5KHj1s7ZluZ9yKFy",
      "prodToken": "prod_BqrDoFZe1Nf04wXr",
      "companyToken": "comp_3fgfgNjMfe5Bcst7",
      "prodName": "This is name test",
      "prodImage": "",
      "prodImages": "",
      "prodWeight": "",
      "prodDimW": "",
      "prodDimL": "",
      "prodDimH": "",
      "prodUpc": "",
      "prodNumber": "123",
      "prodPrice": "",
      "prodCostPrice": "",
      "prodDescription": "This is a description",
      "prodAlert": "",
      "prodLowlevel": "3",
      "prodSlug": "",
      "prodVisible": "2",
      "inventoryCount": "3",
      "archived": "1"
    },
    {
      "id": "4",
      "productToken": "prod_DRPBsXOgYfHqqcDB",
      "collectionToken": "clcs_5KHj1s7ZluZ9yKFy",
      "prodToken": "prod_DRPBsXOgYfHqqcDB",
      "companyToken": "comp_3fgfgNjMfe5Bcst7",
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
      "prodAlert": "",
      "prodLowlevel": "",
      "prodSlug": "",
      "prodVisible": "1",
      "inventoryCount": "",
      "archived": "1"
    }
  ]
}
```

This endpoint retrieves a Specific Collecdtion and its products.

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/collections/[collectiontoken,collectionSlug]`

### URL Parameters

| Parameter      | Description                 |
| -------------- | --------------------------- |
| collectionTken | Token of the Collection, Or |
| collectionSlug | Slug of the collection      |















# Brands

## Get All Brands

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/brands \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/brands",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
[
  {
    "companyToken": "comp_sfgb50s0dsdgsfh5g",
    "brandToken": "brnd_2UJFjRsFMRECMtcqSvTx",
    "brandName": "arrow-down",
    "brandImage": "9-2-2020/1599064728110__1059__photo_2020-07-26_13-44-22.jpg"
},
  {
    "companyToken": "comp_sfgb50s0dsdgsfh5g",
    "brandToken": "brnd_2UJFjRsFMRECMtcqSvTx",
    "brandName": "arrow-down",
    "brandImage": "9-2-2020/1599064728110__1059__photo_2020-07-26_13-44-22.jpg"
}
]
```

This endpoint retrieves all brands

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/brands`

## Get a Specific Brand

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/brands/[brandToken] \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/brands/[brandToken]",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
    "companyToken": "comp_sfgb50s0dsdgsfh5g",
    "brandToken": "brnd_2UJFjRsFMRECMtcqSvTx",
    "brandName": "arrow-down",
    "brandImage": "9-2-2020/1599064728110__1059__photo_2020-07-26_13-44-22.jpg"
}
```

This endpoint retrieves a Specific brand.

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/brands/[brandToken]`

### URL Parameters

| Parameter  | Description        |
| ---------- | ------------------ |
| brandToken | Token of the Brand |





# Cart

## New Cart

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/cart/ \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{"customerToken" : "cusst444"}'

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/collections",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"customerToken\" : \"cusst444\"}",
  CURLOPT_HTTPHEADER => array(
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this

```json
{
  "cartToken": "cart_k3YtQ3MRqtTZBBQ90WBMotTt",
  "companyToken": "comp_3fgfgNjMfe5Bcst7",
  "siteToken": "site_123",
  "customerToken": "cust_RqpJFDxXBB1LBJXZqSVYpuBl",
  "status": "cart created"
}
```

This endpoint creates a cart

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/cart`

### Query Parameters

| Parameter     | Required | Unique | Description                                 |
| ------------- | -------- | ------ | ------------------------------------------- |
| customerToken | false    | -      | Customer Token (creates a new one if empty) |

## Get A Cart

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/cart/[cartToken,customerToken] \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/cart/[cartToken,customerToken]",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
  "companyToken": "comp_3fgfgNjMfe5Bcst7",
  "siteToken": "site_123",
  "cartToken": "cart_33FkeUtvV7PXTwMOVCCcVa0S",
  "customerToken": "cust_111",
  "cartTotal": "",
  "cartCreated": "1529255077",
  "cartLastTouched": "1529255077",
  "deleted": "0",
  "pricing": {
    "total": 1319.85
  },
  "cartProds": [
    {
      "cartToken": "cart_33FkeUtvV7PXTwMOVCCcVa0S",
      "cartProdToken": "cp_jCqyXOHIH6ZwEecEMVMYDyr4",
      "cartProdQuantity": "6",
      "prodToken": "prod_xo22yxyybFUhVU3V",
      "deleted": "0",
      "product": {
        "prodToken": "prod_xo22yxyybFUhVU3V",
        "companyToken": "comp_3fgfgNjMfe5Bcst7",
        "prodName": "Ner Mitzvah On The Go Shabbos Set",
        "prodImage": "5-30-2018/1527707245740__578534__NM-23020.jpg",
        "prodImages": [],
        "prodWeight": "",
        "prodDimW": "",
        "prodDimL": "",
        "prodDimH": "",
        "prodUpc": "706132230208",
        "prodNumber": "NM-23020",
        "prodPrice": "100",
        "prodCostPrice": "",
        "prodDescription": "",
        "prodAlert": "",
        "prodLowlevel": "",
        "prodSlug": "",
        "prodVisible": "1",
        "prodAllowCheckout": "0",
        "prodCheckInvetory": "1",
        "prodTrackInventory": "1",
        "inventoryCount": "5",
        "prodCollections": []
      },
      "pricing": {
        "total": 600
      }
    },
    {
      "cartToken": "cart_33FkeUtvV7PXTwMOVCCcVa0S",
      "cartProdToken": "cp_UBV7udWZ1NtZnivHnOzdJojM",
      "cartProdQuantity": "2",
      "prodToken": "prod_dx6Ki74Qvb3vOhZn",
      "deleted": "0",
      "product": {
        "prodToken": "prod_dx6Ki74Qvb3vOhZn",
        "companyToken": "comp_3fgfgNjMfe5Bcst7",
        "prodName": "AquaPockets Bottle Carrier Black",
        "prodImage": "5-30-2018/1527707366286__376332__ST-STBG82BLK.jpg",
        "prodImages": [],
        "prodWeight": "",
        "prodDimW": "",
        "prodDimL": "",
        "prodDimH": "",
        "prodUpc": "088838850363",
        "prodNumber": "ST-STBG82BLK",
        "prodPrice": "120",
        "prodCostPrice": "",
        "prodDescription": "",
        "prodAlert": "",
        "prodLowlevel": "",
        "prodSlug": "",
        "prodVisible": "1",
        "prodAllowCheckout": "1",
        "prodCheckInvetory": "0",
        "prodTrackInventory": "0",
        "inventoryCount": "1",
        "prodCollections": []
      },
      "pricing": {
        "total": 240
      }
    },
    {
      "cartToken": "cart_33FkeUtvV7PXTwMOVCCcVa0S",
      "cartProdToken": "cp_YeeR4joVNdgSwjfSoPESkiH8",
      "cartProdQuantity": "3",
      "prodToken": "prod_nHc1b0iV8NsN2RGw",
      "deleted": "0",
      "product": {
        "prodToken": "prod_nHc1b0iV8NsN2RGw",
        "companyToken": "comp_3fgfgNjMfe5Bcst7",
        "prodName": "Samsonite Solyte 21\" Purple ccxx",
        "prodImage": "",
        "prodImages": null,
        "prodWeight": "",
        "prodDimW": "",
        "prodDimL": "",
        "prodDimH": "",
        "prodUpc": "",
        "prodNumber": "SM-738504895",
        "prodPrice": "159.95",
        "prodCostPrice": "10",
        "prodDescription": "",
        "prodAlert": "",
        "prodLowlevel": "",
        "prodSlug": "",
        "prodVisible": "1",
        "prodAllowCheckout": "0",
        "prodCheckInvetory": "0",
        "prodTrackInventory": "0",
        "inventoryCount": "3",
        "prodCollections": []
      },
      "pricing": {
        "total": 479.85
      }
    }
  ]
}
```

This endpoint retrieves a cart by cart token or customer token

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/cart/[cartToken,customerToken]`

### URL Parameters

| Parameter     | Required                 | Unique | Description                  |
| ------------- | ------------------------ | ------ | ---------------------------- |
| customerToken | true (or cart token)     | -      | Customer Token for this cart |
| cartToken     | true (or customer token) | -      | cart Token to retreive       |

## Add cart to customer

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/cart/combine/carttoken/ \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123, customertoken : cust_123' \
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/cart/combine/carttoken",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"customerToken\" : \"cusst444\"}"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this

```json
{
  "companyToken": "comp_3fgfgNjMfe5Bcst7",
  "siteToken": "site_123",
  "cartToken": "cart_6yZ0bcIz0isgUMYJTOk6fnr4",
  "customerToken": "cust_123",
  "cartTotal": "",
  "cartCreated": "1529353254",
  "cartLastTouched": "1529353254",
  "deleted": "0",
  "pricing": {
    "total": 639.8
  },
  "cartProds": [
    {
      "cartToken": "cart_6yZ0bcIz0isgUMYJTOk6fnr4",
      "cartProdToken": "cp_xTg1gL9IplaOpFlnNUFkcep3",
      "cartProdQuantity": "4",
      "prodToken": "prod_nHc1b0iV8NsN2RGw",
      "deleted": "0",
      "product": {
        "prodToken": "prod_nHc1b0iV8NsN2RGw",
        "companyToken": "comp_3fgfgNjMfe5Bcst7",
        "prodName": "Samsonite Solyte 21\" Purple ccxx",
        "prodImage": "",
        "prodImages": null,
        "prodWeight": "",
        "prodDimW": "",
        "prodDimL": "",
        "prodDimH": "",
        "prodUpc": "",
        "prodNumber": "SM-738504895",
        "prodPrice": "159.95",
        "prodCostPrice": "10",
        "prodDescription": "",
        "prodAlert": "",
        "prodLowlevel": "",
        "prodSlug": "",
        "prodVisible": "1",
        "prodAllowCheckout": "0",
        "prodCheckInvetory": "1",
        "prodTrackInventory": "0",
        "inventoryCount": "3000",
        "prodCollections": []
      },
      "pricing": {
        "total": 639.8
      }
    }
  ]
}
```

This endpoint Adds a user to a cart

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/cart/combine/cartToken`

### URL Parameters

| Parameter | Required | Unique | Description        |
| --------- | -------- | ------ | ------------------ |
| combine   | true     | -      | To combine 2 carts |
| cartToken | true     | -      | Cart to transfer   |

# Cart Products

## Add Product to cart

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/cartprods/cartToken \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{ "cartProdQuantity" : "1", "prodToken" : "prod_nHc1b0iV8NsN2RGw", "customerToken" : "cust_111" }'

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/cartprods/cartToken",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
    CURLOPT_POSTFIELDS => "{ \"cartProdQuantity\" : \"1\", \"prodToken\" : \"prod_nHc1b0iV8NsN2RGw\", \"customerToken\" : \"cust_111\" }",

  CURLOPT_HTTPHEADER => array(
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this

```json
{
  "cartToken": "cart_33FkeUtvV7PXTwMOVCCcVa0S",
  "cartProdToken": "cp_lJgk0e8n8ZM7d2hJBTutM0R6",
  "cartProdQuantity": "1",
  "customerToken": "cust_111",
  "status": "Prod Added"
}
```

> if Prod in cart already The above command returns JSON structured like this

```json
{
  "cartToken": "cart_uaBOzPYHQ42upIDFWX6WIftq",
  "prodToken": "prod_nHc1b0iV8NsN2RGw",
  "status": "Prod Updated"
}
```

This endpoint Adds a product to a cart

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/cartprods/cartToken`

### Query Parameters

| Parameter        | Required | Unique | Description                                   |
| ---------------- | -------- | ------ | --------------------------------------------- |
| cartToken        | false    | -      | Cart to add product to (creates one if enpty) |
| customerToken    | false    | -      | Customer Token (creates a new one if empty)   |
| prodToken        | true     | -      | Variant Token                                 |
| cartProdQuantity | true     | -      | Quantity to add to cart                       |

## Edit cart product

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/cartprods/cartProdToken \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{ "cartProdQuantity" : "1" }'

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/cartprods/cartProdToken",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
    CURLOPT_POSTFIELDS => "{ \"cartProdQuantity\" : \"1\"}",

  CURLOPT_HTTPHEADER => array(
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this

```json
{
  "cartProdToken": "cp_Yrr8oQ2BiZMTcUllOqG83Drv",
  "cartProdQuantity": "50",
  "prodToken": "prod_nHc1b0iV8NsN2RGw"
}
```

This endpoint Edits a product in cart

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/carts/cartToken`

### Query Parameters

| Parameter        | Required | Unique | Description             |
| ---------------- | -------- | ------ | ----------------------- |
| cartProdQuantity | true     | -      | Quantity to add to cart |

## Get A Cart Product

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/cartprods/cartProdToken[cartToken,customerToken] \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/cartprods/cartProdToken",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
  "cartToken": "cart_uaBOzPYHQ42upIDFWX6WIftq",
  "cartProdToken": "cp_Yrr8oQ2BiZMTcUllOqG83Drv",
  "cartProdQuantity": "5",
  "prodToken": "prod_nHc1b0iV8NsN2RGw",
  "deleted": "0"
}
```

This endpoint retrieves a cart products

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/cart/[cartToken,customerToken]`

### URL Parameters

| Parameter     | Required | Unique | Description                    |
| ------------- | -------- | ------ | ------------------------------ |
| cartProdToken | true     | -      | cart product Token to retreive |

## Delete a Product from cart

```shell
curl --request DELETE \
  --url https://api.omnifront.cloudsnob.com/cartprod/cartProdToken \
  --header 'content-type: application/json' \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/cartprod/cartProdToken",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "DELETE",
  CURLOPT_HTTPHEADER => array(
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
  "token": "prod_token",
  "deleted": "true"
}
```

This endpoint deletes (archives) a cart product

### HTTP Request

`DELETE https://api.omnifront.cloudsnob.com/cartprod/cartProdToken`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| Token     | The Token of the cart tproduct |

# Customers

## Create/Edit Customer

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/customers/ \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{ "customerFirstName" : "Moishe", "customerLastName" : "Blue", "customerEmail" : "mschwartz@evselt.com", "customerPassword" : "123456Aa" }'

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/customers/",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
   CURLOPT_POSTFIELDS => "{ \"customerFirstName\" : \"Moishe\", \"customerLastName\" : \"Blue\", \"customerEmail\" : \"mschwartz@evselt.com\", \"customerPassword\" : \"123456Aa\" }",


  CURLOPT_HTTPHEADER => array(
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this

```json
{
  "customerToken": "cust_xBedClkqViWqaBVSQ4D7ZSXm",
  "customerEmail": "mschwartahz@evselt.com",
  "customerFirstName": "Moishe",
  "customerLastName": "Blue",
  "customerPhone": null
}
```

This endpoint Creates/edits a customer

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/customers/`

### Query Parameters

| Parameter           | Required | Unique | Description           |
| ------------------- | -------- | ------ | --------------------- |
| customerEmail       | true     | true   | Customer Email        |
| customerFirstName   | true     | false  | Customer First Name   |
| customerLastName    | true     | false  | Customer Last Name    |
| customerPhone       | false    | false  | Customer Phone Number |
| customerPassword    | true     | false  | Customer Password     |
| customerCompanyName | false    | false  | Company Name          |

### URL Parameters - for edit

| Parameter     | Required | Unique | Description                   |
| ------------- | -------- | ------ | ----------------------------- |
| customerToken | true     | true   | Token of the customer to edit |

## Get A Specific Customer

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/customers/customerToken \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/customers/customerToken",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
  "companyToken": "comp_3fgfgNjMfe5Bcst7",
  "customerToken": "cust_xBedClkqViWqaBVSQ4D7ZSXm",
  "customerFirstName": "Moishe",
  "customerLastName": "Blue",
  "customerEmail": "mschwartahz@evselt.com",
  "customerPhone": "",
  "dateCreated": "1529341050",
  "guest": "0",
  "archived": "0"
}
```

This endpoint retrieves a Specific customer (requires a custtoken in the header)

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/customers/customerToken`

### URL Parameters

| Parameter     | Required | Unique | Description                      |
| ------------- | -------- | ------ | -------------------------------- |
| customerToken | true     | -      | Toke of the customer to retreive |

## Delete a Specific customer - (not allowed)

```shell
curl --request DELETE \
  --url https://api.omnifront.cloudsnob.com/customers\
  --header 'content-type: application/json' \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/customers",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "DELETE",
  CURLOPT_HTTPHEADER => array(
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
  "token": "cust_token",
  "deleted": "true"
}
```

This endpoint deletes (soft) a customer

### HTTP Request

`DELETE https://api.omnifront.cloudsnob.com/customers`

# Customer Login

## Login

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/login \
  --header 'cache-control: no-cache' \
  --header 'token: 123' \
  --data '{\n "customerEmail" : "tesst@gmail.com",\n  "customerPassword" : "Abc12345"\n}'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/signup",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
    CURLOPT_POSTFIELDS => "{\n\t\"customerEmail\" : \"test@gmail.com\",\n\t\"customerPassword\" : \"Abc12345\"\n}",
  CURLOPT_HTTPHEADER => array(
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this:

```json
{
  "userToken": "usr_123",
  "companyToken": "comp_3fgfgNjMfe5Bcst7",
  "name": "Moses Schwartz",
  "email": "mschwartz@evelt.com",
  "phone": "8455008070",
  "createdOn": "1505148766",
  "lastLogin": "1529415579"
}
```

This endpoint returns loged in user.

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/login`

### Request Headers (to combine existing cart)

| Parameter     | Required | Description                    |
| ------------- | -------- | ------------------------------ |
| customerToken | true     | Current (Guest) Customer Token |


### Query Parameters

| Parameter        | Required | Description        |
| ---------------- | -------- | ------------------ |
| customerEmail    | true     | Customer Email.    |
| customerPassword | true     | Customer Password. |

# Addresses

## Add/Edit Address

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/addresses/[addressToken] \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{ "customerToken" : "cust_123", "address" : "123 Main street", "address2" : "unit 4", "addressCity" : "Monsey", "addressState" : "NY", "addressZip" : "10952", "addressCountry" : "USA" }'

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/cartprods/cartToken",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{ \"customerToken\" : \"cust_123\", \"address\" : \"123 Main street\", \"address2\" : \"unit 4\", \"addressCity\" : \"Monsey\", \"addressState\" : \"NY\", \"addressZip\" : \"10952\", \"addressCountry\" : \"USA\" }",

  CURLOPT_HTTPHEADER => array(
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this

```json
{
  "customerToken": "cust_123",
  "address": "123 Main street",
  "address2": "unit 4",
  "addressCity": "Monsey",
  "addressState": "NY",
  "addressZip": "10952",
  "addressToken": "adrs_NO1gKGybxtbysMKmAUip9lN0"
}
```

This endpoint Adds/Edits a address

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/addresses/[addressToken]`

### Query Parameters

| Parameter        | Required                                | Unique | Description                                  |
| ---------------- | --------------------------------------- | ------ | -------------------------------------------- |
| customerToken    | true                                    | false  | Customer Token                               |
| addressLabel     | false                                   | false  | Address Label (home,work)                    |
| addressFirstName | false                                   | false  | Address First Name (first name of recipient) |
| addressLastName  | false                                   | false  | Address Last Name (last name of recipient)   |
| address          | true                                    | false  | Address                                      |
| address2         | false                                   | false  | Address Line 2                               |
| addressCity      | true                                    | false  | City                                         |
| addressState     | true                                    | false  | State                                        |
| addressZip       | true                                    | false  | Zip Code                                     |
| addressCountry   | true (If empty it entres United States) | false  | Country                                      |
| addressDefault   | false                                   | false  | Mark as default address                      |
| phoneNumber      | false                                   | false  | Phone Number                                 |
| mobileNumber     | false                                   | false  | Mobile Number                                |

### URL Parameters (for edit)

| Parameter    | Required | Unique | Description           |
| ------------ | -------- | ------ | --------------------- |
| addressToken | true     | false  | Address Token to edit |

## Get All Addresses for Customer

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/addresses \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/addresses",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
[
  {
    "addressToken": "adrs_NfE2VChqZC3mKdtpYqzT7GY7",
    "address": "13 Main street",
    "address2": "unit 4",
    "addressCity": "Monsey",
    "addressState": "NY",
    "addressZip": "10952",
    "addressCountry": "USA",
    "customerToken": "cust_123"
  },
  {
    "addressToken": "adrs_NO1gKGybxtbysMKmAUip9lN0",
    "address": "123 Main street",
    "address2": "unit 4",
    "addressCity": "Monsey",
    "addressState": "NY",
    "addressZip": "10952",
    "addressCountry": "USA",
    "customerToken": "cust_123"
  }
]
```

This endpoint retrieves all addresses for a specific customer

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/addresses`

## Get A Specific Address

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/addresses/addressToken \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/addresses/addressToken",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
  "addressToken": "adrs_NO1gKGybxtbysMKmAUip9lN0",
  "address": "123 Main street",
  "address2": "unit 4",
  "addressCity": "Monsey",
  "addressState": "NY",
  "addressZip": "10952",
  "addressCountry": "USA",
  "customerToken": "cust_123"
}
```

This endpoint retrieves a specific address

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/addresses/addressToken`

### URL Parameters

| Parameter    | Required | Unique | Description          |
| ------------ | -------- | ------ | -------------------- |
| AddressToken | true     | -      | Token of the Address |

## Delete a Address

```shell
curl --request DELETE \
  --url https://api.omnifront.cloudsnob.com/addresses/addressToken \
  --header 'content-type: application/json' \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/addresses/addressToken",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "DELETE",
  CURLOPT_HTTPHEADER => array(
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
  "token": "prod_token",
  "deleted": "true"
}
```

This endpoint deletes (archives) a address

### HTTP Request

`DELETE https://api.omnifront.cloudsnob.com/addresses/addressToken`

### URL Parameters

| Parameter | Description                        |
| --------- | ---------------------------------- |
| Token     | The Token of the address to delete |

# Checkout

## Chekout Step 1 (email,address)

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/checkout/info \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{"contactEmail" : "mschwartz@test.com","addressToken" : "adrs_123"}'

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/checkout/info",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"contactEmail\" : \"m@evelt.com\",\"addressToken\" : \"adrs_123\"}",
  CURLOPT_HTTPHEADER => array(
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this

```json
{
  "id": "1",
  "cartToken": "cart_uVCTu26zon4Zjut2YZ399BiG",
  "customerToken": "cust_CrMpXsC9jVuzpOtLg58OqfBT",
  "addressToken": "adrs_Ik8y7FrJHm8wgkzqPtNVVHOB",
  "shippingMethod": "",
  "shippingMethodId": "",
  "contactEmail": "schwart@ygmaitl.com",
  "shippingMethodsJson": [
    {
      "desc": "UPS Ground",
      "rate": 19.5433333333,
      "negotiated_rate": 17.86,
      "currency": "USD",
      "service_code": "03",
      "est_delivery_time": "2018-07-02T23:00:00-00:00",
      "package_type": "",
      "rate_detail": [
        {
          "amount": 18.04,
          "currency": "USD",
          "type": "TransportationCharges"
        },
        {
          "amount": 0,
          "currency": "USD",
          "type": "376"
        },
        {
          "amount": 1.26,
          "currency": "USD",
          "type": "375"
        },
        {
          "amount": 16.78,
          "currency": "USD",
          "type": "BaseServiceCharge"
        }
      ],
      "billing_weight": 10,
      "carrier": "ups",
      "origRate": 18.04,
      "id": "3jiJ0s56y9uGcPBHK7ZV2CzU"
    },
    {
      "desc": "UPS 3 Day Select",
      "rate": 63.2341666667,
      "negotiated_rate": 57.79,
      "currency": "USD",
      "service_code": "12",
      "est_delivery_time": "2018-06-28T23:00:00-00:00",
      "delivery_days": 3,
      "package_type": "",
      "rate_detail": [
        {
          "amount": 58.37,
          "currency": "USD",
          "type": "TransportationCharges"
        },
        {
          "amount": 0,
          "currency": "USD",
          "type": "376"
        },
        {
          "amount": 4.32,
          "currency": "USD",
          "type": "375"
        },
        {
          "amount": 54.05,
          "currency": "USD",
          "type": "BaseServiceCharge"
        }
      ],
      "billing_weight": 10,
      "carrier": "ups",
      "origRate": 58.37,
      "id": "EG4D9iRy6kjpdJQPUNbKr2ZC"
    },
    {
      "desc": "UPS 2nd Day Air",
      "rate": 91.975,
      "negotiated_rate": 84.05,
      "currency": "USD",
      "service_code": "02",
      "est_delivery_time": "2018-06-27T23:00:00-00:00",
      "delivery_days": 2,
      "package_type": "",
      "rate_detail": [
        {
          "amount": 84.9,
          "currency": "USD",
          "type": "TransportationCharges"
        },
        {
          "amount": 0,
          "currency": "USD",
          "type": "376"
        },
        {
          "amount": 6.29,
          "currency": "USD",
          "type": "375"
        },
        {
          "amount": 78.61,
          "currency": "USD",
          "type": "BaseServiceCharge"
        }
      ],
      "billing_weight": 10,
      "carrier": "ups",
      "origRate": 84.9,
      "id": "hZVIvkPiaHUT9y7rjW1MGeJA"
    },
    {
      "desc": "UPS Second Day Air AM",
      "rate": 106.025833333,
      "negotiated_rate": 96.89,
      "currency": "USD",
      "service_code": "59",
      "est_delivery_time": "2018-06-27T10:30:00-00:00",
      "delivery_days": 2,
      "package_type": "",
      "rate_detail": [
        {
          "amount": 97.87,
          "currency": "USD",
          "type": "TransportationCharges"
        },
        {
          "amount": 7.25,
          "currency": "USD",
          "type": "375"
        },
        {
          "amount": 90.62,
          "currency": "USD",
          "type": "BaseServiceCharge"
        },
        {
          "amount": 0,
          "currency": "USD",
          "type": "376"
        }
      ],
      "billing_weight": 10,
      "carrier": "ups",
      "origRate": 97.87,
      "id": "pNTxEPIdbSg14VKHCk59AWlz"
    },
    {
      "desc": "UPS Next Day Air Saver",
      "rate": 147.658333333,
      "negotiated_rate": 134.94,
      "currency": "USD",
      "service_code": "13",
      "est_delivery_time": "2018-06-26T15:00:00-00:00",
      "delivery_days": 1,
      "package_type": "",
      "rate_detail": [
        {
          "amount": 136.3,
          "currency": "USD",
          "type": "TransportationCharges"
        },
        {
          "amount": 0,
          "currency": "USD",
          "type": "376"
        },
        {
          "amount": 10.1,
          "currency": "USD",
          "type": "375"
        },
        {
          "amount": 126.2,
          "currency": "USD",
          "type": "BaseServiceCharge"
        }
      ],
      "billing_weight": 10,
      "carrier": "ups",
      "origRate": 136.3,
      "id": "FmNSVesj1TaJovy7OlPkGgMQ"
    },
    {
      "desc": "UPS Next Day Air",
      "rate": 147.734166667,
      "negotiated_rate": 135.01,
      "currency": "USD",
      "service_code": "01",
      "est_delivery_time": "2018-06-26T10:30:00-00:00",
      "delivery_days": 1,
      "package_type": "",
      "rate_detail": [
        {
          "amount": 136.37,
          "currency": "USD",
          "type": "TransportationCharges"
        },
        {
          "amount": 0,
          "currency": "USD",
          "type": "376"
        },
        {
          "amount": 10.1,
          "currency": "USD",
          "type": "375"
        },
        {
          "amount": 126.27,
          "currency": "USD",
          "type": "BaseServiceCharge"
        }
      ],
      "billing_weight": 10,
      "carrier": "ups",
      "origRate": 136.37,
      "id": "23vPxVH0RpCOJdUzTtms7GnF"
    },
    {
      "desc": "UPS Next Day Air Early AM",
      "rate": 182.834166667,
      "negotiated_rate": 167.08,
      "currency": "USD",
      "service_code": "14",
      "est_delivery_time": "2018-06-26T08:30:00-00:00",
      "delivery_days": 1,
      "package_type": "",
      "rate_detail": [
        {
          "amount": 168.77,
          "currency": "USD",
          "type": "TransportationCharges"
        },
        {
          "amount": 0,
          "currency": "USD",
          "type": "376"
        },
        {
          "amount": 12.5,
          "currency": "USD",
          "type": "375"
        },
        {
          "amount": 156.27,
          "currency": "USD",
          "type": "BaseServiceCharge"
        }
      ],
      "billing_weight": 10,
      "carrier": "ups",
      "origRate": 168.77,
      "id": "EsUOKwL8aAoTtYuWS1cF60BM"
    }
  ],
  "address": {
    "addressToken": "adrs_Ik8y7FrJHm8wgkzqPtNVVHOB",
    "address": "123 Main street",
    "address2": "unit 4",
    "addressCity": "Monsey",
    "addressState": "NY",
    "addressZip": "10952",
    "addressCountry": "USA",
    "customerToken": "cust_CrMpXsC9jVuzpOtLg58OqfBT"
  },
  "pricing": {
    "productsTotal": 200,
    "subTotal": 200
  }
}
```

This endpoint starts a checkout (returns all avail shipping methods if adress token is set)

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/checkout/info`

### Query Parameters

| Parameter        | Required                                                         | Unique | Description                                                 |
| ---------------- | ---------------------------------------------------------------- | ------ | ----------------------------------------------------------- |
| addressToken     | true (possible to post this in a other call then contact email)  | -      | Customer Address                                            |
| contactEmail     | true (possible to post this in a other call then address tokenl) |        | Customer Email (Gets filled automaticlly if not set)        |
| contactPhone     | true (possible to post this in a other call then address tokenl) |        | Customer Phone (Gets filled automaticlly if not set)        |
| contactFirstName | false                                                            | false  | Customer First Name (Gets filled automaticlly if not set)   |
| contactLastName  | false                                                            | false  | Customer Last Name (Gets filled automaticlly if not set)    |
| companyName      | false                                                            | false  | Customer Company Name (Gets filled automaticlly if not set) |

## Chekout Step 2 (Choose shipping method)

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/checkout/shippingmethod \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{"shippingMethodId" : "123456789"}'

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/checkout/shippingmethod",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"shippingMethodId\" : \"123456789\"}",
  CURLOPT_HTTPHEADER => array(
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this

```json
{
  "id": "1",
  "cartToken": "cart_uVCTu26zon4Zjut2YZ399BiG",
  "customerToken": "cust_CrMpXsC9jVuzpOtLg58OqfBT",
  "addressToken": "adrs_Ik8y7FrJHm8wgkzqPtNVVHOB",
  "shippingMethod": "",
  "shippingMethodId": "3jiJ0s56y9uGcPBHK7ZV2CzU",
  "contactEmail": "schwart@ygmaitl.com",
  "shippingMethodsJson": [
    {
      "desc": "UPS Ground",
      "rate": 19.5433333333,
      "negotiated_rate": 17.86,
      "currency": "USD",
      "service_code": "03",
      "est_delivery_time": "2018-07-02T23:00:00-00:00",
      "package_type": "",
      "rate_detail": [
        {
          "amount": 18.04,
          "currency": "USD",
          "type": "TransportationCharges"
        },
        {
          "amount": 0,
          "currency": "USD",
          "type": "376"
        },
        {
          "amount": 1.26,
          "currency": "USD",
          "type": "375"
        },
        {
          "amount": 16.78,
          "currency": "USD",
          "type": "BaseServiceCharge"
        }
      ],
      "billing_weight": 10,
      "carrier": "ups",
      "origRate": 18.04,
      "id": "3jiJ0s56y9uGcPBHK7ZV2CzU"
    },
    {
      "desc": "UPS 3 Day Select",
      "rate": 63.2341666667,
      "negotiated_rate": 57.79,
      "currency": "USD",
      "service_code": "12",
      "est_delivery_time": "2018-06-28T23:00:00-00:00",
      "delivery_days": 3,
      "package_type": "",
      "rate_detail": [
        {
          "amount": 58.37,
          "currency": "USD",
          "type": "TransportationCharges"
        },
        {
          "amount": 0,
          "currency": "USD",
          "type": "376"
        },
        {
          "amount": 4.32,
          "currency": "USD",
          "type": "375"
        },
        {
          "amount": 54.05,
          "currency": "USD",
          "type": "BaseServiceCharge"
        }
      ],
      "billing_weight": 10,
      "carrier": "ups",
      "origRate": 58.37,
      "id": "EG4D9iRy6kjpdJQPUNbKr2ZC"
    },
    {
      "desc": "UPS 2nd Day Air",
      "rate": 91.975,
      "negotiated_rate": 84.05,
      "currency": "USD",
      "service_code": "02",
      "est_delivery_time": "2018-06-27T23:00:00-00:00",
      "delivery_days": 2,
      "package_type": "",
      "rate_detail": [
        {
          "amount": 84.9,
          "currency": "USD",
          "type": "TransportationCharges"
        },
        {
          "amount": 0,
          "currency": "USD",
          "type": "376"
        },
        {
          "amount": 6.29,
          "currency": "USD",
          "type": "375"
        },
        {
          "amount": 78.61,
          "currency": "USD",
          "type": "BaseServiceCharge"
        }
      ],
      "billing_weight": 10,
      "carrier": "ups",
      "origRate": 84.9,
      "id": "hZVIvkPiaHUT9y7rjW1MGeJA"
    },
    {
      "desc": "UPS Second Day Air AM",
      "rate": 106.025833333,
      "negotiated_rate": 96.89,
      "currency": "USD",
      "service_code": "59",
      "est_delivery_time": "2018-06-27T10:30:00-00:00",
      "delivery_days": 2,
      "package_type": "",
      "rate_detail": [
        {
          "amount": 97.87,
          "currency": "USD",
          "type": "TransportationCharges"
        },
        {
          "amount": 7.25,
          "currency": "USD",
          "type": "375"
        },
        {
          "amount": 90.62,
          "currency": "USD",
          "type": "BaseServiceCharge"
        },
        {
          "amount": 0,
          "currency": "USD",
          "type": "376"
        }
      ],
      "billing_weight": 10,
      "carrier": "ups",
      "origRate": 97.87,
      "id": "pNTxEPIdbSg14VKHCk59AWlz"
    }
  ],
  "address": {
    "addressToken": "adrs_Ik8y7FrJHm8wgkzqPtNVVHOB",
    "address": "123 Main street",
    "address2": "unit 4",
    "addressCity": "Monsey",
    "addressState": "NY",
    "addressZip": "10952",
    "addressCountry": "USA",
    "customerToken": "cust_CrMpXsC9jVuzpOtLg58OqfBT"
  },
  "pricing": {
    "productsTotal": 200,
    "shipping": 19.5433333333,
    "subTotal": 219.543333333
  }
}
```

This endpoint selects a shipping method id (returned with each method) and returns the new total

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/checkout/shippingmethod`

### Query Parameters

| Parameter        | Required | Unique | Description             |
| ---------------- | -------- | ------ | ----------------------- |
| shippingMethodId | true     |        | ID of the method to use |

## Chekout Step 3 (Payment)

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/checkout/shippingmethod \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{"cardNumbers" : "4242424242424242", "expMonth" : "12", "expYear" : "2020", "cvv" : "123", "amount" : "333" }'

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/checkout/shippingmethod",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"cardNumbers\" : \"4242424242424242\", \"expMonth\" : \"12\", \"expYear\" : \"2020\", \"cvv\" : \"123\", \"amount\" : \"333\" }",

  CURLOPT_HTTPHEADER => array(
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this

```json
{
  "status": "success",
  "order": {
    "orderProducts": [
      {
        "cartToken": "cart_uVCTu26zon4Zjut2YZ399BiG",
        "cartProdToken": "cp_WI1VQfFpPAoKcVx9jTcvXzIo",
        "cartProdQuantity": 2,
        "prodToken": "prod_3aiNdXcBQ2CPxPny",
        "deleted": "0",
        "product": {
          "prodToken": "prod_3aiNdXcBQ2CPxPny",
          "companyToken": "comp_3fgfgNjMfe5Bcst7",
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
          "prodCollections": ["clcs_ip9Hw1k7ejnviHFi"]
        },
        "pricing": {
          "total": 200
        },
        "shipping": {
          "totalWeight": 10
        }
      }
    ],
    "orderEmail": "schwart@ygmaitl.com",
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
      "id": "NOiHJ45TzMC7ZGRtnclUdFvI"
    },
    "orderTotal": 218.7,
    "orderPaymentMethod": {
      "id": "ch_1ChkN1EmQpkAHEEPmN542zTH",
      "object": "charge",
      "amount": 2187,
      "amount_refunded": 0,
      "application": null,
      "application_fee": null,
      "balance_transaction": "txn_1ChkN1EmQpkAHEEPVfxP8ewh",
      "captured": true,
      "created": 1530131767,
      "currency": "usd",
      "customer": null,
      "description": "Moishes charge",
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
        "url": "/v1/charges/ch_1ChkN1EmQpkAHEEPmN542zTH/refunds"
      },
      "review": null,
      "shipping": null,
      "source": {
        "id": "card_1ChkN1EmQpkAHEEP2UxF9wqr",
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
        "fingerprint": "d6DaoacmudCLi151",
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
    "siteToken": "site_123",
    "companyToken": "comp_3fgfgNjMfe5Bcst7",
    "customerToken": "cust_CrMpXsC9jVuzpOtLg58OqfBT",
    "orderToken": "ordr_KHojLPQGj4j6vZRyn3GBPeGu"
  }
}
```

This endpoint pays the checkout and creates an order

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/checkout/payment`

### Query Parameters

| Parameter           | Required             | Unique | Description                                                                                                                          |
| ------------------- | -------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| cardNumbers         | true(if no token)    | false  | Card Numbers                                                                                                                         |
| expMonth            | true (if no token)   | false  | Card Exp Month                                                                                                                       |
| expYear             | true (if no token)   | false  | Card Exp Year                                                                                                                        |
| cvv                 | true (if no token)   | false  | Card CVV                                                                                                                             |
| cardToken           | true (if no numbers) | fasle  | cardToken. if card has billing address, and you do not send sameAsShipping: false, it will take shipping address for billing address |
| billingAddressLine2 | false                | fasle  | Billing Address Line 2                                                                                                               |
| billingZip          | false                | fasle  | Billing Address Zip                                                                                                                  |
| billingAddress      | false                | fasle  | Billing Address                                                                                                                      |
| billingCity         | false                | fasle  | Billing Address City                                                                                                                 |
| billingState        | false                | fasle  | Billing Address State                                                                                                                |
| billingName         | false                | fasle  | Billing Address Name                                                                                                                 |
| billingPhone        | false                | fasle  | Billing Phone Number                                                                                                                 |
| billingMobile       | false                | fasle  | Billing Mobile Number                                                                                                                |
| billingCountry      | false                | fasle  | Billing Address Country                                                                                                              |
| sameAsShipping      | true                 | fasle  | Will set billing address same as shipping even if cardToken is provided (see above)                                                  |
| billingAddressToken | false                | fasle  | Billing Address Token                                                                                                                |

## Checkout Apply Coupon

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/checkout/applycoupon \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{"couponCode" : "SUMMER20"}'

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/checkout/applycoupon",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"contactEmail\" : \"m@evelt.com\",\"addressToken\" : \"adrs_123\"}",
  CURLOPT_HTTPHEADER => array(
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this

```json
{
  "id": "117",
  "cartToken": "cart_E4uK4GcsbriLcQdangGrvYSq",
  "customerToken": "cust_HgjzzebMZgssVUqv2aCYbBUk",
  "couponCodes": ["SUMMER50"],
  "addressToken": "",
  "shippingMethod": "",
  "shippingMethodId": "",
  "shippingAddress": "",
  "shippingAddress2": "",
  "shippingZip": "",
  "shippingState": "",
  "shippingCity": "",
  "contactEmail": "",
  "contactFirstName": "",
  "contactLastName": "",
  "companyName": "",
  "contactPhone": "",
  "shippingMethodsJson": "",
  "pricing": {
    "productsTotal": 329.95,
    "origTotal": 329.95,
    "totalCouponDiscount": 164.975,
    "totalAfterCoupon": 164.98,
    "tax": 0,
    "subTotal": 164.98,
    "total": 164.98
  },
  "couponCodesInfo": [
    {
      "name": "SUMMER50",
      "msg": "Sucssecfully applied",
      "status": "valid"
    }
  ],
  "couponCodeInfo": [
    {
      "name": "SUMMER50",
      "msg": "Sucssecfully applied",
      "status": "valid"
    }
  ]
}
```

This endpoint applies a coupon code to a cart

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/checkout/applycoupon`

### Query Parameters

| Parameter  | Required | Unique | Description     |
| ---------- | -------- | ------ | --------------- |
| couponCode | true     | -      | The Coupon Code |

##Checkout Remove Coupon

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/checkout/removecoupon \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{"couponCode" : "SUMMER20"}'

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/checkout/removecoupon",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"contactEmail\" : \"m@evelt.com\",\"addressToken\" : \"adrs_123\"}",
  CURLOPT_HTTPHEADER => array(
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this

```json
{
  "id": "117",
  "cartToken": "cart_E4uK4GcsbriLcQdangGrvYSq",
  "customerToken": "cust_HgjzzebMZgssVUqv2aCYbBUk",
  "couponCodes": [],
  "addressToken": "",
  "shippingMethod": "",
  "shippingMethodId": "",
  "shippingAddress": "",
  "shippingAddress2": "",
  "shippingZip": "",
  "shippingState": "",
  "shippingCity": "",
  "contactEmail": "",
  "contactFirstName": "",
  "contactLastName": "",
  "companyName": "",
  "contactPhone": "",
  "shippingMethodsJson": "",
  "pricing": {
    "productsTotal": 329.95,
    "origTotal": 329.95,
    "totalCouponDiscount": null,
    "totalAfterCoupon": 329.95,
    "tax": 0,
    "subTotal": 329.95,
    "total": 329.95
  },
  "couponCodesInfo": []
}
```

This endpoint removes a coupon code from a cart

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/checkout/removecoupon`

### Query Parameters

| Parameter  | Required | Unique | Description     |
| ---------- | -------- | ------ | --------------- |
| couponCode | true     | -      | The Coupon Code |


#Payment Manager

## Get all Cards for customer

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/paymentmanager/cards \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/paymentmanager/cards",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
[
  {
    "cardToken": "cc_HJex2VlBc15i",
    "cardTokenStripe": "card_1CjpRDEmQpkAHEEPpwvwB4q4",
    "lastFour": "",
    "expMonth": "12",
    "expYear": "2020",
    "cvv": "123",
    "companyToken": "",
    "customerToken": "cust_lRerwQnjCPEu9AxYzdIrMKlm"
  }
]
```

This endpoint retrieves all card for a specific customer

### HTTP Request

`GET https://api.omnifront.cloudsnob.com/paymentmanage/cards`

### URL Parameters

| Parameter | Description      |
| --------- | ---------------- |
| cards     | To get all cards |

## Add Card to Customer

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/paymentmanager/addcard/ \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{ "cardNumbers" :"132456789", "expMonth" : "12", "expYear" : "2020", "cvv" : "132", "billingAddress" : "12 Main Street", "billingAddress2" : "Apt. 2", "billingZip" : "10952", "billingCity" : "Brooklyn", "billingState" : "NY", "isDefault" : true }'

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/paymentmanager/addcard",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
 CURLOPT_POSTFIELDS => "{ \"cardNumbers\" :\"132456789\", \"expMonth\" : \"12\", \"expYear\" : \"2020\", \"cvv\" : \"132\", \"billingAddress\" : \"12 Main Street\", \"billingAddress2\" : \"Apt. 2\", \"billingZip\" : \"10952\", \"billingCity\" : \"Brooklyn\", \"billingState\" : \"NY\", \"isDefault\" : true }",
  CURLOPT_HTTPHEADER => array(
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this

```json
{
  "cardNumbers": "132456789",
  "expMonth": "12",
  "expYear": "2020",
  "cvv": "132",
  "billingAddress": "12 Main Street",
  "billingAddress2": "Apt. 2",
  "billingZip": "10952",
  "billingCity": "Brooklyn",
  "billingState": "NY",
  "isDefault": true,
  "customerToken": "cust_6qljyfUYPQH052JlIDz5cUp0",
  "cardToken": "cc_TJ2KfN3u2pcF"
}
```

This endpoint adds a card to a customer

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/paymentmanager/addcard`

### Query Parameters

| Parameter       | Required | Unique | Description            |
| --------------- | -------- | ------ | ---------------------- |
| cardNumbers     | true     | false  | Card Numbers           |
| expMonth        | true     | false  | Card Exp Month         |
| expYear         | true     | false  | Card Exp Year          |
| cvv             | true     | false  | Card Cvv               |
| nameOnCard      | false    | false  | Name On Card           |
| billingAddress  | true     | false  | Card Billing Address   |
| billingAddress2 | true     | false  | Card Billing Address 2 |
| billingZip      | true     | false  | Card Billing Zip       |
| billingCity     | true     | false  | Card Billing City      |
| billingState    | true     | false  | Card Billing State     |
| billingCountry  | false    | false  | Card Billing Country   |
| billingPhone    | false    | false  | Card Billing Phone     |
| billingMobile   | false    | false  | Card Billing Mobile    |
| isDefault       | false    | false  | Card Default (Bool)    |

## Mark card as default

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/paymentmanager/markdefault/ \
  --header 'cache-control: no-cache' \
  --header 'postman-token: e0dee5b6-94b0-0dd3-f67d-b88804ec5b74' \
  --header 'token: 123' \
  --data '{ "cardToken" :"132456789"}'

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/paymentmanager/markdefault",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "POST",
 CURLOPT_POSTFIELDS => "{ \"cardToken\" :\"132456789\" }",
  CURLOPT_HTTPHEADER => array(
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
?>

```

> The above command returns JSON structured like this

```json
{
  "cardToken": "132456789"
}
```

This endpoint adds a card to a customer

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/paymentmanager/markdefault`

### Query Parameters

| Parameter | Required | Unique | Description |
| --------- | -------- | ------ | ----------- |
| cardToken | true     | false  | Card Token  |

## Remove card from customer

```shell
curl --request DELETE \
  --url https://api.omnifront.cloudsnob.com/paymentmanager/removecard \
  --header 'content-type: application/json' \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/paymentmanager/removecard",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "DELETE",
  CURLOPT_HTTPHEADER => array(
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this

```json
{
  "cardToken": "132456789"
}
```

This endpoint removes a card from a customer

### HTTP Request

`DELETE https://api.omnifront.cloudsnob.com/paymentmanager/removecard`

### Query Parameters

| Parameter | Required | Unique | Description |
| --------- | -------- | ------ | ----------- |
| cardToken | true     | false  | Card Token  |

# Navigations

## Get a Navigation

```shell
curl --request GET \
  --url https://api.omnifront.cloudsnob.com/navigations/[navigationToken/navigationSlug] \
  --header 'token: 123'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/navigations/[navigationToken/navigationSlug]",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "content-type: application/json",
    "token: 123"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "companyToken": "comp_3fgfgNjMfe5Bcst7",
  "navigationToken": "nav_0hunlFryeREclg9f",
  "name": "My Nav",
  "slug": "my-nav-slug",
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
        "companyToken": "comp_3fgfgNjMfe5Bcst7",
        "prodName": "A. Saks Expandable 26\" Soft Duffel Bag Black",
        "prodImage": "5-30-2018/1527713527563__436164__AS-AE26.jpg",
        "prodImages": [],
        "prodWeight": "",
        "prodDimW": "",
        "prodDimL": "",
        "prodDimH": "",
        "prodUpc": "",
        "prodNumber": "AS-AE26",
        "prodPrice": "175",
        "prodCostPrice": "",
        "prodDescription": "",
        "prodAlert": "",
        "prodLowlevel": "",
        "prodSlug": "",
        "prodVisible": "1",
        "prodAllowCheckout": "0",
        "prodCheckInvetory": "0",
        "prodTrackInventory": "0",
        "inventoryCount": 0,
        "shippingProduct": 1,
        "prodCollections": ["clcs_e49y9ZuhyE6E9wuz"],
        "shippiprodCheckInvetory ngProduct": 0
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
          "companyToken": "comp_3fgfgNjMfe5Bcst7",
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

# Password Reset

## Forgot Password (Send email)

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/password/reset \
  --data '{"customerEmail" : "test@gmail.com","siteToken" : "site_222"}'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/password/reset/",
  CURLOPT_CUSTOMREQUEST => "POST",
    CURLOPT_POSTFIELDS => "{\"email\" : \"test@gmail.com\",\"siteToken\" : \"site_444\"}",

  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "postman-token: 2750e0c6-36f9-f805-e258-8faa1663618a"
      ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
  "status": "success"
}
```

This endpoint send a reset password link to a user (Be careful, it always returns success even if email is not in our system vd"l)

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/password/forgot`

### Request Parameters

| Parameter     | Description    |
| ------------- | -------------- |
| customerEmail | customer email |
| siteToken     | Site Token     |

## Restore Password (from hash)

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/restorepassword \
  --data '{ "hash" : "pass_q5w3c4eqawjmnu8urhdudkm5hslrslp4xlbtb2wewt53woqgr", "newPassword" : "123456789" }'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.omnifront.cloudsnob.com/restorepassword/",
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{ \"hash\" : \"pass_q5w3c4eqawjmnu8urhdudkm5hslrslp4xlbtb2wewt53woqgr\", \"newPassword\" : \"1234eeeeee56\" }",

  CURLOPT_HTTPHEADER => array(
    "cache-control: no-cache",
    "postman-token: 2750e0c6-36f9-f805-e258-8faa1663618a"
      ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

> The above command returns JSON structured like this:

```json
{
  "status": "success"
}
```

This endpoint saves users new password

### HTTP Request

`POST https://api.omnifront.cloudsnob.com/restorepassword`

### Request Parameters

| Parameter   | Description        |
| ----------- | ------------------ |
| hash        | hash sent by email |
| newPassword | new password       |
