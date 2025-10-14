---
layout: post
title: "Làm gì sau khi mới mua được VPS/Server"
description: "There is no one who loves pain itself, who seeks after it and wants to have it, simply because it is pain..."
comments: true
keywords: "dummy content, lorem ipsum"
---

- VPS chạy ubuntu
- OS khác tui không biết đâu nhé
- Người chơi thuộc hệ LAMP

## Chỉnh lại múi giờ hệ thống

Chỉnh sang múi Việt Nam Ho Chi Minh City +7. Là người VN thì phải biết VN +7 nhé.
```
dpkg-reconfigure tzdata
```

## Cài Apche, cài MySQL

```
sudo apt update
sudo apt install apache2
sudo apt install mysql-server
```

## Tạo mật khẩu root cho MySQL

```
sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '{{MẬT KHẨU}}';
exit
```

## Giúp php làm việc được apache và mysql, cài phpmyadmin

```
sudo apt install php libapache2-mod-php php-mysql
sudo apt install phpmyadmin
sudo a2enmod rewrite
sudo a2enmod ssl
```

## Khởi động lại apche

```
sudo systemctl restart apache2
```