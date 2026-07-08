# JARVIS OS

JARVIS OS est un assistant IA personnel conçu pour automatiser des tâches, aider au développement logiciel et coordonner des agents spécialisés.

Le projet suit une idée simple : construire le cerveau avant les workflows.

## Point de départ

Avant d'ouvrir n8n ou d'ajouter des agents, JARVIS OS doit définir :

- pourquoi il existe ;
- comment il décide ;
- quand il agit ;
- quand il demande confirmation ;
- comment il choisit entre local et cloud ;
- comment il apprend de ses erreurs.

## Documents principaux

- `docs/vision.md` : objectif, priorités et principes fondateurs.
- `docs/architecture.md` : architecture initiale et responsabilités des composants.
- `docs/roadmap.md` : étapes de construction.
- `docs/decisions.md` : journal des décisions importantes.
- `docs/principles.md` : règles techniques de comportement de JARVIS OS.

## Structure

- `docs/` : documentation fondatrice.
- `workflows/` : futurs workflows n8n.
- `docker/` : services locaux lancés avec Docker.
- `database/` : schémas, migrations et notes liées à PostgreSQL.
- `prompts/` : prompts réutilisables.
- `memory/` : mémoire projet, préférences et contexte durable.
- `scripts/` : scripts utiles au projet.
- `tests/` : tests du routeur, des agents et des workflows.
- `backups/` : sauvegardes.

## Infrastructure locale

PostgreSQL et pgAdmin sont définis dans `docker/postgres/docker-compose.yml`.

- PostgreSQL : `localhost:5432`
- Base : `jarvis`
- Utilisateur : `jarvis`
- Mot de passe : `jarvis_password`
- pgAdmin : `http://localhost:5050`
- Email pgAdmin : `admin@jarvis-os.com`
- Mot de passe pgAdmin : `admin123`

Dans pgAdmin, le host PostgreSQL à utiliser est `postgres` quand pgAdmin tourne dans le même Docker Compose.

## Prochaine étape

Définir précisément le format interne utilisé par Jarvis Core pour classifier une demande et choisir un agent.
