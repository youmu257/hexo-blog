---
title: Laravel migration 和 seed 筆記
categories: PHP
---
## 前言
在接觸到 laravel 前我完全不知道有 migration 這樣的東西可以用，只會下 raw sql 去新增表格和調整欄位
有了 migration 可以快速 DB 環境，也算是可以對 DB table 做一個版控
再搭配 seed 可以把基礎資料也寫入 DB，對於搬移程式碼十分方便
簡直看見新大陸  <img src="https://i.imgur.com/qKlTMip.png" width=126 height=116 />

## 環境
- OS : Windows 10

# 安裝流程
* 下載我的筆記用專案
    * ```git clone https://github.com/youmu257/laravel-note.git```
* ```composer install```
* ```php artisan key:generate```
* ```cp .env.example .env```
* 調整 .env
    * 寫入你的 DB 設定
    ```
    DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=laravel
    DB_USERNAME=user
    DB_PASSWORD=password
    ```

# 建立 migration 檔案
* ```php artisan make:migration create_migration_example_table```
    * create_order_table 表示建立一個產生 migration_example table 的 migration
    * 會依照當前時間生成這樣的檔案 2020_09_03_162217_create_migration_example_table.php

# migration 寫法
* 用法參考[官方文件](https://laravel.tw/docs/5.2/migrations)或我的 [laravel筆記](https://github.com/youmu257/laravel-note)

# 執行 migration
* ```php artisan migration```
    * 會執行 databases/migrations 中的有 extends Illuminate\Database\Migrations\Migration 的 class 
    * 會執行所有 class 中的 up function
        * 如建立 table 或更改欄位
        * 同時把每個更改紀錄寫入 migrations table (此為```php artisan migration```自動建立)
* migrations table 中有一個欄位是 batch
    * 如果要做 rollback 可以用 batch 為單位做回朔
* ```php artisan migration:rollback```
    * 會執行所有 class 中的 down function
        * 所以如果 up 是新建 table，down 就是刪除這張 table

# Seeder
* 都提到 migration 就一起講 seeder
    * 基本上就是寫基本資料進資料庫
* 建立 seeder 指令是 ```php artisan make:seeder UsersTableSeeder```
    * UsersTableSeeder 是要建立的 seeder 檔名
* 會發現預設就有一個 DatabaseSeeder，用途是控制要執行哪些 seeder
    * 在 migration 時帶 --seed 參數會執行 DatabaseSeeder
        * ```php artisan migration --seed```
    * 單純執行 DatabaseSeeder 用 ```php artisan db:seed```
* 如果要執行特定的 seeder 帶 --class 參數
    * ```php artisan db:seed --class=UserTableSeeder```

# 結語
* DB schema 的版控機制
    * migration 除了在新環境可以快速建立起基本的 DB 外，同時也能做快速的 rollback
* 寫得好還可以當一種文件看，寫不好一個 rollback 毀天滅地



# 參考
* [Laravel migration](https://laravel.tw/docs/5.2/migrations)
* [Laravel Seeder](https://laravel.tw/docs/5.2/seeding)