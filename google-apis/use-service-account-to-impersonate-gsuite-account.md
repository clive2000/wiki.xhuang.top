# Use service account to impersonate gsuite account

1. In gsuite admin console, delegate api \(admin.google.com - secuirty - Manage API client access\). [https://developers.google.com/identity/protocols/OAuth2ServiceAccount](https://developers.google.com/identity/protocols/OAuth2ServiceAccount)
2. In your application, generate delegated\_credential by impersonating user
3. Profit



Alternatively, you can use service account to access team drive, documented here: [https://stackoverflow.com/questions/43243865/how-to-access-team-drive-using-service-account-with-google-drive-net-api-v3](https://stackoverflow.com/questions/43243865/how-to-access-team-drive-using-service-account-with-google-drive-net-api-v3)

