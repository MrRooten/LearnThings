1. cookie_domain，设置Cookie的域名
2. cookie_httponly，设置HTTPONLY
3. cookie_path，设置Cookie在哪个PATH下才能被读取
4. cookie_secure，设置Cookie只能在https页面中被传输与读取

http://example.com可以读取http://example.com:8080的Cookie  
https://example.com可以读取http://example.com的cookies  
cookie_secure=true的情况下，http:// example.com不能读取https:// example.com的Cookie  
cookie_httponly=true的情况下，JavaScript不能读取这个Cookie  
cookie_path=/admin/的情况下，http:// example.com/不能读取http:// example.com/admin/的Cookie  
cookie_domain=.example.com的情况下，http:// a.example.com可以读取http:// b.example.com的Cookie  