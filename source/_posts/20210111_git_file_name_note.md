---
title: Sourcetree 檔名大小寫偵測不到問題
categories: git
---
## 前言
因為遇到第二次還需要估狗去找解法，還是紀錄一下這麼狀況和解法
~~而且最近太少更新筆記了~~

## 環境
- OS : Windows 10
- Sourcetree

# 情境
1. 檔案已經 commit 過了
    * 先 commit 一個 test.txt 的檔案
    ![](https://i.imgur.com/ddDIeo5.png)
2. 更改檔名時，且只更改大小寫部分
    * 改為 Test.txt
    ![](https://i.imgur.com/QcpkKin.png)
3. Sourcetree 切到 File status
    * 什麼改變都沒有
    ![](https://memeprod.sgp1.digitaloceanspaces.com/user-wtf/1587384378140.jpg)
4. 用指令檢查
    * cmd 輸入 git status
    ![](https://i.imgur.com/K9TyHwH.png)
    * 發現偵測不到改動

# 解法
* 先把檔名改回去 test.txt
* 打開 cmd 輸入指令，用指令更改檔名
    * ```git mv test.txt Test.txt```
* 回到 Sourcetree 發現可以正常偵測到改動了

# 結語
* 事不過三，這次一定記住

# 參考
* [關於檔名的大小寫](https://gitbook.tw/posts/2018-06-05-case-sensitive)