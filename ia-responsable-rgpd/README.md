# ENSA·Assistant IA : système d'IA responsable et conforme au RGPD

Projet du module **Éthique et Droit du Numérique**, ENSA Béni Mellal (filière IA & Cybersécurité), encadré par Pr. Touil. Année universitaire 2025–2026.
Réalisé par Hassnae Latouti.

Application web qui permet aux étudiants et au personnel de poser des questions à un assistant IA tout en respectant le RGPD et la loi marocaine 09-08. Les données personnelles sont bloquées **avant** d'être envoyées au modèle, et chaque échange est tracé.

## Fonctionnalités

- Inscription et connexion, mots de passe hachés avec bcrypt
- Conditions d'utilisation (CGU) à accepter explicitement avant le premier accès
- **Filtre RGPD** (`rgpd.py`) : détecte les données personnelles (par exemple une adresse e-mail), affiche une alerte et bloque la requête
- Réponses générées par Llama 3.3-70B via l'API Groq, avec mention « contenu généré par une IA »
- **Mode dégradé** local si l'API est indisponible
- Journal horodaté des échanges dans SQLite, avec suppression individuelle (droit à l'effacement, Art. 17)
- Page profil pour corriger ses données (droit de rectification, Art. 16)

## Volet juridique et éthique

Le rapport ([docs/Rapport_EDN_LATOUTI.pdf](docs/Rapport_EDN_LATOUTI.pdf)) contient :

- l'analyse juridique : bases légales, droits des personnes, principes du RGPD, AIPD (Art. 35), registre des traitements (Art. 30), procédure en cas de violation, conformité CNDP ;
- la cartographie des risques éthiques avec matrice probabilité × gravité ;
- le cadre de gouvernance : acteurs, supervision humaine, transparence ;
- la politique d'utilisation (CGU) et la définition de conformité en 10 critères.

L'énoncé du projet est dans [docs/Enonce_Mini-Projet_EDN.pdf](docs/Enonce_Mini-Projet_EDN.pdf).

## Technologies

Python (Flask), SQLite, templates Jinja2 (HTML/CSS), API Groq (Llama 3.3-70B), bcrypt, python-dotenv.

## Structure

```
app.py          contrôleur Flask (routes)
database.py     base SQLite et journalisation
rgpd.py         filtre des données personnelles
degrade.py      réponses locales si l'API est indisponible
templates/      login, register, cgu, index, historique, profil
docs/           rapport et énoncé
```

## Lancer le projet

```bash
pip install -r requirements.txt
cp .env.example .env      # puis renseigner GROQ_API_KEY
python app.py
```

Ouvrir ensuite http://127.0.0.1:5000

## Note

Prototype pédagogique réalisé dans le cadre d'un module universitaire. La clé API est stockée dans un fichier `.env` qui n'est pas versionné.
