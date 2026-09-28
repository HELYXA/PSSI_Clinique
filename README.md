# PSSI : Clinique du Parc

Construction d'une **Politique de Sécurité des Systèmes d'Information (PSSI)** pour un établissement de santé fictif, du recueil des besoins jusqu'au plan de déploiement.

Projet réalisé en groupe de 5 pendant un atelier de 3 jours, dans le cadre de mon **Bachelor Cybersécurité** (Nexa Digital School, 2026-2027).

---

## Le scénario

La *Clinique du Parc* est un établissement MCO (médecine, chirurgie, obstétrique) **fictif**, fourni comme cas d'étude :

- 300 lits et 2 centres de consultation externes, activité 24h/24
- ~900 agents, avec une forte rotation (vacations, gardes)
- une DSI locale de 3 personnes, sans RSSI dédié sur site
- des données de santé (DPI, PACS, monitoring) hébergées dans un datacenter certifié HDS
- des dispositifs médicaux connectés, dont certains anciens et non patchables
- des sauvegardes encore locales, avec une réplication en cours de déploiement
- une forte dépendance aux tiers : éditeur du DPI, mainteneurs, IT du groupe

---

## La démarche

### Jour 1 : cadrer
- Questionnaire de recueil des besoins pour un interlocuteur **métier**, sans jargon de sécurité
- Définition du périmètre selon 4 dimensions : entités, systèmes, données, utilisateurs
- Formulation de 3 objectifs **SMART**
- Cartographie des actifs (primaires et supports)
- Registre de 6 menaces : erreur humaine, partage de comptes, divulgation, ransomware, compromission par télémaintenance, phishing

### Jour 2 : structurer
- Gouvernance SSI : ce qui existe, ce qui manque (RSSI dédié, comité SSI, cellule de crise)
- Positionnement des fonctions RSSI / SOC / CERT / cellule de crise
- Matrice **RACI** sur 4 décisions types
- Analyse des référentiels applicables : HDS, RGPD, ISO 27001/27002, guides ANSSI, CIS Controls, NIST
- Choix de mesures techniques et organisationnelles, chacune reliée à une menace et à une source

### Jour 3 : déployer
- Fiches de contrôle avec indicateurs chiffrés et cibles
- Plan de déploiement : formation, calendrier sur 6 mois, communication
- Matrice impact / complexité pour prioriser les actions restantes
- Soutenance orale

---

## Les choix clés

**Objectifs retenus**
1. Réaliser au moins un test de restauration par trimestre du DPI, du PACS et des données critiques
2. Isoler 100 % des dispositifs médicaux dans leur réseau dédié, en supprimant ou en documentant chaque dérogation
3. Généraliser les comptes nominatifs et le MFA sur les accès distants, avec désactivation des comptes sous 48 h après un départ

**Actions prioritaires** (impact fort, complexité faible)
- MFA sur le VPN et les accès de télémaintenance
- Comptes nominatifs et procédure de départ
- Premier test de restauration

**Mesures écartées, avec justification**
- Remplacer tous les dispositifs non patchables : irréaliste en coût et en délai, l'isolement réseau sert de mesure compensatoire
- Couper le VPN des médecins libéraux : casserait le fonctionnement de la clinique, on sécurise l'accès plutôt que de le supprimer
- Bloquer la télémaintenance la nuit : incompatible avec une activité 24h/24, on préfère des accès ouverts sur demande avec une plage limitée

---

## Ce que ce projet m'a appris

- **Parler métier avant de parler technique.** Demander « que se passerait-il si le dossier patient tombait une journée ? » plutôt que « quel est votre RTO ? ».
- **Un objectif SMART doit rester tenable.** On a remplacé des cibles RTO/RPO qu'on ne connaissait pas par un engagement mesurable : tester la restauration chaque trimestre. Le premier test sert justement à mesurer le temps réel de reprise.
- **Chaque mesure doit avoir une menace et un responsable.** Sinon, elle ne tient ni face à un jury ni dans la réalité.
- **Il faut savoir justifier ce qu'on écarte**, pas seulement ce qu'on retient.
- **Le vrai risque, c'est l'écart entre la théorie et la pratique.** La séparation réseau des dispositifs médicaux existait sur le papier, mais des dérogations la contournaient dans les faits.
- **Le cas particulier du HDS :** c'est une certification, mais elle est rendue obligatoire par le Code de la santé publique dès qu'on héberge des données de santé.

---

## Compétences mobilisées

Gouvernance SSI · Analyse de risques · Conformité HDS / RGPD · ISO 27001 / 27002 · Guides ANSSI · Matrice RACI · Objectifs SMART · Indicateurs de sécurité · Sécurité des dispositifs médicaux (IoMT) · Conduite du changement

---

> Le scénario est fictif et les livrables du groupe ne sont pas publiés ici. Ce dépôt présente la démarche et ce que j'en ai retenu.
