# Still Aura

**流韵 — Moments remain.**

Still Aura 是一款专注于精准调整、细腻色彩分级与个性化影像表达的照片编辑器。

我们相信，摄影创作并不止于按下快门的瞬间。Still Aura 致力于打造简洁、专注的数字暗房，让每一次调整都服务于创作意图。

## 品牌理念

**影像静止，感受犹存。**

摄影定格瞬间，但创作并不会随着快门落下而结束。

Still Aura 将后期处理视为摄影表达的延续，让摄影者能够有意识地塑造光线、影调与色彩，自由呈现自己的创作意图。

## 环境搭建

Still Aura 基于 **Tauri 2、React、TypeScript、Vite 和 Rust** 构建，支持 Windows 和 Android 平台。

### 环境要求

开始之前，请安装以下工具：

**通用环境要求**：

- [Node.js](https://nodejs.org/)（长期支持版 LTS）
- [Rust](https://rustup.rs/)（稳定版工具链）
- npm（随 Node.js 一同安装）

**Windows 平台**：

- [Microsoft C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/)（安装 **使用 C++ 的桌面开发** 工作负载）
- Microsoft Edge WebView2 运行时

**Android 平台**：

- [Android Studio](https://developer.android.com/studio)
- Android SDK、Platform Tools、Build Tools 和 Command-line Tools
- Android NDK
- JDK 17，或当前 Android Gradle 插件要求的兼容版本
- 已配置的 Android 模拟器，或开启 USB 调试的实体设备

进行 Android 开发前，请配置 `JAVA_HOME`、`ANDROID_HOME` 和 `NDK_HOME` 环境变量。

有关各平台的详细要求，请参阅 [Tauri 环境要求文档](https://v2.tauri.app/start/prerequisites/)。

### 项目结构

```text
still-aura/
├── src/
│   ├── app/                  # 应用初始化、路由
│   ├── components/           # 通用 UI
│   ├── features/
│   │   ├── library/          # 图片库
│   │   ├── editor/           # 编辑器
│   │   ├── adjustments/      # 调整工具
│   │   └── export/           # 导出
│   ├── hooks/
│   ├── services/             # Tauri 命令调用
│   ├── stores/               # 编辑状态
│   └── styles/
├── src-tauri/
│   ├── src/
│   │   ├── lib.rs
│   │   └── commands/
│   ├── capabilities/
│   ├── gen/android/          # Android 原生工程
│   ├── Cargo.toml
│   └── tauri.conf.json
├── crates/
│   └── still-aura-core/      # 独立 Rust 图像处理库
├── public/
├── LICENSE
├── README.md
├── package.json
└── pnpm-lock.yaml
```

### 安装依赖

```bash
npm ci
```

### Windows 开发

以开发模式启动桌面应用：

```bash
npm run tauri dev
```

构建 Windows 应用：

```bash
npm run tauri build
```

### Android 开发

安装所需的 Rust 编译目标：

```bash
rustup target add aarch64-linux-android
rustup target add armv7-linux-androideabi
rustup target add i686-linux-android
rustup target add x86_64-linux-android
```

初始化 Android 工程（仅首次配置时需要）：

```bash
npm run tauri android init
```

启动 Android 模拟器或连接实体设备，然后执行：

```bash
npm run tauri android dev
```

构建 Android 应用：

```bash
npm run tauri android build
```

正式发布 Android 应用前，需要配置应用签名。

### 常用命令

| 命令 | 说明 |
| --- | --- |
| `npm run dev` | 启动 Vite 开发服务器 |
| `npm run build` | 构建前端项目 |
| `npm run tauri dev` | 运行 Windows 桌面应用 |
| `npm run tauri build` | 构建 Windows 应用 |
| `npm run tauri android dev` | 运行 Android 应用 |
| `npm run tauri android build` | 构建 Android 应用 |

### 故障排查

如果 Android 构建失败，请确认已安装 Android SDK、NDK 和 JDK，并检查相关环境变量是否指向有效目录。

如果 Windows 构建失败，请确认已安装 MSVC C++ 构建工具和 WebView2 运行时。

如需更多帮助，请参阅 [Tauri 2 官方文档](https://v2.tauri.app/)。

## 开发路线图

Still Aura 正在持续开发中。我们的目标是为 Windows 和 Android 打造一款精准、简洁且富有表现力的照片编辑器。

本路线图用于跟踪主要功能的开发与发布进度。随着项目推进，功能优先级和版本计划可能调整。

### v0.1.0 — 基础架构

*搭建跨平台应用基础。*

- [ ] 初始化 Tauri 2、React、TypeScript 和 Rust
- [ ] 建立跨平台共享应用架构
- [ ] 配置 Windows 开发与构建流程
- [ ] 配置 Android 开发与构建流程
- [ ] 实现桌面端与移动端响应式布局
- [ ] 建立初步设计系统与深色主题
- [ ] 配置自动化构建与基础测试

### v0.2.0 — 图片库

*导入、浏览和管理照片。*

- [ ] 支持导入 JPEG 和 PNG 图片
- [ ] 集成原生文件与照片选择器
- [ ] 显示图片缩略图和元数据
- [ ] 实现图片浏览与选择
- [ ] 提供缩放、平移和适应屏幕功能
- [ ] 实现基础图片缓存

### v0.3.0 — 基础图像编辑

*构建实用的图片编辑工具，完善基础图像处理体验。*

- [ ] 实现图片裁剪与自定义宽高比
- [ ] 支持图片旋转、翻转与拉直
- [ ] 支持调整图片尺寸与分辨率
- [ ] 实现文字水印与图片水印
- [ ] 支持水印位置、大小、透明度调整
- [ ] 实现图片边框与留白功能
- [ ] 支持边框颜色、宽度与比例调整
- [ ] 实现多图拼接（横向、纵向、网格布局）
- [ ] 支持拼接间距、背景颜色与排列方式调整
- [ ] 实现编辑效果实时预览
- [ ] 支持导出 JPEG 和 PNG 图片

### v0.4.0 — 基础影调调整

*引入摄影后期的核心调整能力，实现对光线与色彩的精细控制。*

- [ ] 实现曝光与亮度调整
- [ ] 实现对比度调整
- [ ] 实现高光与阴影调整
- [ ] 实现白色色阶与黑色色阶调整
- [ ] 实现色温与色调调整
- [ ] 实现饱和度与自然饱和度调整
- [ ] 实现清晰度与纹理调整
- [ ] 支持调整参数实时预览
- [ ] 实现编辑前后效果对比
- [ ] 支持撤销与重做操作

### v0.5.0 — 非破坏性编辑工作流

*保留原始影像，让每一次编辑都可以自由调整与恢复。*

- [ ] 构建非破坏性图像调整流水线
- [ ] 支持保存与恢复编辑参数
- [ ] 引入项目文件或 Sidecar 伴随文件
- [ ] 实现编辑历史记录
- [ ] 支持创建与应用预设
- [ ] 完善 JPEG 和 PNG 导出功能
- [ ] 支持自定义导出质量与分辨率

### v0.6.0 — RAW 处理

*建立数字暗房的核心能力。*

- [ ] 集成 RAW 解码流水线
- [ ] 支持部分相机 RAW 格式
- [ ] 实现去马赛克处理与白平衡
- [ ] 引入相机色彩配置文件
- [ ] 改进高光恢复能力
- [ ] 增加影调曲线
- [ ] 支持直方图显示
- [ ] 改进高位深图像处理

### v0.7.0 — 高级色彩调整

*更精细地控制色彩与影调。*

- [ ] RGB 综合曲线与独立通道曲线
- [ ] HSL 色彩调整
- [ ] 色彩分级控制
- [ ] 色彩校准工具
- [ ] 锐化与降噪
- [ ] 支持镜头校正
- [ ] 改进色彩管理与导出一致性

### v0.8.0 — 局部调整

*实现更精准的选择性编辑。*

- [ ] 线性渐变与径向渐变蒙版
- [ ] 画笔蒙版
- [ ] 亮度范围与颜色范围蒙版
- [ ] 对蒙版区域进行独立调整
- [ ] 蒙版叠加显示与可视化
- [ ] 优化交互式蒙版性能

### v0.9.0 — 性能与工作流

*完善各平台的编辑体验。*

- [ ] 在支持的平台上实现 GPU 加速图像处理
- [ ] 优化大尺寸图像渲染与缓存
- [ ] 改进 Android 内存管理
- [ ] 支持批量导出
- [ ] 增加桌面端键盘快捷键
- [ ] 改进 Android 触摸与手势操作
- [ ] 扩展自动化测试与兼容性覆盖

### v0.10.0 — 测试版

*为稳定公开发布做好准备。*

- [ ] 完成主要功能集成
- [ ] 提升稳定性与错误处理能力
- [ ] 开展 Windows 和 Android 兼容性测试
- [ ] 检查无障碍支持与本地化
- [ ] 完善应用图标与品牌视觉
- [ ] 发布测试版构建与更新说明
- [ ] 修复阻碍发布的问题

### v1.0.0 — 正式版

*发布 Still Aura 的首个稳定版本。*

- [ ] 发布 Windows 稳定版本
- [ ] 发布 Android 稳定版本
- [ ] 发布完整用户文档
- [ ] 公布支持的 RAW 格式与相机兼容性信息
- [ ] 完善非商业许可证文档
- [ ] 建立维护与安全更新机制

### 版本发布记录

| 版本 | 开发阶段 | 发布时间 |
| ------- | --- | --- |
| v0.1.0 | 工程基础 | |
| v0.2.0 | 图片图库 | |
| v0.3.0 | 基础图像编辑：裁剪、水印、边框、拼接 | |
| v0.4.0 | 基础影调调整：曝光、亮度、色彩 | |
| v0.5.0 | 非破坏性编辑工作流 | |
| v0.6.0 | RAW 影像处理 | |
| v0.7.0 | 高级色彩调整 | |
| v0.8.0 | 局部调整 | |
| v0.9.0 | 性能优化与工作流 | |
| v0.10.0 | Beta 测试 | |
| v1.0.0 | 正式稳定版 | |

### 路线图规划

路线图中的内容属于规划目标，并非确定的发布承诺。只有功能完成开发、通过测试并包含在已发布版本中，才会被标记为完成。

## 许可证

Still Aura 采用 [**PolyForm Noncommercial License 1.0.0**](PolyForm%20NonCommercial%201.0.0.txt) 许可证。

本项目采用源码可见（Source-Available）模式，并非采用 OSI 认可的开源许可证。

在遵守许可证条款的前提下，允许个人使用、学习源代码、修改和再分发等非商业行为。

**本项目的公开许可证不授权商业使用。**

以下商业用途需要另行获得授权：

- 为付费客户编辑照片。
- 在商业摄影工作室中使用 Still Aura。
- 将 Still Aura 用于收费摄影或影像编辑服务。
- 将 Still Aura 集成到商业软件产品中。
- 以商业目的分发或销售 Still Aura 及其修改版本。

根据许可证条款，部分组织享有额外的使用权限。所有许可范围均以许可证完整正文为准。

完整条款请参阅 [LICENSE](PolyForm%20NonCommercial%201.0.0.txt)。

---

**Still Aura · 流韵**.

*Moments remain.*
