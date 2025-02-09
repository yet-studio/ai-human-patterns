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
    </header>

    <!-- Content -->
    <main class="w-full max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pt-10">
        <!-- Main content here -->
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