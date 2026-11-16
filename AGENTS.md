# AGENTS.md — 美食與鍋物探店圖鑑（專案開發規範）

## 1. 專案目的與定位
本專案為個人美食知識庫網站《芷琳的美食與鍋物探店圖鑑 (Gourmet & Hot Pot Wiki)》，旨在系統化記錄特色火鍋、韓式烤肉與早午餐的探店心得、必點菜單與避雷筆記。
本文件的目的是讓 AI 協作工具在新增或修改任何餐廳分頁時，能嚴格遵守一致的視覺風格、目錄結構與排版規範，實現模組化快速擴充。

## 2. 目錄結構與檔案命名規範
所有檔案必須遵守以下路徑與命名規則（一律使用小寫英文字母與連字號 `-`）：
- `index.html`：網站首頁，包含網站簡介與所有探店筆記的卡片總覽。
- `style.css`：全站唯一的共用樣式表，禁止在單一 HTML 檔案內寫 `<style>` 覆蓋全站版型。
- `spots/spotXX-restaurant-type.html`：所有餐廳探店內文皆放置於 `spots/` 資料夾下，檔名必須以兩位數編號開頭（例如 `spot01-hotpot.html`、`spot02-korean-bbq.html`、`spot03-brunch.html`）。

## 3. 網頁整體風格與色彩系統
- **設計風格**：溫暖食記圖鑑風（Warm Gourmet Wiki），卡片圓角設計、重點資訊標籤化、閱讀輕鬆無壓迫感。
- **色彩系統**（定義於 `style.css` 的 `:root`）：
  - 主色調（暖陶磚紅）：`#9a3412`
  - 強調色（食慾亮橘）：`#ea580c`
  - 網站背景色（暖奶油白）：`#fffbf5`
  - 卡片底色（純白）：`#ffffff`
- **語言與格式規範**：一律使用**台灣習慣的繁體中文**，每篇探店筆記必須包含「推薦星等（滿分 5.0）」、「必點菜單清單」與「點餐避雷筆記」。

## 4. 探店分頁標準 HTML 結構（新增頁面必備骨架）
當 AI 需要建立新的餐廳探店頁面（例如 `spots/spot03-xxx.html`）時，**必須**完整複製以下 HTML 結構，不可遺漏導覽列與頁尾文章切換器：

```html
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>餐廳或主題名稱 | 美食與鍋物探店圖鑑</title>
  <link rel="stylesheet" href="../style.css">
</head>
<body>
  <header class="site-header">
    <div class="container header-inner">
      <a href="../index.html" class="brand">🍲 美食與鍋物探店圖鑑</a>
      <nav><a href="../index.html">← 返回美食地圖</a></nav>
    </div>
  </header>

  <main class="container article-container">
    <div class="meta-bar">
      <span class="badge">料理分類標籤</span>
      <span class="rating">⭐ 推薦指數：X.X / 5.0</span>
      <span class="date">造訪日期：YYYY-MM</span>
    </div>
    <h1>探店標題</h1>
    <p class="lead">用兩句話總結這家店的最大特色與適合聚餐的情境。</p>

    <h2>一、湯頭與用餐環境亮點</h2>
    <p>描述店內氛圍、座位舒適度與服務特色...</p>

    <h2>二、必點菜單與口味實測</h2>
    <ul>
      <li><strong>招牌菜色一</strong>：口感與風味描述。</li>
      <li><strong>招牌菜色二</strong>：口感與風味描述。</li>
    </ul>

    <div class="callout">
      <strong>💡 點餐與避雷筆記：</strong> 訂位建議、隱藏吃法或需要避開的雷區寫在這裡。
    </div>

    <h2>三、消費與交通資訊</h2>
    <div class="info-box">
      <p><strong>📍 地區商圈：</strong> 台北市區 / 捷運站周邊</p>
      <p><strong>💰 平均客單價：</strong> NT$ XXX ～ XXX / 人</p>
    </div>

    <div class="chapter-nav">
      <a href="上一篇檔名.html" class="nav-btn">← 上一篇探店</a>
      <a href="../index.html" class="nav-btn">圖鑑總覽</a>
      <a href="下一篇檔名.html" class="nav-btn">下一篇探店 →</a>
    </div>
  </main>

  <footer class="site-footer">
    <div class="container">Gourmet & Hot Pot Wiki · Built with AGENTS.md Rules</div>
  </footer>
</body>
</html>
