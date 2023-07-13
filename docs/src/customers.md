# Customers


## Create/Edit Customer

This endpoint Creates/edits a customer

### HTTP Request

`POST https://apistore.csomni.com/customers/`

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

| Parameter             | Required | Unique | Description                   |
| --------------------- | -------- | ------ | ----------------------------- |
| header: customerToken | true     | true   | Token of the customer to edit |

```shell
curl --request POST \
  --url https://apistore.csomni.com/customers/ \
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
  --header 'token: 123' \
  --data '{ "customerFirstName" : "Sarah", "customerLastName" : "Jones", "customerEmail" : "sjones1@evselt.com", "customerPassword" : "123456Aa" }'

```

> The above command returns JSON structured like this

```json
{
  "id": 51150,
  "customerFirstName": "Sarah",
  "customerLastName": "Jones",
  "customerEmail": "sjones1@gmail.com",
  "customerPhone": "",
  "customerCompanyName": "",
  "dateCreated": "1639760040",
  "customerStatus": "",
  "customerTypes": null,
  "customerGroups": null,
  "isLoggedIn": 1,
  "customerDocs": null,
  "taxExempt": null,
  "taxExemptID": null,
  "createdAt": "2021-12-17 16:54:00",
  "editedAt": "2021-12-17 16:54:00",
  "customerToken": "cs_123456"
}
```

## Get A Specific Customer

```shell
curl --request GET \
  --url https://apistore.csomni.com/customers/ \
  --header 'token: 123'
  --header 'customerToken: cs_123456'
```

> The above command returns JSON structured like this:

```json
{
  "id": 51150,
  "customerFirstName": "Sarah",
  "customerLastName": "Jones",
  "customerEmail": "sjones1@gmail.com",
  "customerPhone": "",
  "customerCompanyName": "",
  "dateCreated": "1639760040",
  "customerStatus": "",
  "customerTypes": null,
  "customerGroups": null,
  "isLoggedIn": 1,
  "customerDocs": null,
  "taxExempt": null,
  "taxExemptID": null,
  "createdAt": "2021-12-17 16:54:00",
  "editedAt": "2021-12-17 16:57:31"
}
```

This endpoint retrieves a Specific customer (requires a custtoken in the header)

### HTTP Request

`GET https://apistore.csomni.com/customers/customerToken`

### URL Parameters

| Parameter     | Required | Unique | Description                       |
| ------------- | -------- | ------ | --------------------------------- |
| customerToken | true     | -      | Token of the customer to retreive |

## Delete a Specific customer - (not allowed)

```shell
curl --request DELETE \
  --url https://apistore.csomni.com/customers/{customerToken}\
  --header 'content-type: application/json' \
  --header 'token: 123'
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

`DELETE https://apistore.csomni.com/customers/{customerToken}`
