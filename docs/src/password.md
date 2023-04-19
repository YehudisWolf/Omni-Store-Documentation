# Password Reset

## Forgot Password (Send email)

```shell
curl --request POST \
  --url https://api.omnifront.cloudsnob.com/password/forgot \
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