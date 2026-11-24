# ENSA·Assistant IA : système d'IA responsable et conforme au RGPD

Projet du module **Éthique et Droit du Numérique**, ENSA Béni Mellal (filière IA & Cybersécurité), encadré par Pr. Touil. Année universitaire 2025–2026.
Réalisé par Hassnae Latouti.

Conception d'un assistant IA pédagogique pour les étudiants et le personnel de l'ENSA, en conformité avec le **RGPD** et la loi marocaine **09-08** (CNDP). Les données personnelles sont bloquées avant d'être envoyées au modèle, et chaque échange est tracé.

## Le prototype

Application web (Flask, SQLite, API Groq avec Llama 3.3-70B) qui comprend :

- inscription et connexion, mots de passe hachés avec bcrypt ;
- conditions d'utilisation (CGU) à accepter explicitement avant le premier accès ;
- **filtre RGPD** : détection des données personnelles (par exemple une adresse e-mail), alerte et blocage de la requête avant l'appel à l'IA ;
- réponses générées par IA avec mention « contenu généré par une IA », et **mode dégradé** local si l'API est indisponible ;
- journal horodaté des échanges, avec suppression individuelle (droit à l'effacement, Art. 17) ;
- page profil pour corriger ses données (droit de rectification, Art. 16).

Les captures d'écran et le code commenté de `app.py` sont dans le rapport (section 4).

## Volet juridique et éthique

Le rapport ([docs/Rapport_EDN_LATOUTI.pdf](docs/Rapport_EDN_LATOUTI.pdf)) contient :

- l'analyse juridique : bases légales, droits des personnes, principes du RGPD, AIPD (Art. 35), registre des traitements (Art. 30), procédure en cas de violation, conformité CNDP ;
- la cartographie des risques éthiques avec matrice probabilité × gravité ;
- le cadre de gouvernance : acteurs, supervision humaine, transparence ;
- la politique d'utilisation (CGU) et la définition de conformité en 10 critères.

L'énoncé du projet est dans [docs/Enonce_Mini-Projet_EDN.pdf](docs/Enonce_Mini-Projet_EDN.pdf).

## Technologies

Python (Flask), SQLite, templates Jinja2 (HTML/CSS), API Groq (Llama 3.3-70B), bcrypt, python-dotenv.

## Contenu du dépôt

```
docs/
  Rapport_EDN_LATOUTI.pdf     rapport complet du projet
  Enonce_Mini-Projet_EDN.pdf  énoncé du module
```
