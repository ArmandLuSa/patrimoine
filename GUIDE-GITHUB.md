# 🚀 Guide de publication — Patrimoine v2

Objectif : app accessible depuis n'importe quel appareil (toi + Victoria), données privées et sauvegardées à chaque modification.

**Architecture :** 2 repos GitHub
- `patrimoine` (**public**) → héberge l'app via GitHub Pages. Zéro donnée perso dedans.
- `patrimoine-data` (**privé**) → contient `data.json` (vos données). L'app lit/écrit dedans via l'API GitHub. Chaque sauvegarde = un commit (historique complet).

---

## Étape 1 — Créer les 2 repos (5 min)

1. Va sur [github.com](https://github.com) (crée un compte si besoin).
2. **Repo app** : bouton **New** → nom `patrimoine` → **Public** → Create repository.
   - Clique **uploading an existing file** → glisse `index.html` → Commit.
3. **Repo données** : **New** → nom `patrimoine-data` → **Private** ⚠️ → Create.
   - Upload → glisse `data.json` → Commit.

## Étape 2 — Activer GitHub Pages (1 min)

Dans le repo `patrimoine` : **Settings → Pages** → Source : `Deploy from a branch` → Branch : `main` / `(root)` → Save.

→ 2 minutes plus tard, l'app est en ligne sur :
`https://TON-PSEUDO.github.io/patrimoine/`
(mets cette URL en favori sur PC + téléphone)

## Étape 3 — Créer le token (3 min)

1. GitHub → photo de profil → **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
2. Nom : `patrimoine-app` · Expiration : **1 an** (mets un rappel).
3. **Repository access** : *Only select repositories* → coche uniquement `patrimoine-data`.
4. **Permissions → Repository permissions → Contents : Read and write**. Rien d'autre.
5. Generate → **copie le token** (affiché une seule fois).

## Étape 4 — Configurer l'app (1 min, à faire sur chaque appareil)

Ouvre l'app → **Réglages → Synchronisation GitHub** :
- Repo : `TON-PSEUDO/patrimoine-data`
- Token : colle le token
- ✅ coche « Sauvegarde auto »
- **Tester la connexion** → doit afficher `privé ✓`
- **Pull** pour charger les données.

Le token reste dans le navigateur de l'appareil, il n'est jamais commité.

## Étape 5 — Victoria (2 options)

- **Simple** : elle ouvre la même URL et colle **le même token** (Réglages, 1 fois par appareil).
- **Propre** : elle crée son compte GitHub → dans `patrimoine-data` : Settings → Collaborators → l'inviter → elle génère son propre token (étape 3).

---

## Usage quotidien

- Ouvre l'URL → les données GitHub se chargent automatiquement si plus récentes.
- Chaque modification est sauvegardée en local instantanément + pushée sur GitHub (~4 s après, si auto activé). La pastille en bas de la barre latérale indique l'état : 🟢 sync · 🟠 modifs non pushées · 🔴 erreur.
- Boutons **Pull / Push** manuels dans Réglages si besoin.
- **Historique** : repo `patrimoine-data` → `data.json` → History = toutes les versions, restaurables.

## ⚠️ À savoir

- **Documents du coffre** : stockés dans le navigateur (pas sur GitHub, pour ne pas gonfler le repo). Les originaux restent sur ton OneDrive → le coffre sert de classeur de consultation rapide. L'**export complet** (Réglages) les inclut si tu veux une sauvegarde.
- **Conflits** : si vous modifiez tous les deux en même temps hors ligne, le dernier Push gagne (l'historique Git permet de récupérer). En pratique à deux : quasi jamais un problème.
- **Utilisation sans GitHub** : l'app marche aussi en double-cliquant `index.html` (données en local + export/import manuel).
- **Token expiré** (dans 1 an) : régénérer (étape 3) et recoller dans Réglages.

## Mise à jour de l'app

Quand une nouvelle version d'`index.html` existe : repo `patrimoine` → `index.html` → ✏️ (edit) → tout remplacer → Commit. Les données ne sont pas touchées.
