adm
===

Configure
# Register OAuth Client
```
bin/console acme:oauth-server:client:create --redirect-uri="CLIENT_HOST" --grant-type="authorization_code" --grant-type="password" --grant-type="refresh_token" --grant-type="token" --grant-type="client_credentials"
```

# Use case
ex: 
1 - Open 
```
PROVIDER_HOST/oauth/v2/auth?client_id=CLIENT_ID&response_type=code&redirect_uri=CLIENT_HOST
```
where client ID is <id>_<random>

2 - click authorize.accept
3 - pass code to
```
PROVIDER_HOST/oauth/v2/token?client_id=CLIENT_ID&client_secret=CLIENT_SECRET&grant_type=authorization_code&redirect_uri=http%3A%2F%2Fclinet.local%2F&code=CODE
```
and get
```
{"access_token":"NTJkNDQzZDEyMzE2OGIzNmEwYjk1NDdjOTIyNGZmM2Y5Zjg3Y2I5ZTBhYmFlMTZjMTJmNmVhM2ZhZTg0NTlkNw","expires_in":3600,"token_type":"bearer","scope":null,"refresh_token":"ZjQwZDVkMTNkMDJiMTEzMTI0ZWVmYTk0MGI4MWRlN2Q1NWZiYWI3NzE2ZDc0NWI4YzhlMzg0ZmJlY2ViN2VjNg"}
```
4 - use access token to fetch data from secured area
```
http://localhost:8000/api/test?access_token=NTJkNDQzZDEyMzE2OGIzNmEwYjk1NDdjOTIyNGZmM2Y5Zjg3Y2I5ZTBhYmFlMTZjMTJmNmVhM2ZhZTg0NTlkNw
```
