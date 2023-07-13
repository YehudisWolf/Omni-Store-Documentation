# Customer Login

## NOTE: 
1. isLoggedIn and Guest columns in CUSTOMER table are no longer supported and will be phased out. Look for isLoggedIn in loginToken table for logged in status of a session
2. When a customer logs into a Store account, both Customer table and loginToken table set their records column 'isLoggedIn' to 'true'. When a customer logs out their account, only that specific session is logged out. Only when all sessions belonging to a customer are logged out, does the customer table 'isLoggedIn' change to 'false'.
3. When a customer accounts' 'status' is listed as 'cs_awaiting_approval', only the customerToken, customerStatus, Email and First Name are returned.


## Login

This endpoint returns logged in user.


### HTTP Request

`POST https://apistore.csomni.com/login`

### Request Headers (to combine existing cart)

| Parameter     | Required | Description                    |
| ------------- | -------- | ------------------------------ |
| customerToken | true     | Current (Guest) Customer Token |

### Query Parameters

| Parameter        | Required | Description        |
| ---------------- | -------- | ------------------ |
| customerEmail    | true     | Customer Email.    |
| customerPassword | true     | Customer Password. |

```shell
curl --request POST \
  --url https://apistore.csomni.com/login \
  --header 'cache-control: no-cache' \
  --header 'token: 123' \
  --data '{\n "customerEmail" : "tesst@gmail.com",\n  "customerPassword" : "Abc12345"\n}'
```

> If the 'customerStatus' is 'cs_awaiting_approval' The above command returns JSON structured like this:
```json
{
    "customerToken": "cs_123456",
    "customerStatus": "cs_awaiting_approval",
    "customerEmail": "123456@evelt.com",
    "customerFirstName": "Sarah"
}
```

> If the 'customerStatus' is NOT 'cs_awaiting_approval' The above command returns JSON structured like this:

```json
{
  "id": 0,
  "customerFirstName": "test",
  "customerLastName": "test",
  "customerEmail": "abcd@gmail.com",
  "customerPhone": "0322487455",
  "customerCompanyName": "abc",
  "dateCreated": "1638353521",
  "customerStatus": "",
  "customerTypes": null,
  "customerGroups": null,
  "isLoggedIn": 1,
  "customerDocs": null,
  "taxExempt": null,
  "taxExemptID": null,
  "createdAt": "2021-12-01 10:12:01",
  "editedAt": "2021-12-01 13:42:53",
  "customerToken": "cs_123456"
}
```

## Logout

### HTTP Request

`POST https://apistore.csomni.com/login/logout`

### Request Headers (to combine existing cart)

| Parameter     | Required | Description                    |
| ------------- | -------- | ------------------------------ |
| customerToken | true     | Current (Guest) Customer Token |
| token         | true     | Site Token                     |



```shell
curl --location --request POST 'https://apistore.csomni.com/V1.10/login/logout' \
--header 'token: site_123456' \
--header 'customerToken: cs_123456'
```

> The above command returns JSON structured like this:

```json
[]
```
