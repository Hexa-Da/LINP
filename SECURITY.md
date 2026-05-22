# Sécurité — secrets et clés

## Fichiers jamais versionnés

| Fichier | Emplacement |
|---------|-------------|
| `.env` | Racine du projet |
| `google-services.json` | `android/app/` |
| `GoogleService-Info.plist` | `ios/App/App/` |
| Keystores (`*.keystore`, `*.jks`) | `android/app/` |

Copier les modèles `.example`, puis télécharger les vrais fichiers depuis la [console Firebase](https://console.firebase.google.com) → projet **LINP** → Paramètres → vos applications Android / iOS.

## Configuration locale

```bash
cp .env.example .env
# Remplir toutes les variables VITE_* et GOOGLE_AUTH_*

cp android/app/google-services.json.example android/app/google-services.json
# Remplacer YOUR_* par les valeurs du fichier téléchargé depuis Firebase

cp ios/App/App/GoogleService-Info.plist.example ios/App/App/GoogleService-Info.plist
# Idem pour iOS
```

## Clés exposées sur GitHub ?

1. **Révoquer / régénérer** les clés API : [Google Cloud Console](https://console.cloud.google.com/apis/credentials) → projet `linp-58b43`.
2. Mettre à jour `.env` et les fichiers Firebase locaux (non commités).
3. Ne jamais committer de clés dans `src/firebase.ts` : uniquement `import.meta.env.VITE_*`.

## Configuration web

Toutes les clés Firebase web passent par `.env` (`VITE_FIREBASE_*`). Le fichier `src/firebase.ts` ne contient **aucune** clé en dur.
