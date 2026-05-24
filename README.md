# Arch Linux Multi-GPU LLM Cluster
4x NVIDIA P106-100 GPU Cluster running Qwen 3.5:27B on Arch Linux.

**Status**: ✅ Operational (Multi-GPU acceleration active, 4/4 GPUs recognized)

---

## 📋 Project Overview

This repository documents a complete optimization guide for running a 27B parameter large language model (Qwen 3.5) on Arch Linux with 4x consumer-grade NVIDIA GPUs. The infrastructure is fully operational with all 4 GPUs recognized (IDs 0-3).

### Why This Matters
- **Real-world infrastructure**: Demonstrates production-grade ML inference system building.
- **Optimization challenges**: Solving complex hardware/software integration issues.
- **Scalability**: 4x GPU setup (24GB VRAM) enables larger models.
- **Educational value**: Walkthrough for multi-GPU configurations.

---

## 🖥️ System Specifications

### Hardware
| Component | Details |
|-----------|---------|
| **CPU** | Intel i5-6500 (4 cores / 4 threads) |
| **System RAM** | 16GB DDR4 |
| **iGPU** | Intel HD Graphics 530 |
| **dGPU (x4)** | 4x NVIDIA P106-100 (6GB each = **24GB total VRAM**) |
| **Storage** | 119 GB (Btrfs) |

### Model
- **Model Name**: Qwen 3.5:27B
- **Framework**: Ollama (Local LLM runtime)

---

## ✅ Deployment Status
- [x] NVIDIA Drivers (v535+)
- [x] CUDA / OpenCL
- [x] GRUB DRM settings (nvidia-drm.modeset=1)
- [x] Multi-GPU detection (IDs 0, 1, 2, 3 validated)
- [x] LLM inference functional on 4x GPUs

---

## 🔍 GPU Verification (nvidia-smi)

All GPUs are correctly communicating with the driver:

```
+-----------------------------------------------------------------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
|===============================+======================+======================|
|   0  NVIDIA P106-100    Off  | 0000:01:00.0     Off |                  N/A |
|   1  NVIDIA P106-100    Off  | 0000:02:00.0     Off |                  N/A |
|   2  NVIDIA P106-100    Off  | 0000:03:00.0     Off |                  N/A |
|   3  NVIDIA P106-100    Off  | 0000:04:00.0     Off |                  N/A |
+-------------------------------+----------------------+----------------------+
```

---

## 🔧 System Optimizations
- **Persistence Mode**: enabled for all 4 GPUs.
- **Kernel**: Optimized for low-latency inference.
- **CPU Management**: auto-cpufreq tuned for thermal efficiency.
- **Memory Management**: ZRAM enabled for overflow protection.

---

## 🐛 Troubleshooting (Driver Communication)
Issues resolved by:
1. Complete DKMS stack rebuild.
2. Kernel/NVIDIA version alignment.
3. PCI bus access verification for P106 cards.

---

## 📊 Performance Metrics

### Expected Throughput
- **4x GPU Parallel**: Optimized inference across 4 P106 nodes.
- **Memory Footprint**: ~17GB (model) + ~2-3GB (CUDA overhead).

---

## 🔄 Current Status
- **Status**: ✅ Operational (Actively Maintained)
- **Next Steps**: Benchmark multi-GPU parallel inference and model fine-tuning.

---

## 🏷️ Tags
`arch-linux` `nvidia-gpu` `qwen` `ollama` `cuda` `ml-infrastructure` `gpu-computing` `llm` `ai`

## Cross-References
- **Infrastructure Architecture:** See [sovereign-ai-infrastructure/infrastructure/arch-linux-cluster](../sovereign-ai-infrastructure/infrastructure/arch-linux-cluster)
- **GPU Monitoring:** See [python-security-analytics](../python-security-analytics) for monitoring scripts.
