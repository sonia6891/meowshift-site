# 喵的，又要上班了 Meowshift 官網

輪班 App「喵的，又要上班了」（英文 Meowshift，日文にゃんシフト，韓文냥시프트）的介紹網頁，預計用 GitHub Pages 公開在 https://meowshift.pocketjoystudio.com/ （`CNAME` 檔不要刪；pocketjoystudio.com 是工作室共用網域，這裡只用 meowshift 子網域）。這個 repo 只有網頁檔案（HTML、CSS、圖片），沒有 App 或伺服器的程式，也沒有 build；樣式都在 `assets/style.css`，沒有外部字型、沒有追蹤碼。

## 網址

| 網址 | 內容 |
|---|---|
| `/` | 繁體中文首頁（第一次來會照瀏覽器語言轉到對應語言版） |
| `/zh-Hans/` `/en/` `/ja/` `/ko/` `/hi/` `/vi/` `/da/` `/ru/` `/id/` `/tr/` `/de/` `/fr/` `/pl/` `/th/` `/it/` `/nl/` `/pt/` `/es/` | 其他 18 種語言首頁（和 App Store 商店頁的 19 種語言一樣） |
| `/privacy.html`、`/privacy-<語言>.html` | 隱私權政策（19 種語言） |
| `/terms.html`、`/terms-<語言>.html` | 服務條款（19 種語言） |
| `/support.html`、`/support-<語言>.html` | 客服支援（19 種語言） |
| `/delete-account.html` | 刪除帳號與資料（只有中文） |

隱私權政策、服務條款、客服、刪除帳號這幾頁是從 App repo（`meow-work-app` 的 GitHub main，2026-11-21 `6b6840a6`）原封不動複製過來的，檔名和舊網址一樣：舊的 `https://sonia6891.github.io/meow-work-app/privacy-en.html` 就是新的 `https://meowshift.pocketjoystudio.com/privacy-en.html`。App repo 裡這些頁面由 `scripts/legal-pages.mjs` 產生；**條款改了，要把新的 html 再複製過來**，不要在這裡手改。

## 首頁的字從哪裡來

- App 名稱、副標題、開頭那句話、「前 7 天 PRO 全開」、四張功能卡（班表、薪水、假別、每天更輕鬆）、免費版和 PRO 的清單、最後一行「僅供參考」：都直接取自 App repo 的商店文字 `store/i18n-metadata/<語言>.json` 的 `name`、`subtitle`、`description`。商店文字改了，首頁也要跟著改。
- 只有少數字是網站自己寫的：區塊標題、「你的資料，你作主」四點、價格說明那句、商店按鈕上的小字。
- 首頁和功能卡的圖：App Store 3.0 那組行銷圖（`marketing/img/<語言>/`，中、簡、日、韓、英各一組；其他語言用英文那組，和 App Store 一樣）、`store/v4-marketing-20261020/art/` 的貓和插畫背景、App 圖示 `native/ios/App/App/Assets.xcassets/AppIcon.appiconset/AppIcon-512@2x.png`。分享預覽圖是 `assets/img/og-<語言>.jpg`（1200×630）。

## 數字和出處

| 數字 | 出處 |
|---|---|
| PRO 月繳 NT$99、年繳 NT$790（只在繁中頁顯示，標「台灣價格」） | `supabase/functions/billing-config/index.ts` 第 27–29 行（`monthly:99`、`yearly:790`、`currency:"TWD"`） |
| 前 7 天 PRO 全開 | 各語言 `store/i18n-metadata/<語言>.json` 的 `description` 第二段 |
| 免費版：1 份工作、這個月和下個月的排班 | 同上，「免費版」那段 |
| 19 種語言 | 同上，以及 `store/i18n-metadata/` 的 19 個檔案 |

其他國家的價格（日圓、韓元、美元…）App Store 會依台灣價換算、也可能調整，所以網站不寫，只寫「以 App Store、Google Play 顯示的為準」。

## 什麼時候要改這裡

- **改價**：改繁中首頁 `index.html` 方案卡的 NT$99、NT$790，和上表。
- **新版本、商店文字改了**：照新的 `store/i18n-metadata/*.json` 更新各語言首頁的功能卡和方案清單。
- **換商店截圖**：換掉 `assets/shots/<語言>/` 裡同名的圖（540 寬 webp）。
- **換 App 圖示**：換 `assets/img/icon-192.png`、`apple-touch-icon.png`、`favicon.png`，並重做 `og-*.jpg`。
- **新增語言**：多一個資料夾 `<語言>/index.html`，每一頁的語言選單和 `hreflang` 都要加上它。
- 商店連結：App Store `id6817588985`（繁中連台灣商店、英文連美國商店、其他語言用不分國家的連結），Google Play `com.lumilab.meowwork`。
