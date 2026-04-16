# lhwork
灵职集市


灵职集市 (lhwork)
> 灵活用工平台 - 连接雇主与服务提供商
项目简介
灵职集市是一个面向灵活用工场景的在线交易平台，支持项目发布、投标、服务购买、订单管理、钱包结算等核心功能。
技术栈
前端: HTML5 + CSS3 + JavaScript (Tailwind CSS)
后端: Node.js + Express.js
数据库: MySQL 8.0
进程管理: PM2
Web服务器: Nginx
快速开始
```bash
# 一键启动
./start.sh

# 一键停止
./stop.sh

# 一键部署 (需要sudo)
sudo -S -p '' ./deploy.sh
```
主要功能
✅ 用户注册/登录 (JWT认证)
✅ 服务发布与管理
✅ 项目发布与投标
✅ 在线订单交易
✅ 钱包与提现
✅ 站内消息
✅ 服务评价
✅ 管理后台
文档
详细技术架构文档: ARCHITECTURE.md
目录结构
```
lingzhijishi/
├── frontend/          # 前端页面
├── server/            # 后端服务
│   ├── routes/        # API路由
│   ├── middleware/    # 中间件
│   ├── config/        # 配置
│   └── scripts/       # 脚本
├── deploy.sh         # 部署脚本
├── start.sh          # 启动脚本
├── stop.sh           # 停止脚本
└── ARCHITECTURE.md   # 架构文档
```
服务地址
前台首页: http://localhost/
管理后台: http://localhost/admin
健康检查: http://localhost/health
License
MIT


开源项目，有需求的大佬可以自行下载部署完善，有兴趣一同完善的加V l45458900
