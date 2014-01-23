silex-oauth-demo
================

Demonstration application for gigablah/silex-oauth.

You may use the sample nginx configuration below (assuming php-fpm socket):

```
server {
    listen 80;
    server_name localhost;

    gzip on;
    gzip_min_length 1000;

    location / {
        root /var/www/silex-oauth-demo/public;
        index index.php;
        try_files $uri /index.php$is_args$args;
    }

    location ~ \.php$ {
        root /var/www/silex-oauth-demo/public;
        fastcgi_pass php5-fpm;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include /etc/nginx/fastcgi_params;
    }
}
```
