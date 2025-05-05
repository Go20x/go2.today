---
title: "Ubuntu Nginx"
description: "Host my web site"
date: "May 5 2025"
---

`sudo mkdir -p /var/www/your_domain/html`

```
<html>
    <head>
        <title>Welcome to your_domain!</title>
    </head>
    <body>
        <h1>Success!  The your_domain server block is working!</h1>
    </body>
</html>
```

`sudo nano /etc/nginx/sites-available/your_domain`

```
server {
        listen 80;
        listen [::]:80;

        root /var/www/your_domain/html;
        index index.html index.htm index.nginx-debian.html;

        server_name your_domain www.your_domain;

        location / {
                try_files $uri $uri/ =404;
        }
}
```

`sudo ln -s /etc/nginx/sites-available/your_domain /etc/nginx/sites-enabled/`

`sudo nginx -t`

`sudo systemctl restart nginx`

`sudo certbot --nginx -d example.com -d www.example.com`