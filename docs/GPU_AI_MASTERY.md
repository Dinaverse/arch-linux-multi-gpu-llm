# 🚀 GUIDE MAÎTRE : INFRASTRUCTURE IA HEADLESS (4x NVIDIA P106-100)

Ce document centralise la configuration, l'optimisation et la stratégie d'évolution de votre laboratoire de calcul distribué sous Arch Linux.

---

## 🛠️ 1. CONFIGURATION SYSTÈME & PILOTES (ARCH LINUX)

### A. Initialisation des GPUs "Mining" (P106-100)
Les cartes P106-100 n'ont pas de sortie vidéo. Le défi est de forcer le chargement des pilotes NVIDIA sans interface graphique pour le calcul CUDA.

*   **Modification de `/etc/mkinitcpio.conf` :**
    ```bash
    MODULES=(intel_agp i915 nvidia nvidia_modeset nvidia_uvm nvidia_drm)
    ```
    *Note : `i915` charge l'iGPU Intel pour l'affichage, libérant les 24 Go de VRAM NVIDIA.*

*   **Paramètres GRUB (`/etc/default/grub`) :**
    ```text
    GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet nvidia-drm.modeset=1"
    ```

### B. Optimisations de Performance
*   **Kernel Linux-Zen :** Meilleure gestion de l'ordonnancement pour les LLM.
*   **Persistence Mode :** Indispensable pour éviter la latence de réveil des GPUs.
    ```bash
    sudo systemctl enable --now nvidia-persistenced
    ```
*   **Gestion de la RAM (ZRAM) :** Avec 16 Go de RAM système, ZRAM compense les débordements lors du chargement de gros modèles (Qwen 27B).
    ```text
    # /etc/systemd/zram-generator.conf
    [zram0]
    zram-size = ram / 1
    compression-algorithm = zstd
    ```

---

## 🧠 2. ÉCOSYSTÈME IA (OLLAMA, TENSORRT, PYTORCH)

### A. Moteur d'Inférence : Ollama
*   **Multi-GPU :** Ollama détecte nativement vos 4 cartes et partitionne les modèles.
*   **Modèle Cible :** Qwen 3.5:27B (~17 Go) s'exécute entièrement dans la VRAM (24 Go).
*   **Optimisation :** Toujours privilégier les quantifications `Q4_K_M` pour un équilibre parfait entre précision et vitesse.

### B. Environnements de Développement
*   **PyTorch & TensorRT :** Configurés pour exploiter `sm_61` (architecture Pascal).
*   **Bridge Natif :** Utilisation de scripts Python (`subprocess`) pour lier l'IA aux outils de Kali Linux sans la latence des containers.

---

## 🌐 3. EXPLOITATION DU CATALOGUE NVIDIA NGC

Bien que votre architecture soit Pascal, le catalogue NGC reste une mine d'or via Docker :

| Outil | Compatibilité P106-100 | Usage Suggéré |
| :--- | :--- | :--- |
| **NVIDIA Riva** | ✅ Excellente | STT/TTS pour piloter le lab à la voix. |
| **RAPIDS (v23.08)** | ✅ Stable | Analyse de logs massive (millions de lignes/sec). |
| **Triton Server** | ✅ Stable | Service de modèles multiples en parallèle. |
| **Morpheus** | ⚠️ Expérimental | Détection de menaces (nécessite adaptation Pascal). |

### Stratégie Docker pour NGC :
Utilisez toujours des images spécifiant CUDA 11.x ou 12.1 pour garantir la compatibilité avec l'architecture `sm_61`.
Exemple : `nvcr.io/nvidia/pytorch:23.08-py3`

---

## 🛡️ 4. ÉVOLUTION CYBERSÉCURITÉ & AUTONOMIE

L'objectif est de transformer ce lab en un "Agent de Sécurité Souverain" :
1.  **Native Bridge :** Le serveur MCP (`mcp-security-server.js`) fait le pont entre Open WebUI et les 28 outils Kali.
2.  **Confidentialité :** Zéro Cloud. Toutes les données de scan et les logs restent dans votre réseau local.
3.  **Réseau Distribué :** 
    *   **Cerveau :** Arch Linux (4x GPU).
    *   **Interface :** Dell Precision (32 Go RAM).
    *   **Exécution :** Kali Linux (64 Go RAM).

---
*Document généré le 19 Mai 2026 - Configuration Lab "Hacker-DIY"*
