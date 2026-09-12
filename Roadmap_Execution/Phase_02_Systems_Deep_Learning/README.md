[← Back to Master Execution Table](../../README.md)

# Phase 2: Systems + Deep Learning — Autodiff NN Framework & Network Intrusion Detector

**Timeline:** February – April 2027 (~12 Weeks)  
**Compute Tier:** Local CPU/WSL2 + free Colab burst — $0–20/mo  
**Project Directory:** `Project_Autodiff_Intrusion_Detector/`  
**No Academic Freezes** (between semesters).

---

## ⚡ The 30/70 Efficiency Rule (Fluff Filter)

| Course | ▶️ MUST WATCH (Core Theory & Depth) | ❌ SKIP / FAST-FORWARD |
|--------|------------------------------------|------------------------|
| **Deep Learning Specialization (C1–C5)** | C1: Weeks 2–4 (Neural Network Forward/Backprop, Vectorization). C2: Weeks 1–2 (Optimization: Momentum, RMSprop, Adam; Regularization: Dropout, Weight Decay). C3: ML Project Strategy (Train/Dev/Test split, Orthogonalization). C4: CNN Architectures (ResNet, Inception, Transfer Learning). C5: RNN/LSTM/GRU, Attention Mechanism, Transformer Encoder-Decoder. | C1: Week 1 (Python/NumPy basics). C2: Week 3 (Hyperparameter tuning process overview). C4: Week 3 (Object Detection API tutorials). C5: Week 3 (Speech/Trigger Word detection tutorials). |
| **fast.ai (Lessons 1–8)** | Lesson 2: Data blocks, DataLoaders, GPU pipeline. Lesson 3: Multi-label classification, Siamese networks. Lesson 4: Collaborative filtering, Embeddings. Lesson 5: Tabular modeling, Decision trees as differentiable functions. Lesson 6: NLP (ULMFiT, Text Classification). Lesson 7: ResNet from scratch, `nn.Module` internals. Lesson 8: Transformers from scratch (GPT, BERT internals). | Lesson 1: Image classification "Hello World" (too basic). |
| **Stanford CS144 (Networking)** | Lectures: TCP Flow Control (Sliding Window), Congestion Control (Reno/CUBIC/BBR), Socket Programming. **Labs 0–6: Minnow TCP Stack implementation (complete all labs)**. | Basic OSI model overview, introductory Ethernet/IP header explanations. |
| **Linux Journey** | Advanced: Kernel modules, Syscalls, `perf`/`ftrace` internals, `eBPF` fundamentals. | Command line basics, file permissions, package management. |
| **Windows Internals / Sysinternals** | Sysmon Event ID mapping, ETW architecture, Process/Thread internals, Kernel Memory dump analysis. | Basic GUI administration, user account management. |

---

## 📅 Flagship Milestone Schedule (12-Week Breakdown)

### 🏃 Sprint 1: Core Mathematical Derivation & Data Structures (Weeks 1–3: Feb 1 – Feb 21)
* **Week 1 (Autodiff Engine Architecture):**
  * Derive Vector-Jacobian Products (VJPs) for `matmul`, `conv2d`, `softmax_cross_entropy`, `gelu`, `layernorm`.
  * Define `Tensor` node structure: `data` (contiguous buffer), `grad` (accumulator), `creator_op`, `backward_closure`.
  * Implement topological sort (Kahn's algorithm) on DAG for reverse-mode backprop ordering.
* **Week 2 (Core Operations & Gradient Correctness):**
  * Implement C++20 `Tensor` class with SIMD-aware memory layout (contiguous row-major buffers).
  * Implement gradient check utility: `max_relative_error(grad_analytic, grad_numeric) < 1e-6` for all primitives.
  * Unit test against NumPy `gradcheck` on random tensors.
* **Week 3 (Network Stack Foundation — CS144 Minnow Labs 0–2):**
  * Complete Minnow Labs: `ByteStream`, `Checksum`, `WrappingInt32`, `StreamReassembler`.
  * Derive 64-bit sequence number unwrapping logic from 32-bit wire format.

---

### 🏃 Sprint 2: Low-Level Implementation — Zero Wrappers (Weeks 4–7: Feb 22 – Mar 21)
* **Week 4 (Autodiff Optimizer & Neural Net Modules):**
  * Implement `AdamW` optimizer with weight decay decoupling: $\theta_{t+1} = \theta_t - \eta \cdot (\hat{m}_t / (\sqrt{\hat{v}_t} + \epsilon) + \lambda \theta_t)$.
  * Build `Linear`, `Conv2d`, `MultiHeadAttention` modules using only autodiff primitives.
  * Train a 2-layer MLP on CIC-IDS2017 subset to validate engine correctness.
* **Week 5 (Minnow TCP Labs 3–5 — Sender, Connection, Network Interface):**
  * Implement `TCPSender` with adaptive RTT estimator (Jacobson/Karels) and sliding window.
  * Implement `TCPConnection` full state machine (RFC 793) combining Sender + Receiver.
  * Implement `NetworkInterface` ARP table + Ethernet frame encapsulation.
* **Week 6 (TUN/TAP Kernel Integration):**
  * Open `/dev/net/tun`, bind virtual interface, handle IP packet routing between user-space stack and host.
  * Validate 2-way HTTP traffic (client inside Minnow $\leftrightarrow$ Python HTTP server on host) captured in Wireshark.
* **Week 7 (Deep Anomaly Detector Training):**
  * Using autodiff engine, train a Deep Autoencoder on NSL-KDD / CIC-IDS2017 flow features (entropy, packet rates, flag distributions).
  * Train supervised MLP classifier on extracted latent representations.

---

### 🏃 Sprint 3: Benchmarking against Standard Baselines (Weeks 8–9: Mar 22 – Apr 4)
* **Week 8 (Compute Engine Benchmarks):**
  * Benchmark `matmul` throughput (FP32) against NumPy + OpenBLAS on identical CPU: Target $\le 2.5\times$ NumPy.
  * Gradient check full network: Max relative error $\le 10^{-6}$ vs. finite-difference.
  * Memory footprint: $< 100$ MB for 1M parameter model training.
* **Week 9 (Network Stack & NIDS Benchmarks):**
  * Minnow TCP throughput: $\ge 2.0$ Gbps over loopback TAP device (measured via `iperf3`).
  * NIDS Inference Latency: $\le 1.5$ ms per 1,000 packets on CPU.
  * Detection Metrics: F1-Score $\ge 0.93$, False Positive Rate $\le 2.5\%$ on CIC-IDS2017 test split.

---

### 🏃 Sprint 4: Adversarial Attack / Stress Testing & GDB Patching (Weeks 10–11: Apr 5 – Apr 18)
* **Week 10 (TCP Reassembly Memory Bomb — CWE-400):**
  * Craft malicious fragmented TCP stream with 10GB logical offset gaps to trigger unbounded memory allocation in `StreamReassembler`.
  * Attach GDB: `watch reassembler._unassembled_bytes` and trace memory growth until OOM kill.
  * Patch: Enforce strict maximum reassembly buffer capacity (e.g., 64KB per flow); drop overlapping out-of-window segments.
* **Week 11 (Autodiff Graph Cycle & Adversarial Packet Evasion):**
  * Introduce cycle in computational graph during dynamic `if` branching; trigger infinite recursion in `backward()`.
  * Trace stack overflow: `gdb -ex "catch throw" -ex "bt 30"`.
  * Patch: Implement Tarjan's SCC cycle detection before backward pass; fail fast with clear error.
  * Fast Gradient Sign Method (FGSM) on inter-arrival time features: $\delta = \epsilon \cdot \text{sign}(\nabla_x J)$ to evade detector while preserving TCP validity.
  * Re-train with adversarial examples; verify robust accuracy $\ge 85\%$.

---

### 🏃 Sprint 5: Documentation & Post-Mortem Writeup (Week 12: Apr 19 – Apr 25)
* **Week 12 (Final Artifacts):**
  * `DERIVATION.md`: Matrix calculus for autodiff, Jacobson RTT equations, autoencoder reconstruction loss.
  * `BENCHMARK_REPORT.md`: Profiling logs, flame graphs, throughput comparison tables.
  * `PCAP_EXPLOIT_LOGS/`: Raw `.pcap` files of memory bomb and FGSM evasion attacks + patch verification.
  * Tag `v2.0-autodiff-nids-complete`.

---

## 🏗 System Architecture

```text
┌───────────────────────────────────────────────────────────────────────────┐
│              Flagship Hybrid: Autodiff Engine & TCP NIDS                  │
├───────────────────────────────────────────────────────────────────────────┤
│                                                                           │
│  ┌─────────────────────────────────┐   ┌───────────────────────────────┐  │
│  │   Pure C++20 / Python Autodiff  │   │     Minnow User-Space TCP     │  │
│  │         Compute Engine          │   │         Network Stack         │  │
│  │                                 │   │                               │  │
│  │  ┌───────────────────────────┐  │   │  ┌─────────────────────────┐  │  │
│  │  │ Dynamic Computational     │  │   │  │ TUN/TAP Interface       │  │  │
│  │  │ Graph (DAG) + Tape        │  │   │  │ (Raw L2/L3 Packet Sink) │  │  │
│  │  └─────────────┬─────────────┘  │   │  └───────────┬─────────────┘  │  │
│  │                │                │   │              │                │  │
│  │  ┌─────────────▼─────────────┐  │   │  ┌───────────▼─────────────┐  │  │
│  │  │ Tensor Core: Matmul,      │  │   │  │ Stream Reassembler &    │  │  │
│  │  │ Conv2D, Cross-Entropy     │  │   │  │ TCP State Machine       │  │  │
│  │  └─────────────┬─────────────┘  │   │  └───────────┬─────────────┘  │  │
│  │                │                │   │              │                │  │
│  │  ┌─────────────▼─────────────┐  │   │  ┌───────────▼─────────────┐  │  │
│  │  │ Reverse-Mode Autodiff     │  │   │  │ Session Flow Rebuilder  │  │  │
│  │  │ (VJP: Vector-Jacobian)    │  │   │  │ (5-Tuple Connection Trk)│  │  │
│  │  └─────────────┬─────────────┘  │   │  └───────────┬─────────────┘  │  │
│  │                │                │   │              │                │  │
│  │  ┌─────────────▼─────────────┐  │   │              │                │  │
│  │  │ AdamW / SGD Optimizers    │  │   │              │                │  │
│  │  └─────────────┬─────────────┘  │   │              │                │  │
│  └────────────────┼────────────────┘   └──────────────┼────────────────┘  │
│                   │                                   │                   │
│                   │ Trained Weights                   │ Reconstructed     │
│                   │ (No PyTorch runtime)              │ TCP Payloads      │
│                   ▼                                   ▼                   │
│  ┌─────────────────────────────────────────────────────────────────────┐  │
│  │            Real-Time Network Intrusion Detection Engine             │  │
│  │  - Deep Autoencoder for Packet Anomaly Detection                     │  │
│  │  - Flow-Level Multi-Layer Perceptron (MLP) Classifier                │  │
│  │  - Flags SYN Floods, Port Scans, Exfiltration, Shellcode Payloads   │  │
│  │  - Live Wireshark / PCAP Validation & Syslog Alerting Engine        │  │
│  └─────────────────────────────────────────────────────────────────────┘  │
└───────────────────────────────────────────────────────────────────────────┘
```

---

## 🔬 The S++++++ Audit Protocol

### Stage 1: Derive — Mathematical Foundations
- **Reverse-Mode Autodiff VJP for Matrix Multiplication:**
  $$
  \text{Forward: } Y = X W \quad \frac{\partial L}{\partial X} = \frac{\partial L}{\partial Y} W^T, \quad \frac{\partial L}{\partial W} = X^T \frac{\partial L}{\partial Y}
  $$
- **Softmax Cross-Entropy Gradient:**
  $$
  \frac{\partial L}{\partial z_i} = p_i - \mathbb{1}_{i=y}
  $$
- **Jacobson RTT Estimator:**
  $$
  \text{EstimatedRTT} \gets (1-\alpha)\text{EstimatedRTT} + \alpha \cdot \text{SampleRTT}
  $$
  $$
  \text{DevRTT} \gets (1-\beta)\text{DevRTT} + \beta \cdot |\text{SampleRTT} - \text{EstimatedRTT}|
  $$
  $$
  \text{RTO} = \text{EstimatedRTT} + 4 \cdot \text{DevRTT}
  $$

### Stage 2: Implement — Zero Wrappers
- Pure C++20 tensor core; no PyTorch/TensorFlow in inference or training path.
- Minnow TCP stack from CS144 labs (C++20).

### Stage 3: Benchmark — Performance Targets
| Metric | Target | Baseline |
|--------|--------|----------|
| Autodiff MatMul vs NumPy | $\le 2.5\times$ | OpenBLAS single-thread |
| Gradient Accuracy | $\le 10^{-6}$ rel error | Finite difference check |
| TCP Reassembler Throughput | $\ge 2.0$ Gbps | Linux kernel loopback |
| NIDS Latency | $\le 1.5$ ms/1k pkts | Suricata baseline |
| Detection F1 | $\ge 0.93$ | Random Forest baseline |

### Stage 4: Break & Patch
- TCP reassembly memory exhaustion (CWE-400) → capacity limits + window checks.
- Autodiff graph cycle (CWE-834) → Tarjan's SCC pre-pass.
- FGSM adversarial evasion → adversarial retraining.

---

## ✅ Exit Criteria Checklist
- [ ] Autodiff engine trains 4-layer NN from scratch on CPU without PyTorch.
- [ ] Gradient check utility validates all ops within $10^{-6}$ tolerance.
- [ ] Minnow TCP stack achieves 2-way HTTP traffic via TAP device (Wireshark verified).
- [ ] NIDS processes live flows and flags SYN flood/port scan with F1 $\ge 0.93$.
- [ ] Break-and-Patch cycle fully executed: exploits reproduced in GDB and remediated.