# 图片尺寸工坊

双击 `index.html` 或 `打开图片尺寸工坊.command`，使用现代 Chrome / Safari 浏览器。无需安装依赖、启动服务或联网。

1. 拖入图片或点击选择，支持同时添加多张。
2. 设置像素宽高和 PNG、JPG、WebP 格式。
3. 比例不同时，先选择「手动裁剪」，拖动画面、调节放大比例，点击「确认当前裁剪」；或明确选择「完整保留并补边」。没有拉伸选项。
4. 点击「下载当前图片」。多张图片在列表中逐张确认并下载。

修改目标尺寸会使所有图片的旧确认失效。导出使用新文件名，由浏览器管理下载位置，不修改原始文件。JPG 透明区域使用白底；PNG/WebP 默认保留透明。补边背景选择对 JPG 的透明区域也生效。

限制：每次最多 50 张、每张不超过 50 MB / 8000 万像素；输出宽高 1–8192，总面积不超过 3200 万像素。HEIC、RAW、SVG 不支持，GIF 等动图只导出一帧；颜色和 EXIF 等元数据不保留，不适用于印刷色彩管理。大图建议少量处理，以减少浏览器内存占用。

## 下载给别人使用

在 GitHub 仓库点击 **Code → Download ZIP**，解压后用浏览器打开 `index.html`。Mac 也可以双击 `打开图片尺寸工坊.command`。仅使用工具无需 Node.js 或 Playwright。

## 开发验证

浏览器测试需要 Node.js、Playwright 和已安装的 Chrome。准备好 Playwright 后运行：

```bash
node tests/browser.cjs
```

如果 Playwright 安装在其他位置，可设置 `PLAYWRIGHT_MODULE` 为其模块路径。测试使用生成的红蓝图片，不读取个人图片；实际验证 PNG 尺寸与裁剪像素、JPG 白色补边、WebP 文件头和比例确认流程。测试会生成 `preview.png`（不纳入 Git）。当前已验证 macOS Chrome，其他系统及 Safari 尚待验证。
