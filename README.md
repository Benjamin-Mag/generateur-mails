# Générateur de mails — audibene

Application web (page unique `src/index.html`) pour générer les mails et SMS envoyés aux patients et partenaires audioprothésistes. Salesforce ne permet pas de personnaliser facilement ses modèles de mail — cette app génère le texte, une extension Chrome/Edge (ColleurMailSF) le colle ensuite dans l'éditeur Salesforce.

Déployée sur GitHub Pages : https://benjamin-mag.github.io/generateur-mails/

## Utilisation

Choisir un modèle (onglets **Patient** / **Partenaire**), remplir les champs (nom, heure de RDV, etc.), copier le texte généré (bouton copier) et le coller dans Salesforce via l'extension ColleurMailSF, ou directement à la main.

Onglets : **Patient** · **Partenaire** · **Anamnèse** · **Templates** · **Bibliothèque**, + Tutoriel / Réglages.

## Déploiement

Push sur `main` → déploiement automatique GitHub Actions.

```
git add src/index.html && git commit -m "..." && git push
```

## Projets frères (couplés)

- **ColleurDoctolib** (`..\Colleur Doco\`) — copie les infos patient depuis Salesforce ; les boutons "📋 Coller depuis Salesforce" de l'onglet Patient/Partenaire de cette app lisent le JSON qu'il produit (clés `patient`/`partenaire`/`adresse`). Si l'un des deux change le nom de ces clés, l'autre casse silencieusement.
- **ColleurMailSF** (`..\ColleurMailSF\`) — colle le mail généré ici dans l'éditeur Salesforce (format attendu : `sujet\ncorps` en texte brut dans le presse-papier).

## Dossier public/

Le workflow de déploiement ne publie que `src/` :
- `src/public/ColleurMailSF.zip` — copie de secours de l'extension ColleurMailSF, téléchargeable depuis Réglages
- `src/public/privacy.html` — politique de confidentialité (Edge Add-ons Store)
