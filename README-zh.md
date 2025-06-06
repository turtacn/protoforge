# Protoforge

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Contribution Guide](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](./CONTRIBUTING.md)
[![English Document](https://img.shields.io/badge/lang-English-blue.svg)](./README.md)

**Protoforge: 一个企业级的、Go 原生的多智能体 AI 系统构建、编排与扩展框架。**

## 项目简介

Protoforge 是一个开源框架，旨在赋能开发者、中小企业（SME）和独立软件供应商（ISV）构建复杂且可靠的 AI 驱动应用。它为创建由多个智能体协同工作的复杂工作流，提供了一个健壮、可扩展且安全的基础。

Protoforge 的诞生是为了应对 AI 智能体领域对生产级、Go 原生解决方案的迫切需求。它融合了 LangChain、Microsoft AutoGen 等业界领先平台的成熟思想，并结合了 Golang 语言本身所具备的高性能、高并发和简洁性优势。

[阅读英文版文档](./README.md)。

## 核心痛点与解决方案

当前 AI 智能体框架的生态虽然活跃，但也呈现出碎片化的状态。许多强大的工具主要基于 Python 实现，这为企业级应用（尤其是以 Go 为技术栈核心的团队）带来了挑战。主要痛点包括：

* **性能瓶颈**：Python 的全局解释器锁（GIL）限制了单节点上 I/O 密集型和计算密集型任务的真正并行能力。
* **集成复杂性**：将基于 Python 的 AI 系统集成到现有的 Go 企业级架构中，过程可能繁琐且低效。
* **安全与治理缺失**：许多开源工具需要投入大量精力才能增加企业级的安全性、多租户和合规性功能。
* **学习曲线陡峭**：使用现有模型来编排复杂的、有状态的多智能体协作流程，可能相当困难。

**Protoforge 通过以下方式应对这些挑战：**

* **Go 原生性能**：从零开始使用 Golang 构建，确保高并发、低延迟和高效的资源利用。
* **无缝集成**：为简化与现有企业系统的集成而设计，提供对 gRPC 和 REST API 的一等支持。
* **企业级与安全性**：私有化部署、基于角色的访问控制（RBAC）、多租户和详细的审计日志是其核心架构的一部分。
* **先进的编排引擎**：一个受 LangGraph 启发的、强大的基于图的工作流引擎，允许定义、可视化并执行复杂的、有状态的、可循环的智能体工作流。
* **可视化与低代码工具支持**：其后端经过精心设计，能够为一个可视化的、拖拽式的界面（类似 Flowise/LangFlow）提供支持，极大地降低了构建和管理智能体工作流的技术门槛。

## 主要功能特性

* **模块化与可扩展的插件架构**：轻松扩展新功能，如新的大语言模型（LLM）、向量数据库、工具（API、数据库）和记忆后端。
* **多智能体协作**：设计和编排复杂的多智能体系统，使智能体能够协同工作、委派任务并完成复杂目标。支持群聊、分层任务拆解等多种协作模式。
* **基于图的工作流引擎**：将智能体交互定义为有状态的图，从而实现循环、反思和“人在回路”等高级功能。
* **统一的 API 层**：通过一致且强大的 API 与框架交互，同时支持 gRPC（追求性能）和 REST（确保广泛兼容性）。
* **丰富的数据与检索集成（RAG）**：内置对高级“检索增强生成”模式的支持，并提供受 LlamaIndex 启发的灵活索引和检索策略。
* **完整的可观测性**：开箱即用地支持结构化日志、监控指标（Prometheus）和分布式追踪（OpenTelemetry），方便您监控和调试系统。
* **内置安全与知识产权保护**：为本地/私有云部署而设计，其功能可确保数据隐私，并有助于管理代码生成中的知识产权问题。
* **可视化工作流构建器支持**：所有核心逻辑都通过 API 暴露，旨在为低代码、可视化的工作流编辑器提供动力。

## 架构概览

Protoforge 基于一个清晰的、分层的架构，该架构实现了关注点分离，并提升了模块化和可测试性。

![架构图](https://github.com/turtacn/protoforge/raw/main/docs/assets/architecture_zh.png)

关键分层如下：
1.  **展现层（Presentation Layer）**：通过 gRPC、REST API 和 WebSocket 连接暴露系统功能。它是所有外部客户端（包括命令行工具和可视化 UI）的入口点。
2.  **应用层（Application Layer）**：包含核心业务逻辑和用例实现。它负责编排领域实体以执行任务，例如执行一个工作流或管理智能体。
3.  **领域层（Domain Layer）**：框架的心脏。它定义了核心概念、实体和接口，如 `Agent`、`Tool`、`Workflow` 和 `Message`。该层完全独立于任何外部技术。
4.  **基础设施层（Infrastructure Layer）**：为领域层中定义的接口提供具体实现。这包括针对 LLM 客户端、数据库、向量存储、日志记录器和其他外部服务的适配器。

想深入了解我们的架构、组件设计和技术决策，请参阅我们的[**架构设计文档 (`docs/architecture.md`)**](./docs/architecture.md)。

## 快速开始

*（本部分将在初始代码库可用后，更新包含构建、安装和运行的详细说明。）*

### 环境要求

* Go 1.20.2+
* Docker & Docker Compose
* （其他依赖项将在此处列出）

### 构建与运行

```bash
# 克隆仓库
git clone https://github.com/turtacn/protoforge.git
cd protoforge

# (构建和运行命令将在这里补充)
````

## 贡献指南

我们欢迎来自社区的任何贡献！无论您是想修复错误、添加新功能还是改进文档，我们都非常感谢您的帮助。请阅读我们的[**贡献指南 (`CONTRIBUTING.md`)**](CONTRIBUTING.md)来开始。

## 许可证

Protoforge 采用 [MIT 许可证](LICENSE)。