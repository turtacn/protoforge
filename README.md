# Protoforge

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Contribution Guide](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](./CONTRIBUTING.md)
[![中文文档](https://img.shields.io/badge/lang-中文-blue.svg)](./README-zh.md)

**Protoforge: An Enterprise-Grade, Go-Native Framework for Building, Orchestrating, and Scaling Multi-Agent AI Systems.**

## Overview

Protoforge is an open-source framework designed to empower developers, SMEs (Small and Medium-sized Enterprises), and ISVs (Independent Software Vendors) to build sophisticated and reliable AI-driven applications. It provides a robust, scalable, and secure foundation for creating complex workflows orchestrated by multiple intelligent agents.

Born from the need for a production-ready, Go-native alternative in the AI agent landscape, Protoforge combines the battle-tested concepts of leading platforms like LangChain and Microsoft AutoGen with the performance, concurrency, and simplicity of Golang.

[Read this document in Chinese](./README-zh.md).

## The Problem & Our Solution

The current landscape of AI agent frameworks is vibrant but fragmented. While many powerful tools exist (predominantly in Python), they often present challenges for enterprise adoption, especially within Go-centric ecosystems. Key pain points include:

* **Performance Bottlenecks:** Python's Global Interpreter Lock (GIL) can limit true parallelism for I/O-bound and CPU-bound tasks in a single node.
* **Integration Complexity:** Integrating Python-based AI systems into existing Go-based enterprise infrastructure can be cumbersome and inefficient.
* **Security & Governance Gaps:** Many open-source tools require significant effort to add enterprise-grade security, multi-tenancy, and compliance features.
* **Steep Learning Curve:** Orchestrating complex, stateful, multi-agent collaborations can be difficult with existing models.

**Protoforge addresses these challenges by providing:**

* **Go-Native Performance:** Built from the ground up in Golang for high concurrency, low latency, and efficient resource utilization.
* **Seamless Integration:** Designed for easy embedding into existing enterprise systems with first-class support for gRPC and REST APIs.
* **Enterprise-Grade & Secure:** Features like private deployment, role-based access control (RBAC), multi-tenancy, and detailed audit logs are core to the architecture.
* **Advanced Orchestration Engine:** A powerful graph-based engine, inspired by LangGraph, allows for defining, visualizing, and executing complex, stateful, and cyclical agent workflows.
* **Visual & Low-Code Tooling:** A backend designed to support a visual, drag-and-drop interface (similar to Flowise/LangFlow), dramatically lowering the barrier to entry for building and managing agentic workflows.

## Key Features

* **Modular & Extensible Plugin Architecture:** Easily extend the framework with new LLMs, vector stores, tools (APIs, databases), and memory backends.
* **Multi-Agent Collaboration:** Design and orchestrate sophisticated multi-agent systems where agents can work together, delegate tasks, and achieve complex goals. Supports patterns like group chats and hierarchical task decomposition.
* **Graph-Based Workflow Engine:** Define agent interactions as stateful graphs, enabling loops, reflection, and human-in-the-loop interventions.
* **Unified API Layer:** Interact with the framework through a consistent and powerful API, available via gRPC (for performance) and REST (for broad compatibility).
* **Rich Data & Retrieval Integration (RAG):** Built-in support for advanced Retrieval-Augmented Generation patterns, with flexible indexing and retrieval strategies inspired by LlamaIndex.
* **Full Observability:** Out-of-the-box support for structured logging, metrics (Prometheus), and distributed tracing (OpenTelemetry) to monitor and debug your systems.
* **Built-in Security & IP Protection:** Designed for on-premise/private cloud deployment, with features to ensure data privacy and help manage intellectual property concerns in code generation.
* **Visual Workflow Builder Support:** All core logic is exposed via APIs designed to power a low-code, visual workflow editor.

## Architecture Overview

Protoforge is built on a clean, layered architecture that separates concerns and promotes modularity and testability.

![Architecture Diagram](https://github.com/turtacn/protoforge/raw/main/docs/assets/architecture_en.png)

The key layers are:
1.  **Presentation Layer:** Exposes the system's functionality via gRPC, REST APIs, and WebSocket connections. This is the entry point for all external clients, including CLIs and visual UIs.
2.  **Application Layer:** Contains the core business logic and use case implementations. It orchestrates the domain entities to perform tasks, such as executing a workflow or managing agents.
3.  **Domain Layer:** The heart of the framework. It defines the core concepts, entities, and interfaces, such as `Agent`, `Tool`, `Workflow`, and `Message`. This layer is completely independent of any external technology.
4.  **Infrastructure Layer:** Provides concrete implementations for the interfaces defined in the domain layer. This includes adapters for LLM clients, databases, vector stores, loggers, and other external services.

For a deep dive into our architecture, component design, and technical decisions, please see our [**Architecture Document (`docs/architecture.md`)**](./docs/architecture.md).

## Getting Started

*(This section will be updated with build, installation, and run instructions once the initial codebase is available.)*

### Prerequisites

* Go 1.20.2+
* Docker & Docker Compose
* (Other dependencies will be listed here)

### Build & Run

```bash
# Clone the repository
git clone [https://github.com/turtacn/protoforge.git](https://github.com/turtacn/protoforge.git)
cd protoforge

# (Build and run commands will be added here)
````

## Contributing

We welcome contributions from the community\! Whether you're interested in fixing bugs, adding new features, or improving documentation, your help is appreciated. Please read our [**Contribution Guide (`CONTRIBUTING.md`)**](CONTRIBUTING.md) to get started.

## License

Protoforge is licensed under the [MIT License](LICENSE).
