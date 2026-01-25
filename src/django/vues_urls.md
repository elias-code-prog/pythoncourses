
# Les URLs : L'Aiguillage du site

Le fichier `urls.py` est le standardiste de votre application. Son seul rôle est de regarder l'adresse tapée par l'utilisateur et de passer l'appel à la bonne fonction (la Vue).

### 1. La structure du fichier `urls.py`

Dans Django, on sépare généralement les URLs du projet global des URLs de chaque application.

**Étape A : Dans `monsite/urls.py` (le projet global)**
On dit à Django d'inclure les URLs de l'application blog :

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('blog.urls')), # On redirige tout vers l'app blog
]

```

**Étape B : Dans `blog/urls.py` (votre application)**
Vous devez créer ce fichier manuellement s'il n'existe pas :

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.liste_articles, name='liste_articles'),
    path('article/<int:id>/', views.detail_article, name='detail_article'),
]

```
# Les Vues (`views.py`) : La logique métier

La **Vue** est une fonction (ou une classe) qui reçoit une requête web et doit impérativement renvoyer une réponse (souvent du HTML).

### 1. Une vue simple (Hello World)

```python
from django.http import HttpResponse

def accueil(request):
    return HttpResponse("Bienvenue sur la page d'accueil !")

```

### 2. Une vue avec Template et ORM

C'est la forme la plus courante. La vue va chercher des données et les envoie au fichier HTML.

```python
from django.shortcuts import render, get_object_or_404
from .models import Article

def liste_articles(request):
    # 1. On récupère les données via l'ORM
    articles = Article.objects.all().order_by('-date_publication')
    
    # 2. On les envoie au template via un dictionnaire (le "context")
    return render(request, 'blog/liste.html', {'articles': articles})

```

### 3. Les URLs dynamiques

Pour afficher un article précis, on passe son `id` (ou sa clé primaire) dans l'URL.

```python
def detail_article(request, id):
    # On récupère l'article ou on renvoie une erreur 404 si l'ID n'existe pas
    article = get_object_or_404(Article, id=id)
    return render(request, 'blog/detail.html', {'article': article})

```

### A retenir

1. **Le paramètre `request**` : Chaque vue reçoit cet objet qui contient tout (qui est l'utilisateur ? quel navigateur utilise-t-il ? qu'a-t-il tapé dans le formulaire ?).
2. **Le `name` dans les URLs** : Toujours donner un nom à vos routes (`name='liste_articles'`). Cela permet de changer l'adresse URL plus tard sans casser tous les liens du site.
3. **`render` vs `HttpResponse**` :
* `HttpResponse` : Pour envoyer du texte brut.
* `render` : Pour envoyer un fichier HTML complet en y injectant des données.


---

### Mini-TP

1. Créez une fonction `contact` dans `views.py` qui renvoie un message simple.
2. Ajoutez une route dans `urls.py` pour que cette vue soit accessible via l'adresse `/contact/`.
3. **Défi** : Modifiez la vue pour qu'elle utilise un fichier `contact.html` au lieu d'un texte brut.


## Les Vues : La Logique de notre Application

La vue est l'endroit où vous écrivez votre code Python. Son rôle est simple : elle reçoit une **Requête** (Request) et doit renvoyer une **Réponse** (Response).

### 1. Le fonctionnement interne d'une vue

Une vue effectue généralement quatre étapes :

1. **Récupérer** les informations de la requête (ex: l'ID de l'article dans l'URL).
2. **Extraire** les données de la base via l'ORM (ex: `Article.objects.get(id=1)`).
3. **Traiter** la logique (ex: vérifier si l'utilisateur est connecté).
4. **Générer** la réponse (ex: via un template HTML).


### 2. Les Vues Basées sur des Fonctions (FBV)

C'est la méthode la plus simple et la plus explicite, idéale pour débuter.

```python
from django.shortcuts import render, get_object_or_404
from .models import Article

def detail_article(request, id):
    # On récupère l'article ou on renvoie une erreur 404
    article = get_object_or_404(Article, pk=id)
    
    context = {
        'article': article,
        'titre_page': f"Détail de {article.titre}"
    }
    
    return render(request, 'blog/detail.html', context)

```

### 3. Les Vues Basées sur des Classes (CBV)

Quand vous faites des choses répétitives (afficher une liste, créer un objet), Django propose des classes toutes prêtes pour gagner du temps.

```python
from django.views.generic import ListView, DetailView
from .models import Article

# Cette classe remplace toute une fonction manuelle
class ArticleListView(ListView):
    model = Article
    template_name = 'blog/liste.html'
    context_object_name = 'articles' # Le nom utilisé dans le HTML

```


### 4. Les raccourcis indispensables

Pour écrire un code propre, Django propose des fonctions "raccourcis" :

* **`render()`** : Combine un template avec un dictionnaire de données et renvoie du HTML.
* **`redirect()`** : Envoie l'utilisateur vers une autre URL (très utilisé après avoir validé un formulaire).
* **`get_object_or_404()`** : Tente de récupérer un objet, et si l'ID n'existe pas, affiche une page 404 propre au lieu de faire planter le serveur.


### A retenir 
Le dictionnaire que vous envoyez dans `render` s'appelle le **Contexte**.
C'est le seul moyen pour que vos variables Python deviennent utilisables dans votre fichier HTML.

* **Côté Python (`views.py`)** : `{'nom': 'Elias'}`
* **Côté HTML (`template.html`)** : `{{ nom }}`

---

### Mini-TP : "La Vue de Recherche"

Créer une vue `recherche` qui :

1. Récupère un mot-clé envoyé via une URL (ex: `?q=python`).
*Indice : `request.GET.get('q')*`
2. Filtre les articles dont le titre contient ce mot-clé.
3. Renvoie le résultat à un template nommé `resultats.html`.
