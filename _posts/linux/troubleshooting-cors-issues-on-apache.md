---
layout: post
title: Hello World
tags: [linux]
---

## Troubleshooting CORS Issues On Apache 
Sometime I got this errors from Chrome browser. This is a cross-domain issue. To solve this , we need to edit .htaccess file.

Failed to load https://example.com: Response to preflight request doesn't pass access control check: No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'http://abc.com' is therefore not allowed access.

To accept requests from the http://abc.com
```
<ifModule mod_headers.c>
    Header set Access-Control-Allow-Origin "http://abc.com"
</ifModule>
```

Or accept any kind of domain, we could use the "*"
```
<ifModule mod_headers.c>
    Header set Access-Control-Allow-Origin "*"
</ifModule>
```
Then, we may got the next error:
XMLHttpRequest cannot load http://abc.com. Request header field Content-Type is not allowed by Access-Control-Allow-Headers.

We need to indicate which headers are safe for http://abc.com. So we need to edit the .htaccess file like:
```
<ifModule mod_headers.c>
    Header set Access-Control-Allow-Origin "*"
    Header set Access-Control-Allow-Headers "Origin, X-Requested-With, Content-Type, Accept"
</ifModule>
```
If it is still not work, you should make sure mod_headers and mod_rewrite is enabled.  
```
apache2ctl -M
```

If you do not see rewrite_module (shared), you need to enter below command to enable it.  
```
sudo a2enmod rewrite & sudo service apache2 restart
```

If you do not see headers_module (shared), you need to enter below command to enable it.  
```
sudo a2enmod headers & sudo service apache2 restart
```
