# Programmation AINM v1.8.1 — version épurée terrain + réception automatique

## Objectif

L'application a été recentrée sur quatre usages :

1. **AHT / AJT** : consultation rapide par les agents, chantier par chantier ;
2. **Semaine** : lecture des programmations reçues/importées, avec S9 (ITC/ZEP) et S11 (consignation) clairement séparés ;
3. **Préparer la prog** : création de la demande hebdomadaire à partir des chantiers et configurations existants, puis export dans la trame Excel UOTx ;
4. **Administration** : réception des mails, import manuel XLSX, référentiel Contrat Travaux, sauvegardes et flux CR OFF.

Les anciens menus techniques ne sont plus présentés dans la navigation terrain.

## Réception des mails SNCF

Architecture retenue :

`Outlook SNCF → Power Automate → boîte Gmail relais → Apps Script → Programmation AINM`

- le flux Power Automate ne traite que les mails autorisés, notamment ceux de Christophe Gervais avec pièces jointes ;
- le marqueur `AINM_PROGRAMMATION` permet à la passerelle de ne prendre que les messages destinés à l'application ;
- la PWA récupère les fichiers XLSX, conserve les lignes Petit / Dahmani (variantes historiques comprises), puis les classe par semaine et chantier ;
- chaque appareil conserve son propre anti-doublon : plusieurs agents peuvent donc récupérer la même programmation ;
- un bouton **Importer XLSX** reste disponible en secours.

## Référentiel Contrat Travaux

La v1.8.1 peut synchroniser le catalogue local de l'application **Contrat Travaux / Atelier Contrats** lorsqu'il est disponible dans le même navigateur et sous la même origine web.

Formats reconnus :

- catalogue moderne : `ZEP`, `SEL`, `SEU`, `CONSIGNATION` ;
- ancien catalogue Atelier Contrats : `kind=ZEP/SEL` avec type de ZEP séparé ;
- export JSON ou CSV du catalogue en solution de secours.

Le choix reste **manuel** : l'application n'infère jamais qu'une ZEP ou une consignation est applicable. Elle permet de rechercher le code, la gare, la ligne, les voies, la consigne source et sa version, puis de reporter la référence choisie dans S9 ou S11.

## S9 / S11 et CR OFF

Le flux interne `ainm.programmation.feed.v1` publie, par semaine et chantier :

- `itcS9` ← colonne V (S9 / ZEP / ITC) ;
- `consignationS11` ← colonne W (S11 / consignation) ;
- horaires, jours, voies, travaux, moyens et références.

Il est destiné au raccordement de l'application CR OFF. Un export JSON manuel est également disponible dans Administration.

## Fichiers

- `index.html` : PWA complète ;
- `sw.js` : cache hors ligne ;
- `manifest.webmanifest` + `icons/` : installation mobile ;
- `bridge-apps-script/AINM_Programmation_Bridge.gs` : passerelle Gmail/Apps Script ;
- `GUIDE-CONFIGURATION-V1.8.md` : configuration pas à pas ;
- `scripts/update-termux.sh` : mise à jour du dépôt Git avec sauvegarde automatique.

## Version

**1.8.1**

## Correctif 1.8.1 — anti-cache
Si un téléphone affiche encore une ancienne interface après déploiement, ouvrir `reset-ainm.html`. Cette page supprime uniquement les caches `ainm-prog-chantier-*` et désinscrit le service worker dont la portée est `/AINM-prog-chantier/`. Elle ne supprime ni localStorage ni IndexedDB.
