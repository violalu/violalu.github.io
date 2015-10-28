# violalu.github.io
# Heath Check in docker registry
 ## /debug/health/ is used to chheck docker registry heath, but seems there is no way to automatically registry current health check althrough there are serveral check implementation

# docker registry v2 oauth
https://github.com/docker/distribution/blob/master/docs/spec/auth/token.md
The most important is the www-authentication header which contains realm : url of oauth server
How to authenticate

Registry V1 clients first contact the index to initiate a push or pull. Under the Registry V2 workflow, clients should contact the registry first. If the registry server requires authentication it will return a 401 Unauthorized response with a WWW-Authenticate header detailing how to authenticate to this registry.

For example, say I (username jlhawn) am attempting to push an image to the repository samalba/my-app. For the registry to authorize this, I will need push access to the samalba/my-app repository. The registry will first return this response:

HTTP/1.1 401 Unauthorized
Content-Type: application/json; charset=utf-8
Docker-Distribution-Api-Version: registry/2.0
Www-Authenticate: Bearer realm="https://auth.docker.io/token",service="registry.docker.io",scope="repository:samalba/my-app:pull,push"
Date: Thu, 10 Sep 2015 19:32:31 GMT
Content-Length: 235
Strict-Transport-Security: max-age=31536000

{"errors":[{"code":"UNAUTHORIZED","message":"access to the requested resource is not authorized","detail":[{"Type":"repository","Name":"samalba/my-app","Action":"pull"},{"Type":"repository","Name":"samalba/my-app","Action":"push"}]}]}
Note the HTTP Response Header indicating the auth challenge:

Www-Authenticate: Bearer realm="https://auth.docker.io/token",service="registry.docker.io",scope="repository:samalba/my-app:pull,push"
This format is documented in Section 3 of RFC 6750: The OAuth 2.0 Authorization Framework: Bearer Token Usage

This challenge indicates that the registry requires a token issued by the specified token server and that the request the client is attempting will need to include sufficient access entries in its claim set. To respond to this challenge, the client will need to make a GET request to the URL https://auth.docker.io/token using the service and scope values from the WWW-Authenticate header.
 
# http cache
 ## https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching?hl=zh-cn

# yum && rpm installocalinstall
 ```
 yum localinstall *.rpm
 rpm -ivh **.rpm
 rpm -e *
 rpm -qa|grep mysql
 rpm -q mysql
 ```

 ## rpm usage : http://www.thegeekstuff.com/2010/07/rpm-command-examples/
 ## build rpm from source using rpmbuild:
  http://www.thegeekstuff.com/2015/02/rpm-build-package-example/

