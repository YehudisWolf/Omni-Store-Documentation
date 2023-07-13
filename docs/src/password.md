# Password Reset

## Forgot Password (Send email)

```shell
curl --request POST \
  --url https://apistore.csomni.com/password/forgot \
  --data '{"customerEmail" : "test@gmail.com","siteToken" : "site_222"}'
```

> The above command returns JSON structured like this:

```json
{
  "status": "success"
}
```

This endpoint send a reset password link to a user (Be careful, it always returns success even if email is not in our system vd"l)

### HTTP Request

`POST https://apistore.csomni.com/password/forgot`

### Request Parameters

| Parameter     | Description    |
| ------------- | -------------- |
| customerEmail | customer email |
| siteToken     | Site Token     |

## Restore Password (from hash)

```shell
curl --request POST \
  --url https://apistore.csomni.com/restorepassword \
  --data '{ "hash" : "pass_1234567", "newPassword" : "123456789" }'
```

> The above command returns JSON structured like this:

```json
{
  "status": "success"
}
```

This endpoint saves users new password

### HTTP Request

`POST https://apistore.csomni.com/restorepassword`

### Request Parameters

| Parameter   | Description        |
| ----------- | ------------------ |
| hash        | hash sent by email |
| newPassword | new password       |
