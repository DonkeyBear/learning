# 快取策略 — Redis 三種模式與失效策略已建立

完成 Lesson 0008，建立快取的完整心智模型：

- **三種模式**：
  1. Cache-Aside（最常見）：app 先查 Redis，miss 再查 DB 並回填
  2. Read-Through：快取層代理 DB 查詢，app 只跟快取溝通
  3. Write-Through / Write-Behind：寫入時同步/非同步更新快取

- **失效策略**：
  1. TTL（最簡單）：設定過期時間
  2. Cache Invalidation（最難）：資料變更時主動刪除/更新快取
  3. 經典解法：先刪快取 → 再更新 DB → 再設 TTL

**核心洞察**：「There are only two hard things in Computer Science: cache invalidation and naming things.」——Phil Karlton。快取失效是所有策略中最容易出錯的環節。

**Implications:** 已能在 FastAPI 中整合 Redis 做快取。快取是系統設計面試中的核心元件。

**相關課程**：[[0007-database-design-index-n1]] [[0010-system-design-interview]]
