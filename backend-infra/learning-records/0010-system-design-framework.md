# 系統設計面試 — 四步框架已內化，前十課知識已串聯

完成 Lesson 0010，建立系統設計面試的完整框架：

- **四步框架**：
  1. **釐清需求**（5 min）：問功能範圍、使用者量、讀寫比、延遲要求——不要直接畫圖
  2. **估算規模**（5 min）：QPS、儲存、頻寬——讓數字說話，每個設計決策有數字支撐
  3. **畫出 High-Level 架構**（20 min）：逐層展開（DNS → LB → App → Cache → DB → Storage）
  4. **Deep Dive**（15 min）：挑 2-3 個核心元件深入討論 trade-off

- **實戰案例**：練習了 URL Shortener 的完整設計，涵蓋 301 vs 302 redirect、ID 生成算法、hash collision、Redis 快取策略

**核心洞察**：「系統設計面試不是在考你知不知道答案，而是在考你如何思考。」數字是設計決策的語言——當你說「需要快取」，你要能說出 QPS 是多少。

**Implications:** 前十堂課的知識在系統設計題中全部被調用。已具備後端面試的核心能力基礎，可繼續往部署安全（Lesson 0011）和更多實戰案例延伸。

**相關課程**：[[0001-http-lifecycle]] ~ [[0009-docker-containerization]]（全部前十課）、[[0011-production-deploy-security]]
