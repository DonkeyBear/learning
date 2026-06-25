---
name: teach-style
description: Dark-mode lesson shell with highlight.js syntax highlighting. Use alongside teach — when the user types /teach and /teach-style together at session start, or whenever a lesson HTML is being generated.
---

# Teach Style

載入後，所有由 `teach` skill 生成的課件 HTML 必須是 **深色模式** 主題，並整合 highlight.js 語法高亮。此 skill 不單獨執行——與 teach 並列載入，在課件生成時自動作用。

## 多課程倉庫結構

此 repo 是一個多課程共用的 monorepo。每個課程獨立放在一個 kebab-case 命名的子目錄中，repo 根目錄不直接放置任何課程檔案。

生成課程時：
- 根據課程主題自動產生 kebab-case 課程名稱（如 `python-basics`、`rust-ownership`）
- 在 repo 根目錄下建立該課程子目錄
- `teach` skill 的所有 workspace 檔案（`MISSION.md`、`NOTES.md`、`lessons/`、`assets/` 等）都放在該課程目錄內

```
learning/                    ← repo 根目錄（不放課程檔案）
├── python-basics/           ← 課程子目錄（kebab-case）
│   ├── MISSION.md
│   ├── NOTES.md
│   ├── lessons/
│   │   ├── 0001-xxx.html
│   │   └── 0002-yyy.html
│   └── assets/
│       └── style.css
├── rust-ownership/
│   └── ...
```

## 課件 HTML 結構

課件的深色模式樣式統一存放在該套課程目錄下的 `assets/style.css`，所有課件透過相對路徑 `../assets/style.css` 引用同一份。首次生成課件時一併建立這個檔案與目錄；後續課件不再重複生成樣式，只引用。

每個課件使用以下結構：

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
<div class="footer">
  <p>有疑問嗎？直接問你的 AI 老師來獲得協助。</p>
</div>
</body>
</html>
```

## 語法高亮

### 主題選擇

選擇一個與深色模式搭配的 highlight.js 主題（如 `atom-one-dark`、`monokai-sublime`、`github-dark` 等）。選擇後記錄於 `NOTES.md`，整個課程的所有課件必須使用同一個主題，保持一致性。

完整主題列表：`https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.11.1/styles/`

### 核心載入（每個課件都要有）

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.11.1/styles/{theme}.min.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.11.1/highlight.min.js"></script>
<script>hljs.highlightAll();</script>
```

### 額外語言語法檔

highlight.js **自動偵測**以下語言，不須額外載入：
JavaScript、TypeScript、Python、CSS、HTML、JSON、Bash、C、C++、Java、Ruby、Rust、SQL、XML、Markdown、YAML。

僅在課件使用以下語言時，才加入對應 `<script>`（放在 `hljs.highlightAll()` 之前）：

| 語言 | CDN 路徑 |
|------|----------|
| Go | `languages/go.min.js` |
| Kotlin | `languages/kotlin.min.js` |
| Swift | `languages/swift.min.js` |
| Dart | `languages/dart.min.js` |
| Elixir | `languages/elixir.min.js` |
| Haskell | `languages/haskell.min.js` |
| Zig | `languages/zig.min.js` |

完整列表：`https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.11.1/languages/`

### 程式碼區塊標記

highlight.js 透過 `class="language-*"` 辨識語言。常用值：

`language-javascript` `language-typescript` `language-python` `language-rust` `language-bash` `language-json` `language-css` `language-html` `language-sql` `language-yaml` `language-markdown` `language-java` `language-cpp` `language-ruby` `language-go` `language-kotlin` `language-swift`

```html
<pre><code class="language-python">
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b
</code></pre>
```

## 生成時自我檢查

每當生成一個課件 HTML，寫入前確認：

- [ ] 深色模式主題
- [ ] 選擇一個適合課件內容的 highlight.js 深色主題，載入並呼叫 `hljs.highlightAll()`
- [ ] 整個課程的所有課件使用同一個 highlight.js 主題（首次選擇後記錄於 `NOTES.md`）
- [ ] 每個程式碼區塊有正確的 `class="language-*"`
- [ ] 必要時載入額外語言語法檔
- [ ] 課件放在正確的課程子目錄 `{course}/lessons/` 內，而非 repo 根目錄
- [ ] 引用 `../assets/style.css`（首次生成時一併建立 `assets/` 目錄與檔案），不內聯樣式
