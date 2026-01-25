#  Créer son premier projet Django

C'est ici que tout commence. Nous allons passer d'un dossier vide à un serveur web fonctionnel. Suivez bien chaque étape, l'ordre est primordial !

### 1. Préparation du terrain

Assurez-vous d'être dans votre dossier de projet et que votre environnement virtuel est **activé**.

```bash
# Activation (rappel)
# Windows : 
.venv\Scripts\activate
# Mac/Linux : 
source .venv/bin/activate

```

### 2. Installation de Django

On installe la dernière version stable de Django via `pip`. et `pip3` pour les Mac

```bash
#Windows :
pip install django
#Mac/linux :
pip3 install django
```

### 3. Création du Projet (La structure globale)

Un "Projet" Django est le conteneur global de votre site. Tapez la commande suivante (n'oubliez pas le **point** à la fin, il est très important pour garder une structure propre) :

```bash
django-admin startproject monsite .

```

> **Pourquoi le point ?** Sans le point, Django crée un sous-dossier inutile qui complique la gestion des fichiers. Avec le point, il installe tout directement là où vous êtes.

### 4. Création de l'Application (Le module métier)

Dans Django, un projet est divisé en **Applications**. Un projet "Site de Cours" pourrait avoir une application `cours`, une application `utilisateurs`, etc. Créons notre première app :

```bash
#Windows :
python manage.py startapp blog
#Mac/linux :
python3 manage.py startapp blog
```

### 5. Enregistrer l'application

Django ne devine pas que vous avez créé une app. Il faut lui dire !
Ouvrez le fichier `monsite/settings.py` et cherchez la liste `INSTALLED_APPS`. Ajoutez `'blog',` à la liste :

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    # Votre application ici :
    'blog',
]

```

### 6. Lancer le serveur    

C'est le moment de vérité. Tapez cette commande :

```bash
#Windows :
python manage.py runserver
#Mac / Linux :
python3 manage.py runserver
```

Ouvrez votre navigateur et allez à l'adresse : `http://127.0.0.1:8000`.
Si vous voyez une fusée décoller, félicitations : **votre serveur Django est en vie !**


### Comprendre les fichiers générés

| Fichier | Rôle |
| --- | --- |
| `manage.py` | Votre couteau suisse. C'est via ce fichier qu'on lance toutes les commandes. |
| `settings.py` | La configuration (base de données, langue, apps installées). |
| `urls.py` | L'aiguillage du site (qui va vers quelle page). |
| `models.py` | (Dans le dossier blog) Où on définit nos données. |
| `views.py` | (Dans le dossier blog) Où on écrit notre logique Python. |

---

### L'erreur à ne pas faire

> Ne fermez jamais votre terminal pendant que `runserver` tourne, sinon votre site s'arrêtera. Pour reprendre la main sur le terminal, faites `Ctrl + C`.

