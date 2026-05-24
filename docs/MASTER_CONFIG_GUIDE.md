# Master Configuration Guide: Arch Linux Multi-GPU LLM Inference

## 1. System Overview
- **CPU:** Intel i5-6500 (4C/4T)
- **System RAM:** 16GB
- **iGPU:** Intel HD Graphics 530 (Display Output)
- **dGPU (x4):** 4x NVIDIA P106-100 (24GB total VRAM)
- **Model:** Qwen 3.5:27B (Inference optimized)

## 2. Installations
- **Drivers:** `nvidia-dkms`, `nvidia-utils`
- **Compute:** `cuda`, `opencl-nvidia`
- **Support:** `linux-headers`, `dkms`
- **Repositories:** `[multilib]` enabled.

## 3. Critical Configuration (GRUB)
Ensure `/etc/default/grub` contains:
`GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet nvidia-drm.modeset=1"`

Update GRUB:
`sudo grub-mkconfig -o /boot/grub/grub.cfg`

## 4. Post-Reboot Verification
1. Verify GPUs: `nvidia-smi`
2. Verify Ollama: `ollama list`
3. Inference: `ollama run qwen3.5:27b`

## 5. Recommended Optimizations
- **Persistence:** `sudo systemctl enable --now nvidia-persistenced`
- **Performance Kernel:** `linux-zen`
- **Power Management:** `auto-cpufreq`
- **Memory/ZRAM:** `zram-generator` configured for memory pressure.

## 6. Minimalist UI (Hacker Style)
- **TUI Login:** `ly`
- **Terminal:** `alacritty`
- **WM:** `sway` (Wayland) or `i3wm` (X11)

## 7. Known Issues & Troubleshooting

### Error: nvidia-smi Driver Communication Failed
**Status:** Ongoing investigation.
- **Symptom:** `nvidia-smi` fails to communicate with the driver.
- **Potential Causes:**
    - Driver version mismatch or improper load.
    - Kernel update conflicts (DKMS rebuild required).
    - PCIe bus resource contention.
- **Troubleshooting Path:** Rebuild DKMS modules and verify module loading order (must ensure iGPU initializes first).
EOF
,file_path: