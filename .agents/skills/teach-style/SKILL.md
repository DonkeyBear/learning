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

## 子規範

此 skill 的詳細規範拆分為以下檔案，生成課件時須全部遵守：

| 檔案 | 涵蓋內容 |
|------|----------|
| [LESSON-TEMPLATE.md](./LESSON-TEMPLATE.md) | 課件 HTML 結構、返回索引連結與 CSS 樣式指南 |
| [HIGHLIGHT.md](./HIGHLIGHT.md) | highlight.js 主題選擇、語言載入、code block 標記 |
| [INDEX-SYNC.md](./INDEX-SYNC.md) | 新增課程/課堂時同步更新 `index.html` |
| [PACKAGES.md](./PACKAGES.md) | 外部套件整合指引（Chart.js, KaTeX, Mermaid.js CDN 引入） |

## 生成時自我檢查

每當生成一個課件 HTML，寫入前確認：

- [ ] 深色模式主題
- [ ] 課件結構符合 [LESSON-TEMPLATE.md](./LESSON-TEMPLATE.md)（含 `← 回到課程索引` 連結）
- [ ] highlight.js 主題、語言、code block 標記符合 [HIGHLIGHT.md](./HIGHLIGHT.md)
- [ ] 若是有外部圖表、數學公式或流程圖，依照 [PACKAGES.md](./PACKAGES.md) 引入並初始化對應的套件
- [ ] 若是全新課程或有新課堂，`index.html` 已按 [INDEX-SYNC.md](./INDEX-SYNC.md) 更新
- [ ] 課件放在正確的課程子目錄 `{course}/lessons/` 內，而非 repo 根目錄
- [ ] 引用 `../assets/style.css`（首次生成時一併建立 `assets/` 目錄與檔案），不內聯樣式
