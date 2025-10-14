---
layout: post
title: "Ghi chú cài Cordova"
description: "There is no one who loves pain itself, who seeks after it and wants to have it, simply because it is pain..."
comments: true
keywords: "dummy content, lorem ipsum"
---

## Cài nodejs mới nhất và cài git mới nhất

- NodeJS: https://nodejs.org/en
- Git: https://git-scm.com/downloads

## Cài cordova qua NodeJS

``
npm install -g cordova
``

## Tai Gradle mới nhất

https://gradle.org/ Tải bản mới nhất
> Gradle 7.6, Gradle 8.7 chỉ tương thích jdk-11 thôi

## Tải jdk-22 hoặc mới nhất

https://www.oracle.com/java/technologies/javase/jdk22-archive-downloads.html

## Tải commanline tools

https://developer.android.com/studio?hl=vi

> Giải nén commandline-tools ra, tạo 1 thư mục latest và chuyển hết nội
> dung nó vào latest. Tạo 1 thư mục SDK và cho hết commandline-tools vào

## Tạo biến môi trường và chỉnh PATH cho windows

> **ANDROID_HOME** (user & Sys): C:\SDK 
> **JAVA_HOME** (user & sys) : C:\Program Files\Java\jdk-22
> **PATH**: Thêm đường dẫn đến **bin** của Gradle

## Cài platform-tools và build-tools

> cmdline-tools mới hiện tại chỉ tưởng thích jdk-22

Vào **SDK/cmdline-tools/latest/bin**
```
sdkmanager --list
sdkmanager "platform-tools" "build-tools;35.0.0"
```