# Arch Linux Multi-GPU LLM Cluster

## Description
Cluster de calcul haute performance composé de 4 GPU NVIDIA P106-100 pour l'inférence locale de modèles LLM (Qwen 3.5:27B).

## Résolution des problèmes (NVIDIA Driver)
Erreurs de communication avec le pilote NVIDIA ("driver communication failed") résolues par :
1. Vérification du chargement du module (`lsmod | grep nvidia`).
2. Sondage manuel (`modprobe nvidia`).
3. Reconstruction et réinstallation des modules DKMS (`dkms remove ... && dkms install ...`).

## Contenu
- Scripts d'optimisation GPU
- Configuration système pour multi-GPU
- Guide de déploiement Ollama

## Documentation
Voir le dossier /docs pour les spécifications techniques et les guides de configuration.
EOF
,file_path: