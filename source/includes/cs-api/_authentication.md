# Authentication #

CycleSoftware uses different authentication mechanisms. 

## HTTP Basic Authentication ##

The credentials consist of a `username`, `password` and `api-key`. The `username` and `password` should be provided using the Basic HTTP authentication http header. The api-key is usage is documented per service.

## SOAP/WSDL Authentication ##

The credentials consist of a `username`, `password` and `api-key`. The `username` and `password` should be provided within the `Authentication` element as documented per request. For `dealer_id` the actual store id within the account or api-key can be provided.
