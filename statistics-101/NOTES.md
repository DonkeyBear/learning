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

2026-06-29 修正 `0001-shape-of-data.html` 及 `0004-bayes-theorem.html` 時發現：
1. 課程中多處使用了固定 `1fr 1fr` 兩欄，在手機或小視窗下兩張圖表擠在一起，改用 `auto-fit + minmax`。
2. 長公式與四欄數據表格在手機端會爆版面或折行，透過對公式與表格使用 `overflow-x: auto` 以及 `white-space: nowrap` 強制不換行來提供橫向滾動支援，確保所有螢幕尺寸的內容完整度。
