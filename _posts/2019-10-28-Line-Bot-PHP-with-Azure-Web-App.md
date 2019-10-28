---
layout: post
title:  "Line Bot PHP with Azure Web App"
date:   2019-10-28 11:16:30 +0800
categories: faith hsu update
---
本教學使用[line bot php sdk][line-bot-php-sdk]搭載[Azure Web App][azure-web-app]

一、設定Azure Web service
1. 首先創建一個Web App Service  
進入Azure portal後, 先建立App Service (可選免費方案)  
再create一個Web app, stack選擇php 7.3  
  
2. 設定deployment方式  
於部屬中心選單中，選擇使用FTP方式來部屬 (最簡潔),  
可於`FTP/認證`→`應用程式認證`選單中, 得到FTP deploy的相關資訊  
Azure PHP Web Service部屬方式即設定成功  
  
二、準備line bot環境  
TODO   
1. 設定/申請line bot帳號  
2. 設定Messaging API的Webhook URL (須為https)  
```
https://{azure-project-name}.azurewebsites.net/line/echo_bot.php
```

三、準備line-bot-sdk-php環境  
1. 下載line-bot-sdk-php程式碼，並以line-bot-sdk-tiny為範例  
```
$ git clone https://github.com/line/line-bot-sdk-php.git
$ cd line-bot-sdk-php/line-bot-sdk-tiny
```
  
2. 修改`echo_bot.php`中的channel_secret與channel_access_token為自己line-bot Messaging API設定上的值
```
$channel_secret = 'your channel secret'
$channel_access_token = 'your access token'
```
  
3. 將修改過的line-bot-sdk-tiny資料夾上傳到azure部屬中心的FTP位址  
  
4. 完成  
可於line Messaging API的Webhook URL進行Verify測試
  
四、line bot測試  
使用個人帳號加入line-bot帳號進行測試, 可獲得echo回應  
  
[line-bot-php-sdk]: https://github.com/line/line-bot-sdk-php
[azure-web-app]: https://azure.microsoft.com/zh-tw/services/app-service/web/
