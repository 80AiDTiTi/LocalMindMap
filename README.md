# LocalMindMap

單檔心智圖工具：免安裝、離線可用，資料存在自己的瀏覽器，也可以選擇同步到自己的 Google Drive。

整個程式只有一個 `index.html`（繪圖引擎 SimpleMindMap 整包內嵌），沒有後端、不收集任何資料。

## 特色

- 單一 HTML 檔案，免安裝、免註冊；斷網也能開啟與編輯
- 資料自動存於瀏覽器本機（IndexedDB），關掉重開還在
- 多分頁心智圖（分頁數量不限），每張圖各自記住設定
- 7 種版型：邏輯結構圖、思維導圖（雙邊）、組織架構圖、目錄組織圖、時間軸（橫式／直式）、魚骨圖
- 24 色色票；每顆節點可個別設定底色、字色、框線、連線顏色與虛實、超連結
- 搜尋、復原（Undo）、縮放與適應畫面；節點文字可用 Shift+Enter 換行
- 匯入／匯出 Markdown（自有格式，可往返編輯）、匯入一般的大綱式 Markdown
- JSON 無損備份與還原；本機備份清單最多保留 10 份
- 匯出 PNG（白底）、SVG
- 可選的 Google Drive 同步：本機與雲端兩邊都改過時會先跳出衝突提示，不默默覆蓋
- 中英雙語介面

## 快速開始

1. 下載 `index.html`。
2. 用瀏覽器打開即可使用；也可以放到任何靜態網站空間（例如 GitHub Pages、Cloudflare Pages、Netlify）用網址開啟。

本機編輯與存檔不需網路。換瀏覽器或清除瀏覽器資料前，請先用「檔案 → 備份（JSON）」或匯出 Markdown 保存你的圖。

## Google Drive 同步設定（選用）

同步功能完全看個人決定，不設定也不影響本機使用。要啟用同步：

1. 到 [Google Cloud Console](https://console.cloud.google.com/) 建立一個專案，並啟用 **Google Drive API**。
2. 設定 **OAuth 同意畫面**。若發布狀態維持「測試中」，請把你自己的 Google 帳號加入「測試使用者」清單（只有清單上的帳號能登入同步）。
3. 建立 **OAuth 2.0 用戶端 ID**，類型選「網頁應用程式」，並把你開啟本工具的網址（來源）加入「已授權的 JavaScript 來源」。
4. 打開 `index.html`，找到檔案中這一行，把值換成你的用戶端 ID：

   ```
   const GOOGLE_CLIENT_ID = 'YOUR_GOOGLE_CLIENT_ID';
   ```

5. 重新載入頁面，點右上角的雲端圖示登入，即可綁定或新建雲端同步檔案。

注意：登入憑證約 1 小時到期，屆時重新登入即可；同步檔案會存放在你自己的 Google Drive（應用程式專屬範圍），不會動到其他檔案。

## 檔案格式

- **Markdown（主要格式）**：第 3 版。檔首有版本與系統設定註解，節點樣式以 `{鍵=值}` 後綴保存，可完整往返編輯。第 1、2 版的檔案可直接匯入（舊版型代碼會自動對應）。
- **JSON 備份**：無損格式，包含全部圖與樣式，用於備份與還原。

## 授權

MIT License，見 [LICENSE](LICENSE)。

內嵌的繪圖引擎 [SimpleMindMap](https://github.com/wanglin2/mind-map) 亦為 MIT 授權。
