---
title: Laravel 寄信範例
categories: PHP
---
## 前言
近期工作替商品做了下訂的功能，寫了一堆寄信功能，像是下訂成功、下訂失敗、請求報價、信箱驗證信和優惠碼通知信等...
那就來記錄一下寄信的寫法吧

## 環境
- OS : Windows 10

# 筆記說明
* 程式可以參考我的 [laravel筆記](https://github.com/youmu257/laravel-note)
* 建立 Controller
    * ```php artisan make:controller MailController```
* 新增 app\Mail 來放建立信件的物件
* 新增 resources\views\email 來放信件的 html template
    * 用 Blade Templates 去建立信件樣板
    * 可以用 ```@include``` 去匯入部分樣板
    * 我的筆記程式參考這個[樣板](https://github.com/ColorlibHQ/email-templates/tree/master/10)
* 在 MailService 用 Mail 去寄信
    ```
    $sampleMail = new SampleMail($smapleData);
    Mail::to($receiverMail)
        ->send($sampleMail);
    ```
    * 可以傳入 ```$smapleData``` 信件需要的資料
        * 可以用 ```{{ $text1 }}``` 顯示傳入變數
    * Mail::to 設定收件者信箱
* 寄件者和寄件者名稱會吃 env
    ```
    MAIL_FROM_ADDRESS="sender@gmail.com"
    MAIL_FROM_NAME="寄件者"
    ```
* 在 env 設定 smtp
    * 測試寄信結果我會用 [Mailtrap](https://mailtrap.io/)
    ```
    MAIL_MAILER=smtp
    MAIL_HOST=smtp.mailtrap.io
    MAIL_PORT=2525
    MAIL_USERNAME=test_username
    MAIL_PASSWORD=test_password
    MAIL_ENCRYPTION=tls
    ```
    * ![](https://i.imgur.com/SOijQdm.png)

# 結語
* 寄信不難，只是麻煩



# 參考
* [Laravel Controller](https://laravel.com/docs/8.x/controllers)
* [Blade Templates](https://laravel.com/docs/8.x/blade)
* [Email template](https://colorlib.com/wp/responsive-html-email-templates/)
* [laravel傳送郵件](https://www.itread01.com/content/1549881756.html)
