# L'Authentification (User Management)

Django est livré avec un modèle **User** intégré qui gère déjà :

* Les noms d'utilisateur (username) et mots de passe.
* Le hachage sécurisé des mots de passe (PBKDF2).
* Les groupes et les permissions.
* Les sessions de connexion (rester connecté).

### 1. L'objet `User`

Pour utiliser les utilisateurs dans votre code, il suffit de les importer :

```python
from django.contrib.auth.models import User

```

### 2. Les Vues de Connexion/Déconnexion

Django propose des vues "clé en main". Vous n'avez même pas besoin d'écrire la logique Python, juste les templates HTML.

**Dans `monsite/urls.py` :**

```python
from django.urls import path, include

urlpatterns = [
    # Inclut automatiquement login, logout, password_change, etc.
    path('accounts/', include('django.contrib.auth.urls')), 
]

```

### 3. Créer le Template de Connexion

Par défaut, Django cherche un fichier nommé `registration/login.html`.

```html
{% extends "base.html" %}

{% block content %}
  <h2>Connexion</h2>
  <form method="post">
    {% csrf_token %}
    {{ form.as_p }}
    <button type="submit">Se connecter</button>
  </form>
{% endblock %}

```

### 4. Protéger l'accès (Contrôle d'accès)

C'est ici que l'on décide qui peut voir quoi.

#### A. Dans les Vues (Python)

On utilise le décorateur `@login_required`. Si un utilisateur non connecté tente d'accéder à cette vue, il est automatiquement redirigé vers la page de connexion.

```python
from django.contrib.auth.decorators import login_required

@login_required
def rediger_article(request):
    # Seuls les utilisateurs connectés arrivent ici
    return render(request, 'blog/ecrire.html')

```

#### B. Dans les Templates (HTML)

On utilise la variable `user` qui est toujours disponible dans le contexte.

```html
{% if user.is_authenticated %}
    <p>Bienvenue, {{ user.username }} !</p>
    <a href="{% url 'logout' %}">Se déconnecter</a>
{% else %}
    <a href="{% url 'login' %}">Se connecter</a>
{% endif %}

```

---

### 5. L'utilisateur connecté et les données

Lorsqu'un utilisateur est connecté, vous pouvez lier des données à son compte. Par exemple, lier un article à son auteur :

```python
def creer_article(request):
    if request.method == "POST":
        form = ArticleForm(request.POST)
        if form.is_valid():
            article = form.save(commit=False)
            article.auteur = request.user # On lie l'article à l'utilisateur actuel
            article.save()
            return redirect('liste_articles')

```


### A retenir: Le Hachage

 **ne jamais** essayer de stocker des mots de passe en texte brut. Django ne "connaît" pas votre mot de passe ; il stocke une empreinte mathématique (un hash). Même si un pirate vole la base de données, il ne pourra pas lire les mots de passe.

---

### Mini-TP

1. Créez une vue `mon_profil` qui affiche le nom et l'email de l'utilisateur connecté.
2. Protégez cette vue avec `@login_required`.
3. Ajoutez un lien dans votre barre de navigation qui change selon que l'utilisateur est connecté ou non.
