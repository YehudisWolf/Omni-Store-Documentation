# Sites

## GET site info

### HTTP Request

`GET https://apistore.csomni.com/sites`

## Get A Specific Site

```shell
curl --request GET \
  --url https://apistore.csomni.com/sites/ \
  --header 'token: [site_token]'
```

> The above command returns JSON structured like this:

```json
{
    "siteToken": "############",
    "siteName": "#############",
    "address1": "7 Sedgewick Place",
    "address2": "Apt. 4",
    "city": "Brooklyn",
    "state": "NY",
    "zipCode": "11206",
    "country": "US",
    "logo": "https://opticsforce.com/img/####.png",
    "phoneNumber": "1234568901"
}
```
