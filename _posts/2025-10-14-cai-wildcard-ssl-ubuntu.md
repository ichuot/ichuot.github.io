---
layout: post
title: "Cài widldcard SSL Letsencrypt cho VPS/Server"
description: "There is no one who loves pain itself, who seeks after it and wants to have it, simply because it is pain..."
comments: true
keywords: "dummy content, lorem ipsum"
---

- VPS chạy ubuntu
- Cài thông qua Certbot
- DNS dùng cloudflare


## Cài Certbot trên ubuntu

```
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
sudo snap set certbot trust-plugin-with-root=ok
sudo snap install certbot-dns-cloudflare
```

## Lấy API Token từ cloudflare

- Tạo 1 file chứa token nội dung và lưu tên **cloudflare.ini** trong /root, và chmod 600
- Vào https://dash.cloudflare.com/profile/api-tokens tạo token
- Nên tạo All Zone, ko dùng 1 domain cụ thể mắc công
```
  # Cloudflare API token used by Certbot
  dns_cloudflare_api_token = token_lấy_tứ_cloudflare
```

## Tạo chứng chỉ

```
sudo certbot certonly \
    -d muamu.online \
    -d *.muamu.online \
    --dns-cloudflare \
    --dns-cloudflare-credentials ~/cloudflare.ini \
    --dns-cloudflare-propagation-seconds 60
```

## Hiện đường dẫn đến key

```
certbot certificates
```

## Cài SSL cho apache (nếu chưa có)

```
sudo a2enmod ssl
```

## Thêm SSL vào Virtual Host của apache

```
<VirtualHost *:443>
  ServerName {{TÊN MIỀN}}
  ServerAlias *.{{TÊN MIỀN}}

  DocumentRoot /home/DIR_WWW
  <Directory /home/DIR_WWW>
    Options FollowSymLinks
    AllowOverride All
    Require all granted
  </Directory>
  SSLEngine on
  SSLCertificateFile /etc/letsencrypt/live/{{TÊN MIỀN}}/fullchain.pem
  SSLCertificateKeyFile /etc/letsencrypt/live/{{TÊN MIỀN}}/privkey.pem
</VirtualHost>
```