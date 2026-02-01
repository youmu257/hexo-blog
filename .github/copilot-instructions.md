# Hexo Blog 專案通用規則

## 專案類型
這是一個 Hexo 靜態網站部落格專案。

## 建立新文章規則

### 檔案位置
- 路徑：`source/_posts/`

### 檔名規則
- 格式：`yyyyMMdd_描述.md`
- 範例：`20260129_docker_install.md`

### 文章內容範本
```markdown
---
title: 標題
categories: 分類名稱
---
## 前言
前言內容....

## 環境
- OS : Windows 10
- 其他環境資訊

## 步驟
步驟說明....

# 結語
結語內容.....

# 參考
* [參考連結名稱](https://example.com)
```

### 現有分類參考
- PHP
- git
- 工具教學
- 資料庫

### 寫作風格
- 使用繁體中文
- 技術指令使用 code block 包覆
- 圖片可使用 imgur 外連或放置於 `source/images/` 目錄
