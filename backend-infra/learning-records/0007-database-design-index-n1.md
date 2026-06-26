# 資料庫設計 — 索引、N+1、連線池的理解已補足

完成 Lesson 0007，從 Firebase/Firestore（NoSQL）使用者視角補足關聯式資料庫知識盲區：

- **索引原理**：B-tree 結構，類似書籍目錄；無索引 = 全表掃描 = O(n)
- **N+1 問題**：ORM 最常見的效能陷阱——SELECT users → 對每個 user 再 SELECT orders（1+N 次查詢）
- **連線池**：資料庫連線很貴，pool 讓你重用連線；pool_size ≈ (CPU cores × 2) + 1
- **關聯式 vs NoSQL**：關聯式適合 structured data + 多表 join；NoSQL 適合 denormalized + 高寫入吞吐

**核心洞察**：Firestore 幫你處理了索引和水平擴展，但也隱藏了 SQL 世界的重要概念。面試中你需要能用 SQL 思維解釋問題。

**Implications:** 已能判斷何時用 SQL、何時用 NoSQL。下一步自然過渡到快取——索引做到 0.1ms，Redis 做到 0.01ms。

**相關課程**：[[0008-caching-strategies]]
