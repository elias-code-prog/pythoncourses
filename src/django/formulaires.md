
# Les Formulaires Django : La gestion des entrées

Le rôle d'un formulaire Django est triple :

1. **Générer** automatiquement le code HTML des champs.
2. **Valider** les données (est-ce un e-mail valide ? le texte est-il trop court ?).
3. **Nettoyer** les données pour éviter les failles de sécurité.

### 1. Créer un formulaire (Le fichier `forms.py`)

Il est recommandé de créer un fichier `forms.py` dans le dossier de votre application.

```python
from django import forms
from .models import Article

# Option A : Le formulaire manuel (indépendant d'un modèle)
class ContactForm(forms.Form):
    nom = forms.CharField(max_length=100)
    email = forms.EmailField()
    message = forms.TextField()

# Option B : Le ModelForm (lié directement à votre base de données)
class ArticleForm(forms.ModelForm):
    class Meta:
        model = Article
        fields = ['titre', 'contenu', 'auteur'] # Les champs à afficher

```


### 2. Traiter le formulaire dans la Vue (`views.py`)

C'est ici que l'on gère les deux moments de vie d'un formulaire :

* **GET** : L'utilisateur arrive sur la page (on affiche le formulaire vide).
* **POST** : L'utilisateur clique sur "Envoyer" (on vérifie et on enregistre).

```python
from django.shortcuts import render, redirect
from .forms import ArticleForm

def creer_article(request):
    if request.method == "POST":
        form = ArticleForm(request.POST) # On remplit le formulaire avec les données reçues
        if form.is_valid():
            form.save() # Magie : ça crée l'article en base de données !
            return redirect('liste_articles')
    else:
        form = ArticleForm() # Formulaire vide pour le premier affichage
        
    return render(request, 'blog/article_form.html', {'form': form})

```

### 3. Afficher le formulaire dans le Template (`.html`)

Django rend l'affichage extrêmement simple.

```html
<form method="post">
    {% csrf_token %} {{ form.as_p }} <button type="submit">Enregistrer</button>
</form>

```

> Le `{% csrf_token %}` : C'est un jeton de sécurité que Django génère pour s'assurer que le formulaire vient bien de votre site et non d'un site pirate. Sans lui, le formulaire sera rejeté.


### 4. Personnaliser l'affichage

Si `{{ form.as_p }}` est trop simple, vous pouvez boucler sur les champs pour appliquer vos propres classes CSS (Bootstrap par exemple) :

```html
{% for field in form %}
    <div class="form-group">
        <label>{{ field.label }}</label>
        {{ field }}
        {% if field.errors %}
            <span class="text-danger">{{ field.errors }}</span>
        {% endif %}
    </div>
{% endfor %}

```

### A retenir 

 `form.is_valid()` ne vérifie pas seulement si les champs sont remplis, elle vérifie aussi le **type**. Si un étudiant tape "Bonjour" dans un `EmailField`, `is_valid()` renverra `False` et Django générera automatiquement un message d'erreur en rouge sans que vous ayez à coder quoi que ce soit.

---

### Mini-TP : "Le Livre d'Or"

1. Créez un modèle `Message` (nom, contenu, date).
2. Créez un `ModelForm` correspondant.
3. Créez une vue qui affiche tous les messages passés ET le formulaire pour en ajouter un nouveau sur la même page.
4. Testez l'enregistrement et vérifiez que les données apparaissent en base.

