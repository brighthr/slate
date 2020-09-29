# Authentication

Before you can integrate with our APIs, you must set up your development environment to get OAuth 2.0 client ID and secret credentials for the sandbox and live environments. You exchange these credentials for an access token that authorizes your REST API calls. To test your web and mobile apps, you create sandbox accounts.

To request acces, please contact us <a href='mailto:github@brighthr.com'>here</a>.

Once you have your client ID, you can request an Access Token.

```shell
curl -v https://someurl/oauth2/token \
   -H "Accept: application/json" \
   -u "client_id:secret" \
   -d "grant_type=client_credentials"
```

> Make sure to replace `secret` with your client key.

Once you have the access token you can use it to make API calls by providing it in your headers as in the example.

```
curl -v -X GET https://someurl \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer Access-Token"
```

> Make sure to replace `Access-Token` with your client key.

<aside class="notice">
You must replace <code>Access-Token</code> with your granted access token.
</aside>

### URL for Dev and Production

Development: https://sandbox-api.brighthr.com/v1/location  \
Production: https://api.brighthr.com/v1/location

</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>