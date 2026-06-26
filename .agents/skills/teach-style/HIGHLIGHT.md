# 語法高亮

## 主題選擇

選擇一個與深色模式搭配的 highlight.js 主題（如 `atom-one-dark`、`monokai-sublime`、`github-dark` 等）。選擇後記錄於 `NOTES.md`，整個課程的所有課件必須使用同一個主題，保持一致性。

完整主題列表：`https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.11.1/styles/`

## 核心載入（每個課件都要有）

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.11.1/styles/{theme}.min.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.11.1/highlight.min.js"></script>
<script>hljs.highlightAll();</script>
```

## 額外語言語法檔

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

## 程式碼區塊標記

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
