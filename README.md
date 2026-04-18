# Portefolio — Alexis MATHIEU

Site portfolio statique (**Vite**, **React**, **TypeScript**, GSAP, Lenis, **Three.js / R3F** pour le hero). Code source : [github.com/alexismathieu-ui/Portefolio](https://github.com/alexismathieu-ui/Portefolio).

**Site en ligne (après activation de GitHub Pages)** : [alexismathieu-ui.github.io/Portefolio](https://alexismathieu-ui.github.io/Portefolio/)

## Pousser le code vers GitHub

À la racine du dossier du projet (celui qui contient `package.json`) :

```bash
git init
git add .
git commit -m "Portfolio Vite + React"
git branch -M main
git remote add origin https://github.com/alexismathieu-ui/Portefolio.git
git push -u origin main
```

Si `git remote add` échoue car `origin` existe déjà :

```bash
git remote set-url origin https://github.com/alexismathieu-ui/Portefolio.git
git push -u origin main
```

### Le dépôt GitHub a déjà un README (historique différent)

Tu peux fusionner l’historique distant avec le tien :

```bash
git pull origin main --allow-unrelated-histories
# résoudre les conflits si Git en signale, puis :
git push -u origin main
```

Ou, si le dépôt distant ne contient qu’un README à remplacer et tu acceptes d’écraser :

```bash
git push -u origin main --force
```

(à utiliser seulement si tu es sûr de ne pas perdre de travail sur GitHub.)

## Publier sur GitHub Pages

1. Sur le dépôt : **Settings** → **Pages** → **Build and deployment** → **Source** : **GitHub Actions**.
2. Le workflow [`.github/workflows/deploy-github-pages.yml`](.github/workflows/deploy-github-pages.yml) build et publie `dist` à chaque push sur `main` ou `master`.
3. L’URL du site est en général **`https://alexismathieu-ui.github.io/Portefolio/`** (le `base` Vite utilise automatiquement le nom du dépôt `Portefolio`).

## Démarrage en local

```bash
npm install
npm run dev
```

Build de production :

```bash
npm run build
npm run preview
```

Tester un build comme sur Pages (sous-chemin) :

```powershell
$env:GITHUB_REPOSITORY='alexismathieu-ui/Portefolio'; npm run build; npm run preview
```

## Personnalisation

- **Profil, bio, compétences, liens** : [`src/data/profile.ts`](src/data/profile.ts)
- **Projets** : [`src/data/projects.ts`](src/data/projects.ts)
- **CV** : [`public/cv.pdf`](public/cv.pdf)

## Accessibilité & performances

- Le hero **WebGL** est désactivé sur petits écrans, si le CPU est faible ou si **`prefers-reduced-motion`** est activé : fond **CSS** de secours.
- **Lenis** est désactivé lorsque `prefers-reduced-motion` est activé.

## Messages dans la console du navigateur

- **React DevTools** en dev uniquement.
- **`THREE.Clock` déprécié** : vérifier `three@0.182.0` et cache navigateur.
- **`chrome-extension://…`** : souvent une extension, pas le site.
