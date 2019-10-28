---
layout: post
title:  "Line Bot with Azure Web App"
date:   2019-10-28 11:16:30 +0800
categories: jekyll update
---
本教學使用[line bot python sdk][line-bot-python-sdk]搭載[Azure Web App][azure-web-app]

一、設定Azure Web service
1. 首先創建一個Web App Service
進入Azure portal後, 先建立App Service (可選免費方案)
再create一個Web app, stack選擇python 3.7

2. 設定deployment方式
於部屬中心選單中，選擇使用local git方式來部屬 (使用過cloud shell或FTP均無法成功),
設定成功後會得到一個.git位址, 也就是可用來部屬python應用程式的位址
可於FTP/認證→使用者認證選單中, 設定存取此git repository的使用者帳密資訊
Azure Python Web Service部屬方式即設定成功

二、準備line bot環境
TODO 
1. 設定/申請line bot帳號
2. 設定Messaging API的Webhook URL (須為https)
```
https://{azure-project-name}.azurewebsites.net/callback
```

三、準備line-bot-sdk-python環境
1. 下載line-bot-sdk-python程式碼，並以falsk-echo為範例
```
$ git clone https://github.com/line/line-bot-sdk-python.git
$ cd line-bot-sdk-python/examples/falsk-echo
```

2. 修改channel_secret與channel_access_token為自己line-bot上的值
```
channel_secret = 'your channel secret'
channel_access_token = 'your access token'
```

3. 將修改過的app.py及requirments.txt複製到azure部屬中心的git repository

4. add、commit並push到git repository，即會觸發heku進行部屬流程

5. 完成
可於line Messaging API的Webhook URL進行Verify測試(此處不通, 還未確認原因)

四、line bot測試
使用個人帳號加入line-bot帳號進行測試, 可獲得echo回應

[line-bot-python-sdk]: https://github.com/line/line-bot-sdk-python
[azure-web-app]: https://azure.microsoft.com/zh-tw/services/app-service/web/
