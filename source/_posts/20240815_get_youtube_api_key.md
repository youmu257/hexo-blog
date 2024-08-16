---
title: 取得 Youtube API 金鑰
date: 2024-08-15 23:57:13
categories: 工具教學
---
## 前言
為了抓 Youtube 影片資訊來做 side project
手動整理影片資訊太累了\
決定用 Youtube 來抓資料
所以首先要先有 API key

## 建立 Google Cloud 專案
* 打開 [Google Console](https://console.cloud.google.com/apis/dashboard)
* 建立第一個專案
![](/images/get_youtube_api_key_1.PNG)
* 輸入專案名稱並建立專案
![](/images/get_youtube_api_key_2.PNG)

## 啟用 Youtube API
* 啟用 API 和服務
![](/images/get_youtube_api_key_3.PNG)
* 搜尋 ```youtube data api v3```
![](/images/get_youtube_api_key_4.PNG)
![](/images/get_youtube_api_key_5.PNG)
* 啟用 Youtube data api v3
![](/images/get_youtube_api_key_6.PNG)

## 建立金鑰
* 到[憑證頁面](https://console.cloud.google.com/apis/credentials)
* 建立憑證
![](/images/get_youtube_api_key_7.PNG)
* 選擇 API 金鑰
![](/images/get_youtube_api_key_8.PNG)
* 這樣就會產生好金鑰了
![](/images/get_youtube_api_key_9.PNG)

## 參考
[如何取得 Youtube API 金鑰](https://gg90052.github.io/blog/yt_api_key/)