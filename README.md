# 戴夫清单 · PWA 版

桌面版（Neutralino）的 iPhone 移植版：单页 PWA，数据存 localStorage，支持 JSON 导出/导入备份。
主屏幕独立模式下数据持久（不受 Safari 7 天清除策略影响），Service Worker 缓存后可离线使用。

## 本地预览

```bash
cd davelist-pwa
python -m http.server 8123
# 浏览器打开 http://localhost:8123
```

注意：Service Worker 要求 http(s) 环境或 localhost，直接双击 index.html（file://）无法注册 SW。

## 部署到 GitHub Pages（免费 HTTPS，iPhone 安装的前提）

1. 在 GitHub 新建一个**公开**仓库（如 `davelist-pwa`）
2. 推送本目录全部内容：

```bash
cd davelist-pwa
git init && git add -A && git commit -m "davelist pwa"
git remote add origin https://github.com/<你的用户名>/davelist-pwa.git
git push -u origin main
```

3. 仓库 Settings → Pages → Source 选 `main` 分支 `/ (root)` → Save
4. 等 1-2 分钟，得到地址：`https://<你的用户名>.github.io/davelist-pwa/`

## iPhone 安装（添加到主屏幕）

1. iPhone 用 Safari 打开上面的地址
2. 点底部「分享」按钮 → 「添加到主屏幕」
3. 确认后桌面出现「戴夫清单」图标，打开即全屏独立 App，无 Safari 地址栏

## 数据备份

- 右上角 `⋯` 菜单：
  - **导出到文件**：下载 `davelist-backup-日期.json`（存到「文件」App）
  - **复制到剪贴板**：粘贴到微信/备忘录随时备份
  - **从文件导入**：选 json 文件恢复，导入前会确认覆盖
- 换手机 / 重装前先导出一次即可

## 桌面版数据迁移

桌面版数据键同为 `davelistTasksV1`，格式相同。桌面版右上角 `⋯` 菜单同样支持导出（若旧版无此菜单，可从
`%LOCALAPPDATA%` 下 Neutralino 存储中取出，或直接在 iPhone 上重建清单）。
