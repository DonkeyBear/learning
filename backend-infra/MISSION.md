# Mission: 後端基礎架構知識

## Why
我已經能用 Python + FastAPI + Firebase + uvicorn 寫出一個可以 CRUD 的後端並部署到 VM 上，但對中間的「膠水層」理解不夠（CORS、反向代理、API 網關、鑑權、資安）。我希望補足這些底層知識，讓自己能在後端面試中有自信地回答架構題，並在實務上做出正確的設計決策。

## Success looks like
- 能清楚解釋一個 HTTP request 從瀏覽器發出到伺服器回應的完整路徑，包含每個中間環節的角色
- 能在白板上畫出一個標準的現代後端部署架構圖（Load Balancer → Reverse Proxy → API Server → Database），並說明每一層的職責
- 能正確設定 CORS、Nginx 反向代理、JWT/OAuth2 鑑權，並解釋為什麼這樣設定
- 面試被問到「你們的服務怎麼做鑑權？」或「CORS 是什麼？」時，能給出有深度的回答
- 能辨識常見的資安威脅（XSS、CSRF、SQL Injection）並知道防禦策略

## Constraints
- 以中文學習（術語保留英文）
- 每次學習時間不宜過長，偏好短而密集的課程單元
- 需要實作練習，不只是理論
- 目標是能通過後端工程師面試（約 1-3 個月準備期）

## Out of scope
- 前端框架或 UI 開發
- DevOps/CI-CD 管線深入（可之後再學）
- 容器化（Docker/K8s）— 目前先聚焦單機部署的理解
- 資料庫內部原理（索引、查詢優化等）
