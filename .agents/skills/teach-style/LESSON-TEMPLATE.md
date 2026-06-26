# 課件 HTML 結構與樣式指南

課件的深色模式樣式統一存放在該套課程目錄下的 `assets/style.css`，所有課件透過相對路徑 `../assets/style.css` 引用同一份。首次生成課件時一併建立這個檔案與目錄；後續課件不再重複生成樣式，只引用。

## 完整模板

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>{Lesson Title}</title>
<link rel="stylesheet" href="../assets/style.css">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.11.1/styles/{theme}.min.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.11.1/highlight.min.js"></script>
<!-- 僅在課件使用非自動偵測語言時載入額外語法檔 -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.11.1/languages/{lang}.min.js"></script>
<script>hljs.highlightAll();</script>
</head>
<body>
<!-- Lesson content here -->

<nav class="lesson-nav">
  <a href="../../index.html">← 回到課程索引</a>
</nav>
</body>
</html>
```

## 返回課程索引連結

每個課件 HTML 必須在內容末尾（`</body>` 之前）放置返回連結。從課件位置 `{course}/lessons/000N-slug.html` 到根目錄 `index.html` 的相對路徑為 `../../index.html`。

編輯既有課件時，若發現缺少返回連結，一併補上。

## 樣式指南 (CSS Style Guide)

所有自訂與課件專屬樣式皆應集中於 `assets/style.css` 檔案中，不得使用 HTML 內聯樣式 (inline style) 或 `<style>` 標籤。

### 返回連結樣式 (`.lesson-nav`)

若該課程的 `assets/style.css` 尚未定義 `.lesson-nav`，請在該 CSS 檔案內補上以下樣式：

```css
.lesson-nav {
  margin-top: 3rem;
  padding-top: 1rem;
  border-top: 1px solid var(--border);
}
.lesson-nav a {
  color: var(--accent);
  text-decoration: none;
}
.lesson-nav a:hover {
  text-decoration: underline;
}
```
