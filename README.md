# AINM Prog PWA v1.5 — Prototype automatisation CR OFF

Ajouts :
- module « Automatisation CR OFF » depuis la programmation ;
- configuration destinataire et heure cible par chantier ;
- préparation d'un tableau CR OFF à partir des opérations AINM ;
- accès AHT/AJT conservé ;
- test technique de lecture silencieuse d'un AJT SharePoint depuis la PWA ;
- aucun envoi de mail réel dans ce prototype.

Limite volontaire : l'ouverture d'un fichier SharePoint protégé peut fonctionner alors que sa lecture par `fetch()` est bloquée par les règles d'authentification/CORS Microsoft. Le test intégré permet de le constater sur le poste SNCF avant de choisir le pont Power Automate/OneDrive.
