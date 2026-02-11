# 👁️ Architecture Hybride $\beta$-VAE-GAN : Synthèse d'Images Rétiniennes

[![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white)](https://pytorch.org/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python)](https://www.python.org/)
[![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)]()

> **Projet de Fin de Semestre - Master SDA (Science des Données et Analyse)** > *Faculté Polydisciplinaire de Safi - Université Cadi Ayyad*

## 📝 Description du Projet

La **Rétinopathie Diabétique** est une cause majeure de cécité. Le développement de modèles de diagnostic (IA) est souvent freiné par le manque d'images médicales annotées et le déséquilibre des classes (peu de cas sévères par rapport aux cas sains).

Ce projet propose une solution générative basée sur une architecture hybride **$\beta$-VAE-GAN** (Variational Autoencoder + Generative Adversarial Network). L'objectif est de générer des images synthétiques de fonds d'œil réalistes pour l'augmentation de données.

## 🧠 Architecture Technique

Notre modèle combine les forces de deux architectures :
1.  **$\beta$-VAE (Variational Autoencoder)** : Assure la cohérence structurelle de l'œil (disque optique, forme circulaire) et structure l'espace latent.
2.  **DCGAN (Deep Convolutional GAN)** : Le discriminateur force le générateur (décodeur du VAE) à produire des détails nets et des textures réalistes (vaisseaux sanguins).

**Fonction de Perte Composite :**
$$\mathcal{L}_{Total} = \mathcal{L}_{Reconstruction} + \beta D_{KL} + \mathcal{L}_{Adversarial}$$

## 📂 Dataset et Prétraitement

Nous utilisons le dataset public **APTOS 2019 Blindness Detection**.

**Pipeline de Prétraitement (Méthode Ben Graham) :**
* Redimensionnement en $128 \times 128$.
* Soustraction du flou gaussien local (pour corriger les variations d'éclairage).
* Rognage circulaire automatique.

## 📊 Résultats (Après 100 Époques)

Le modèle a été entraîné sur GPU (NVIDIA T4). Les métriques finales témoignent d'une convergence stable :

| Métrique | Valeur Finale | Interprétation |
|:---|:---:|:---|
| **SSIM** (Structural Similarity) | **0.455** | Bonne préservation de la structure globale de l'œil. |
| **PSNR** (Peak Signal-to-Noise Ratio) | **23.43 dB** | Niveau de bruit faible, image nette. |
| **L1 Loss** | **0.082** | Excellente fidélité de reconstruction. |

### Visualisation
*(Les images générées montrent clairement le disque optique et la vascularisation)*

## 🚀 Installation et Utilisation

1.  **Cloner le dépôt :**
    ```bash
    git clone [https://github.com/VOTRE_NOM_UTILISATEUR/NOM_DU_REPO.git](https://github.com/VOTRE_NOM_UTILISATEUR/NOM_DU_REPO.git)
    cd NOM_DU_REPO
    ```

2.  **Installer les dépendances :**
    ```bash
    pip install torch torchvision matplotlib numpy opencv-python split-folders
    ```

3.  **Lancer l'entraînement :**
    Ouvrez le notebook `vae-dcgan.ipynb` et exécutez les cellules séquentiellement. Assurez-vous d'avoir téléchargé le dataset APTOS via Kaggle API.

## 👥 Auteurs

* **Yassine MABCHOUR**
* **Asmae HADAR**

**Encadrant :** Pr. Mohamed ESSALIH  
*Année Universitaire 2025-2026*

---