工商信息查询系统
一个支持批量查询工商信息、保存历史记录并导出结果的Web应用。前端基于React和Tailwind CSS，后端使用Cloudflare Workers和KV存储。
功能

批量查询公司信息（每行输入一个公司名称）
保存查询历史记录（存储在Cloudflare Workers KV）
导出查询结果为Excel
响应式UI，现代化的设计

项目结构
business-query-system/
├── public/
│   └── index.html        # 前端入口
├── server/
│   └── worker.js        # Cloudflare Workers 脚本
├── .gitignore
└── README.md

部署步骤
1. 托管到GitHub

创建一个新的GitHub仓库（例如 business-query-system）。
初始化本地项目：git init
git add .
git commit -m "Initial commit"
git remote add origin <your-repo-url>
git push -u origin main



2. 部署前端到Cloudflare Pages

登录 Cloudflare Dashboard。
转到 Pages > Create a project > Connect to Git.
选择你的GitHub仓库。
配置构建：
Build command: 无需构建（静态文件）
Build output directory: public


部署后，获取分配的域名（例如 your-project.pages.dev）。

3. 部署后端到Cloudflare Workers

安装 Wrangler CLI：npm install -g @cloudflare/wrangler


登录 Wrangler：wrangler login


创建 Workers 项目：mkdir worker
cp server/worker.js worker/index.js
cd worker
wrangler init


配置 wrangler.toml：name = "business-query-worker"
compatibility_date = "2025-05-16"
[kv_namespaces]
binding = "BUSINESS_KV"
id = "<your-kv-namespace-id>"


创建 KV 命名空间：wrangler kv:namespace create "BUSINESS_KV"


部署 Workers：wrangler deploy


更新前端 index.html 中的 API 地址为 Workers 的URL（例如 https://business-query-worker.your-account.workers.dev）。

4. 运行本地开发环境

前端：直接打开 public/index.html 或使用本地服务器（如 npx serve public）。
后端：使用 Wrangler 运行 Workers：wrangler dev



注意事项

当前查询使用模拟数据，实际部署需接入真实工商信息API（如企查查）。
确保 Workers KV 已正确配置以存储历史记录。
Cloudflare Pages 提供免费的SSL和CDN支持。

许可证
MIT
