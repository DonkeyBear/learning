# Statistics-101 Teaching Notes

## 課程設定

- **highlight.js 主題**：`atom-one-dark`（全課程統一）
- **語言**：繁體中文（zh-TW）
- **色彩主題**：科學青綠（teal `#2dd4bf`）＋暖琥珀（amber `#f59e0b`）——統計學專屬，與後端課程藍色調區隔
- **樣式**：CSS 變數體系（見 `assets/style.css`），佈局與間距不變

## 教學偏好

- **故事驅動**：以歷史上的著名實驗與悖論（高爾頓釘板、蒙提霍爾、女士品茶等）作為每個概念的敘事主軸
- **直覺優先**：先建立 mental model，再補公式。避免「公式轟炸」
- **互動練習**：每堂課至少包含一個互動測驗或視覺化元件，確保 retrieval practice
- **ROADMAP.md** 提供的是需求大綱，課程編排可彈性調整，不須逐項照搬

## 使用者背景

- 程式開發者，熟悉邏輯思考與數值運算
- 統計學與機率論近乎零基礎
- 學習動機：滿足好奇心、建立廣度認知

## 版面 RWD 實作規則

> 適用所有課程 HTML（statistics-101 及未來各模組）

### ✅ 並排 Grid 的正確寫法

凡是需要「小螢幕上下排、大螢幕並排」的區塊，**一律使用 `auto-fit` + `minmax`**，禁止寫死 `grid-template-columns: 1fr 1fr`。

```css
/* ✅ RWD 友善：寬度不足時自動換行 */
display: grid;
grid-template-columns: repeat(auto-fit, minmax(<最小寬度>, 1fr));
gap: 1rem;

/* ❌ 禁止：永遠兩欄，不管螢幕多窄 */
display: grid;
grid-template-columns: 1fr 1fr;
```

> [!WARNING]
> **卡片與 Callout 的橫向並排限制**：如果卡片（`.card`）或 Callout 內的文字內容較長，或數量過多（3 個以上），**即使在大螢幕上也不應橫向並排**。由於頁面主體最大寬度限制為 `720px`，並排會使每欄寬度過窄（如低於 `240px`）導致文字嚴重擠壓。此類情況請使用 `.stack-cards` 類別進行垂直上下排列。

### minmax 最小寬度參考

| 用途 | 建議 minmax 最小值 |
|---|---|
| 卡片式概念對比（如：中央趨勢 vs 離散程度） | `200px` |
| 圖表並排（如：身高分布 vs 收入分布） | `260px` |
| 三欄以上（如：對稱 / 右偏 / 左偏） | 使用 `repeat(auto-fit, minmax(180px, 1fr))` |

### ✅ LaTeX 公式防爆版面

當 LaTeX 公式（如 KaTeX）過寬時，會直接撐開外層容器破壞排版。
- **作法**：使用包裹容器配合 `overflow-x: auto`。
- **範例**：
  ```html
  <div class="math-scroll">
    $$ P(H \mid E) = \frac{P(E \mid H) \cdot P(H)}{P(E)} $$
  </div>
  ```
  ```css
  .math-scroll {
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
    padding: 0.25rem 0;
  }
  ```

### ✅ 複雜表格（Table）的 RWD

表格在小螢幕上易因單元格自動換行或寬度不足而擠壓變形，但不應隨意以 `@media` 丟棄/隱藏欄位。
- **作法**：使用滾動條容器包裹，並對 `th`, `td` 設定 `white-space: nowrap`，不設定硬性的 `min-width`。
- **範例**：
  ```html
  <div class="table-responsive">
    <table>
      <thead>...</thead>
    </table>
  </div>
  ```
  ```css
  .table-responsive {
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
  }
  .table-responsive th,
  .table-responsive td {
    white-space: nowrap;
  }
  ```

### 背景

## 課與課之間的銜接規則

> 2026-06-29 建立，同日依據前段課件樣式修正統一

每當生成新的一課（第 N 課）時，同步更新前一課（第 N−1 課）的結尾，加入：

1. **下一課預告**（`<h2>下一課預告</h2>`）：使用獨立的 `<h2>下一課預告</h2>` 標題（**禁止使用** `.callout` 或 `.callout.tip` 包裹預告區塊），用 3–5 句話說明上一課學到的概念如何自然延伸至下一課主題。並在下方放置一個居中的跳轉按鈕，樣式如下：
   ```html
   <div style="text-align: center; margin: 1.5rem 0;">
     <a href="下一課檔名.html" style="display: inline-block; padding: 0.6em 1.4em; background: var(--accent); color: #0f1119; border-radius: 6px; font-weight: 600; text-decoration: none;">
       → 前往 Lxxxx：下一課標題
     </a>
   </div>
   ```
2. **底部導覽連結**：使用乾淨的 `<nav class="lesson-nav">`（flex 排版已在 `assets/style.css` `.lesson-nav` 類別中定義），**僅保留**「← 回到課程索引」連結，**不要**在 `nav` 內放入下一課的文字連結，保持頁面簡潔。

這是強制規則——不能只新增課程檔案，必須回頭把前一課的結尾打開、接上。

2026-06-29 修正 `0001-shape-of-data.html` 及 `0004-bayes-theorem.html` 時發現：
1. 課程中多處使用了固定 `1fr 1fr` 兩欄，在手機或小視窗下兩張圖表擠在一起，改用 `auto-fit + minmax`。
2. 長公式與四欄數據表格在手機端會爆版面或折行，透過對公式與表格使用 `overflow-x: auto` 以及 `white-space: nowrap` 強制不換行來提供橫向滾動支援，確保所有螢幕尺寸的內容完整度。
