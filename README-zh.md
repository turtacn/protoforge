# ProtoForge

*面向自主代码生成、产品原型设计、迭代开发和知识产权保护的开源AI智能体框架 — 由可组合LLM智能体驱动，专为私有化全栈研发工作流而设计。*

[English Version | 英文版本](README.md)

## 项目概述

ProtoForge是一个专为中小企业（SME）和独立软件供应商（ISV）设计的综合性AI智能体框架，旨在加速产品开发生命周期。基于Go语言核心构建，ProtoForge为自主代码生成、快速原型设计和知识产权保护提供安全、可扩展的企业级解决方案。

### 核心痛点解决

- **碎片化开发流程**：传统研发过程在原型设计、开发和知识产权保护之间缺乏无缝集成
- **AI集成受限**：现有框架无法为敏感代码生成提供企业级安全性和合规性
- **扩展性约束**：大多数AI智能体框架在并发多智能体编排和水平扩展方面存在困难
- **知识产权保护缺口**：当前解决方案缺乏内置的代码溯源跟踪和许可证合规机制
- **复杂的多语言集成**：难以在不同编程语言和平台间创建统一的工作流

### 核心价值主张

ProtoForge通过提供以下能力转变传统研发工作流：

1. **自主代码生成**：内置质量保证和测试的AI驱动代码创建
2. **智能原型设计**：具备迭代优化能力的快速原型开发
3. **知识产权保护框架**：全面的许可证扫描、代码水印和溯源跟踪
4. **企业级安全**：基于角色的访问控制和审计日志的私有化部署
5. **可组合智能体架构**：支持自定义智能体工作流和集成的模块化设计

## 主要功能特性

### 🚀 **三级火箭研发流程**
- **第一级**：基于AI辅助设计和验证的原型生成
- **第二级**：具备自动化测试和代码审查的迭代开发
- **第三级**：包含许可证合规和代码归属的知识产权保护

### 🛡️ **安全优先架构**
- 内置安全智能体，实现自主威胁检测和响应
- 具备加密通信的私有化部署
- 基于角色的访问控制（RBAC）和全面审计跟踪
- 支持GDPR、ISO 27001等行业标准的合规框架

### 🔧 **可扩展智能体框架**
- 支持自定义工具和集成的插件式架构
- Go核心配合Python/JavaScript扩展的多语言支持
- 具备拖拽界面的可视化工作流设计器
- 用于无缝集成的RESTful API和gRPC接口

### 📊 **企业级可观测性**
- 实时监控和性能指标
- 复杂智能体工作流的分布式追踪
- 具备结构化事件关联的集中化日志
- 自定义仪表板和告警系统

## 架构概览

ProtoForge采用面向可扩展性和可维护性的分层微服务架构：

```mermaid
graph TD
    %% 系统架构概览图
    subgraph UI[用户界面层（User Interface Layer）]
        A1[Web控制台（Web Console）] 
        A2
我将继续完成README-zh.md文件的内容，并接着完成任务二的架构设计文档。

### 继续README-zh.md内容

```markdown
        A2[CLI工具（CLI Tools）]
        A3[可视化编辑器（Visual Editor）]
    end

    subgraph API[API网关层（API Gateway Layer）]
        B1[REST API网关（REST Gateway）]
        B2[gRPC服务（gRPC Services）]
        B3[认证授权（Auth & Authorization）]
    end

    subgraph CORE[核心引擎层（Core Engine Layer）]
        C1[代理编排器（Agent Orchestrator）]
        C2[工作流引擎（Workflow Engine）]
        C3[代码生成器（Code Generator）]
    end

    subgraph AGENT[智能体层（Agent Layer）]
        D1[原型设计代理（Prototype Agent）]
        D2[开发测试代理（DevTest Agent）]
        D3[安全防护代理（Security Agent）]
    end

    subgraph INFRA[基础设施层（Infrastructure Layer）]
        E1[向量数据库（Vector DB）]
        E2[知识图谱（Knowledge Graph）]
        E3[监控日志（Monitoring & Logging）]
    end

    UI --> API
    API --> CORE
    CORE --> AGENT
    AGENT --> INFRA
```

详细架构信息请参见[架构文档](docs/architecture.md)。

## 快速开始

### 环境要求

* Go 1.20.2 或更高版本
* Docker 和 Docker Compose（容器化部署）
* Git 版本控制工具

### 安装步骤

```bash
# 克隆代码仓库
git clone https://github.com/turtacn/protoforge.git
cd protoforge

# 初始化Go模块
go mod tidy

# 构建应用程序
make build

# 使用默认配置运行
./bin/protoforge server --config configs/default.yaml
```

### 基本使用示例

```go
package main

import (
    "context"
    "log"
    
    "github.com/turtacn/protoforge/pkg/agent"
    "github.com/turtacn/protoforge/pkg/workflow"
)

func main() {
    // 初始化ProtoForge客户端
    client, err := agent.NewClient(&agent.Config{
        APIEndpoint: "http://localhost:8080",
        APIKey:      "your-api-key",
    })
    if err != nil {
        log.Fatal(err)
    }

    // 创建原型生成工作流
    wf := workflow.NewBuilder().
        AddAgent("prototype", agent.TypePrototype).
        AddAgent("validator", agent.TypeValidator).
        Connect("prototype", "validator").
        Build()

    // 执行工作流
    result, err := client.ExecuteWorkflow(context.Background(), wf, &workflow.Input{
        ProjectSpec: "创建用户管理REST API",
        Language:    "go",
        Framework:   "gin",
    })
    
    if err != nil {
        log.Fatal(err)
    }
    
    log.Printf("生成的代码: %s", result.GeneratedCode)
}
```

### Docker部署

```bash
# 使用Docker Compose快速启动
docker-compose up -d

# 访问Web控制台
open http://localhost:3000
```

## 应用场景

### 1. 产品研发三级火箭工作流

```go
// 第一级：原型生成
prototype := protoforge.NewPrototypeAgent()
spec, err := prototype.GenerateFromRequirements(ctx, requirements)

// 第二级：迭代开发
developer := protoforge.NewDeveloperAgent()
code, err := developer.ImplementPrototype(ctx, spec)

// 第三级：知识产权保护
ipAgent := protoforge.NewIPProtectionAgent()
report, err := ipAgent.ScanAndProtect(ctx, code)
```

### 2. 开发自主安全防护系统的各类AI智能体

```go
// 持续威胁监控的安全智能体
securityAgent := protoforge.NewSecurityAgent(&SecurityConfig{
    ThreatModels:    []string{"injection", "privilege-escalation"},
    ResponseActions: []string{"quarantine", "alert", "remediate"},
})

// 部署自主防护
err := securityAgent.Deploy(ctx, &DeploymentConfig{
    MonitoringScope: "full-stack",
    AutoRemediation: true,
})
```

## 配置管理

ProtoForge支持通过YAML文件进行灵活配置：

```yaml
# configs/default.yaml
server:
  host: "0.0.0.0"
  port: 8080
  tls:
    enabled: false

agents:
  prototype:
    model: "gpt-4"
    max_tokens: 2048
  security:
    threat_detection: true
    auto_response: true

database:
  vector_db:
    provider: "chroma"
    connection_string: "http://localhost:8000"
```

## 贡献指南

我们欢迎社区贡献！详情请参见[贡献指南](CONTRIBUTING.md)。

### 开发环境设置

```bash
# Fork并克隆代码仓库
git clone https://github.com/yourusername/protoforge.git

# 安装开发依赖
make dev-setup

# 运行测试
make test

# 热重载运行
make dev
```

### 贡献领域

* 智能体实现和扩展
* 流行工具的集成连接器
* 文档和示例
* 性能优化
* 安全增强

## 许可证

ProtoForge基于MIT许可证发布。详情请参见[LICENSE](LICENSE)文件。

## 社区与支持

* **文档**: [docs.protoforge.dev](https://docs.protoforge.dev)
* **问题反馈**: [GitHub Issues](https://github.com/turtacn/protoforge/issues)
* **讨论交流**: [GitHub Discussions](https://github.com/turtacn/protoforge/discussions)
* **Discord**: [ProtoForge Community](https://discord.gg/protoforge)

## 发展路线图

* [ ] 可视化工作流设计器（2025年Q2）
* [ ] 高级多语言支持（2025年Q3）
* [ ] 企业SSO集成（2025年Q3）
* [ ] Kubernetes操作器（2025年Q4）
* [ ] 自定义智能体市场（2026年Q1）

---

**ProtoForge** - 锻造AI驱动开发工作流的未来。
