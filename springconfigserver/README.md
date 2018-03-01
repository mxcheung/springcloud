 curl http://localhost:8080/whoami/Mr_Pink
$ curl http://localhost:8080/whoami/Mr_Pink
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    59  100    59    0     0     59      0  0:00:01 --:--:--  0:00:01   290Hello!  You're Mr_Pink and you'll become a(n) Developer...

 $ curl http://root:s3cr3t@localhost:8888/config-client/development/master
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   277    0   277    0     0      0      0 --:--:--  1:11:37 --:--:--   104{"name":"config-client","profiles":["development"],"label":"master","version":"ddb40beecb66095725560d88cd08f21cb1fa8855","state":null,"propertySources":[{"name":"https://github.com/mxcheung/springcloud/config-client-development.properties","source":{"user.role":"Developer"}}]}

 
//curl -X POST --data-urlencode d3v3L   http://root:password@localhost:10000/encrypt
//curl -X POST --data-urlencode AQBku+lI9MyUDpQylJS/Ru1B7Nkr269SYdEqLRKkgZNNNrt9qrTk6CyfKaqgDvuWuHR3QjRoqfhcZDvc36CJzo8zErBiJvNm+fQoGV7gw2/ZYL7Qh4vLdMUl2r5dfwUL4Rmre/YB7qMGkN5dET20NpXELx/st2Vjm4ofRHuB5QXoSsrsXL7z5/H99Rb6r9kND8Rkfh/RQJowtdYXPBqTOJl29CuOqkvz3yJPWPqUu513p/NVSleGIWZCecsP4kBIG0jIKxy9W8bPgASNQuWwldBhDObIHsKiALbVLAbwpgeE/W8DXzMk+GSaq/kwB4+02pQhDXdxghLtgFx1IERt7136EQhabRwIxbTgxrnW1YGeIlPW2iSS46vPOTGS9wJZk7c=  http://root:password@localhost:10000/decrypt
//https://github.com/spring-projects/spring-security/blob/master/crypto/src/test/java/org/springframework/security/crypto/encrypt/EncryptorsTests.java

public class EncryptionTest   {

    @Before
    public void setup() {
    }

    
    @Test
    public void shouldEncryptAndDecrypt() throws Exception {
        Resource resource = new UrlResource("classpath:/config-server.jks");
        String defaultSecret = "my-k34-s3cr3t";
        char[] password = "my-s70r3-s3cr3t".toCharArray();
         String defaultAlias = "config-server-key";

         KeyStoreKeyFactory keys = new KeyStoreKeyFactory(resource, password);


        KeyStoreTextEncryptorLocator key = new KeyStoreTextEncryptorLocator(keys,defaultSecret, defaultAlias);
        
        Map<String, String> keys2 = new HashMap<String, String>();
        keys2.put("name", "hello2");
        keys2.put("profiles", "dev");
        TextEncryptor encryptor = key.locate(keys2);
        
        String encryptedText = encryptor.encrypt("d3v3L");
        encryptedText = "AQAsYW3Xjw/1zjS3MPbJw6Pr2ZcLS+NRcy4XRlvgTkSbtNnc4pG+TqWq+wPMONv2xInye/Jb0zMjXZiU8uYnhB2cvWbKtcFJNo5bbNFzgz18DCCA0wY2LQEm7QoErNsutrtV4BCopWDZ8wX5Y8GL9aea+T1GnmbCkU9Vngn572ZO9YdSds/bJPyKZsPVbcQgxghdcK+Gqy4zK8WaSUF1y9nMrh6uce6gR1JTStun/Mbu77bhlrl0ID940O1quI3uOI8BGFy7+lJq2XUzrLr8GfhHq4lCHhqbaq/PqF6IAmsMx8m6Q0y5ZPIYXlS+5VEBqJp10zewM5EnFcKBTqWTnbXMDpnOES+u6Fp40tGf0pLs96glBPUQjecrbGH/NBZWhCU=";
        encryptedText = "AQBku+lI9MyUDpQylJS/Ru1B7Nkr269SYdEqLRKkgZNNNrt9qrTk6CyfKaqgDvuWuHR3QjRoqfhcZDvc36CJzo8zErBiJvNm+fQoGV7gw2/ZYL7Qh4vLdMUl2r5dfwUL4Rmre/YB7qMGkN5dET20NpXELx/st2Vjm4ofRHuB5QXoSsrsXL7z5/H99Rb6r9kND8Rkfh/RQJowtdYXPBqTOJl29CuOqkvz3yJPWPqUu513p/NVSleGIWZCecsP4kBIG0jIKxy9W8bPgASNQuWwldBhDObIHsKiALbVLAbwpgeE/W8DXzMk+GSaq/kwB4+02pQhDXdxghLtgFx1IERt7136EQhabRwIxbTgxrnW1YGeIlPW2iSS46vPOTGS9wJZk7c=";
        String decryptedText = encryptor.decrypt(encryptedText);
        encryptedText = "AQAsYW3Xjw/1zjS3MPbJw6Pr2ZcLS+NRcy4XRlvgTkSbtNnc4pG+TqWq+wPMONv2xInye/Jb0zMjXZiU8uYnhB2cvWbKtcFJNo5bbNFzgz18DCCA0wY2LQEm7QoErNsutrtV4BCopWDZ8wX5Y8GL9aea+T1GnmbCkU9Vngn572ZO9YdSds/bJPyKZsPVbcQgxghdcK+Gqy4zK8WaSUF1y9nMrh6uce6gR1JTStun/Mbu77bhlrl0ID940O1quI3uOI8BGFy7+lJq2XUzrLr8GfhHq4lCHhqbaq/PqF6IAmsMx8m6Q0y5ZPIYXlS+5VEBqJp10zewM5EnFcKBTqWTnbXMDpnOES+u6Fp40tGf0pLs96glBPUQjecrbGH/NBZWhCU=";

    }

}
