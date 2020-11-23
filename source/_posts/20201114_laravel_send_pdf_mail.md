---
title: Laravel 寄信夾帶 PDF 範例
categories: PHP
---
## 前言
由於遇到需要夾帶訂單資訊的PDF的需求，順便紀錄一下產生PDF夾進信件的筆記
其實還有其他的套件可以產生PDF，但多數人都推薦 Snappy，尤其是包含中文的情境
不過 Snappy 不支援 windows ，所以接下來的筆記僅適用 linux

## 環境
- OS : unubtu

# 前置安裝
* 使用 Snappy PDF 套件
    * ```composer require barryvdh/laravel-snappy```
* 安裝必要相關檔案
    * 64 位元用 composer 下載 wkhtmltopdf 和 wkhtmltoimage
        * ```composer require h4cc/wkhtmltopdf-amd64 0.12.x```
        * ```composer require h4cc/wkhtmltoimage-amd64 0.12.x```
    * 複製檔案到指定位置
    ```
    sudo cp vendor/h4cc/wkhtmltoimage-amd64/bin/wkhtmltoimage-amd64 /usr/local/bin/
    sudo cp vendor/h4cc/wkhtmltopdf-amd64/bin/wkhtmltopdf-amd64 /usr/local/bin/
    ```
    * 修改檔案權限
    ```
    sudo chmod +x /usr/local/bin/wkhtmltoimage-amd64 
    sudo chmod +x /usr/local/bin/wkhtmltopdf-amd64
    ```
    * sudo apt-get install -y openssl build-essential xorg libssl-dev
    * sudo apt install libssl1.0-dev
        * [出現Exit with code 1 due to network error: UnknownNetworkError](https://github.com/wkhtmltopdf/wkhtmltopdf/issues/3923)

# 程式部分
* 程式可以參考我的 [laravel筆記](https://github.com/youmu257/laravel-note)
* .env 中加入
    ```
    WKHTML_PDF_BINARY=/usr/local/bin/wkhtmltopdf-amd64
    WKHTML_IMG_BINARY=/usr/local/bin/wkhtmltoimage-amd64
    ```
* 在 config/app.php 中加入 ```'PDF' => Barryvdh\Snappy\Facades\SnappyPdf::class,```
* 產生 PDF 可以參考 app/Mail/SamplePdfMail.php 中的寫法
*  宣告 PDF 檔 ```PDF::loadView('email.sample_pdf', $this->requestData)```
* 產生 PDF 檔並夾帶進信件中 ```->attachData($pdf->output(), 'pdf-sample.pdf')```
* [參考樣板](https://stripo.email/en/demo/?template=6677&project=6782&guid=49908f77-6dd4-4a65-9d2f-032ad469e6da)

# 結語
* 產生 PDF 就是這麼簡單

# 參考
* [Snappy PDF/Image Wrapper for Laravel 5 and Lumen 5.1
](https://github.com/barryvdh/laravel-snappy)
* [Snappy](https://github.com/KnpLabs/snappy#wkhtmltopdf-binary-as-composer-dependencies)
* [樣板來源](https://stripo.email/templates/type/order/)