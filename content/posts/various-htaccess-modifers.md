---
title: "Various .htaccess modifers for the Apache webserver"
date: 2022-02-24
draft: false
description: "Various .htaccess modifers for the Apache webserver."
slug: "various-htaccess-modifers"
tags: ["guide"]
---

{{< lead >}}
I've collected some useful and some not so useful modifers that go in a htaccess file. These were made specifically for LiteSpeed webserver, which shares a lot of the same code so it should be mostly compatbile.
{{< /lead >}}

### Force HTTPS

A generic rewrite to alwasy redirect a http request to https

```
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

### Htaccess Redirect from old domain to new domain

A standard 301 reidrect, basepath `/` to a new domain

```
RewriteEngine on
RewriteBase /
RewriteRule (.*) http://ww.wexample.com/$1 [R=301,L]
```

### Prevent timeouts on a server .htaccess

This is to prevent execution time outs, don't ask why

```
RewriteRule .* - [E=noabort:1]
RewriteRule .* - [E=noconntimeout:1]
```

### 403 Redirect

```
Options -Indexes
ErrorDocument 403 /images/403.php
RewriteEngine on
RewriteRule ^403.php$ /index.php [R=301
```

### Block all IP’s except one.

Need to develop your site? This ones to keep prying eyes away!

```
order deny,allow
deny from all
allow from your (ip)
```

### Whitelist a 401 caused my ModSec for an IP address

Well, this is unique...

```
<IfModule security2_module>
<IF "%{REMOTE_ADDR} == '192.168.1.1'">
SecRuleRemoveById 700001
</IF>
</IfModule>
```

### GEOblocking

GEO blocking it its best!

```
#Online AU can connect
GeoIPEnable On
SetEnvIf GEOIP_COUNTRY_CODE AU AllowCountry
Deny from all
Allow from env=AllowCountry
```

### Block specific countries https://dev.maxmind.com/geoip/legacy/codes/iso3166/

This is also Geoblocking at its best.

```
GeoIPEnable On
#Add countries you wish to deny here
SetEnvIf GEOIP_COUNTRY_CODE RU DenyCountry
Allow from all
Deny from env=DenyCountry
```

### Disble WordPressProtect

This stops LiteSpeed doing something.

```
<IfModule Litespeed>
WordPressProtect throttle, 0
</IfModule>
```

### Disable Modsec

Modsecurity is usually a good thing, but sometimes it needs to be off...

```
<IfModule mod_security.c>
  SecFilterEngine Off
  SecFilterScanPOST Off
</IfModule>
```

### Change document root through .htaccess

This can be handy on a cPanel server, when you can't really change much.

```
RewriteEngine on
RewriteCond %{HTTP_HOST} ^example.com$ [NC,OR]
RewriteCond %{HTTP_HOST} ^www.example.com$
RewriteCond %{REQUEST_URI} !folder/
RewriteRule (.*) /folder/$1 [L]
```
