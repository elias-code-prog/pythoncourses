# L'Interface d'Administration

Contrairement à d'autres frameworks où vous devez coder vous-même vos pages de gestion, Django vous offre un "Back-Office" complet dès l'installation.

### 1. Accéder à l'administration

Par défaut, l'URL est `http://127.0.0.1:8000/admin`. Mais avant d'y entrer, vous avez besoin d'une clé d'accès : le **Super-utilisateur**.

Tapez cette commande dans votre terminal :

```bash
python manage.py createsuperuser
#Mac
python3 manage.py createsuperuser

```

Suivez les instructions (nom d'utilisateur, email, mot de passe).
*Note : Pour des raisons de sécurité, le mot de passe ne s'affiche pas quand vous le tapez.*


### 2. Enregistrer vos modèles

Par défaut, l'administration est vide. Pour voir votre modèle `Article`, vous devez "l'enregistrer" dans le fichier `blog/admin.py`.

```python
from django.contrib import admin
from .models import Article

admin.site.register(Article)

```

### 3. Personnaliser l'affichage (`ModelAdmin`)

L'affichage par défaut n'est pas toujours pratique (il affiche juste le titre). On peut le rendre beaucoup plus puissant en créant une classe de configuration.

Modifiez votre `blog/admin.py` :

```python
@admin.register(Article)
class ArticleAdmin(admin.ModelAdmin):
    # Colonnes à afficher dans la liste
    list_display = ('titre', 'auteur', 'date_publication', 'est_publie')
    
    # Ajouter une barre de recherche
    search_fields = ('titre', 'contenu')
    
    # Ajouter des filtres sur le côté
    list_filter = ('date_publication', 'auteur')
    
    # Rendre certains champs modifiables directement depuis la liste
    list_editable = ('auteur',)

```


### 4. Pourquoi c'est une fonctionnalité pratique ?

* **Sécurité** : L'administration utilise le système de permissions de Django. Vous pouvez créer des comptes pour des rédacteurs qui n'ont le droit de modifier que les articles, mais pas de toucher aux réglages du site.
* **Rapidité** : Pour un client qui veut gérer son catalogue de produits, l'outil est prêt en 5 minutes.
* **Validation** : L'administration utilise vos **Formulaires** internes. Si vous avez défini qu'un titre ne peut pas dépasser 200 caractères, l'interface affichera une erreur si le client essaie d'en mettre plus.


### A retenir

l'interface `/admin` est destinée **uniquement aux administrateurs du site** (le propriétaire du site, les modérateurs). Les visiteurs "normaux" doivent utiliser les templates HTML que vous avez créés dans la partie **T** du MVT.

---

### Mini-TP

1. Créez votre super-utilisateur.
2. Enregistrez votre modèle `Article` dans l'admin.
3. Ajoutez un champ `statut` (ex: Brouillon / Publié) dans votre modèle.
4. Configurez l'admin pour pouvoir filtrer les articles par `statut`.

