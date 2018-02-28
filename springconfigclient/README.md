 curl http://localhost:8080/whoami/Mr_Pink
$ curl http://localhost:8080/whoami/Mr_Pink
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    59  100    59    0     0     59      0  0:00:01 --:--:--  0:00:01   290Hello!  You're Mr_Pink and you'll become a(n) Developer...

 $ curl http://root:s3cr3t@localhost:8888/config-client/development/master
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   277    0   277    0     0      0      0 --:--:--  1:11:37 --:--:--   104{"name":"config-client","profiles":["development"],"label":"master","version":"ddb40beecb66095725560d88cd08f21cb1fa8855","state":null,"propertySources":[{"name":"https://github.com/mxcheung/springcloud/config-client-development.properties","source":{"user.role":"Developer"}}]}

 $ curl http://localhost:8080/whoami/Mr_Pink
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   819  100   819    0     0    819      0  0:00:01 --:--:--  0:00:01  3756Hello!   You're Mr_Pink and you'll become a(n) Developer, but only if your password is 'AgCLved7agRdtQzhGOC7dp0am77nqqWY2FHy/Ot4Dy/1JP9VBdc5RLwfgz5fgWTyGANuv7kuUtZsYGD0WYfu2YdbqKmI4onqafOYXBZlI3pvKJW7c0QI9ot6p2f70qOBgB85/ZYCI71x+9kM9SzIGVWTeh6wiFMWZHpPO/tLee6ykfgalZ1BsVzGJCg6mElk26oDpo7pdl7UUWbcHvKQxalTgDz+eH1WjnMxs2PnJfNb+/zS6T+etWg93U2ak8gNW+F3JXDU9ntM4piFkorLvTm3ecRPJk/lUT6Vn1z4ef93/JIJIEcyLA56/6vN0dFUDyavtcYQAEQFKxuXr9D/LfhIph1hFtT9dPSXzEBCWMAAiR4evUF3sUOb7cY1EXjNDAlkqXtv+9Ysn9/6qCcUsx4k3lywA7s7Al4Prr/Jh/G81naMUKz9dax1WX4iFrCQXBpgY8Qi66Domn1wGrOXsFXVWVkT5/EIL8guzpahSXXD78HLMg3cDeWFKNhDMcTwgWYDWMkwxqUJZ+ivN4vDnadDGpA16vBbFwMmCdoIYnGU4i56rhRKdysx92CuZ51UMND16Sp2HII1AYxQQ3jdfPZZhH2CsfBn2SoT3mCx2vuyKvmBN7UGcud2QY4eKrZ2a34PD9AXn1wtlHoHsxMouDyZEnKI1gjKn9fjCiMPeIzxlNDyx191PnyvTJhph5WzDTCiOypHhBr58ejLn/8r8Sw5'!

https://docs.spring.io/spring-security/site/docs/3.1.x/reference/crypto.html
MAX@MAX-PC MINGW64 /e/git/springcloud (test_encryption)
$ curl http://localhost:8080/whoami/Mr_Pink
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    96    0    96    0     0      0      0 --:--:--  1:11:35 --:--:--   130Hello!   You're Mr_Pink and you'll become a(n) Developer, but only if your password is 'd3v3L'!

After some investigation I found that the Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 5.0 needs to be added in order to avoid the issue. I am not sure how to go about this. Any help is much appreciated.
The "standard" encryption method is 256-bit AES using PKCS #5's PBKDF2 (Password-Based Key Derivation Function #2)

http://forum.spring.io/forum/spring-projects/security/104042-unable-to-initialize-due-to-invalid-secret-key
http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html

local_policy.jar
US_export_policy.jar