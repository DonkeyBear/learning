# 同步 index.html 課程索引

此 repo 根目錄的 `index.html` 是整個 Learning Hub 的課程索引頁面，使用 Vue 3 渲染課程卡片與 modal。每當**建立一個新課程**（新的課程子目錄 + 第一堂課）時，必須同步更新 `index.html` 中的 `courses` 陣列。

## 新增課程

在 `index.html` 的 `setup()` 函數內，找到 `const courses = [` 陣列，新增一個課程物件：

```js
{
  id: 'course-kebab-case',          // 與課程子目錄名稱一致
  icon: '🔧',                        // 一個代表該課程主題的 emoji
  title: '課程標題',
  desc: '一到兩句話描述課程內容與目標。',
  lessons: [
    { title: '第一課標題', href: 'course-kebab-case/lessons/0001-slug.html' },
  ],
},
```

## 新增課堂

每當在現有課程中**新增一堂課**時，要在對應課程的 `lessons` 陣列末尾追加：

```js
{ title: '新課堂標題', href: 'course-kebab-case/lessons/000N-slug.html' },
```

## 注意事項

- `id` 必須與課程子目錄名稱完全一致（kebab-case）
- `icon` 用單一 emoji，不要重複使用已在其他課程使用的 emoji（查看現有課程的 `icon` 欄位確認）
- `href` 路徑相對於 `index.html`，格式為 `{course-id}/lessons/{filename}.html`
- 新增後 `totalLessons` 會自動透過 `computed` 重新計算，無需手動更新
- **不要**更動 `index.html` 的整體結構、Vue 框架版本、或既有課程以外的程式碼
