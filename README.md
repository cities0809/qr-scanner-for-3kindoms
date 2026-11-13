# 三國幻戰 QR 連續掃卡工具

手機連續掃描實體卡片的 QR Code，擷取相機畫面，將 QR 原始內容與截圖送到私人的 Google 試算表與 Google Drive。

## 啟動

1. GitHub Repository → **Settings → Pages** → **Build and deployment**。
2. Source 選 **Deploy from a branch**，Branch 選 **main**，Folder 選 **/(root)**，按 **Save**。
3. 在 iPhone Safari 開啟：https://cities0809.github.io/qr-scanner-for-3kindoms/
4. Apps Script /exec 網址已在 `index.html` 預先設定。
5. 在手機輸入自己於 Apps Script「指令碼屬性」設定的 `WRITE_TOKEN`，不要分享給任何人。
6. 點擊 **啟動鏡頭**，依序掃描卡片，確認畫面出現已寫入，並在 [Google 試算表](https://docs.google.com/spreadsheets/d/1_m1kXUzoqSHXsQ9LjSkYHtWS6RvItIxw421Tt02SVQ4/edit) 的「QR掃描紀錄」檢查結果。

## 架構

- `index.html`：手機掃描器；需要 HTTPS 和相機授權
- `manifest.webmanifest`：PWA manifest
- `icon-192.png`、`icon-512.png`：PWA 圖示
- `.nojekyll`：GitHub Pages 靜態發佈
- Google Apps Script：從 Script Properties 讀取 `WRITE_TOKEN`
- Google Sheets：QR 原始內容與時間等資料
- Google Drive：掃描截圖

## 安全注意

**此版僅供私人測試。** 公開 GitHub Pages 代表網頁程式碼可見，**不要把 `WRITE_TOKEN` 寫入 GitHub**。當前回傳確認機制的 GET 查詢網址可能包含密鑰，並在瀏覽器或伺服器診斷記錄留下痕跡。避免在共用裝置勾選「記住設定」，不要公開掃描內容或 Google 試算表。

尚未進行真實卡片與 Google Drive 的端到端測試。