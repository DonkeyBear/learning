# API 網關 — 多服務路由心智模型建立

完成 Lesson 0004，建立 API 網關（API Gateway）的心理模型：Nginx 適合靜態路由（URL path → upstream），但當服務變多、需要動態路由、rate limiting、auth 統一驗證時，Nginx 的設定檔會變得難以維護。API Gateway（如 Kong、Traefik、FastAPI 自建）把這些 cross-cutting concerns 集中到一個入口點。

**核心洞察**：API Gateway 不是取代 Nginx，而是坐在 Nginx 和微服務之間。Nginx 處理 L7 TCP/SSL，Gateway 處理路由邏輯、auth 驗證、rate limit。

**Implications:** 可繼續往微服務架構深入，或回到單體優先——理解 Gateway 的本質是「把 middleware 從 app 層拉到 infra 層」。

**相關課程**：[[0003-reverse-proxy-mental-model]] [[0005-authentication-authorization]]
