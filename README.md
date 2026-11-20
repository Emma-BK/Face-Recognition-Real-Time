# 👁️ Reconnaissance Faciale en Temps Réel

Application web de **vision par ordinateur** développée avec [Streamlit](https://streamlit.io/), permettant la détection, la reconnaissance et le suivi de visages en temps réel depuis une caméra, une image ou une vidéo, avec un module de contrôle d'accès (whitelist / blacklist) et des alertes vocales.

## ✨ Fonctionnalités

L'interface propose six modes accessibles depuis la barre latérale :

| Mode | Description |
|------|-------------|
| 🏠 **Accueil** | Présentation de l'application et des références chargées |
| 🎥 **Mode Caméra** | Reconnaissance faciale en direct, comptage des personnes uniques, détection YOLO et alertes vocales |
| 🔍 **Recherche avec Image** | Traque d'une personne cible dans le flux de la caméra à partir d'une photo |
| 🖼️ **Analyser Image** | Analyse d'une image statique, annotations des visages et statistiques |
| 🎬 **Recherche dans Vidéo** | Recherche d'une personne dans une vidéo avec rapport horodaté |
| 🔐 **Mode Sécurité** | Gestion de la blacklist : alerte visuelle et vocale lors de la détection d'une personne interdite |

### Détails techniques

- **Reconnaissance faciale** : `face_recognition` (basé sur dlib), avec calcul d'encodages et comparaison par distance (tolérance 0.5).
- **Détection de personnes** : modèle **YOLOv8n** (`ultralytics`) pour le comptage et la surveillance.
- **Alertes vocales** : `pyttsx3` avec voix française et anti-spam (threads + initialisation COM sous Windows).
- **Interface** : Streamlit avec CSS personnalisé (thème sombre).
- **Persistance** : les photos de référence sont lues depuis `personnes_reference/` et la blacklist est sauvegardée dans `blacklist/`.

## 🛠️ Technologies

- Python 3.12
- Streamlit, OpenCV, NumPy, Pillow
- face-recognition / dlib
- ultralytics (YOLOv8)
- pyttsx3

## 📦 Installation

```bash
# 1. Cloner le dépôt
git clone https://github.com/Emma-BK/Face-Recognition-Real-Time.git
cd Face-Recognition-Real-Time

# 2. Créer et activer un environnement virtuel
python -m venv .venv
.venv\Scripts\activate        # Windows
# source .venv/bin/activate   # macOS / Linux

# 3. Installer les dépendances
pip install -r requirements.txt
```

> **Note Windows / dlib** : si l'installation de `face-recognition` échoue, installez d'abord le wheel fourni :
> ```bash
> pip install dlib-19.24.99-cp312-cp312-win_amd64.whl
> pip install -r requirements.txt
> ```

## 🚀 Utilisation

1. Ajoutez des photos des personnes à reconnaître dans le dossier **`personnes_reference/`**.
   Le nom du fichier (`Ahmed_1.jpg`, `Sara.jpg`, …) sert de nom affiché ; le suffixe `_N` est automatiquement retiré pour regrouper plusieurs photos d'une même personne.
2. Lancez l'application :
   ```bash
   streamlit run app.py
   ```
3. Ouvrez l'URL affichée dans le navigateur (généralement `http://localhost:8501`) et choisissez un mode dans le menu latéral.

Pour le mode Sécurité, ajoutez des photos dans l'onglet dédié ; elles sont enregistrées dans le dossier `blacklist/` (créé automatiquement).

> ⚠️ Une webcam est nécessaire pour les modes caméra. Les fichiers `yolov8n.pt` et le wheel dlib sont inclus dans le dépôt.

## 📁 Structure du projet

```
.
├── app.py                                   # Application Streamlit principale
├── requirements.txt                         # Dépendances Python
├── final_prj.ipynb                          # Notebook de développement / expérimentation
├── yolov8n.pt                               # Poids du modèle YOLOv8n
├── dlib-19.24.99-cp312-cp312-win_amd64.whl  # Wheel dlib pour Windows Python 3.12
├── personnes_reference/                     # Photos de référence (à renseigner)
└── blacklist/                               # Photos des personnes interdites (généré à l'exécution)
```

## ⚖️ Considérations éthiques

Ce projet est destiné à un usage pédagogique / de démonstration. La reconnaissance faciale et la surveillance biométrique sont soumises à des réglementations strictes (RGPD, etc.) : obtenez toujours le consentement des personnes concernées avant de collecter ou d'analyser leurs données.

---

👤 **Auteur** : [Emma-BK](https://github.com/Emma-BK)
