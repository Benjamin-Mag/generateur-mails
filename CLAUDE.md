# Projet : Générateur de mails audibene

## ⚠️ Repo git — toujours utiliser ce dossier
`C:\Users\Benjamin.MAGNIER\Documents\generateur-mails\`

### Fichier principal
`src\index.html` (~1960 lignes) — tout le code HTML + CSS + JS dans un seul fichier.

### FAUX AMI — ne jamais modifier
`C:\Users\Benjamin.MAGNIER\Documents\Claude\Projects\Générateur de mail\src\index.html`
→ Ancienne copie locale hors git. Les modifications ici ne sont JAMAIS déployées.

## Déploiement
GitHub Pages — push sur `main` déclenche le déploiement automatique.
```
git add src/index.html && git commit -m "..." && git push
```
URL : https://benjamin-mag.github.io/generateur-mails/

## Extension Chrome/Edge
Dossier : `C:\Users\Benjamin.MAGNIER\Desktop\ColleurMailSF\`
Fichiers clés : `popup.js`, `popup.html`, `manifest.json`

## Architecture appData
- `signatureName`, `phone`, `advisorGenre`, `onboardingDone`
- `sigPatientMail`, `sigPatientSMS`, `sigPartenaireMail` — contiennent des variables `{{nom_conseiller}}` etc.
- `templates[]`, `anamnese{}`, `customSituations[]`, `emailFooter`

## Variables système (auto-injectées dans buildFilledText)
- `{{nom_conseiller}}` → appData.signatureName
- `{{tel_conseiller}}` → appData.phone
- `{{titre_conseiller}}` → "Conseiller/Conseillère audibene"
