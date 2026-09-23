# AgentSmallWorld 🦀

**English** | [简体中文](README_zh.md)

> **A Decentralized, Evolutionary Ecosystem for Autonomous Agents. Built with Rust.**

---

## 🚀 Core Philosophy

*   **Fearless Concurrency**: Leveraging Rust's ownership model to safely manage thousands of simultaneously evolving agents.
*   **Decentralized Orchestration**: No central hub. Tasks are routed through a dynamic **Small-World Network** using `libp2p`.
*   **Evolutionary Genetics**: Agents possess "genes" (Prompts, Tools, Memory) that mutate and crossover based on performance feedback.
*   **Zero-Cost Abstractions**: High-level evolutionary logic with low-level performance control.

---

## 🏗️ Architecture

### 1. Genetic Encoding 🧬
Every agent is defined by a mutable genetic structure stored in efficient binary formats:
*   **Prompt Genes**: Core identity and reasoning patterns.
*   **Tool Genes**: The specific set of APIs and skills the agent can access.
*   **Memory Genes**: Strategies for long-term storage (Vector/Graph).

### 2. The Small-World Graph 🕸️
*   **Local Clustering**: Agents form tight-knit communities for rapid collaboration.
*   **Random Long-Links**: Cross-domain connections ensure the network avoids local optima.
*   **P2P Routing**: Task allocation is driven by reputation-based gossip protocols.

### 3. Evolution Engine ⚡
*   **Auto-Mutation**: Agents modify their own prompt genes when facing edge cases.
*   **Horizontal Transfer**: Successful agents share skill fragments with neighbors.
*   **Energy Conservation**: Execution consumes Token-based energy; survival depends on task efficiency.

---

## 🛠️ Tech Stack

| Component | Technology | Purpose |
| :--- | :--- | :--- |
| **Language** | **Rust** | Memory safety, high performance, and fearless concurrency. |
| **Async Runtime** | **Tokio** | Handling thousands of concurrent agent tasks. |
| **Networking** | **libp2p-rust** | Decentralized P2P communication and identity management. |
| **AI Inference** | **Candle** | Native Rust ML framework for local model execution. |
| **Serialization** | **Serde** | Efficient encoding/decoding of Agent DNA. |
| **Database** | **Sled / RocksDB** | Embedded, high-performance storage for local memory. |

---

## 📖 Getting Started

### Prerequisites
*   Rust 1.75+ (`rustup install stable`)
*   Protobuf Compiler (for libp2p dependencies)

### Installation
```bash
git clone https://github.com/xinfan9/AgentSmallWorld.git
cd AgentSmallWorld
cargo build --release
```

### Running the Genesis Node
```bash
# Start the first node in the small world
cargo run --bin genesis -- --config=config/genesis.toml
```

### Spawning a New Agent
```bash
# Inject a new agent into the network
./target/release/asw-cli agent spawn --name="Rustacean" --specialization="systems_programming"
```

---

## 🧬 Genetic Structure (Rust Example)

In AgentSmallWorld, an agent's "DNA" is defined as a Rust struct:

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
        // Implementation of prompt mutation logic
    }
}
```

---

## 📈 Project Roadmap

1.  **Phase 1: The Spark**: Implement basic P2P connectivity and agent spawning using `libp2p`.
2.  **Phase 2: The Web**: Build the small-world routing algorithm and gossip protocol.
3.  **Phase 3: The Evolution**: Integrate genetic algorithms for prompt and tool optimization using `Candle`.
4.  **Phase 4: The Society**: Enable cross-agent collaboration and resource trading.

---

## 🤝 Contributing

We are looking for Rustaceans interested in:
*   Optimizing **Tokio tasks** for large-scale agent simulations.
*   Enhancing the **libp2p** integration for better NAT traversal.
*   Developing more sophisticated **genetic operators** in pure Rust.

---

> **"Built for speed, designed for evolution. Safe by default."**