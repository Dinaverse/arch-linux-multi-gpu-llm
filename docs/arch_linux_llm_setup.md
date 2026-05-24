# Arch Linux Multi-GPU LLM Inference Setup

## Prerequisites
- Arch Linux
- Kernel: Linux 6.x (linux-zen recommended)

## Installation Steps
1. **NVIDIA Driver Stack**: `sudo pacman -S nvidia-dkms nvidia-utils`
2. **Compute Support**: `sudo pacman -S cuda opencl-nvidia`
3. **GRUB Config**: Add `nvidia-drm.modeset=1` to `GRUB_CMDLINE_LINUX_DEFAULT`.
