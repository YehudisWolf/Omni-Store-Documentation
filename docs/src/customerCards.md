# Customer Cards

## Edit Card

### HTTP Request

`PUT https://apistore.csomni.com/paymentmanager/[cardToken]`

### Query Parameters

| Parameter        | Required                                | Unique | Description                                  |
| ---------------- | --------------------------------------- | ------ | -------------------------------------------- |
| cardNumbers      | false                                   | false  | Numbers on Card                              |
| cvv              | false                                   | false  | 3 Digit Security numbers                     |
| nameOnCard       | false                                   | false  | Cardholder name                              |
| billingAddress   | false                                   | false  | Billing Address                              |
| billingAddress2  | false                                   | false  | Billing Address Line 2                       |
| billingZip       | false                                   | false  | Billing Zip                                  |
| billingCity      | false                                   | false  | Biling City                                  |
| billingState     | false                                   | false  | Billing State                                |
| billingCountry   | false                                   | false  | Billing country                              |
| billingPhone     | false                                   | false  | Billing Phone                                |
| billingMobile    | false                                   | false  | Billing Mobile                               |
| isDefault        | false                                   | false  | Specify if this card should be the default card used on this account |
| expMonth         | false                                   | false  | Card expiry Month                             |
| expYear          | false                                   | false  | Card expiry Year                              |


```shell
curl --location --request PUT 'https://apistore.csomni.com/paymentmanager/cc_123456789' \
--header 'customerToken: cs_987654321' \
--header 'token: site_AbCd' \
--header 'Content-Type: application/json' \
--data '{
    "cardNumbers": "11111111111111111",
    "cvv": "1234",
    "nameOnCard": "My Name Is John",
    "billingAddress": "20 Maple Ave",
    "billingAddress2": "",
    "billingZip": "123456",
    "billingCity": "Bala Cynwyd",
    "billingState": "Pennsylvania",
    "billingCountry": "United States",
    "billingPhone": "1234567890",
    "billingMobile": "",
    "isDefault": true,
    "expMonth": "01",
    "expYear": "11"
}'

> The above command returns JSON structured like this

```json
{
    "cardToken": "cc_123456789",
    "cardTokenStripe": "",
    "numbers": "11111111111111111",
    "lastFour": "6789",
    "expMonth": "01",
    "expYear": "11",
    "cvv": "1234",
    "nameOnCard": "My Name Is John",
    "billingAddress": "20 Maple Ave",
    "billingAddress2": "",
    "billingCity": "Bala Cynwyd",
    "billingState": "Pennsylvania",
    "billingZip": "123456",
    "billingPhone": "1234567890",
    "billingMobile": "",
    "billingCountry": "United States",
    "zipMatched": null,
    "avsMatched": null,
    "companyToken": "",
    "customerToken": "",
    "isDefault": 1,
    "archived": 0,
    "createdAt": "2023-04-20 21:17:19",
    "editedAt": "2023-04-20 22:31:19"
}
```

