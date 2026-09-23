# AgentSmallWorld 🦀

[English](README.md) | **简体中文**

> **一个去中心化、自进化的自主智能体生态系统。基于 Rust 构建。**

AgentSmallWorld 是一个基于 **Rust** 打造的极致 Agent 编排框架。它利用 Rust 的内存安全和高并发特性，构建了一个去中心化、自组织、具备自然选择机制的数字生命社会。在这里，Agent 不再是静态的工具，而是能够社交、学习并不断进化的数字物种。

---

## 🚀 核心理念

*   **无畏并发 (Fearless Concurrency)**：利用 Rust 的所有权模型，安全地管理成千上万个同时演化的智能体。
*   **去中心化编排**：没有中心调度枢纽。任务通过基于 `libp2p` 的动态**小世界网络**进行路由和分发。
*   **进化遗传学**：Agent 拥有“基因”（提示词、工具集、记忆结构），并根据任务表现进行突变和交叉进化。
*   **零成本抽象**：在保持高性能底层控制的同时，提供高层级的进化逻辑抽象。

---

## 🏗️ 架构设计

### 1. 基因编码 (Genetic Encoding) 🧬
每个 Agent 都由可突变的基因结构定义，采用高效的二进制格式存储：
*   **提示词基因 (Prompt Genes)**：定义核心身份、行为约束和推理模式。
*   **工具基因 (Tool Genes)**：定义 Agent 可调用的 API 和技能边界。
*   **记忆基因 (Memory Genes)**：定义长期记忆的存储策略（向量或图谱）。

### 2. 小世界网络 (The Small-World Graph) 🕸️
*   **局部聚类**：相似的 Agent 形成紧密社区，实现低延迟的快速协作。
*   **随机长连**：跨领域的随机连接确保网络不会陷入局部最优，促进跨界创新。
*   **P2P 路由**：任务分配不再依赖中心服务器，而是基于声誉的 gossip 协议进行传递。

### 3. 进化引擎 (Evolution Engine) ⚡
*   **自动突变**：当 Agent 遇到边缘情况时，会尝试修改自身的提示词基因，成功的突变将被保留。
*   **横向迁移**：成功的 Agent 可以将自己的“技能片段”分享给邻居，加速群体智慧的扩散。
*   **能量守恒**：执行任务消耗基于 Token 的能量，Agent 必须通过高效完成任务来维持生存。

---

## 🛠️ 技术栈

| 组件 | 技术选型 | 作用 |
| :--- | :--- | :--- |
| **编程语言** | **Rust** | 内存安全、高性能、无畏并发。 |
| **异步运行时** | **Tokio** | 处理成千上万个并发 Agent 任务。 |
| **网络通信** | **libp2p-rust** | 去中心化的 P2P 通信和身份管理。 |
| **AI 推理** | **Candle** | HuggingFace 开发的纯 Rust ML 框架，支持本地模型运行。 |
| **序列化** | **Serde** | 高效编解码 Agent 的 DNA 序列。 |
| **数据存储** | **Sled / RocksDB** | 嵌入式、高性能的本地记忆存储。 |

---

## 📖 快速开始

### 前置要求
*   Rust 1.75+ (`rustup install stable`)
*   Protobuf 编译器 (用于 libp2p 依赖)

### 安装与构建
```bash
git clone https://github.com/xinfan9/AgentSmallWorld.git
cd AgentSmallWorld
cargo build --release
```

### 运行创世节点
```bash
# 启动小世界中的第一个节点
cargo run --bin genesis -- --config=config/genesis.toml
```

### 生成新 Agent
```bash
# 向网络中注入一个新的智能体
./target/release/asw-cli agent spawn --name="Rustacean" --specialization="系统编程"
```

---

## 🧬 基因结构示例 (Rust)

在 AgentSmallWorld 中，Agent 的“DNA”被定义为 Rust 结构体：

```rust
use serde::{Serialize, Deserialize};

#[derive(Serialize, Deserialize, Clone, Debug)]
pub struct AgentDNA {
    pub id: String,
    pub prompt_gene: String,
    pub tool_genes: Vec<String>,
    pub fitness_score: f64,
    pub generation: u32,
}

impl AgentDNA {
    pub fn mutate(&mut self) {
        // 提示词突变逻辑的具体实现
    }
}
```

---

## 📈 项目路线图

1.  **第一阶段：火花 (The Spark)**：使用 `libp2p` 实现基础的 P2P 连通性和 Agent 生成。
2.  **第二阶段：织网 (The Web)**：构建小世界路由算法和 gossip 协议。
3.  **第三阶段：进化 (The Evolution)**：集成基于 `Candle` 的遗传算法，优化提示词和工具选择。
4.  **第四阶段：社会 (The Society)**：实现跨 Agent 协作和资源交易机制。

---

## 🤝 参与贡献

我们正在寻找对以下领域感兴趣的 Rust 开发者：
*   优化 **Tokio 任务**以支持大规模 Agent 模拟。
*   增强 **libp2p** 集成以改善 NAT 穿透能力。
*   在纯 Rust 中开发更复杂的**遗传算子**。

---

> **“为速度而生，为进化而设计。默认安全。”**