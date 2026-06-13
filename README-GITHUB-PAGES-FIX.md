# GitHub Pages 修正版说明

本包已将 Vite 构建产物中的绝对路径改为相对路径，适合部署到 GitHub Pages 的项目子路径，例如：

`https://<username>.github.io/<repo>/`

部署方式：

1. 将本目录下的所有文件作为 GitHub Pages 发布目录。
2. 不要只把外层 zip 上传后直接访问。GitHub Pages 发布目录中需要能直接看到 `index.html`、`assets/`、`manifest.webmanifest`、`sw.js`。
3. 如果你之前打开过白屏版本，请在浏览器开发者工具 Application / Service Workers 中 unregister 旧 Service Worker，并清空缓存后再访问。

已修正：

- `index.html` 中 `/assets/...` 改为 `./assets/...`
- `manifest.webmanifest` 中 `start_url` 和 `scope` 改为 `./`
- JS 中 `navigator.serviceWorker.register("/sw.js")` 改为 `./sw.js`
- `sw.js` 中缓存清单和 fallback 改为相对路径
