<img width="2560" height="1305" alt="image" src="https://github.com/user-attachments/assets/cd38cf27-b2cd-477c-9cf4-bf32a6101042" /># lhwork
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


## 灵职集市 - 部署环境清单

    ---

    ### 一、服务器配置要求

    | 项目 | 最低配置 | 推荐配置 | 当前服务器 |
    |------|---------|---------|-----------|
    | 操作系统 | Ubuntu 20.04+ / CentOS 8+ | **Ubuntu 24.04 LTS** | Ubuntu 24.04 LTS ✅ |
    | CPU | 2核 | 4核+ | 16核 ✅ |
    | 内存 | 2GB | 4GB+ | 15GB ✅ |
    | 磁盘 | 20GB | 50GB+ | 947GB ✅ |
    | 带宽 | 2Mbps | 5Mbps+ | — |

    ---

    ### 二、必须安装的软件

    | 软件 | 版本 | 用途 | 安装命令 |
    |------|------|------|---------|
    | **Node.js** | ≥18.x（当前22.22.2） | 后端运行环境 | `curl -fsSL https://deb.nodesource.com/setup_22.x \| sudo -E bash - && sudo apt-get install -y nodejs` |
    | **npm** | 随Node.js自带 | 包管理器 | `npm -v`（验证） |
    | **PM2** | 最新版 | 进程管理/守护进程 | `npm install -g pm2` |
    | **Nginx** | 1.18+（当前1.24.0） | Web服务器/反向代理 | `sudo apt install nginx` |
    | **MySQL** | 8.0+ | 数据库 | `sudo apt install mysql-server mysql-client` |

    ---

    ### 三、项目依赖（npm packages）

    ```
    express ^4.18.2
    mysql2 ^3.6.5
    bcryptjs ^2.4.3
    jsonwebtoken ^9.0.3
    uuid ^9.0.1
    cors ^2.8.5
    dotenv ^16.3.1
    ```

    ---

    ### 四、数据库配置

    | 项目 | 值 |
    |------|-----|
    | 主机 | localhost |
    | 端口 | 3306 |
    | 用户 | debian-sys-maint |
    | 数据库名 | lingzhijishi |
    | 字符集 | utf8mb4 |

    **初始化命令**：
    ```bash
    mysql -u root -p < server/schema.sql
    ```

    ---

    ### 五、端口占用

    | 端口 | 服务 | 用途 |
    |------|------|------|
    | 80 | Nginx | Web访问 |
    | 3000 | Node.js | API服务 |
    | 443 | Nginx | HTTPS（可选） |

    ---

    ### 六、目录结构

    ```
    /home/allen/www/lingzhijishi/     # 项目源码
    /var/www/lingzhijishi/            # 前端静态文件（Nginx根目录）
    /home/allen/.pm2/                 # PM2进程管理
    ```

    ---

    ### 七、PM2 开机启动

    ```bash
    # 设置PM2开机自启
    sudo env PATH=$PATH:/usr/bin pm2 startup systemd -u $USER --hp $HOME

    # 保存当前进程列表
    pm2 save

    # 查看服务状态
    systemctl status pm2-allen
    ```

    ---

    ### 八、部署步骤

    ```bash
    # 1. 上传项目到 /home/用户名/www/项目名/
    # 2. 进入后端目录
    cd /home/用户名/www/lingzhijishi/server

    # 3. 安装依赖
    npm install

    # 4. 配置环境变量
    cp .env.example .env
    # 编辑 .env 填写数据库信息

    # 5. 导入数据库
    mysql -u root -p < ../server/schema.sql

    # 6. 启动服务
    pm2 start ecosystem.config.js

    # 7. 配置Nginx反向代理（参考项目nginx配置）

    # 8. 设置开机自启
    pm2 save
    sudo env PATH=$PATH:/usr/bin pm2 startup systemd -u $USER --hp $HOME
    ```

    ---

    ### 九、验证部署成功

    ```bash
    curl http://localhost/api/home        # 应返回200
    curl http://localhost/               # 应返回前端页面
    pm2 status                           # 应显示 lingzhijishi online
    ```

    ---

    ### 十、防火墙（如需要）

    ```bash
    sudo ufw allow 80/tcp   # HTTP
    sudo ufw allow 443/tcp  # HTTPS
    sudo ufw enable
    ```
开源项目，有需求的大佬可以自行下载部署完善，有兴趣一同完善的加V l45458900
