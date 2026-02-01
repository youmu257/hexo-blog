---
title: MEE6 連結 YouTube 通知教學
categories: 工具教學
---
## 前言
MEE6 是 Discord 上非常熱門的機器人，其中一個實用功能就是可以連結 YouTube 頻道，當有新影片上傳時自動發送通知到指定頻道。本篇將介紹兩種設定方式，並說明各自的優缺點。

## 環境
- MEE6 Bot（需要加入你的 Discord 伺服器）
- YouTube 頻道

## 方法一：直接連結 YouTube 頻道(比較不推薦)

### 設定步驟
1. 進入 [MEE6 Dashboard](https://mee6.xyz/dashboard)
2. 選擇你的 Discord 伺服器
3. 點擊左側選單的 **社群通知**
4. 找到 **YouTube 通知** 並點擊啟用
5. 輸入要追蹤的 YouTube 頻道網址或名稱
6. 選擇要發送通知的 Discord 頻道
7. 自訂通知訊息（可選）
8. 儲存設定

### 限制說明
⚠️ **重要提醒：此方法對直播待機室（Premiere/預告）無效！**

MEE6 的 YouTube 直接連結功能是透過偵測「新上傳的影片」來觸發通知。這代表：
- ✅ 一般上傳影片：正常通知
- ❌ 直播待機室：**不會通知**
- ❌ 預定首播（Premiere）：**不會通知**
- ✅ 直播結束後：當直播結束並轉為影片存檔時，才會發送通知

如果你需要在直播開始前（待機室階段）就收到通知，請使用下方的 RSS 訂閱方法。

## 方法二：使用 RSS 訂閱（推薦）

RSS 訂閱可以更即時地偵測到頻道的新內容，包含直播待機室。

### 步驟一：取得 YouTube Channel ID

YouTube Channel ID 是一串以 `UC` 開頭的識別碼，取得方式如下：

#### 方法 A：從頻道頁面網址取得
1. 前往該 YouTube 頻道頁面
2. 查看網址列，格式可能是：
   - `https://www.youtube.com/channel/UC123456789abcdefg` → `UC123456789abcdefg` 就是 Channel ID
   - 如果網址是 `https://www.youtube.com/@頻道名稱`，請用下面的方法

#### 方法 B：從頻道頁面原始碼取得
1. 前往該 YouTube 頻道頁面
2. 按下 `Ctrl + U` 開啟原始碼
3. 按下 `Ctrl + F` 搜尋 `channel_id`
4. 找到類似 `channel_id=UC123456789abcdefg` 的內容
5. `UC` 開頭的那串就是 Channel ID

#### 方法 C：使用線上工具
1. 前往 [Comment Picker - YouTube Channel ID](https://commentpicker.com/youtube-channel-id.php)
2. 貼上頻道網址
3. 點擊查詢即可取得 Channel ID

### 步驟二：生成 RSS 連結

取得 Channel ID 後，將其代入以下 RSS 格式：

```
https://www.youtube.com/feeds/videos.xml?channel_id=你的CHANNEL_ID
```

以祈菈‧貝希毛絲的頻道為例 Channel ID 是 `UCcOWs8dB_1w9GGYUU6TGATg`，則 RSS 連結為：
```
https://www.youtube.com/feeds/videos.xml?channel_id=UCcOWs8dB_1w9GGYUU6TGATg
```

### 步驟三：在 MEE6 設定 RSS 訂閱

1. 進入 [MEE6 Dashboard](https://mee6.xyz/dashboard)
2. 選擇你的 Discord 伺服器
3. 點擊左側選單的 **設尋通知**
4. 找到 **RSS 訂閱** 並點擊啟用，建立我的 RSS 來源
![](/images/mee6_discord_youtube3-1.png)
5. 在 RSS URL 欄位貼上剛才生成的 RSS 連結
6. 選擇要發送通知的 Discord 頻道
![](/images/mee6_discord_youtube3-2.png)
7. 儲存設定
8. 完成會出現一筆啟用的 RSS 訂閱
![](/images/mee6_discord_youtube3-3.png)
9. Discord 會馬上收到一筆最新的 youtube 影片/直播通知

## 兩種方法比較

| 項目 | 直接連結 YouTube | RSS 訂閱 |
|------|-----------------|----------|
| 設定難度 | ⭐ 簡單 | ⭐⭐ 中等 |
| 一般影片通知 | ✅ 支援 | ✅ 支援 |
| 直播待機室通知 | ❌ 不支援 | ✅ 支援 |
| 通知速度 | 較慢 | 較快 |
| 穩定性 | 穩定 | 穩定 |

## 結語
如果你只需要追蹤一般上傳影片，直接連結 YouTube 是最簡單的選擇。但如果你需要追蹤直播待機室或想要更即時的通知，建議使用 RSS 訂閱方式。兩種方法可以同時使用，但要注意可能會收到重複通知。

## 參考
* [MEE6 官方網站](https://mee6.xyz/)
