## 你好，我是 CaryHe-maker

武汉大学计算机学院 2024 级本科生，计算机科学与技术专业。目前主要在做两个方向：计算机视觉（全景视频里的目标跟踪）和 Agent 系统。

### 项目

**[Track360](https://github.com/CaryHe-maker/360-VideoTargetingSystem)** · 360° 全景视频单目标跟踪 · Python / PyTorch

全景图有接缝和形变，普通跟踪器直接用效果不好。Track360 每帧取一个跟随目标的局部视图交给 ARTrackV2，再把结果投回全景图，不重新训练模型。

- 360VOT 测试集（120 条序列）上 S<sub>dual</sub> 为 0.512，开启实验性的丢失找回后为 0.532；同一个模型直接在全景图上跟踪是 0.368，论文里最好的同类框架是 0.534
- RTX 4060 笔记本上约 37 FPS，提供命令行和 Python 接口
- 实验都记在评测日志里，包括没有成功的尝试；目标丢失后的找回目前效果有限，是接下来要做的部分
- 以上是 V2.0 开发分支的结果，尚未合并到 `main`

**[MultiAgentOS](https://github.com/CaryHe-maker/MultiAgentOS)** · 模块化的 Agent 编排与执行系统 · TypeScript

三人合作的项目，还在早期。设计上把业务推进（Workflow）和授权、调度、执行（Kernel）分开：模型只能提出动作，由 Kernel 决定是否执行；跨模块的数据都经过 Schema 校验。

- 第一个里程碑（M1）的目标是一个只读的仓库分析系统：Planner 和 CodeViewer 两个 Agent 接力，输出带代码来源的分析报告
- 目前完成的是架构文档、接口契约、定义目录和用 fake 组件跑通的装配链路，真实的 Agent 循环还在实现中，代码在 `feat/M1` 分支
- 我负责 Workflow、用户交互与 CLI、基础设施和测试工具

**[Ai-Desktop-Companions](https://github.com/CaryHe-maker/Ai-Desktop-Companions)** · 一个 Electron 写的 Windows 桌面宠物，点击角色打开对应 AI 服务的官方网页聊天。

### 联系

邮箱：1981033510@qq.com
