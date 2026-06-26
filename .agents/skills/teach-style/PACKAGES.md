# 外部套件整合指引 (External Package Integration Guidelines)

當課件（Lesson HTML）需要呈現圖表、數學公式或非數據圖表時，請遵循本指引選擇並引入對應的外部套件。請一律使用 CDN 引入，並選擇合適的套件。

---

## 1. 畫圖表 (Data Charts) — Chart.js

用於需要呈現數據圖表（如折線圖、柱狀圖、圓餅圖等）的場景。

### CDN 引用寫法
```html
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
```

### 使用範例
在 HTML 中加入 `canvas` 畫布，並用 JavaScript 初始化圖表：
```html
<div style="width: 100%; max-width: 600px; margin: 0 auto;">
  <canvas id="myChart"></canvas>
</div>

<script>
  const ctx = document.getElementById('myChart').getContext('2d');
  new Chart(ctx, {
    type: 'bar',
    data: {
      labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
      datasets: [{
        label: '# of Votes',
        data: [12, 19, 3, 5, 2, 3],
        borderWidth: 1
      }]
    },
    options: {
      scales: {
        y: {
          beginAtZero: true
        }
      }
    }
  });
</script>
```

---

## 2. 寫公式 (Mathematical Formulas & Equations) — KaTeX

用於需要呈現數學公式、演算法推導、統計公式等場景。

### CDN 引用寫法
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.17.0/dist/katex.min.css" integrity="sha384-vlBdW0r3AcZO/HboRPznQNowvexd3fY8qHOWkBi5q7KGgqJ+F48+DceybYmrVbmB" crossorigin="anonymous">

<!-- The loading of KaTeX is deferred to speed up page rendering -->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.17.0/dist/katex.min.js" integrity="sha384-AtrdNsnxl/75rvBneBVH7DtOvCxSVahR2zWqle1coBKd8DEmLoviqNeJSx64gNAs" crossorigin="anonymous"></script>

<!-- To automatically render math in text elements, include the auto-render extension: -->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.17.0/dist/contrib/auto-render.min.js" integrity="sha384-bjyGPfbij8/NDKJhSGZNP/khQVgtHUE5exjm4Ydllo42FwIgYsdLO2lXGmRBf5Mz" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>
```

### 使用範例
引入上述腳本與樣式後，KaTeX 會自動將頁面中的 LaTeX 語法渲染為公式。
- **行內公式 (Inline Math)**：使用 `\( ... \)`
- **區塊公式 (Block Math)**：使用 `$$ ... $$` 或 `\[ ... \]`

```html
<p>這是一個行內公式的例子：\( E = mc^2 \)。</p>
<p>這是一個區塊公式：</p>
$$ f(x) = \int_{-\infty}^{\infty} \hat{f}(\xi)\,e^{2\pi i \xi x}\,\dots $$
```

---

## 3. 非數據圖表 (Non-data Diagrams / Flowcharts) — Mermaid.js

用於呈現流程圖 (Flowchart)、時序圖 (Sequence Diagram)、狀態圖 (State Diagram)、架構圖或關係圖等非數值型圖表。

### CDN 引用寫法
```html
<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.esm.min.mjs';
  mermaid.initialize({
    startOnLoad: true,
    theme: 'dark',
    themeVariables: {
      fontFamily: 'Inter, "Noto Sans TC", system-ui, sans-serif'
    }
  });
</script>
```

### 使用範例
在 HTML 中加入 `pre` 或 `div` 元素，並賦予 `class="mermaid"`：
```html
<pre class="mermaid">
flowchart LR
    A["客戶端"] -->|"HTTP 請求"| B("伺服器")
    B -->|"回傳回應"| A
</pre>
```

### ⚠️ Mermaid.js 避坑指南與語法規範

1. **引號保護 Link Labels（重要）**：如果箭頭或連結上的文字（Arrow label）包含任何特殊字元（如斜線 `/`、星號 `*`、括號 `( )`、破折號等），必須使用雙引號包裹，否則會觸發語法解析錯誤。
   - **錯誤**：`GW -->|GET /* (導向請求)| Redirect`
   - **正確**：`GW -->|"GET /* (導向請求)"| Redirect`
2. **節點標籤雙引號保護**：包含 HTML 標籤、表情符號、中文字元或特殊符號的節點標籤建議用雙引號保護。
   - **正確**：`User(["使用者"])`
3. **行內樣式綁定 (Inline Class Binding)**：為節點套用自訂樣式類別（classDef）時，優先使用行內雙冒號語法 (`NodeID:::ClassName`)，而非在圖表尾端使用全域的 `class` 宣告。這能避免 class 命名衝突，並提高 Mermaid 解析器的相容性。
   - **正確**：`APIService["📝 API Service"]:::service`
   - **避免**：`class APIService service;`

---

## 4. 拒絕 ASCII 與提升版面美感 (Modern Layout vs. ASCII)

為維護教材的專業感與現代化視覺體驗，**禁止使用 ASCII 字元畫圖（如使用 `┌─┐`, `│` 等框線組合成的圖表）**。請改用以下兩種現代化替代方案：

### 方案 A：使用 Mermaid.js 繪製流程與架構
適用於時序、流程、網路架構等具有明確關聯與方向性的關係圖。

### 方案 B：使用 CSS Grid/Flexbox 與 Card 布局展示結構性數據
適用於規模估算、規格對比、三欄式決策等靜態結構化資訊。相較於繪製成複雜的圖表，直接使用排版布局能提供極佳的「儀表板 (Dashboard)」體驗，且載入效能更佳。

#### 📊 實作範例：規模估算卡片布局
```html
<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 1rem; margin: 1.5rem 0;">
  <div class="card" style="margin: 0; display: flex; flex-direction: column; justify-content: space-between; border-left: 4px solid var(--accent); background: var(--card-bg);">
    <h4 style="margin: 0 0 0.5rem; color: var(--accent); font-size: 1rem;">📊 QPS 吞吐量</h4>
    <div style="font-size: 0.9rem; line-height: 1.6;">
      <p style="margin: 0.3rem 0;"><strong>寫入：</strong>1,200 QPS</p>
      <p style="margin: 0.3rem 0;"><strong>讀取：</strong>12,000 QPS</p>
    </div>
  </div>
  <div class="card" style="margin: 0; display: flex; flex-direction: column; justify-content: space-between; border-left: 4px solid var(--warning); background: var(--card-bg);">
    <h4 style="margin: 0 0 0.5rem; color: var(--warning); font-size: 1rem;">💾 儲存空間估算</h4>
    <div style="font-size: 0.9rem; line-height: 1.6;">
      <p style="margin: 0.3rem 0;"><strong>每筆資料：</strong>約 130 bytes</p>
      <p style="margin: 0.3rem 0;"><strong>五年容量：</strong>約 24 TB</p>
    </div>
  </div>
</div>
```
