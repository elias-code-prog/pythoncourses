# Le Moteur de Rendu (Templates)

Le moteur de rendu de Django (**Django Template Language** ou **DTL**) permet d'injecter de la logique (boucles, conditions) directement dans votre HTML. Son but est de rester simple pour que même un designer puisse le comprendre.

### 1. La Syntaxe de base

Il n'y a que trois symboles fondamentaux à retenir :

* **`{{ variable }}`** : **Affiche** une valeur (ex: le titre d'un article).
* **`{% tag %}`** : **Logique** (ex: une boucle `for`, un `if`, ou charger des fichiers statiques).
* **`{# commentaire #}`** : Pour annoter votre code sans qu'il apparaisse dans le navigateur.



### 2. L'Héritage de Template (Le concept DRY)

C'est la fonctionnalité préférée des développeurs. Au lieu de copier-coller votre menu et votre pied de page sur 50 pages, vous créez un **squelette** (`base.html`) et les autres pages viennent "s'insérer" dedans.

**Le fichier `base.html` (Le parent) :**

```html
<!DOCTYPE html>
<html>
<head>
    <title>{% block title %}Mon Site{% endblock %}</title>
</head>
<body>
    <nav>Mon Menu de Navigation</nav>

    <main>
        {% block content %}
        {% endblock %}
    </main>

    <footer>Copyright 2026</footer>
</body>
</html>

```

**Le fichier `liste.html` (L'enfant) :**

```html
{% extends 'blog/base.html' %}

{% block content %}
    <h1>Tous mes articles</h1>
    {% for article in articles %}
        <p>{{ article.titre }}</p>
    {% endfor %}
{% endblock %}

```


### 3. Les Filtres (Modifier l'affichage)

Les filtres permettent de transformer une variable avant de l'afficher en utilisant le symbole "pipe" `|`.

* `{{ titre|upper }}` : Affiche le titre en MAJUSCULES.
* `{{ texte|truncatewords:20 }}` : Coupe le texte après 20 mots (parfait pour les aperçus).
* `{{ date_pub|date:"D d M Y" }}` : Formate la date proprement.

### 4. Les Balises Logiques (Tags)

#### La boucle `for`

C'est ce qui permet d'afficher une liste d'articles provenant de la base de données.

```html
<ul>
{% for article in articles %}
    <li>{{ article.titre }} - Publié par {{ article.auteur }}</li>
{% empty %}
    <li>Aucun article pour le moment.</li>
{% endfor %}
</ul>

```

#### La condition `if`

```html
{% if user.is_authenticated %}
    <p>Bonjour {{ user.username }} !</p>
{% else %}
    <a href="/login">Connectez-vous</a>
{% endif %}

```

### 5. Charger des fichiers statiques (CSS, Images)

Pour que Django sache où trouver votre CSS ou vos images, il faut utiliser le tag `static`.

```html
{% load static %}
<link rel="stylesheet" href="{% static 'css/style.css' %}">
<img src="{% static 'images/logo.png' %}" alt="Logo">

```

---

### Mini-TP : "La mise en page pro"

1. Créez un fichier `base.html` avec une barre de navigation simple.
2. Créez une page `accueil.html` qui hérite de `base.html`.
3. Dans la vue de l'accueil, envoyez une liste de noms d'étudiants.
4. Dans le template, affichez cette liste en mettant le premier nom en gras (Indice : utilisez `{% if forloop.first %}`).

