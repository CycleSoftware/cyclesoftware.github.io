# Authentication #

CycleSoftware uses different authentication mechanisms. 

## HTTP Basic Authentication ##

The credentials consist of a `username`, `password` and `api-key`. The `username` and `password` should be provided using the Basic HTTP authentication http header. The api-key is usage is documented per service.

## SOAP/WSDL Authentication ##

The credentials consist of a `username`, `password` and `api-key`. The `username` and `password` should be provided within the `Authentication` element as documented per request. For `dealer_id` the actual store id within the account or api-key can be provided.

## OAUTH2 Authentication ##
TWSC API is available throught Oauth2 authentication

## Scopes ##
Credentials are linked to a set of scopes. Every endpoint is also linked to a set of scopes. If the required scope is not available for the credentials the API will provide an HTTP Unauthorized error.
