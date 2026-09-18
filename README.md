# Programmation AINM — PWA

Application statique PWA pour la programmation hebdomadaire AINM.

## Fichiers
- `index.html` : application
- `manifest.webmanifest` : manifeste PWA
- `sw.js` : service worker / mode hors ligne
- `icons/` : icônes Android / installation

## Déploiement
Le projet est compatible avec GitHub Pages. Le service worker nécessite HTTPS (fourni par GitHub Pages) ou localhost.

## Version 1.1 — Accès AHT / AJT
- Configuration par chantier du secteur AHT/AJT (1 à 7) et du libellé de fichier.
- Bouton AHT / AJT dans la programmation.
- Ouverture directe du fichier AHT hebdomadaire calculé à partir de l'année/semaine ISO.
- Repli vers le dossier SharePoint de la semaine si le nom du fichier diffère.
- Montereau préconfiguré : secteur 6 / Melun - Montereau pour les nouvelles installations.
- AJT préparé côté interface ; l'ouverture directe sera activée lorsque la nomenclature exacte AJT sera connue.
