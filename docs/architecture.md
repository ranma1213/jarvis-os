# Architecture

L'architecture de JARVIS OS doit rester simple au départ, mais prête à grandir.

## Schéma initial

```text
Utilisateur
    |
    v
Telegram
    |
    v
Jarvis Core
    |
    v
Classifier la demande
    |
    v
Routeur intelligent
    |
    +--> Agent général
    +--> Agent dev
    +--> Agent recherche
    +--> Agent automatisation
    +--> Agent mémoire
    |
    v
Réponse + mémoire + journal de décision si nécessaire
```

## Composants

### Telegram

Interface d'entrée principale au début du projet. Telegram reçoit les demandes utilisateur et transmet le message à JARVIS Core.

### Jarvis Core

Centre de décision du système. Il ne doit pas agir immédiatement. Il doit d'abord comprendre la demande, estimer le risque, choisir un agent et décider s'il faut demander confirmation.

### Classifier

Analyse la demande et identifie :

- l'intention ;
- le niveau de risque ;
- le besoin de mémoire ;
- le besoin d'outil ;
- le modèle recommandé ;
- l'agent cible.

### Routeur intelligent

Choisit l'agent ou le workflow adapté. Au début, il peut ne router que vers un seul agent. Sa structure doit cependant permettre l'ajout progressif d'agents spécialisés.

### Agents

Chaque agent a une responsabilité claire. Un agent ne doit pas décider seul de contourner les règles globales de JARVIS OS.

### Mémoire

Stocke les informations utiles au long terme : préférences, décisions, erreurs, contexte projet, habitudes utilisateur. La mémoire ne doit pas devenir un journal brut illisible.

## Principes d'architecture

- Le routeur est plus important que les agents.
- Les agents exécutent, mais JARVIS Core décide.
- Chaque action risquée doit passer par une étape de validation.
- La mémoire doit être utile, courte et consultable.
- Les workflows n8n doivent rester compréhensibles.
- Les choix techniques importants doivent être inscrits dans `decisions.md`.
