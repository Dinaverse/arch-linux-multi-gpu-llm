# 🚀 MASTER GUIDE: HEADLESS AI INFRASTRUCTURE (4x NVIDIA P106-100)

This document centralizes configuration, optimization, and evolution strategy for your distributed compute laboratory under Arch Linux.

---

## 🛠️ 1. SYSTEM & DRIVER CONFIGURATION (ARCH LINUX)

### A. Initializing "Mining" GPUs (P106-100)
P106-100 cards lack physical video outputs. The challenge is to force loading NVIDIA drivers without a GUI for CUDA computing.

*   **Modify `/etc/mkinitcpio.conf`:**
    ```bash
    MODULES=(intel_agp i915 nvidia nvidia_modeset nvidia_uvm nvidia_drm)
    ```
    *Note: `i915` loads the Intel iGPU for display, freeing the 24GB of NVIDIA VRAM.*

*   **GRUB Parameters (`/etc/default/grub`):**
    ```text
    GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet nvidia-drm.modeset=1"
    ```

### B. Performance Optimizations
*   **Linux-Zen Kernel:** Better scheduling management for LLMs.
*   **Persistence Mode:** Essential to avoid GPU wake-up latency.
    ```bash
    sudo systemctl enable --now nvidia-persistenced
    ```
*   **RAM Management (ZRAM):** With 16GB system RAM, ZRAM compensates for overflows when loading large models (Qwen 27B).
    ```text
    # /etc/systemd/zram-generator.conf
    [zram0]
    zram-size = ram / 1
    compression-algorithm = zstd
    ```

---

## 🧠 2. AI ECOSYSTEM (OLLAMA, TENSORRT, PYTORCH)

### A. Inference Engine: Ollama
*   **Multi-GPU:** Ollama natively detects your 4 cards and partitions models.
*   **Target Model:** Qwen 3.5:27B (~17GB) runs entirely in VRAM (24GB).
*   **Optimization:** Always prioritize `Q4_K_M` quantizations for a perfect balance between precision and speed.

### B. Development Environments
*   **PyTorch & TensorRT:** Configured to leverage `sm_61` (Pascal architecture).
*   **Native Bridge:** Uses Python scripts (`subprocess`) to link AI with Kali Linux tools without container latency.

---

## 🌐 3. LEVERAGING THE NVIDIA NGC CATALOG

Although your architecture is Pascal, the NGC catalog remains a goldmine via Docker:

| Tool | P106-100 Compatibility | Suggested Usage |
| :--- | :--- | :--- |
| **NVIDIA Riva** | ✅ Excellent | STT/TTS to voice-control the lab. |
| **RAPIDS (v23.08)** | ✅ Stable | Massive log analysis (millions of lines/sec). |
| **Triton Server** | ✅ Stable | Serving multiple models in parallel. |
| **Morpheus** | ⚠️ Experimental | Threat detection (requires Pascal adaptation). |

### Docker Strategy for NGC:
Always use images specifying CUDA 11.x or 12.1 to ensure compatibility with `sm_61` architecture.
Example: `nvcr.io/nvidia/pytorch:23.08-py3`

---

## 🛡️ 4. CYBERSECURITY EVOLUTION & AUTONOMY

The goal is to transform this lab into a "Sovereign Security Agent":
1.  **Native Bridge:** The MCP server (`mcp-security-server.js`) bridges Open WebUI and the 28 Kali tools.
2.  **Confidentiality:** Zero Cloud. All scan data and logs remain on your local network.
3.  **Distributed Network:** 
    *   **Brain:** Arch Linux (4x GPU).
    *   **Interface:** Dell Precision (32GB RAM).
    *   **Execution:** Kali Linux (64GB RAM).

---
*Document generated May 19, 2026 - "Hacker-DIY" Lab Configuration*
EOF
,file_path: