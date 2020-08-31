---
title: rethinkDB 筆記
categories: 資料庫
---
# 前言
上一篇記錄 [stf 的安裝流程](https://youmu257.github.io/2020/08/31/20200831_stf/)，其中有使用到 rethinkdb
當時再用時看了老半天才發現他那看起來像 ORM 的寫法就是他的語法
害我看教學看好久，想說怎麼都沒有寫 raw sql 的語法

# 介紹
主要講 rethinkDB 的特色，他與傳統資料庫的差異在於適合用於實時的系統上
傳統資料在如果要確保資料是最新的必須一直下 SELECT 指令去檢查資料是否有變動
但 ReQL (rethinkDB 的查詢語法) 可以用 [Changefeeds](https://rethinkdb.com/docs/changefeeds/ruby/) 去監聽資料是否變動，大幅降低不必要的 request

## 後台
* 確定 rethinkDB 正常運作
    * sudo /etc/init.d/rethinkdb start
* 打開瀏覽器輸入 http://localhost:8080
    ![](https://i.imgur.com/NryMN3s.png)

* 切到 Data Explorer
* 輸入指令即可操作 DB

## 指令
* 新建資料庫
    * ```r.dbCreate("test")```
    * 按下 run，成功會回傳資訊
    ```
    {
        "config_changes": [
            {
                "new_val": {
                    "id": "e55b79bb-32e8-44d6-9911-d3d44c5cfc5a" ,
                    "name": "test"
                } ,
                "old_val": null
            }
        ] ,
        "dbs_created": 1
    }
    ```
* 新建 table
    * ```r.db("test").tableCreate("test1")```
    * 按下 run，成功會回傳資訊
    ```
    {
        "config_changes": [
            {
                "new_val": {
                    "db": "test" ,
                    "durability": "hard" ,
                    "id": "48be759d-7179-498d-be98-6bc45ab9ae46" ,
                    "indexes": [ ],
                    "name": "table1" ,
                    "primary_key": "id" ,
                    "shards": [
                        {
                            "nonvoting_replicas": [ ],
                            "primary_replica": "debian_aav" ,
                            "replicas": [
                                "debian_aav"
                            ]
                        }
                    ] ,
                    "write_acks": "majority" ,
                    "write_hook": null
                } ,
                "old_val": null
            }
        ] ,
        "tables_created": 1
    }
    ```
* insert 資料
    *  寫入資料以 json 格式
    ```
    r.db("test").table("table1").insert({
        id: 1,
        title: "test title",
        content: "test content"
    })
    ```
    * 按下 run，成功會回傳資訊
    ```
    {
        "deleted": 0 ,
        "errors": 0 ,
        "inserted": 1 ,
        "replaced": 0 ,
        "skipped": 0 ,
        "unchanged": 0
    }
    ```
* 取得資料
    * get 只能用於主鍵
        * ```r.db("test").table("table1").get(1)```
        * 按下 run，成功會回傳資訊
        ```
        {
            "id": 1,
            "title": "test title",
            "content": "test content"
        }
        ```
    * filter 可以當成 where 條件
        * ```r.db("test").table("table1").filter({title: "test title"})```
* 更新資料
    * 先取得得資料才能更新，跟下 where 條件的概念一樣
    * ```r.db("test").table("table1").get(1).update({title: "new title"})```

# 參考
* [Changefeeds in RethinkDB](https://rethinkdb.com/docs/changefeeds/ruby/)
* [Rethink DB 初探](https://medium.com/bryanyang0528/rethink-db-%E5%88%9D%E6%8E%A2-42d4d477a72b)