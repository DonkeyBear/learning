# Learning Record 0011: 自建後端部署安全

## 日期
2026-06-26

## 學到了什麼
- Defense in Depth（縱深防禦）是部署安全的核心理念——四層防禦：平台 → OS → 反向代理 → 應用
- 防提權需要組合拳：SSH key only + 非 root 執行 + 移除 SUID + 自動更新 + Fail2Ban + SELinux/AppArmor
- 速率限制要分三層：Nginx limit_req（擋在應用前）→ slowapi（精細控制）→ Fail2Ban（動態封鎖）
- 未鑑權 API 用 IP 作為 rate limit key，不同端點不同限制值
- 單一 VM 擋不住大流量 DDoS——需要 Cloudflare 這類前置 CDN/DDoS 清洗服務
- 端口掃描是背景噪音，只要只開 80/443 就無需擔心
- fly.io 預設 deny all、強制 HTTPS、Anycast 分散流量，但不提供 WAF 或 IP 白名單
- GCP VM 需要手動設定 VPC Firewall、iptables、SSH 加固

## 為什麼重要
這堂課直接回答了「我把自己的 API 部署到公網後會發生什麼事」的焦慮。
從面試角度看，這是後端工程師必備的部署知識。

## 相關資源
- [[production-security-checklist]] 參考文件

## 後續學習方向
- 可以深入了解 Cloudflare WAF / GCP Cloud Armor 的配置
- 可以實戰演練：在 VM 上實際跑一次 fail2ban + nginx + slowapi 的完整部署
- 了解 Kubernetes 環境下的安全機制（NetworkPolicy、PodSecurityPolicy）
