# Magento 2 Alternative Http Header
A Magento 2 module that uses a custom http remote address header used by Cloudflare or other CDN/proxies.

## Description
This Magento 2 module adds the HTTP_CF_CONNECTING_IP and HTTP_X_FORWARDED_FOR headers to be used within the application. 
By default Cloud Distribution Network (CDN) like Cloudflare or other proxies intercept the original server request and send
a new request to the actual site server. By doing this, the server receives the CDN's remote address in the $_SERVER[REMOTE_ADDR]
value which is not what we want. Functionality that relies on IP detection to do stuff doesnt function properly because 
of this. This extension lets magento know to search for values in $_SERVER[HTTP_CF_CONNECTING_IP] or 
SERVER[HTTP_X_FORWARDED_FOR] and use these values as the remote address if they exist.

## Installation Instructions
_Install using composer_
```$xslt
composer require ccerda0520/alternative-http-header
php bin/magento module:enable CCerda_AlternativeHttpHeader
php bin/magento setup:upgrade
```