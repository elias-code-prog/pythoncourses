# Les Fonctions et les Modules

Dans ce chapitre, nous allons apprendre à ne plus nous répéter (**DRY : Don't Repeat Yourself**) et à ranger notre code dans des tiroirs logiques.

## 1. Les Fonctions

Une fonction est un bloc de code auquel on donne un nom. On peut l'appeler à tout moment pour qu'il effectue une tâche précise.

### Définition et Appel

On utilise le mot-clé `def` pour définir une fonction.

```python
def saluer_etudiant(nom, cours="Python"):
    """Cette fonction affiche un message de bienvenue."""
    return f"Bonjour {nom}, bienvenue dans le cours de {cours} !"

# Appel de la fonction
message = saluer_etudiant("Elias")
print(message)

```

### Paramètres vs Arguments

* **Paramètres** : Ce sont les variables définies dans la parenthèse de la fonction (`nom`, `cours`).
* **Arguments** : Ce sont les valeurs réelles que vous passez lors de l'appel (`"Elias"`).

### L'importance du `return`

Une erreur classique est de confondre `print()` et `return`.

* `print()` affiche juste quelque chose dans le terminal.
* `return` renvoie une valeur que le programme peut stocker dans une variable et réutiliser plus tard.



## 2. Les Modules

Un **module** est simplement un fichier `.py` contenant des fonctions et des variables. Lorsque votre code devient trop long, vous le divisez en plusieurs fichiers.

### Importer un module existant

Python possède une "bibliothèque standard" immense. Vous n'avez pas besoin de réinventer la roue pour faire des maths ou gérer des dates.

```python
import math
import random

print(math.sqrt(16))      # Affiche 4.0 (Racine carrée)
print(random.randint(1, 10)) # Affiche un nombre entier entre 1 et 10

```

### Créer notre propre module

Imaginons deux fichiers dans votre dossier :

1. **`outils.py`** (Le module) :
```python
def addition(a, b):
    return a + b

```


2. **`main.py`** (Votre programme principal) :
```python
from outils import addition

resultat = addition(10, 5)
print(f"Le résultat est : {resultat}")

```

## 3. Les Packages (Bibliothèques)

Un **Package** est un dossier qui contient plusieurs modules. C'est ce que vous utiliserez avec **Django**.

Pour installer des packages créés par la communauté (comme Django, Pandas, ou Requests), on utilise l'outil `pip`.

```bash
# Dans votre terminal (avec l'environnement virtuel activé !)
pip install requests

```

Une fois installé, vous pouvez l'utiliser dans votre code :

```python
import requests

reponse = requests.get("https://api.github.com")
print(reponse.status_code) # Affiche 200 si tout va bien

```

---

### Résumé

* **Fonction** : Une machine à faire une tâche (dans un fichier).
* **Module** : Un fichier `.py` (contient plusieurs fonctions).
* **Package** : Un dossier (contient plusieurs modules).

---

### Mini-TP

1. Créez un module `conversions.py` avec une fonction qui transforme les degrés Celsius en Fahrenheit.
2. Dans votre fichier principal `main.py`, importez cette fonction.
3. Demandez une température à l'utilisateur et affichez le résultat converti.

