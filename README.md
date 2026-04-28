# 词元AI生图工坊

界面

![](https://raw.githubusercontent.com/lxj5820/nano-banana/refs/heads/main/%E7%95%8C%E9%9D%A2.png)

基于 AI 的在线图片生成工具，支持文生图、图生图、合集管理与批量下载。

![Platform](https://img.shields.io/badge/Platform-Web-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Version](https://img.shields.io/badge/Version-V9.0-orange)

## 功能特性

### 图片生成
- 多模型支持：`nano-banana`、`nano-banana-2`、`nano-banana-pro`、`GPT-Image-2`、`GPT-Image-2-All`、`Doubao-Seedream-5.0`、`Doubao-Seedream-4.5`、`Doubao-Seedream-4.0`
- 多画质选项：1K / 2K / 3K / 4K（根据模型动态可选）
- 可调节生成数量（1-4张）
- 多种画幅比例（各模型支持不同比例，详见下方模型对照表）
- 多任务并发生成
- 生成进度动画（构思 → 绘制 → 渲染 → 完成）

### 模型对照表

| 显示名称 | API 模型名 | 图生图 | 画质 | 支持比例 |
|---|---|---|---|---|
| nano-banana | gemini-2.5-flash-image-preview | ✗ | 1K | 1:1, 4:3, 16:9, 9:16, 3:4, 2:3, 3:2, 4:5, 5:4, 21:9 |
| nano-banana-2 | gemini-3.1-flash-image-preview | ✓ | 1K, 2K, 4K | 1:1, 1:4, 1:8, 2:3, 3:2, 3:4, 4:1, 4:3, 4:5, 5:4, 8:1, 9:16, 16:9, 21:9 |
| nano-banana-pro | gemini-3-pro-image-preview | ✓ | 1K, 2K, 4K | 1:1, 4:3, 16:9, 9:16, 3:4, 2:3, 3:2, 4:5, 5:4, 21:9 |
| GPT-Image-2 | gpt-image-2 | ✓ | 1K | auto, 1:1, 2:3, 3:2, 4:3, 3:4, 16:9, 9:16 |
| GPT-Image-2-All | gpt-image-2-all | ✓ | 1K | auto, 1:1, 2:3, 3:2, 4:3, 3:4, 16:9, 9:16 |
| Doubao-Seedream-5.0 | doubao-seedream-5-0-260128 | ✓ | 2K, 3K | 1:1, 4:3, 3:4, 16:9, 9:16, 3:2, 2:3, 21:9 |
| Doubao-Seedream-4.5 | doubao-seedream-4-5-251128 | ✓ | 2K, 4K | 1:1, 4:3, 3:4, 16:9, 9:16, 3:2, 2:3, 21:9 |
| Doubao-Seedream-4.0 | doubao-seedream-4-0-250828 | ✓ | 1K, 2K, 4K | 1:1, 4:3, 3:4, 16:9, 9:16, 3:2, 2:3, 21:9 |

### 参考图模式
- 拖拽、点击上传或 Ctrl+V 快捷粘贴
- 支持多张参考图，左上角序号标记
- 图生图模式（不支持图生图的模型会提示切换）
- 参考图自动压缩（Gemini 最大 1024px，GPT-Image 最大 2048px）
- 重叠对比滑块：参考图与生成结果叠加对比，支持鼠标/触摸拖拽

### 图库管理
- IndexedDB 本地持久化存储
- 合集分类管理（创建/删除合集，图片批量加入合集）
- 多选模式：批量选择、批量加入合集、批量删除
- 放大查看（滚轮缩放、拖拽平移、双击切换、触摸手势）
- 复用参数：从历史记录复用提示词、比例、模型、画质、参考图
- 重试失败：一键重试生成失败的记录
- 单张下载、批量下载为 ZIP 包
- 一键清空图库
- 骨架屏加载效果，分批渲染（懒加载）

### 用户体验
- 生成状态实时反馈（占位图 → 进度动画 → 完成/失败）
- 可调节侧边栏宽度
- 可调节工具栏高度（拖拽手柄）
- 可调节提示词输入框高度
- 内置提示词指南
- 页面离开提醒（生成中时）
- 响应式设计，适配桌面端与移动端
- 微信社群入口（悬停显示二维码）

## 快速开始

### 配置 API Key
1. 点击右上角「设置」按钮
2. 输入你的 API Key（至少 20 字符）
3. 点击保存

API Key 获取地址：[newapi.asia](https://newapi.asia/register?channel=c_ripg6oed)

### 生成图片
1. 输入提示词（最多 2000 字符）
2. （可选）添加参考图
3. 选择模型、画质、比例和生成数量
4. 点击「生成」按钮

### 快捷操作

| 操作 | 方式 |
|------|------|
| 粘贴图片 | Ctrl+V |
| 放大查看 | 点击放大按钮 / 双击图片 |
| 缩放图片 | 滚轮滚动 |
| 平移图片 | 拖拽（需放大后） |
| 关闭查看 | ESC / 点击空白处 |
| 下载单张 | 点击下载按钮 |
| 批量下载 | 历史区「下载」按钮 |
| 复用设置 | 点击复用按钮 |
| 重试失败 | 点击重试按钮 |
| 多选管理 | 点击「管理」按钮 |

## 技术栈

- **前端**：HTML5、CSS3、JavaScript（单文件应用，无框架）
- **存储**：IndexedDB（NanoBananaDB）+ localStorage
- **AI 接口**：
  - Gemini 系列：`newapi.asia/v1beta/models`（URL 参数认证）
  - Doubao/GPT-Image 系列：`newapi.asia/v1`（Bearer Token 认证）
- **压缩**：JSZip 3.10.1

## 项目结构

```
banananet/
├── index.html    # 主页面（单文件应用）
├── 界面.png      # 界面截图
├── 社群.png      # 微信社群二维码
└── README.md     # 项目文档
```

## 提示词技巧

**文生图推荐结构**：
```
主体（数量/特征）+ 动作 + 场景（地点/时间/天气）+ 风格/媒介 + 构图/相机 + 光影/色彩 + 关键细节 + 约束条件
```

**图生图编辑时**：
```
保持（不可改变）+ 改变（修改什么）+ 如何（风格/强度/方向）+ 约束条件
```

## 浏览器兼容性

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## License

MIT License
