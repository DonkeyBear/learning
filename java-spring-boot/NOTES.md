# Teaching Notes

## User Preferences
- 理論課（T-series）與實作課（P-series）分開標記，方便用戶在通勤時挑選理論課閱讀
- 每課應以 HTML 格式輸出，使用 dark-mode 主題（/teach-style）
- 偏好對比式教學：將 Java/Spring Boot 概念對比到已熟悉的 JS/TS/Python/FastAPI
- IDE: IntelliJ Community Edition（免費版），實作課需包含 IntelliJ 操作指引
- 授課語言：繁體中文

## Curriculum Design Principles
- 先給生存包（夠用的 Java 語法）→ 快速進入 Spring Boot → 回頭補強 Java 深度
- 每個面試重點（DI、IOC、Stream、Bean 生命週期、執行緒安全）至少有一節獨立理論課
- 整合專案作為最終產出，貫穿所有實作課
- 實作課使用漸進式專案：從單一 endpoint 逐步擴展到完整 REST API

## Lesson Naming Convention
- T = Theory（理論課，適合手機閱讀）
- P = Practice（實作課，需要電腦跟 IntelliJ）
- 編號格式：`0001-T-<slug>.html` / `0002-P-<slug>.html`

## Visual Theme
- highlight.js 主題：`atom-one-dark`（整個課程統一套用）
- 課程 accent color：Spring Boot 綠 `#6db33f`
- 共用樣式檔：`java-spring-boot/assets/style.css`
