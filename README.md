# AINM Prog PWA v1.7.0 — Passerelle Power Automate

Cette version remplace le projet de connexion directe Outlook par une passerelle adaptée à une boîte SNCF.

## Ajouts v1.7.0
- aucune connexion directe de la PWA à Outlook / Microsoft 365 ;
- écran **Réception prog** raccordable à une passerelle Google Apps Script ;
- récupération au lancement puis périodique des mails transmis par Power Automate ;
- import automatique des pièces jointes XLSX ;
- filtrage strict Petit / Dahmani conservé ;
- détection du rappel d'une semaine future (ex. S48/26) distincte des fichiers actualisés reçus (ex. S40/S41) ;
- accusé de traitement côté boîte relais pour éviter les doubles imports ;
- import manuel XLSX conservé comme secours ;
- toutes les fonctions v1.6.0 sont incluses : import multi-XLSX, journal des mails, saisie rapide semaine et marquage NOUVEAU / REPRIS / MODIFIÉ.

## Fichiers fournis
- `index.html`, `sw.js`, `manifest.webmanifest`, `icons/` : application PWA ;
- `bridge-apps-script/AINM_Programmation_Bridge.gs` : passerelle de réception ;
- `GUIDE-PAS-A-PAS-PASSERELLE-SNCF.md` : installation complète ;
- `scripts/update-termux.sh` : mise à jour du dépôt depuis Termux avec sauvegarde et push optionnel.

## Architecture

`Outlook SNCF → Power Automate → boîte Gmail relais → Apps Script → PWA AINM`

La PWA ne reçoit ni mot de passe ni jeton Microsoft 365. Le fichier source reçu par mail n'est jamais modifié.
