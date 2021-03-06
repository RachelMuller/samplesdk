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
  
- **Step 2:** Find the id of the work type to be adjusted.  Work types can be filtered by direction (inbound/outbound), channel (e.g. voice, sms) and queue type (e.g terminal).

```
  var apiInstance = new GetWorkTypesCollectionApi();
  var orgId = orgId_example;  // string | 
  var authorization = authorization_example;  // string | Authentication token with the value: 'Bearer {accessToken}', where {accessToken} was returned from a call to the authorization endpoint
  var xApiKey = xApiKey_example;  // string | Aspect-provided value used to track API endpoint usage.
  var channelType = channelType_example;  // string | filters results based on Disposition Routing Plan channel type, Example= voice,chat,email (optional) 
  var includeInactive = includeInactive_example; // If the &#39;includeInactive&#39; query parameter is not passed OR set to &#39;false&#39; only active object instances are returned. If &#39;includeInactive&#39; query parameter is passed and set to &#39;true&#39; both active and inactive object instances are returned in the API response. 
  var direction = direction_example; // Direction of a work type. This is used to filter by work type direction.
  var workTypeRulesEmail = workTypeRulesEmail_example; // Email work type rules
  var queueType = queueType_example; // Type of queue. This is used to filter by queue type.
  var friendlyName = ""; // Displayable representation of the entity name. One entry is allowed per supported locale. NOT CURRENTLY SUPPORTED
  
  try
  {
      // Get WorkTypeCollection
      
      WorkTypeList result = apiInstance.GetWorkTypesCollection (orgId, authorization, xApiKey, includeInactive, direction, workTypeRulesEmail, queueType, channelType, friendlyName);
      Debug.WriteLine(result);
  }
  catch (Exception e)
  {
      Debug.Print("Exception when calling GetWorkTypesCollection: " + e.Message );
  }
```

- **Step 3:** Retrieve the current assigned users for the selected work type.

```
  var apiInstance = new GetWorkHandlersCollectionApi();
  var orgId = orgId_example;  // string | 
  var authorization = authorization_example;  // string | Authentication token with the value: 'Bearer {accessToken}', where {accessToken} was returned from a call to the authorization endpoint
  var xApiKey = xApiKey_example;  // string | Aspect-provided value used to track API endpoint usage.
  var workTypeId = workTypeId_example; // string | Aspect-generated unique ID for a work type.  


  try
  {
      // Get WorkHandlersCollection
      
      WorkHandlerList result = apiInstance.GetWorkHandlersCollection (orgId, authorization, xApiKey, workTypeId);
      Debug.WriteLine(result);
  }
  catch (Exception e)
  {
      Debug.Print("Exception when calling GetWorkTypesCollection: " + e.Message );
  }
```

- **Step 4:** Update list of assigned users for the selected work type.
