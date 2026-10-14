# 日常 Daily — 個人生活管理 PWA（第一版）

## 功能
- 待辦事項：新增、編輯、刪除、完成、到期日期
- 習慣追蹤：每日打卡、近七天視覺紀錄
- 每日日誌：心情、文字紀錄、歷史瀏覽
- 旅遊與裝備：建立行程、管理裝備清單
- 汽車管理：保養/維修/燃料/停車/保險稅金等支出、日期、里程
- 月報表：任務、習慣、日誌摘要及近六個月汽車支出
- JSON 手動匯出與匯入
- Service Worker 基本離線快取
- 通知權限測試（不包含背景排程或推播伺服器）

## 重要資料安全說明
- 使用 IndexedDB 儲存資料，資料留在目前瀏覽器/裝置。
- 清除網站資料、移除網站資料或裝置故障可能導致資料遺失。
- 請定期匯出 JSON，並將備份保存到安全位置。
- 匯入會取代目前資料，請先匯出現有資料。
- GitHub Pages 是公開靜態網站託管；請勿把個人日誌、備份檔或其他私密資料提交到 repo。
- 本版不會把紀錄自動同步到雲端。
- 不要把通知當成緊急或可靠鬧鐘。

## Windows 本機測試
最簡單方式：使用 VS Code 安裝 Live Server 擴充套件，開啟資料夾，右鍵 `index.html` → Open with Live Server。
或在 PowerShell 切換到資料夾後執行：
`py -m http.server 8000`
再於電腦開啟 `http://localhost:8000`。本機 HTTP 測試可使用 IndexedDB，但 Service Worker 通常只在 localhost 或 HTTPS 生效。

## 發布到 GitHub Pages
1. 登入 GitHub，建立一個新的 repository，例如 `daily-life-pwa`。
2. 若使用免費方案，將 repository 設為 Public。注意：repo 裡只能放程式碼，不能放個人資料或備份檔。
3. 將本資料夾內的 `index.html`、`manifest.webmanifest`、`sw.js`、`icon.svg`、`README.md` 上傳到 repository 根目錄。
4. 開啟 repository 的 Settings → Pages。
5. 在 Build and deployment 中選擇 Deploy from a branch；Branch 選 `main`，資料夾選 `/(root)`，按 Save。
6. 等待發布完成，打開 GitHub Pages 提供的 HTTPS 網址。
7. 在 iPhone 13 Pro 用 Safari 開啟網址 → 分享 → 加入主畫面 → 加入。從主畫面圖示開啟測試。
8. 先建立幾筆測試資料，匯出 JSON，再測試匯入。確認資料復原成功後，再輸入真實紀錄。

## 更新程式
修改檔案後 commit/push 到 GitHub。部署更新後，關閉並重新開啟 PWA；若仍顯示舊版，可關閉該 App、重新載入網站，必要時移除主畫面捷徑再重新加入。每次更新 Service Worker 的程式快取版本時，請同步修改 `sw.js` 中的 `CACHE_NAME`。

## 提醒與通知
目前僅提供 App 開啟時的逾期提示及通知權限測試。iOS 主畫面 Web App 支援 Web Push，但真正的推播需要 Push API、Service Worker 訂閱流程、VAPID 金鑰與伺服器端推播服務；不能只靠靜態 GitHub Pages 可靠地安排背景提醒。
