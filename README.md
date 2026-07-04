# 🏛️ Patrimoine — cockpit immobilier

Application web de gestion de patrimoine immobilier pour un couple. Un seul fichier HTML, aucune donnée personnelle dans le code.

## Fonctionnalités

- **Vue globale** : patrimoine net, dette, répartition par personne et par bien, projection sur la durée des crédits, flux du mois, cumuls.
- **Par bien** : crédits avec échéancier bancaire réel embarqué, assurances, travaux (budget prévisionnel vs paiements réels rattachés poste par poste), charges, valorisation avec historique.
- **LMNP** : cash-flow, simulateur de loyer avec alerte CFE, suivi d'occupation, comparateur micro-BIC vs réel, plan d'amortissement (art. 39C), scénario de revente, obligations fiscales.
- **Agenda** : échéances fiscales/copro/crédit, récurrence annuelle.
- **Coffre** : documents classés par bien et catégorie (stockage local IndexedDB).
- **Sync GitHub** : les données vivent dans un `data.json` d'un repo privé — multi-appareils, multi-utilisateurs, versionné.

## Installation

Voir `GUIDE-GITHUB.md`. En résumé : ce repo (public) sert l'app via GitHub Pages ; un second repo **privé** contient `data.json` ; l'app s'y connecte avec un token fine-grained limité à ce seul repo.

## Stack

HTML/CSS/JS vanilla + Chart.js (CDN). Pas de build, pas de serveur, pas de dépendance à installer.

## Avertissement

Les modules fiscaux (LMNP, plus-values) donnent des ordres de grandeur — ce n'est pas un conseil fiscal. Faire valider les décisions par un expert-comptable.
