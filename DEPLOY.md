# 部署

- 站点: https://slides.minapp.xin → 服务器 81.69.220.28 (token.minapp.xin)
- 部署目录: `/data/hook/`（deploy.sh、repository.git、token）
- 触发: GitHub Webhook POST `https://hook.minapp.xin/hooks/slides?token=<见 /data/hook/token>` → dispatch.sh → deploy.sh（systemd-run）
- 流程: fetch origin main → 校验 SHA → 展开到 releases/<sha> → 软链 current → `skill2money.html` 同时复制为 `index.html`
- 站点根: `/opt/1panel/apps/openresty/openresty/www/sites/slides.minapp.xin/current`
- 证书: acme.sh（ZeroSSL）自动续期

推送 main 分支即自动部署。