# my-landing

个人网站首页，作为 [lockhart.ren](https://lockhart.ren) 的入口导航页。

## 技术栈

- **Vue 3** + **Vite** — 纯静态构建，无运行时依赖
- CSS 动效背景 + 打字机效果，零额外依赖

## 本地开发

```bash
git clone https://github.com/LockhartANR/my-landing.git
cd my-landing
npm install
npm run dev
```

浏览器打开 `http://localhost:5173`。

## 构建部署

```bash
npm run build    # 输出到 dist/
npm run preview  # 本地预览构建产物
```

构建产物 `dist/` 为纯静态文件，托管到任意 Web 服务器即可。配合 Nginx 反向代理实现多项目路由：

```
/           → my-landing（本首页）
/arknights/ → 明日方舟公招统计
/blog/      → 博客
```

## 许可

MIT License
