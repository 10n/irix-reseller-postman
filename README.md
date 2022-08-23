# IRIX Reseller Api - Postman Collection

## Table of Contents
1. [Import and Configure](#import-and-configure)
2. [Test Authentication](#test-authentication)
3. [Authenticating Test Apis](#authenticating-test-apis)

## Import and Configure

 * Import both collection  and environment in Postman
 * Select environment and edit variables (`CURRENT VALUE` column)
   - `baseUrl` - The base url for all apis 
     - See documentation page
     - Example: `https://[irix-app-domain]/reseller/api`
   - `tokenUrl` - The url for request OAuth Tokens 
     - See documentation page on the `oAuth2Connection` details under the `Token URL`
   - `clientId`
     - Connection details should be received from the application administrator 
   - `clientSecret`
       - Connection details should be received from the application administrator
   - `scopes` 
     - Scopes list that are requested during the authentication step (space separated)


![Edit Environment](/images/environment.png)

## Test Authentication

Documentation about OAuth 2.0 Client Credentials Flow: 
* https://www.oauth.com/oauth2-servers/access-tokens/client-credentials/ 
* https://auth0.com/docs/get-started/authentication-and-authorization-flow/client-credentials-flow


This is a sample for testing that the received client credentials are working
 * Use Request: `Authentication` \ `GetToken with ClientCredentials` 
 * Make sure to configure
   * Basic Authentication (under `Authorisation` tab)
   * Body params:
     * `grant_type` (should be `client_credentials` )
     * `scopes` - is preconfigured to use environment variable {{scopes}}


![Token Authorization](/images/token_authorization.png)

![Token Body](/images/token_body.png)


> **Note:** Postman includes internal utility for requesting Access Tokens with OAuth 2.0 Client Credentials.
> This is just for manual testing or for extracting a `Code Sample`


## Authenticating Test Apis

* Select `Authorization` tab on the main collection and make sure Postman can request tokens that can be used
* Make sure the request inherits the parent `Auth` method or select directly the OAuth 2.0 with Client Credentials
* After generating the Token tha Apis should send proper token in the `Authorisation:` header

![img.png](/images/token_utility.png)