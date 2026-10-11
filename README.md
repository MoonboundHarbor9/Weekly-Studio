# Weekly Studio · 公开代码、私人课表版

这个项目是**空白**的 PWA 周课表，所有发布文件都不包含私人课程数据。

## GitHub Pages 部署

1. 解压项目 ZIP。访问 https://github.com/new ，新建名为 `weekly-studio` 的 **Public** 仓库。GitHub Free 的 Pages 发布通常需要 Public 仓库。
2. 在仓库 **Code → Add file → Upload files** 中上传**解压后的内容**（不是 ZIP 本身）：`index.html`、`manifest.webmanifest`、`service-worker.js`、`icons/` 三张 PNG 图标、`README.md`，以及可选的 `.nojekyll`。文件必须位于仓库根目录，`icons/` 保留子目录。
3. 在仓库 **Settings → Pages → Build and deployment**：Source 选择 **Deploy from a branch**；Branch 选择 `main`、`/(root)`，然后 Save。
4. 你的网页预计为 `https://你的用户名.github.io/weekly-studio/`，以 Pages 设置页给出的实际 URL 为准。GitHub Pages 网站默认对公众开放，仓库设为 Private 不代表网页会私有。

## iPhone 导入已有 22 条事项

1. **不要**上传 `weekly-timetable-backup.json` 到 GitHub。用私下的渠道将这个文件放入 iPhone 的「文件」App，例如在手机的 ChatGPT 里下载原始备份并保存到「文件」，或者通过 AirDrop / iCloud Drive 私下传输。
2. iPhone 的 Safari 打开已经发布的课表网址，先用「分享 → 添加到主屏幕 → 作为网页 App 打开」安装。
3. **从主屏幕启动课表 App**，点 **导入备份**（或空白日期下方的「从手机『文件』中导入备份」）。
4. 在 iPhone 文件选择界面里选择 `weekly-timetable-backup.json`，确认**替换当前事项**。当显示“成功导入 22 条事项”，就完成了。此操作只在你的 iPhone 上保存数据，不会上传到 GitHub。
5. 若要在电脑网页里也显示课程，在电脑网页中同样点击「导入备份」选择同一个 JSON；电脑和 iPhone 不自动同步。

**提示**：iOS 的主屏幕网页 App 通常拥有与 Safari 独立的存储，所以建议先添加主屏幕图标、**然后在该图标打开的 App 中导入**，免得只导入 Safari 造成主屏幕 App 仍然空白。

## 功能和数据保存

- 周一至周日；08:00–23:00；1 小时一格；多个重叠课程并排显示。
- 电脑鼠标拖选时段；手机单日视图、点击格子选开始时间，再在弹窗中修改结束时间。
- 点击课程编辑名称、地点、备注、时间和颜色。备注中的课程链接可点击。
- 导入/导出 JSON、打印、本地浏览器保存、离线缓存。
- 本地保存不等于云端备份；清除网站存储、删除 Web App 或某些系统清理情况可能丢失数据，**定期点“导出备份”**。
- 手机与电脑目前**不能自动同步**。如修改课程，请在修改后导出新 JSON 并在另一端导入（会替换对方当前事项）。

## 文件列表

```text
index.html               网页 UI 和编辑逻辑，不含真实课程
manifest.webmanifest     PWA 名称、启动模式和图标
service-worker.js        离线缓存（只缓存网页静态资源）
icons/icon-180.png       iPhone 图标
icons/icon-192.png       PWA 图标
icons/icon-512.png       PWA 图标
.nojekyll                静态页面发布设置
README.md                使用说明
```

本项目使用 HTML/CSS/JavaScript，无需编译工具或付费服务器。首次离线缓存需要先有一次正常联网访问。
