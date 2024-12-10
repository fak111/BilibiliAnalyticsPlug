当然，以下是您提供的内容经过结构化和美化后的Markdown文档。这将帮助您更清晰地展示项目内容，便于学生或其他读者理解和参考。

---

# Bilibili 数据统计插件

## 视频参考

- **Bilibili 视频**: [cursor从零到1实现，仅需两句话就可以实现一个插件~](https://www.bilibili.com/video/BV1yYq3Y6Emb/?share_source=copy_web&vd_source=fed0463c5e2f2a5d15192f02da148180)

## 项目文档

- **项目文档**: [点击这里访问项目文档](https://vwpecqie443.feishu.cn/wiki/DL2SwwlFwixkgnk7N7Mc3TiBnNg?from=from_copylink)

## 插件描述

### 目标

我想做一个 **Bilibili 数据统计的插件**，能够精准地统计以下数据：

- **播放量**
- **点赞数**
- **投币数**
- **分享次数**
- **收藏次数**
- **转发次数**

这些数据将被清晰地展示出来，方便用户直观地了解视频的受欢迎程度和传播效果。

## 网页格式示例

### 正确的网页格式

请参考以下HTML结构，插件将基于此格式进行数据捕获和统计：

```html
<h1 
  data-title="程序员第一次用Cursor：真的太好用了，宇宙级AI编程解决方案！feat.Cursor 上手体验" 
  title="程序员第一次用Cursor：真的太好用了，宇宙级AI编程解决方案！feat.Cursor 上手体验" 
  class="video-title special-text-indent" 
  data-v-1be0114a="">
  程序员第一次用Cursor：真的太好用了，宇宙级AI编程解决方案！feat.Cursor 上手体验
</h1>
<div class="view-text" data-v-aed3e268="">5.8万</div>
<span class="video-like-info video-toolbar-item-text">1666</span>
<span class="video-coin-info video-toolbar-item-text" data-v-331e415b="">648</span>
<span class="video-fav-info video-toolbar-item-text" data-v-b42ec39c="">3622</span>
```

### 说明

- `<h1>` 标签包含视频标题及相关数据属性。
- `<div class="view-text">` 显示视频的播放量。
- `<span>` 标签分别显示点赞数、投币数和收藏数。

## 插件效果图

![插件效果图](https://github.com/user-attachments/assets/7d87681e-6fec-4fd2-ac59-6b9bfdd21249)

## 目录结构

确保您的项目目录结构如下，以便浏览器能够正确加载扩展程序：

```
bilibili-stats/
├── manifest.json
├── popup/
│   ├── popup.html
│   ├── popup.css
│   └── popup.js
├── scripts/
│   └── content.js
└── icons/
    ├── icon16.png
    ├── icon48.png
    └── icon128.png 
```

### 文件说明

- **manifest.json**: 扩展程序的配置文件。
- **popup/**: 弹出窗口相关文件，包括HTML、CSS和JavaScript。
- **scripts/**: 内容脚本，用于在Bilibili页面上捕获和处理数据。
- **icons/**: 扩展程序图标，分别用于不同的显示尺寸。

## 常见问题及解决方案

### 无法加载扩展程序

**错误信息**:
```
Could not load icon 'icons/icon16.png' specified in 'action'.
无法加载清单。
```

**解决方案**:

1. **检查图标文件路径**:
   - 确保 `manifest.json` 中指定的图标路径与实际目录结构匹配。
   - 例如：
     ```json
     {
       "action": {
         "default_popup": "popup/popup.html",
         "default_icon": {
           "16": "icons/icon16.png",
           "48": "icons/icon48.png",
           "128": "icons/icon128.png"
         }
       },
       "icons": {
         "16": "icons/icon16.png",
         "48": "icons/icon48.png",
         "128": "icons/icon128.png"
       }
     }
     ```

2. **验证图标文件存在性**:
   - 确保 `icons/` 文件夹中包含 `icon16.png`、`icon48.png` 和 `icon128.png` 文件。
   - 确保这些文件是有效的 PNG 格式，且尺寸分别为 16x16、48x48 和 128x128 像素。

3. **使用正确的命令转换图标** (Windows 系统):
   - 在Windows上，使用 `magick` 命令而不是 `convert`。
   - 示例命令：
     ```powershell
     magick icon.svg -resize 16x16 icons/icon16.png
     magick icon.svg -resize 48x48 icons/icon48.png
     magick icon.svg -resize 128x128 icons/icon128.png
     ```

4. **重新加载扩展程序**:
   - 在浏览器的扩展管理页面，移除旧的扩展，然后重新加载已解压的扩展程序。

### 安装ImageMagick并转换图标

1. **安装 ImageMagick**:
   - 下载并安装 [ImageMagick](https://imagemagick.org/script/download.php#windows)。
   - 确保在安装过程中选中“Add application directory to your system path”选项。

2. **转换 SVG 图标为 PNG**:
   - 打开 PowerShell，并导航到项目目录：
     ```powershell
     cd E:\web_front\B_data_Sta
     ```
   - 使用 `magick` 命令进行转换：
     ```powershell
     magick icon.svg -resize 16x16 icons/icon16.png
     magick icon.svg -resize 48x48 icons/icon48.png
     magick icon.svg -resize 128x128 icons/icon128.png
     ```

3. **验证转换结果**:
   - 确保 `icons/` 文件夹中生成了 `icon16.png`、`icon48.png` 和 `icon128.png` 文件，并且它们的尺寸正确。

## 发布扩展程序

### 准备工作

1. **验证所有文件**:
   - 确保 `manifest.json` 文件中所有路径和文件名正确无误。
   - 确保所有图标文件存在且格式正确。

2. **测试扩展程序**:
   - 在本地浏览器中测试扩展程序的功能，确保数据统计和展示正常工作。

### 发布步骤

1. **打包扩展程序**:
   - 在扩展管理页面，选择“打包扩展程序”选项。
   - 选择项目目录，生成 `.zip` 文件。

2. **提交到浏览器扩展商店**:
   - **Chrome**: 前往 [Chrome Web Store Developer Dashboard](https://chrome.google.com/webstore/developer/dashboard) 提交扩展程序。
   - **Firefox**: 前往 [Firefox Add-ons Developer Hub](https://addons.mozilla.org/en-US/developers/) 提交扩展程序。

3. **填写必要信息**:
   - 提供扩展程序的详细描述、截图和其他必要信息。

4. **审核与发布**:
   - 等待浏览器商店的审核，通过后扩展程序将正式上线。

## 总结

通过上述步骤，您可以成功构建、调试和发布一个Bilibili数据统计插件。确保目录结构和文件配置正确，是确保扩展程序正常运行的关键。如果在操作过程中遇到其他问题，欢迎随时提问！

---

希望以上内容能够帮助您更好地组织和展示项目。如果有任何进一步的问题或需要更多帮助，请随时联系我！
