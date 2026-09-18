# AINM Prog Chantier — PWA v1.2

Version PWA avec accès direct SharePoint SNCF aux programmations AHT et AJT.

## AHT / AJT
- AHT : ouverture du fichier hebdomadaire du chantier.
- AJT : ouverture du fichier journalier (lundi à dimanche) selon la semaine sélectionnée.
- Ligne 830 000 : secteur 6.
- Ligne 750 000 : secteur 7.
- Arborescence AHT : `1-AHT LeBonit / année / Sxx`.
- Arborescence AJT : `3-AJT LeBonit / année / Sxx / n-Jour jj-mm-aa`.
- Le libellé de fichier reste configurable dans chaque fiche chantier.
- Boutons de secours vers les dossiers AHT et AJT.

L'application n'enregistre aucun identifiant Microsoft. L'ouverture SharePoint utilise la session SNCF de l'agent.


## v1.4
Correction des liens directs AHT/AJT : utilisation de la route Excel Online SharePoint `/:x:/r/sites/...` avec `csf=1&web=1`, conforme aux liens SNCF copiés depuis SharePoint. Les boutons dossier conservent la route standard `/sites/...`.
