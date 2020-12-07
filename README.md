## samplesdk
## Disclaimer
The code in this repo is sample code only. It is **NOT guaranteed to be bug free and production quality**.

## Examples

Below are the steps to use the Via API for the use case related to reassigning work for agents.

 - **Step 1:** Exchange your client credentials for an oauth token.
 
  ```
    // Configure HTTP basic authorization: basicAuth
    Configuration.Default.Username = "YOUR_USERNAME";
    Configuration.Default.Password = "YOUR_PASSWORD";

    var apiInstance = new AccessTokenApi();
    var realm = realm_example;  // string | organization to request an oauth token for
    var scope = "provisioningapi";  // string | api permissions requested
    var grantType = "client_credentials";  // string | token request type (default to client_credentials)

    try
    {
        // Get oauth token
        TokenResponse result = apiInstance.GetAccessToken(realm, scope, grantType);
        Debug.WriteLine(result);
    }
    catch (Exception e)
    {
        Debug.Print("Exception when calling AccessTokenApi.GetAccessToken: " + e.Message );
    }

  ```
  
