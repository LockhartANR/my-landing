# my-landing

个人网站首页，[lockhart.ren](https://lockhart.ren) 的导航入口。使用 Vue 3 和 Vite，构建后为纯静态页面。

## 本地开发

使用 Node.js 24：

```sh
npm ci
npm run dev
```

访问 http://localhost:5173。

## 构建与预览

```sh
npm run build
npm run preview
python ops/verify.py
```

将 dist/ 托管到静态文件服务即可。仓库内的 CI 负责验证和生成发布包，不执行生产部署。

MIT License。
