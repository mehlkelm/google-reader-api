To protect against [XSRF](http://en.wikipedia.org/wiki/Cross-site_request_forgery) attacks, all state-changing methods require an action token in addition to an [authentication token](Authentication.md). The token can be fetched by making a `GET` request for `/reader/api/0/token` and should be passed in to state-changing requests (generally `POST` requests) with the `T` parameter (see ApiCommonInputs).

The token is valid for 30 minutes. If it is missing or invalid, a 401 HTTP response code will be given and the response will have a `X-Reader-Google-Bad-Token: true` HTTP header.