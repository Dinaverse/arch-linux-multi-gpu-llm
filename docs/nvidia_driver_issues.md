# NVIDIA Driver Communication Failed

## Diagnostic Steps
1. `lsmod | grep nvidia` (Verify module load)
2. Manual probe: `sudo modprobe nvidia_modeset`
3. DKMS rebuild: `sudo dkms remove nvidia/535.xx --all && sudo dkms install nvidia/535.xx`
