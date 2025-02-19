# Configuration Technique - AI Human Patterns
# Version: 2024-2025

# 0. STRATÉGIE MVP (IMMÉDIAT)
# ---------------------------
# Phase 1 - Focus sur le contenu
mkdir -p working/episodes working/patterns

# Structure MVP initiale
# working/
# ├── episodes/        # Interactions IA-Humain documentées
# │   └── ep01.md     # Format: Contexte > Dialogue > Pattern
# └── patterns/       # Patterns identifiés et documentés
#     └── pattern01.md

# Processus MVP:
# 1. Documenter les interactions réelles
# 2. Identifier les patterns émergents
# 3. Itérer et affiner
# 4. Structurer progressivement

# 1. COURT TERME (1-2 MOIS)
# -------------------------
# Version Statique Simple
mkdir ai-human-patterns-web
cd ai-human-patterns-web

# Installation minimale
npm init -y
npm install -D tailwindcss@latest
npx tailwindcss init

# Configuration Tailwind basique
cat > tailwind.config.js << 'EOL'
module.exports = {
  content: ["./src/**/*.{html,md}"],
  theme: {
    extend: {},
  },
}
EOL

# Structure simple
src/
├── index.html        # Page d'accueil basique
└── episodes/         # Conversion MD -> HTML

# 2. MOYEN TERME (2-4 MOIS)
# -------------------------
# Enrichissement Interface
npm install preline
npm install -D vite

# Ajout composants basiques
src/
├── components/
│   ├── EpisodeList.js
│   └── PatternView.js
└── css/
    └── main.css

# 3. LONG TERME (4-6 MOIS)
# ------------------------
# Fonctionnalités Avancées
- Vue Router
- Système de recherche
- Meta-analyses
- Tests unitaires

# Installation complète (quand nécessaire)
npm install vue-router@4
npm install -D @vitejs/plugin-vue
npm install -D vitest @vue/test-utils
npm install -D @testing-library/vue

# 4. OPTIONNEL/FUTUR
# ------------------
# Fonctionnalités à évaluer selon besoins
- GitHub Pages deployment
- Compression webpack
- Dark mode
- PWA features

# Notes:
# - Commencer par le contenu et la documentation
# - Évoluer progressivement vers l'interface technique
# - Adapter la complexité selon les besoins réels
