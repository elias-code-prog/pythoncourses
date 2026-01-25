 **Développement Web Professionnel**.

# Introduction à Django

Si Python est le langage, **Django** est votre boîte à outils géante. On l'appelle le framework pour les *"perfectionnistes sous pression"* car il permet de créer des sites web très rapidement sans sacrifier la sécurité.

### 1. Pourquoi utiliser un Framework ?

Sans Django, pour créer un site, vous devriez coder vous-même :

* La connexion à la base de données.
* Le système de connexion des utilisateurs.
* La sécurité contre les hackers.
* L'interface d'administration pour gérer vos articles.

**Django fait tout cela pour vous, par défaut.** 

C'est ce qu'on appelle la philosophie **"Batteries Included"**.

### 2. Le concept de l'architecture MVT

C'est le point le plus important à comprendre. Django sépare le travail en trois parties :

* **M (Modèle)** : Les données. C'est ici qu'on définit à quoi ressemble un "Utilisateur" ou un "Produit" dans la base de données.
* **V (Vue)** : Le cerveau. C'est la logique Python qui décide quoi afficher (ex: "Cherche les 5 derniers articles").
* **T (Template)** : Le design. C'est le fichier HTML qui affiche les informations à l'utilisateur.

### 3. Comment fonctionne une requête web ?

Voici ce qui se passe quand un utilisateur tape l'adresse de votre site :

1. **L'URL** : Django regarde l'adresse demandée (ex: `/blog/`).
2. **La Vue** : L'URL envoie l'utilisateur vers une fonction Python (la Vue).
3. **Le Modèle** : La Vue va chercher les données dans la base (si besoin).
4. **Le Template** : La Vue prend les données, les injecte dans le HTML et envoie le tout au navigateur de l'étudiant.

---

### Ce qu'on va construire ensemble

Dans cette partie du cours, nous n'allons pas faire de petits exercices. Nous allons construire une **application complète** (comme un Blog) étape par étape.

### Un dernier rappel important

Avant de passer à la suite, assurez-vous que votre **environnement virtuel** (`.venv`) est bien activé dans votre terminal. C'est la règle d'or numéro 1 de Django.

---
    