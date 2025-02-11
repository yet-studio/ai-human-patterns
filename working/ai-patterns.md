# Patterns d'Interaction IA

## Structure de Pattern
- **Description** : Définition claire et concise
- **Déclencheur** : Événement ou contexte d'activation
- **Comportement** : Actions et règles spécifiques
- **Validation** : Critères de succès et vérifications
- **Contexte** : Situation de découverte et justification
- **Validé le** : Date de validation formelle

## Patterns de Communication

### terminal_insert
- **Description** : Mode par défaut pour tout contenu terminal - insertion directe plutôt que présentation
- **Déclencheur** : Détection automatique de contenu destiné au terminal
- **Comportement** :
  - DEFAULT: Insertion directe dans le terminal
  - FALLBACK: Présentation en bloc de code si insertion impossible
  - Format:
    ```bash
    # Description (si nécessaire)
    commande_effective
    ```
  - UI:
    - Bouton libellé "Insert in Terminal"
    - Action par défaut: insertion directe
    - Indication claire du mode terminal
- **Validation** :
  - Vérification de la compatibilité terminal
  - Confirmation de l'exécution
  - Retour d'état si disponible
  - Cohérence UI/UX
- **Contexte** : Optimisation des interactions terminal et standardisation
- **Validé le** : 11 Février 2025

### raw_mode
- **Description** : Mode de communication direct sans reformatage
- **Déclencheur** : Besoin de transmission d'information brute
- **Comportement** :
  - Transmission directe du contenu
  - Pas de reformatage
  - Pas d'embellissement
- **Validation** :
  - Contenu transmis intact
  - Format préservé
  - Efficacité vérifiée
- **Contexte** : Amélioration de l'efficacité des échanges IA-Humain
- **Validé le** : 10 Février 2025

### placeholder_syntax
- **Description** : Utilisation systématique de `{{ ... }}` pour le code inchangé
- **Déclencheur** : Proposition de modification de code
- **Comportement** :
  - Marquage des sections inchangées
  - Focus sur les modifications
  - Clarté visuelle maximale
- **Validation** :
  - Sections clairement identifiées
  - Modifications évidentes
  - Facilité de compréhension
- **Contexte** : Standardisation des propositions de code
- **Validé le** : 11 Février 2025

### proactive_readonly
- **Description** : Assistance premium proactive en mode read-only
- **Déclencheur** : Activation du mode read-only
- **Comportement** :
  - Propositions détaillées sans modifications directes
  - Anticipation des besoins
  - Documentation complète
  - Maintien du niveau premium
- **Validation** :
  - Respect des contraintes read-only
  - Qualité des propositions
  - Satisfaction utilisateur
- **Contexte** : Optimisation de l'assistance en mode read-only
- **Validé le** : 11 Février 2025

## Notes
- Les patterns sont identifiés et documentés au fil des interactions
- L'objectif est d'améliorer l'efficacité de la communication
- La structure des patterns est standardisée pour une meilleure cohérence
- Chaque pattern doit inclure tous les éléments de la structure définie