# Addresses

## Add/Edit Address

```shell
curl --request POST \
  --url https://apistore.csomni.com/addresses/{addressToken} \
  --header 'cache-control: no-cache' \
  --header 'postman-token: 1234567890' \
  --header 'token: 123' \
  --data '{ "customerToken" : "cust_123456",
   "address" : "123 Main street","addressCity" : "Monsey",
    "addressState" : "NY",
    "addressZip" : "10952",
    "addressLabel" : "My Address",
    "addressFirstName" : "My address first",
    "addressLastName" : "My Address Last Name",
    "phoneNumber" : "03356705565"
}'

```

> The above command returns JSON structured like this

```json
{
  "customerToken": "cust_123456",
  "address": "123 Main street",
  "address2": "unit 4",
  "addressCity": "Monsey",
  "addressState": "NY",
  "addressZip": "10952",
  "addressCountry": "USA",
  "addressLabel": "My Address",
  "addressFirstName": "My address first",
  "addressLastName": "My Address Last Name",
  "phoneNumber": "03356705565",
  "addressToken": "adrs_123456",
  "specialValues": ""
}
```

This endpoint for Add/Edit an address

### HTTP Request

`POST https://apistore.csomni.com/addresses/{addressToken}`

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
| addressCountry   | true (If empty it enters United States) | false  | Country                                      |
| addressDefault   | false                                   | false  | Mark as default address                      |
| phoneNumber      | false                                   | false  | Phone Number                                 |
| specialValues    | false                                   | false  | Special values against address token         |

### URL Parameters (for edit)

| Parameter    | Required | Unique | Description           |
| ------------ | -------- | ------ | --------------------- |
| addressToken | true     | false  | Address Token to edit |

## Get All Addresses for Customer

```shell
curl --request GET \
  --url https://apistore.csomni.com/addresses \
  --header 'token: 123'
```

> The above command returns JSON structured like this:

```json
[
  {
    "addressToken": "adrs_123456",
    "addressLabel": "",
    "address": "abcd",
    "address2": "",
    "addressCity": "lahore",
    "addressState": "Punjab",
    "addressZip": "54000",
    "addressFirstName": "test12",
    "addressLastName": "test123",
    "phoneNumber": "0313445214",
    "mobileNumber": "",
    "addressCountry": "United States",
    "addressDefault": 0,
    "customerToken": "cust_123456",
    "specialValues": []
  },
  {
    "addressToken": "adrs_123456",
    "addressLabel": "My Address",
    "address": "123 Main street",
    "address2": "unit 4",
    "addressCity": "Monsey",
    "addressState": "NY",
    "addressZip": "10952",
    "addressFirstName": "My address first",
    "addressLastName": "My Address Last Name",
    "phoneNumber": "03356705565",
    "mobileNumber": "",
    "addressCountry": "USA",
    "addressDefault": 0,
    "customerToken": "cust_123456",
    "specialValues": []
  }
]
```

This endpoint retrieves all addresses for a specific customer

### HTTP Request

`GET https://apistore.csomni.com/addresses`

## Get A Specific Address

```shell
curl --request GET \
  --url https://apistore.csomni.com/addresses/{addressToken} \
  --header 'token: 123'
```

> The above command returns JSON structured like this:

```json
{
  "addressToken": "adrs_123456",
  "addressLabel": "My Address",
  "address": "123 Main street",
  "address2": "unit 4",
  "addressCity": "Monsey",
  "addressState": "NY",
  "addressZip": "10952",
  "addressFirstName": "My address first",
  "addressLastName": "My Address Last Name",
  "phoneNumber": "03356705565",
  "mobileNumber": "",
  "addressCountry": "USA",
  "addressDefault": 0,
  "customerToken": "cust_123456",
  "specialValues": []
}
```

This endpoint retrieves a specific address

### HTTP Request

`GET https://apistore.csomni.com/addresses/{addressToken}`

### URL Parameters

| Parameter    | Required | Unique | Description          |
| ------------ | -------- | ------ | -------------------- |
| AddressToken | true     | -      | Token of the Address |

## Delete a Address

```shell
curl --request DELETE \
  --url https://apistore.csomni.com/addresses/{addressToken} \
  --header 'content-type: application/json' \
  --header 'token: 123'
```

This endpoint deletes (archives) a address

### HTTP Request

`DELETE https://apistore.csomni.com/addresses/{addressToken}`

### URL Parameters

| Parameter | Description                        |
| --------- | ---------------------------------- |
| Token     | The Token of the address to delete |
