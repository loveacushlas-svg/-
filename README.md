Personal Secretary V60 — 手動 Firebase 雲端備份

1. Firebase Console 建立 Spark 免費方案專案（不需付款資訊）。
2. Authentication → Sign-in method → 啟用 Google。Authentication → Settings → Authorized domains 加入你的 GitHub Pages 網域（例如 loveacushlas-svg.github.io）。
3. Firestore Database → 建立資料庫；在 Rules 頁貼上 firestore.rules 的內容並發布。務必使用這組登入者限定規則，不要公開讀寫。
4. 專案設定 → 你的應用程式 → 新增「網頁」應用程式，複製 firebaseConfig 物件中的 apiKey、authDomain、projectId、appId 等欄位，轉為有效 JSON 貼進 APP 設定頁（欄位名稱與值都用雙引號）。
5. 以 HTTPS 部署至 GitHub Pages。登入 Google，按「備份到雲端」。換手機後，在相同網址貼上相同 Firebase 設定、登入相同 Google 帳號，按「從雲端還原」。
6. 本機 IndexedDB 與原有 JSON 匯出/匯入仍保留。雲端只在手動點擊備份時上傳；照片會包含在備份 JSON 中，並分段寫入 Firestore。

注意：Firebase 設定值並非密碼，Firestore Rules 才是資料隔離的關鍵。不要上傳 Service Account 私鑰。Firebase Spark 有免費用量上限，超額時操作可能失敗；請保留 JSON 離線備份。iOS 主畫面 PWA 的彈出式 Google 登入可能受瀏覽器限制，請先於 Safari 測試。
