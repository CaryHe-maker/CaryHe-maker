<div align="center">

# CaryHe-maker

**武汉大学 计算机学院 · 计算机科学与技术 · 2024 级本科生**

计算机视觉 · Agent 系统

[![Email](https://img.shields.io/badge/Email-1981033510%40qq.com-2b6cb0?logo=maildotru&logoColor=white)](mailto:1981033510@qq.com)
[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)](#)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?logo=pytorch&logoColor=white)](#)
[![C++](https://img.shields.io/badge/C%2B%2B-00599C?logo=cplusplus&logoColor=white)](#)

</div>

---

## 项目方向

- **计算机视觉**：全景（360°）视频中的单目标跟踪
- **Agent 系统**：多 Agent 的编排、执行与权限控制

## 项目

### [Track360](https://github.com/CaryHe-maker/360-VideoTargetingSystem) — 360° 全景视频单目标跟踪

`Python` `PyTorch` `OpenCV`

全景图存在接缝和形变，普通跟踪器直接使用效果不佳。Track360 在球面上表示目标，每帧取一个跟随目标的局部视图交给 ARTrackV2，再将结果投回全景图，无需重新训练模型。

最新版本 [v2.1.0](https://github.com/CaryHe-maker/360-VideoTargetingSystem/releases/tag/v2.1.0) 加入长时跟踪的轻代价档，平均每帧约 1.1 次模型前向，包括四项：
- 丢失判定与找回：用相对状态机判断何时不可信，再放大搜索；
- 相机旋转补偿；
- 目标偏离视图中心时的二次定位；
- 用 DINOv2 识别相似物体，避免在干扰物上误放行。

| 360VOT 测试集（120 条序列） | S<sub>dual</sub> | 丢失率 | FPS（RTX 4060 Laptop） |
|---|:---:|:---:|:---:|
| 同一模型直接在全景图上跟踪（对照） | 0.368 | 0.532 | 20.3 |
| Track360 默认配置 | 0.512 | 0.313 | 36.6 |
| Track360 V2.1 轻代价档（`--preset long_term_light`） | 0.528 | 0.309 | 约 25 |
| 论文中最好的同类框架（AiATrack-360） | 0.534 | — | — |

- 提供命令行、Python 接口和权重自动下载；所有模型都可以本地部署。
- 评测流程：
  - 开发集分成调参用和验证用两部分，与官方测试集不重合；
  - 每个配置跑 5 个随机种子，结果附配对置信区间；
  - 消融显示四项改动各有贡献；
  - 评测日志记录了全部 85 组实验，包括未采用的方案。
- 局限：轻代价档在三个数据集上都高于默认配置（+0.015 到 +0.038），但测试集上的置信区间含 0；跳转到错误物体仍是主要损失，是下一阶段的工作。

### [MultiAgentOS](https://github.com/CaryHe-maker/MultiAgentOS) — 模块化的 Agent 编排与执行系统

`TypeScript` `Node.js` `pnpm monorepo`

三人协作项目，处于早期阶段。系统将业务推进（Workflow）与授权、调度、执行（Kernel）分离：模型只能提出动作，是否执行由 Kernel 裁决；跨模块数据均经过运行时 Schema 校验。

- **当前里程碑（M1）**：只读的仓库分析系统，由 Planner 与 CodeViewer 两个 Agent 接力，输出带代码来源的结构化报告
- **进度**：已完成架构文档、接口契约、Agent / Tool 定义目录，以及基于 fake 组件的端到端装配链路；真实的 Agent 循环仍在实现中（`feat/M1` 分支）
- **我的分工**：Workflow、kernel、lease、用户交互与 CLI、基础设施（通信、存储、装配）和测试工具

### 其他

- [Ai-Desktop-Companions](https://github.com/CaryHe-maker/Ai-Desktop-Companions)：基于 Electron 的 Windows 桌面宠物，点击角色即可打开对应 AI 服务的官方网页进行对话。

## 联系方式

📫 1981033510@qq.com
