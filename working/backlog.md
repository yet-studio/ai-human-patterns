# Configuration Technique - AI Human Patterns
# Version: 2024-2025
# Basé sur Preline UI + Tailwind CSS

# 1. INITIALISATION DU PROJET
# ---------------------------
# Création du projet
mkdir ai-human-patterns-web
cd ai-human-patterns-web

# Initialisation de npm
npm init -y

# 2. INSTALLATION DES DÉPENDANCES
# ------------------------------
# Installation de Tailwind CSS
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest
npx tailwindcss init -p

# Installation de Preline UI
npm install preline

# 3. CONFIGURATION DE TAILWIND
# ---------------------------
# Remplacer le contenu de tailwind.config.js par:
cat > tailwind.config.js << 'EOL'
module.exports = {
  content: [
    "./src/**/*.{html,js}",
    "node_modules/preline/dist/*.js",
  ],
  theme: {
    extend: {},
  },
  plugins: [
    require('preline/plugin'),
  ],
}
EOL

# 4. CONFIGURATION DU CSS
# ----------------------
# Créer le fichier CSS principal
mkdir src/css
cat > src/css/main.css << 'EOL'
@tailwind base;
@tailwind components;
@tailwind utilities;
EOL

# 5. CONFIGURATION DU HTML
# -----------------------
# Créer le fichier HTML de base
mkdir src
cat > src/index.html << 'EOL'
<!DOCTYPE html>
<html lang="fr" class="h-full">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Human Patterns</title>
    <link href="./css/main.css" rel="stylesheet">
</head>
<body class="bg-gray-50 dark:bg-slate-900">
    <!-- Navigation -->
    <header class="flex flex-wrap sm:justify-start sm:flex-nowrap z-50 w-full bg-white border-b border-gray-200 text-sm py-3 sm:py-0 dark:bg-gray-800 dark:border-gray-700">
        <!-- Navbar content here -->
        nav
    </header>

    <!-- Content -->
    <main class="w-full max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pt-10">
        <!-- Main content here -->
        test content
    </main>

    <!-- Scripts -->
    <script src="./node_modules/preline/dist/preline.js"></script>
</body>
</html>
EOL

# 6. CONFIGURATION DU BUILD
# ------------------------
# Installation des outils de build
npm install -D vite

# Ajout des scripts dans package.json
npm pkg set scripts.dev="vite"
npm pkg set scripts.build="vite build"
npm pkg set scripts.preview="vite preview"

# 7. CONFIGURATION DE GIT
# ----------------------
# Initialisation de Git
git init

# Création du .gitignore
cat > .gitignore << 'EOL'
node_modules
dist
.DS_Store
EOL

# 8. COMMANDES DE DÉVELOPPEMENT
# ---------------------------
# Démarrer le serveur de développement
npm run dev

# Pour build en production
npm run build

# Pour prévisualiser le build
npm run preview

# 9. NOTES IMPORTANTES
# ------------------
# - Assurez-vous d'avoir Node.js v14+ installé
# - Tous les composants Preline nécessitent JavaScript
# - Le dark mode est configuré par défaut
# - Les chemins dans tailwind.config.js doivent être ajustés selon votre structure

# 10. STRUCTURE DES DOSSIERS FINALE
# -------------------------------
# ai-human-patterns-web/
# ├── node_modules/
# ├── src/
# │   ├── css/
# │   │   └── main.css
# │   ├── js/
# │   │   └── main.js
# │   └── index.html
# ├── .gitignore
# ├── package.json
# ├── postcss.config.js
# └── tailwind.config.js

# 11. INTÉGRATION DU TEMPLATE AI PROMPT
# ----------------------------------
# Copie du template Preline AI Prompt
mkdir -p src/templates
curl -o src/templates/ai-prompt.html https://preline.co/templates/ai-prompt/ai-with-sidebar.html

# Adaptation du template
# - Extraction des composants
mkdir -p src/components
touch src/components/Sidebar.js
touch src/components/Chat.js
touch src/components/Header.js

# Configuration des routes
npm install -D @vitejs/plugin-vue
touch vite.config.js

# 12. CONFIGURATION GITHUB PAGES
# ---------------------------
# Installation des outils de déploiement
npm install -D gh-pages

# Ajout du script de déploiement
npm pkg set scripts.deploy="gh-pages -d dist"

# Configuration du déploiement
cat > .github/workflows/deploy.yml << 'EOL'
name: Deploy to GitHub Pages
on:
  push:
    branches: [ main ]
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Install
        run: npm ci
      - name: Build
        run: npm run build
      - name: Deploy
        uses: JamesIves/github-pages-deploy-action@4.1.5
        with:
          branch: gh-pages
          folder: dist
EOL

# 13. SYSTÈME DE NAVIGATION
# ----------------------
# Installation du router
npm install vue-router@4

# Configuration des routes
mkdir -p src/router
touch src/router/index.js

# Structure des routes
cat > src/router/index.js << 'EOL'
import { createRouter, createWebHistory } from 'vue-router'

const routes = [
  {
    path: '/',
    name: 'Episodes',
    component: () => import('../views/Episodes.vue')
  },
  {
    path: '/analyses',
    name: 'Analyses',
    component: () => import('../views/Analyses.vue')
  }
]

export const router = createRouter({
  history: createWebHistory(),
  routes
})
EOL

# 14. COMPOSANTS DE BASE
# --------------------
# Création des composants Vue
mkdir -p src/components
touch src/components/EpisodeList.vue
touch src/components/AnalysisSidebar.vue
touch src/components/ChatThread.vue
touch src/components/MetaAnalysis.vue

# 15. SYSTÈME DE BUILD PRODUCTION
# ----------------------------
# Configuration de la compression
npm install -D compression-webpack-plugin

# Configuration du build
cat > vue.config.js << 'EOL'
const CompressionPlugin = require('compression-webpack-plugin')

module.exports = {
  configureWebpack: {
    plugins: [
      new CompressionPlugin({
        algorithm: 'gzip',
        test: /\.(js|css|html|svg)$/,
        threshold: 10240,
        minRatio: 0.8
      })
    ]
  }
}
EOL

# 16. TESTS ET VALIDATION
# ---------------------
# Installation des outils de test
npm install -D vitest @vue/test-utils
npm install -D @testing-library/vue

# Configuration des tests
mkdir -p tests/unit
touch tests/unit/EpisodeList.spec.js
touch tests/unit/ChatThread.spec.js

# Ajout du script de test
npm pkg set scripts.test="vitest"
npm pkg set scripts.coverage="vitest run --coverage"
