工商信息查询系统（前端）
 一个免费的工商信息查询系统前端，使用React和Tailwind CSS，部署到Cloudflare Pages。数据来自国家企业信用信息公示系统。

 ## 功能
 - 批量查询真实工商信息
 - 保存历史记录（Cloudflare Workers KV）
 - 导出Excel
 - 响应式UI

 ## 项目结构
 ```
 business-query-system/
 ├── public/
 │   └── index.html
 ├── .gitignore
 └── README.md
 ```

 ## 部署
 1. 推送代码到GitHub。
 2. 在Cloudflare Pages连接GitHub仓库。
 3. 配置构建目录为`public`。

