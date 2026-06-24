# 反向代理與 Nginx — 部署架構概念已建立

完成了 Lesson 0003，建立了反向代理的心理模型：正向代理 vs 反向代理的區別、為什麼 uvicorn 不該直接暴露在 80/443 port、Nginx 的核心能力（SSL termination、靜態檔案、緩衝防護、負載均衡）、以及完整的生產環境 Nginx config。

**Implications:** 現在使用者能理解一個標準的後端部署架構（Nginx → uvicorn → FastAPI）。下一課可以往兩個方向走：(1) API Gateway——當服務從 1 個變成多個時，Nginx 的侷限性；(2) 鑑權——如何在這個架構中實作 JWT/OAuth2。
