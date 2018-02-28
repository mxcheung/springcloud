 curl http://localhost:8080/whoami/Mr_Pink
$ curl http://localhost:8080/whoami/Mr_Pink
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    59  100    59    0     0     59      0  0:00:01 --:--:--  0:00:01   290Hello!  You're Mr_Pink and you'll become a(n) Developer...

 $ curl http://root:s3cr3t@localhost:8888/config-client/development/master
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   277    0   277    0     0      0      0 --:--:--  1:11:37 --:--:--   104{"name":"config-client","profiles":["development"],"label":"master","version":"ddb40beecb66095725560d88cd08f21cb1fa8855","state":null,"propertySources":[{"name":"https://github.com/mxcheung/springcloud/config-client-development.properties","source":{"user.role":"Developer"}}]}

 
 https://github.com/eugenp/tutorials/blob/master/spring-cloud/spring-cloud-config/server/pom.xml
 
 
 $ curl -X POST --data-urlencode d3v3L  http://root:s3cr3t@localhost:8888/encrypt
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   203    0   198  100     5    198      5  0:00:01 --:--:--  0:00:01   812{"timestamp":1519819815718,"status":500,"error":"Internal Server Error","exception":"java.lang.IllegalArgumentException","message":"Unable to initialize due to invalid secret key","path":"/encrypt"}
 
 
 https://github.com/spring-cloud/spring-cloud-commons
 
 
 $ curl http://root:s3cr3t@localhost:8888/config-client/development/master
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   301    0   301    0     0    150      0 --:--:--  0:00:02 --:--:--   148{"name":"config-client","profiles":["development"],"label":"master","version":"6f95d6e2b8b24a508cdb6c1506227244cba9b5ec","state":null,"propertySources":[{"name":"https://github.com/mxcheung/springcloud/config-client-development.properties","source":{"user.role":"Developer","user.password":"d3v3L"}}]}
 