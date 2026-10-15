# My Daily V4

個人生活管理 PWA：待辦、習慣、生活日誌、旅遊與裝備、汽車管理、月報表、訂閱管理。

## 更新方法
1. 先從舊版匯出 JSON 備份，妥善保存。
2. 將本資料夾五個檔案覆蓋 GitHub Pages 儲存庫根目錄的同名檔案。
3. 等待 Pages 部署，重新啟動 iPhone 主畫面 App。若仍顯示舊版，重新整理網頁。
4. 請勿清除 Safari 網站資料或刪除原 App，以免本機 IndexedDB 資料遺失。

## 提醒限制
通知僅在 PWA 開啟、JavaScript 執行時檢查，不保證背景或關閉 App 後觸發。沒有後端推播。訂閱的幣別不自動換算。

## 相容性
維持 IndexedDB 名稱 daily-life-db 與 appdata key；匯入 V3 JSON 時會自動補上 subscriptions 陣列。
