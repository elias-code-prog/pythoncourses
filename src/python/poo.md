# La Programmation Orientée Objet (POO)

Jusqu'à présent, nous avons fait de la programmation "procédurale" : on écrit des fonctions et on les appelle.

La **POO**, c'est une autre façon de penser. Au lieu de voir le code comme une liste d'actions, on le voit comme une collection d'**objets** qui interagissent entre eux.

### 1. Le concept : Classe vs Objet

Pour bien comprendre, utilisez cette analogie :

* **La Classe** : C'est le **plan d'architecte** d'une maison. Le plan n'est pas une maison, c'est juste un dessin qui explique comment elle doit être construite.
* **L'Objet** : C'est la **maison réelle** construite à partir du plan. On peut construire 10 maisons (objets) à partir d'un seul plan (classe).

### 2. Créer une Classe et un Objet

En Python, on utilise le mot-clé `class`. Par convention, le nom d'une classe commence toujours par une **Majuscule**.

```python
class Voiture:
    # Le constructeur : il définit les caractéristiques de base
    def __init__(self, marque, couleur):
        self.marque = marque  # Attribut
        self.couleur = couleur # Attribut

    # Une méthode : c'est une fonction à l'intérieur d'une classe
    def klaxonner(self):
        print(f"La {self.marque} {self.couleur} fait : POUPUÊÊÊT !")

# Création des objets (Instanciation)
ma_voiture = Voiture("Peugeot", "bleue")
ta_voiture = Voiture("Tesla", "rouge")

ma_voiture.klaxonner()
ta_voiture.klaxonner()

```

### 3. Les 3 piliers de la POO

#### A. L'Encapsulation

C'est le fait de regrouper les données (attributs) et les comportements (méthodes) dans une même boîte. On protège ainsi les données.

#### B. L'Héritage

C'est la capacité d'une classe à récupérer les caractéristiques d'une autre classe. C'est la base de Django !

```python
# Classe parente
class Animal:
    def manger(self):
        print("Je mange...")

# Classe enfant (elle hérite d'Animal)
class Chat(Animal):
    def miauler(self):
        print("Miaou !")

mon_chat = Chat()
mon_chat.manger() # Il peut manger car il hérite de la classe Animal

```

#### C. Le Polymorphisme

C'est la capacité d'objets différents à répondre à un même nom de méthode de manière différente. (Exemple : Une méthode `parler()` qui fait "Aboyer" pour un Chien et "Miauler" pour un Chat).


### Pourquoi c'est crucial pour Django ?

Dans Django, vous allez souvent écrire ceci :

```python
class Article(models.Model):
    titre = models.CharField(max_length=100)

```

Ici, notre classe `Article` **hérite** de toutes les fonctionnalités magiques de Django (`models.Model`). Sans la POO, Django serait impossible à utiliser.

---

### Mini-TP 

Créer une classe `Personnage` avec :

1. Des attributs : `nom`, `points_de_vie`, `force`.
2. Une méthode `attaquer(autre_personnage)` : qui retire des points de vie à l'autre personnage en fonction de la force du premier.
3. **Bonus** : Créez une sous-classe `Magicien` qui hérite de `Personnage` et qui a un attribut `mana`.

