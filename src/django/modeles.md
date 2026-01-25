# Les Modèles et la Base de Données

Dans la plupart des frameworks, il faut connaître le langage SQL pour parler à la base de données. Avec Django, on utilise un **ORM** (*Object-Relational Mapper*).

L'ORM fait la traduction pour vous : vous écrivez du **Python**, et Django le traduit en **SQL**.

### 1. Créer un Modèle

Ouvrez le fichier `blog/models.py`. Nous allons créer une structure pour nos articles de blog.

```python
from django.db import models
from django.utils import timezone

class Article(models.Model):
    titre = models.CharField(max_length=200)      # Texte court
    contenu = models.TextField()                 # Texte long
    date_publication = models.DateTimeField(default=timezone.now) # Date et heure
    auteur = models.CharField(max_length=100)

    def __str__(self):
        return self.titre

```

### 2. Les principaux types de champs (Fields)

Django propose de nombreux types de champs pour s'adapter à vos données :

* `CharField` : Pour les textes courts (titre, nom). Nécessite un `max_length`.
* `TextField` : Pour les textes longs (corps de l'article).
* `DateTimeField` : Pour les dates et heures.
* `IntegerField` : Pour les nombres entiers.
* `BooleanField` : Pour les cases à cocher (vrai/faux).
* `ForeignKey` : Pour lier un modèle à un autre (ex: lier un article à un auteur spécifique).

### 3. La Méthode `__str__()`

C'est une petite fonction très utile à l'intérieur de la classe. Elle dit à Django : *"Quand tu dois afficher cet objet (par exemple dans l'administration), utilise le titre plutôt que d'écrire <Article object (1)>"*.


# Les Migrations : Appliquer les changements

Une fois que vous avez écrit votre modèle, votre base de données ne le connaît pas encore. Il faut faire une **Migration**. C'est un processus en deux étapes :

### Étape 1 : Préparer le plan (`makemigrations`)

Django analyse vos fichiers `models.py` et crée un fichier de "planification" des changements.

```bash
#Windows
python manage.py makemigrations
# Mac
python3 manage.py makemigrations
```

### Étape 2 : Appliquer le plan (`migrate`)

Django exécute le plan et crée réellement les tables dans votre base de données (par défaut, un fichier `db.sqlite3`).

```bash
#Windows
python manage.py migrate
# Mac
python3 manage.py migrate
```
###  Mini-TP

Ajouter un champ `nombre_de_vues` (un entier) à leur modèle `Article`.
**Question :** Quelles sont les deux commandes à taper dans le terminal pour que ce changement soit pris en compte ?

