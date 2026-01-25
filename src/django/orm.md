# L'ORM Django : Parler à la Base de Données

L'**ORM** est un traducteur de haut niveau. Son rôle est de faire le pont entre deux mondes qui ne se ressemblent pas :

1. **Le monde Python** (Objets, Classes, Listes).
2. **Le monde SQL** (Tables, Lignes, Colonnes).

## 1. Pourquoi utiliser l'ORM ?

* **Abstraction :** Vous n'avez pas besoin d'écrire de SQL (`SELECT * FROM...`).
* **Sécurité :** Django protège automatiquement votre site contre les **injections SQL** (une attaque de hacker très courante).
* **Flexibilité :** Vous pouvez changer de base de données (passer de SQLite à PostgreSQL ou MySQL) sans changer une seule ligne de votre code Python.


## 2. Le "CRUD" avec l'ORM

Le **CRUD** représente les quatre opérations de base : **C**reate (Créer), **R**ead (Lire), **U**pdate (Modifier), **D**elete (Supprimer).

### A. Create (Créer des données)

Pour enregistrer une nouvelle entrée en base de données :

```python
# Méthode 1 : Instanciation puis save()
nouvel_article = Article(titre="Mon premier post", contenu="Bonjour le monde !")
nouvel_article.save()

# Méthode 2 : La méthode create() (plus rapide)
Article.objects.create(titre="Deuxième post", contenu="L'ORM est génial.")

```

### B. Read (Lire des données)

C'est ici qu'on utilise l'objet `objects` (appelé le "Manager").

```python
# Récupérer TOUS les articles
tous_les_articles = Article.objects.all()

# Récupérer un SEUL article (par son ID)
un_seul = Article.objects.get(id=1)

# Filtrer les données
articles_de_elias = Article.objects.filter(auteur="Elias")

# Rechercher une partie d'un texte (ex: titre contient "Python")
resultats = Article.objects.filter(titre__icontains="python")

```

### C. Update (Modifier des données)

```python
article = Article.objects.get(id=1)
article.titre = "Nouveau Titre"
article.save() # Ne pas oublier le save() !

```

### D. Delete (Supprimer des données)

```python
article = Article.objects.get(id=1)
article.delete()

```


## 3. Les QuerySets : Des listes intelligentes

Lorsque vous faites `Article.objects.filter(...)`, Django ne renvoie pas une simple liste, mais un **QuerySet**.

* **Lazy Loading (Chargement fainéant) :** Django n'interroge la base de données qu'au dernier moment (quand vous affichez vraiment les données). Cela économise énormément de ressources.
* **Chaînage :** Vous pouvez combiner les filtres.
```python
# Exemple : Les articles d'Elias publiés en 2026
Article.objects.filter(auteur="Elias").filter(date__year=2026).order_by('-date')

```

## 4. Explorer l'ORM avec le Shell Python

Un excellent moyen d'apprendre pour les étudiants est d'utiliser le **shell interactif** de Django. C'est un terminal où l'on peut taper du code Django en direct.

Commande à taper dans votre terminal :

```bash
#Windows
python manage.py shell
# Mac/Linux
python3 manage.py shell
```

Puis essayez :

```python
from blog.models import Article
Article.objects.count() # Affiche le nombre d'articles en base

```

### Le conseil : `get()` vs `filter()`

* Utilisez **`get()`** quand vous êtes SÛR qu'il n'y a qu'un seul résultat (ex: par ID). Si rien n'est trouvé, ça fait planter le site.
* Utilisez **`filter()`** quand il peut y avoir 0, 1 ou plusieurs résultats. Si rien n'est trouvé, il renvoie simplement une liste vide, sans faire planter le site.

---

###  Mini-TP

Allez dans le `shell` de Django et :

1. Créez 3 articles avec des auteurs différents.
2. Récupérez l'article qui a l'ID numéro 2.
3. Affichez tous les articles dont le titre contient la lettre "a".
4. Supprimez le dernier article créé.

