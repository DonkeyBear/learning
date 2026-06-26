# 容器化 — Docker 不是虛擬機的心智模型已建立

完成 Lesson 0009，建立容器化的核心概念：

- **Container ≠ VM**：容器共用 host kernel、沒有自己的 OS → 啟動快（秒級 vs 分鐘級）、體積小（MB vs GB）
- **Dockerfile 分層快取**：先 COPY requirements → pip install → 再 COPY 程式碼。不變的層直接從快取拿，大幅加速 build
- **Multi-stage build**：builder stage（含編譯工具）→ 只複製 artifacts 到 runtime stage → 最終 image 極小
- **docker-compose**：一鍵啟動 Nginx + FastAPI + Redis + PostgreSQL 整個開發環境

**核心洞察**：Docker 的精髓不是「把 app 包起來」，而是「用程式碼定義執行環境」——Dockerfile 和 docker-compose.yml 是可版本控制、可重現的 infra-as-code。

**Implications:** 已能寫出生產級 FastAPI Dockerfile 和 docker-compose。容器化是部署安全和 CI/CD 的基礎。

**相關課程**：[[0011-production-deploy-security]]
