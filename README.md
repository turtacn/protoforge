# ProtoForge

*An open-source AI-agent and agentic AI framework for autonomous code generation, product prototyping, iterative development, and IP protection — powered by composable LLM agents and designed for private, full-stack R&D workflow.*

[中文版本 | Chinese Version](README-zh.md)

## Overview

ProtoForge is a comprehensive AI-agent framework specifically designed for SME (Small and Medium Enterprises) and ISV (Independent Software Vendors) to accelerate their product development lifecycle. Built with Go as the core language, ProtoForge provides a secure, scalable, and enterprise-ready solution for autonomous code generation, rapid prototyping, and intellectual property protection.

### Key Pain Points Addressed

- **Fragmented Development Workflow**: Traditional R&D processes lack seamless integration between prototyping, development, and IP protection
- **Limited AI Integration**: Existing frameworks don't provide enterprise-grade security and compliance for sensitive code generation
- **Scalability Constraints**: Most AI-agent frameworks struggle with concurrent multi-agent orchestration and horizontal scaling
- **IP Protection Gaps**: Current solutions lack built-in mechanisms for code provenance tracking and license compliance
- **Complex Multi-Language Integration**: Difficulty in creating unified workflows across different programming languages and platforms

### Core Value Proposition

ProtoForge transforms the traditional R&D workflow by providing:

1. **Autonomous Code Generation**: AI-powered code creation with built-in quality assurance and testing
2. **Intelligent Prototyping**: Rapid prototype development with iterative refinement capabilities  
3. **IP Protection Framework**: Comprehensive license scanning, code watermarking, and provenance tracking
4. **Enterprise Security**: Private deployment with role-based access control and audit logging
5. **Composable Agent Architecture**: Modular design enabling custom agent workflows and integrations

## Key Features

### 🚀 **Three-Stage R&D Rocket**
- **Stage 1**: Prototype Generation with AI-assisted design and validation
- **Stage 2**: Iterative Development with automated testing and code review
- **Stage 3**: IP Protection with license compliance and code attribution

### 🛡️ **Security-First Architecture**
- Built-in security agent for autonomous threat detection and response
- Private deployment with encrypted communication
- RBAC (Role-Based Access Control) and comprehensive audit trails
- Compliance framework supporting GDPR, ISO 27001, and industry standards

### 🔧 **Extensible Agent Framework**
- Plugin-based architecture supporting custom tools and integrations
- Multi-language support with Go core and Python/JavaScript extensions
- Visual workflow designer with drag-and-drop interface
- RESTful APIs and gRPC interfaces for seamless integration

### 📊 **Enterprise Observability**
- Real-time monitoring and performance metrics
- Distributed tracing for complex agent workflows
- Centralized logging with structured event correlation
- Custom dashboards and alerting systems

## Architecture Overview

ProtoForge follows a layered, microservices architecture designed for scalability and maintainability:

```mermaid
graph TD
    %% 系统架构图
    subgraph UI[用户界面层（User Interface Layer）]
        A1[Web控制台（Web Console）] 
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
````

For detailed architecture information, see [Architecture Documentation](docs/architecture.md).

## Quick Start

### Prerequisites

* Go 1.20.2 or higher
* Docker and Docker Compose (for containerized deployment)
* Git for version control

### Installation

```bash
# Clone the repository
git clone https://github.com/turtacn/protoforge.git
cd protoforge

# Initialize Go modules
go mod tidy

# Build the application
make build

# Run with default configuration
./bin/protoforge server --config configs/default.yaml
```

### Basic Usage Example

```go
package main

import (
    "context"
    "log"
    
    "github.com/turtacn/protoforge/pkg/agent"
    "github.com/turtacn/protoforge/pkg/workflow"
)

func main() {
    // Initialize ProtoForge client
    client, err := agent.NewClient(&agent.Config{
        APIEndpoint: "http://localhost:8080",
        APIKey:      "your-api-key",
    })
    if err != nil {
        log.Fatal(err)
    }

    // Create a prototype generation workflow
    wf := workflow.NewBuilder().
        AddAgent("prototype", agent.TypePrototype).
        AddAgent("validator", agent.TypeValidator).
        Connect("prototype", "validator").
        Build()

    // Execute workflow
    result, err := client.ExecuteWorkflow(context.Background(), wf, &workflow.Input{
        ProjectSpec: "Create a REST API for user management",
        Language:    "go",
        Framework:   "gin",
    })
    
    if err != nil {
        log.Fatal(err)
    }
    
    log.Printf("Generated code: %s", result.GeneratedCode)
}
```

### Docker Deployment

```bash
# Quick start with Docker Compose
docker-compose up -d

# Access the web console
open http://localhost:3000
```

## Use Cases

### 1. Product R\&D Three-Stage Workflow

```go
// Stage 1: Prototype Generation
prototype := protoforge.NewPrototypeAgent()
spec, err := prototype.GenerateFromRequirements(ctx, requirements)

// Stage 2: Iterative Development  
developer := protoforge.NewDeveloperAgent()
code, err := developer.ImplementPrototype(ctx, spec)

// Stage 3: IP Protection
ipAgent := protoforge.NewIPProtectionAgent()
report, err := ipAgent.ScanAndProtect(ctx, code)
```

### 2. How to develop AI agents for Autonomous Security Defense System

```go
// Security agent for continuous threat monitoring
securityAgent := protoforge.NewSecurityAgent(&SecurityConfig{
    ThreatModels:    []string{"injection", "privilege-escalation"},
    ResponseActions: []string{"quarantine", "alert", "remediate"},
})

// Deploy autonomous defense
err := securityAgent.Deploy(ctx, &DeploymentConfig{
    MonitoringScope: "full-stack",
    AutoRemediation: true,
})
```

## Configuration

ProtoForge supports flexible configuration through YAML files:

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

## Contributing

We welcome contributions from the community! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Setup

```bash
# Fork and clone the repository
git clone https://github.com/yourusername/protoforge.git

# Install development dependencies
make dev-setup

# Run tests
make test

# Run with live reload
make dev
```

### Contribution Areas

* Agent implementations and extensions
* Integration connectors for popular tools
* Documentation and examples
* Performance optimizations
* Security enhancements

## License

ProtoForge is released under the MIT License. See [LICENSE](LICENSE) file for details.

## Community & Support

* **Documentation**: [docs.protoforge.dev](https://docs.protoforge.dev)
* **Issues**: [GitHub Issues](https://github.com/turtacn/protoforge/issues)
* **Discussions**: [GitHub Discussions](https://github.com/turtacn/protoforge/discussions)
* **Discord**: [ProtoForge Community](https://discord.gg/protoforge)

## Roadmap

* [ ] Visual workflow designer (Q2 2025)
* [ ] Advanced multi-language support (Q3 2025)
* [ ] Enterprise SSO integration (Q3 2025)
* [ ] Kubernetes operator (Q4 2025)
* [ ] Marketplace for custom agents (Q1 2026)

---

**ProtoForge** - Forging the future of AI-powered development workflows.
