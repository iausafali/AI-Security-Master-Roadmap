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
  * Implement `AdamW` optimizer with weight decay decoupling.
  * Build `Linear`, `Conv2d`, `MultiHeadAttention` modules using only autodiff primitives.
  * Train a 2-layer MLP on a CIC-IDS2017 subset to validate engine correctness.
* **Week 5 (Minnow TCP Labs 3–5 — Sender, Connection, Network Interface):**
  * Implement `TCPSender` with adaptive RTT estimator (Jacobson/Karels) and sliding window.
  * Implement `TCPConnection` full state machine combining Sender + Receiver.
  * Implement `NetworkInterface` ARP table + Ethernet frame encapsulation.
* **Week 6 (TUN/TAP Kernel Integration):**
  * Open `/dev/net/tun`, bind virtual interface, handle IP packet routing between user-space stack and host.
  * Validate 2-way HTTP traffic captured in Wireshark.
* **Week 7 (Deep Anomaly Detector Training):**
  * Using the autodiff engine, train a Deep Autoencoder on NSL-KDD / CIC-IDS2017 flow features.
  * Train supervised MLP classifier on extracted latent representations.

---

### 🏃 Sprint 3: Benchmarking against Standard Baselines (Weeks 8–9: Mar 22 – Apr 4)
* **Week 8 (Compute Engine Benchmarks):**
  * Benchmark `matmul` throughput against NumPy + OpenBLAS on an identical CPU: Target ≤ 2.5× NumPy.
  * Gradient check full network: Max relative error ≤ 1e-6 vs. finite-difference.
  * Memory footprint: < 100 MB for 1M parameter model training.
* **Week 9 (Network Stack & NIDS Benchmarks):**
  * Minnow TCP throughput: ≥ 2.0 Gbps over loopback TAP device.
  * NIDS inference latency: ≤ 1.5 ms per 1,000 packets on CPU.
  * Detection metrics: F1 ≥ 0.93, False Positive Rate ≤ 2.5% on the documented test split.

---

### 🏃 Sprint 4: Adversarial Attack / Stress Testing & GDB Patching (Weeks 10–11: Apr 5 – Apr 18)
* **Week 10 (TCP Reassembly Memory Bomb — CWE-400):**
  * Craft malicious fragmented TCP streams inside the controlled lab to test unbounded reassembly behavior.
  * Attach GDB and trace memory growth.
  * Patch with strict reassembly capacity and window checks.
* **Week 11 (Autodiff Graph Cycle & Adversarial Packet Evasion):**
  * Introduce a controlled computational-graph cycle and verify failure handling.
  * Trace stack behavior with GDB.
  * Patch with cycle detection before backward execution.
  * Evaluate FGSM-based feature perturbations against the detector and measure robustness.
  * Re-train with adversarial examples and record the robustness trade-off.

---

### 🏃 Sprint 5: Documentation & Post-Mortem Writeup (Week 12: Apr 19 – Apr 25)
* **Week 12 (Final Artifacts):**
  * `DERIVATION.md`: Matrix calculus for autodiff, Jacobson RTT equations, autoencoder reconstruction loss.
  * `BENCHMARK_REPORT.md`: Profiling logs, flame graphs, throughput comparison tables.
  * `PCAP_EXPLOIT_LOGS/`: Raw `.pcap` files from controlled stress tests and patch verification.
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
│  │  ┌─────────────▼─────────────┐  │   │  │                           │  │
│  │  │ AdamW / SGD Optimizers    │  │   │  │                           │  │
│  │  └─────────────┬─────────────┘  │   │  └───────────────────────────┘  │
│  └────────────────┼────────────────┘                                    │
│                   │                                                      │
│                   ▼                                                      │
│  ┌─────────────────────────────────────────────────────────────────────┐  │
│  │            Real-Time Network Intrusion Detection Engine             │  │
│  │  - Deep Autoencoder for Packet Anomaly Detection                    │  │
│  │  - Flow-Level Multi-Layer Perceptron Classifier                     │  │
│  │  - Live Wireshark / PCAP Validation & Syslog Alerting Engine        │  │
│  └─────────────────────────────────────────────────────────────────────┘  │
└───────────────────────────────────────────────────────────────────────────┘
```

---

## 🔬 Engineering Verification Protocol

### Stage 1: Derive — Mathematical Foundations
- **Reverse-Mode Autodiff VJP for Matrix Multiplication:**
  $$
  \text{Forward: } Y = X W \quad \frac{\partial L}{\partial X} = \frac{\partial L}{\partial Y} W^T, \quad \frac{\partial L}{\partial W} = X^T \frac{\partial L}{\partial Y}
  $$
- **Softmax Cross-Entropy Gradient:**
  $$\frac{\partial L}{\partial z_i} = p_i - \mathbb{1}_{i=y}$$
- **Jacobson RTT Estimator:**
  $$\text{EstimatedRTT} \gets (1-\alpha)\text{EstimatedRTT} + \alpha \cdot \text{SampleRTT}$$
  $$\text{DevRTT} \gets (1-\beta)\text{DevRTT} + \beta \cdot |\text{SampleRTT} - \text{EstimatedRTT}|$$
  $$\text{RTO} = \text{EstimatedRTT} + 4 \cdot \text{DevRTT}$$

### Stage 2: Implement
- Pure C++20 tensor core with no PyTorch/TensorFlow in the core training/inference path.
- Minnow TCP stack from CS144 labs.

### Stage 3: Benchmark
| Metric | Target | Baseline |
|--------|--------|----------|
| Autodiff MatMul vs NumPy | ≤ 2.5× | OpenBLAS single-thread |
| Gradient Accuracy | ≤ 10^-6 rel error | Finite difference check |
| TCP Reassembler Throughput | ≥ 2.0 Gbps | Linux kernel loopback |
| NIDS Latency | ≤ 1.5 ms/1k pkts | Documented baseline |
| Detection F1 | ≥ 0.93 | Random Forest baseline |

### Stage 4: Break & Patch
- TCP reassembly memory exhaustion → capacity limits + window checks.
- Autodiff graph cycle → cycle detection before backward execution.
- Adversarial feature perturbation → robustness evaluation and adversarial retraining.

---

## ✅ Exit Criteria Checklist
- [ ] Autodiff engine trains a multi-layer NN from scratch on CPU without PyTorch.
- [ ] Gradient check utility validates all core ops within 10^-6 tolerance.
- [ ] Minnow TCP stack achieves 2-way HTTP traffic via TAP device (Wireshark verified).
- [ ] NIDS processes documented flows and meets the phase's detection benchmark.
- [ ] Break-and-patch cycle is fully executed in the controlled lab and documented.