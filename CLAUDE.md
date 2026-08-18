# Projet : Générateur de mails audibene

## Repo git — ce dossier
`C:\Users\Benjamin.MAGNIER\Documents\Claude\Projects\Générateur de mail\`
(Déplacé ici le 2026-08-18 depuis `Documents\generateur-mails\`, qui a été supprimé — ce dossier EST maintenant le repo git, avec tout l'historique. Il n'y a plus de "faux ami" séparé.)

### Fichier principal
`src\index.html` (~2200+ lignes) — tout le code HTML + CSS + JS dans un seul fichier.

## Déploiement
GitHub Pages — push sur `main` déclenche le déploiement automatique.
```
git add src/index.html && git commit -m "..." && git push
```
URL : https://benjamin-mag.github.io/generateur-mails/

## Extensions Chrome/Edge liées (dossiers frères, sous Documents\Claude\Projects\)
- `..\ColleurMailSF\` — colle le mail généré dans l'éditeur Salesforce
- `..\Colleur Doco\` — copie les infos patient depuis Salesforce, colle sur Doctolib/Acuitis

### ⚠️ Contrat JSON partagé avec ColleurDoctolib
Les boutons "📋 Coller depuis Salesforce" de `src/index.html` (`pasteSFBtn`/`pasteSFPartBtn`/`pasteSFAddrBtn`, fonction `parseSFClip(key)`) lisent un JSON du presse-papier avec les clés `patient`/`partenaire`/`adresse`. Ce JSON est produit par le bouton "📋 Copier les infos patient" de ColleurDoctolib (`Colleur Doco\popup.js`, fonction `extraireEtCopier`). **Si l'un des deux change le nom de ces clés, l'autre casse silencieusement** (le champ reste vide, pas d'erreur visible). Toujours vérifier les deux côtés ensemble en cas de modif.

## Architecture appData
- `signatureName`, `phone`, `advisorGenre`, `onboardingDone`
- `sigPatientMail`, `sigPatientSMS`, `sigPartenaireMail` — contiennent des variables `{{nom_conseiller}}` etc.
- `templates[]`, `anamnese{}`, `customSituations[]`, `emailFooter`

## Variables système (auto-injectées dans buildFilledText)
- `{{nom_conseiller}}` → appData.signatureName
- `{{tel_conseiller}}` → appData.phone
- `{{titre_conseiller}}` → "Conseiller/Conseillère audibene"
