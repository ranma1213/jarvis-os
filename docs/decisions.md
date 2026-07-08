# Décisions

Ce fichier garde la trace des choix importants de JARVIS OS.

Chaque décision doit expliquer le contexte, le choix retenu et les conséquences. L'objectif est d'éviter de rediscuter les mêmes sujets dans trois mois sans mémoire claire.

## Format

```text
### YYYY-MM-DD - Titre

Contexte :

Décision :

Pourquoi :

Conséquences :
```

## Journal

### 2026-07-08 - Construire le cerveau avant les workflows

Contexte :

La tentation naturelle serait de commencer directement par n8n, Ollama ou des agents prêts à l'emploi.

Décision :

JARVIS OS commence par ses documents fondateurs : vision, architecture, roadmap, décisions et principes techniques.

Pourquoi :

Un système d'agents devient vite confus s'il n'a pas de règles de décision communes. Les workflows doivent implémenter une architecture claire, pas servir de substitut à l'architecture.

Conséquences :

Le premier chantier est documentaire et conceptuel. n8n arrive ensuite, une fois le routeur intelligent et les règles de décision définis.

### 2026-07-08 - Ne pas utiliser les AI Agents n8n au début

Contexte :

n8n propose des fonctionnalités d'agents IA, mais les utiliser trop tôt risque de masquer la logique centrale du système.

Décision :

Le premier workflow n8n sera volontairement simple : Telegram -> Jarvis Core -> classification -> choix d'agent -> réponse.

Pourquoi :

Le routeur intelligent doit appartenir à JARVIS OS, pas être enfermé dans une abstraction trop tôt.

Conséquences :

Même avec un seul agent initial, l'architecture prépare l'ajout futur de plusieurs agents spécialisés.

### 2026-07-08 - Utiliser PostgreSQL dans Docker pour la mémoire

Contexte :

JARVIS OS aura besoin d'une mémoire interrogeable : historique, sessions, projets, logs, erreurs et décisions.

Décision :

La mémoire persistante partira sur PostgreSQL 16 lancé avec Docker Compose. pgAdmin est ajouté dans le même compose pour inspecter la base via une interface graphique.

Pourquoi :

Des fichiers JSON seraient pratiques au début, mais deviendraient vite limitants pour filtrer par date, rechercher dans l'historique, analyser les patterns et relier les données entre elles.

Conséquences :

L'infrastructure de base vit dans `docker/postgres/docker-compose.yml`. PostgreSQL est exposé sur le port `5432`, pgAdmin sur le port `5050`.
