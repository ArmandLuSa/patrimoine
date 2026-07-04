# 📘 Tuto complet — Patrimoine (Armand & Victoria)

> App : **https://armandlusa.github.io/patrimoine/** — à mettre en favori sur chaque appareil (PC + téléphone).

---

## 1. Comment ça fonctionne (en 30 secondes)

Le système repose sur **2 espaces GitHub** :

| | Repo | Contenu | Qui peut le voir |
|---|---|---|---|
| 🖥️ L'application | `patrimoine` (public) | Le code de l'app, hébergé gratuitement par GitHub Pages | Tout le monde (mais **zéro donnée perso** dedans) |
| 🔐 Les données | `patrimoine-data` (privé) | Le fichier `data.json` = TOUT (biens, prêts, travaux, loyers, agenda…) | Uniquement toi (et qui tu invites) |

L'app fait le lien entre les deux grâce au **token** (une clé d'accès collée une fois par appareil) :

- **À l'ouverture** → l'app va chercher la dernière version de `data.json` sur GitHub (*pull*)
- **À chaque modification** → l'app renvoie automatiquement la nouvelle version 4 secondes après (*push*)
- Chaque push = **un commit Git** → historique complet, n'importe quelle version est récupérable

La pastille en bas à gauche te dit tout :
🟢 `Sync GitHub ✓` = tout est sauvegardé · 🟠 `Modifs non pushées` = en cours · 🔴 = problème (va dans Réglages)

---

## 2. La sauvegarde des données (3 niveaux de sécurité)

1. **Instantané — navigateur (localStorage)** : chaque saisie est enregistrée immédiatement sur l'appareil. Même sans internet, tu ne perds rien en fermant l'onglet.
2. **Automatique — GitHub** : 4 s après chaque modification, l'app pousse `data.json` sur le repo privé. C'est LA sauvegarde de référence, partagée entre tous vos appareils.
3. **Manuel — export** (Réglages) :
   - `Exporter data.json` → le fichier de données seul
   - `Export complet` → données **+ documents du coffre** (à faire 1×/trimestre par sécurité, à ranger sur OneDrive)

⚠️ **Les documents du coffre** (PDF uploadés dans l'app) restent dans le navigateur de l'appareil — ils ne partent PAS sur GitHub. Les originaux sont de toute façon sur OneDrive : le coffre sert de classeur de consultation.

### Restaurer une ancienne version
GitHub → repo `patrimoine-data` → clic sur `data.json` → **History** → choisir une version → bouton `...` → View file → Raw → enregistrer → dans l'app : Réglages → Importer un fichier. (Ou demande-moi, je le fais en 1 min.)

---

## 3. Installation pour Victoria — pas à pas (5 min)

**Option simple (recommandée) : elle utilise ton token.**

1. Sur son appareil, ouvrir **https://armandlusa.github.io/patrimoine/**
2. Menu de gauche → **⚙️ Réglages**
3. Dans « Synchronisation GitHub » remplir :
   - Repo : `ArmandLuSa/patrimoine-data`
   - Token : coller **le même token** que le tien (envoie-le lui par un canal sûr : de vive voix, gestionnaire de mots de passe partagé… pas par SMS/mail)
4. Cocher ✅ « Sauvegarde auto sur GitHub »
5. Cliquer **Enregistrer la config** → **Tester la connexion** (doit dire « privé ✓ »)
6. Cliquer **⬇️ Pull** → confirmer → toutes les données apparaissent 🎉

À partir de là, elle utilise l'app normalement : tout ce qu'elle saisit se synchronise avec toi, et inversement.

**Option « comptes séparés » (plus propre, optionnelle) :**
1. Victoria crée son compte sur github.com
2. Toi : repo `patrimoine-data` → Settings → Collaborators → **Add people** → son pseudo → elle accepte l'invitation (mail)
3. Elle : github.com → Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → New : accès uniquement à `patrimoine-data`, permission **Contents : Read and write**
4. Elle colle **son** token dans l'app (étapes 2-6 ci-dessus)

---

## 4. Utiliser l'app au quotidien

| Je veux… | Où |
|---|---|
| Voir le patrimoine global, la trajectoire, qui a payé quoi | **Vue globale** |
| Saisir une dépense, une charge, un loyer encaissé, une estimation | Bouton **＋ Ajouter** (en bas à gauche) — 10 secondes |
| Suivre les crédits, voir l'échéancier bancaire réel | Bien → onglet **Crédits** → 📋 Tableau d'amortissement |
| Suivre le budget travaux vs payé réel | RP Les Lones → **Travaux & meubles** (rattache chaque paiement à un poste budget) |
| Gérer la location Agen : loyer, occupation, cash-flow | LMNP Agen → **Locatif** (heatmap : clique un mois pour changer son statut) |
| Comparer micro-BIC vs réel, amortissements, revente | LMNP Agen → **Fiscalité LMNP** |
| Mettre à jour la valeur d'un bien (1-2×/an) | Bien → **Valorisation** (liens MeilleursAgents/DVF intégrés) |
| Suivre les échéances (taxe foncière, CFE, liasse, AG copro) | **Agenda** — coche ✓ quand c'est fait, les annuelles se recréent seules |
| Classer un document | **Coffre** ou Bien → Documents |

### 🖊️ Le 15 juillet (signature Agen)
Sur la Vue globale, bandeau orange → **Acter la signature** → renseigner la date et les frais de notaire réels → le studio bascule dans le patrimoine, les crédits et KPIs démarrent automatiquement.

---

## 5. Questions fréquentes

**On modifie tous les deux en même temps ?** Le dernier qui sauvegarde gagne. En pratique à deux ce n'est jamais un souci — et l'historique Git permet toujours de récupérer. Réflexe simple : ouvrir l'app = les données fraîches arrivent seules.

**Pas d'internet ?** L'app fonctionne (données locales). La synchro repartira à la prochaine ouverture connectée — pense à Push (Réglages) si la pastille est orange.

**Nouveau PC / téléphone ?** Ouvrir l'URL → Réglages → repo + token → Pull. 2 minutes.

**Token perdu ou compromis ?** GitHub → Settings → Developer settings → Fine-grained tokens → révoquer `patrimoine-app` → en créer un nouveau → le recoller dans l'app (chaque appareil). Les données ne bougent pas.

**Mettre à jour l'app ?** Demande-moi les modifications → je te donne le nouveau `index.html` → repo `patrimoine` → remplacer le fichier. Les données ne sont jamais touchées.

---

*Rappel : les modules fiscaux (LMNP, plus-value) donnent des ordres de grandeur — faire valider les décisions par un expert-comptable.*
