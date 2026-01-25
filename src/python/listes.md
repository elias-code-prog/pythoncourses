
# Les Listes : Organiser vos données

Une **liste** est une collection ordonnée d'éléments. Imaginez un tiroir avec plusieurs compartiments numérotés. Chaque compartiment contient un objet.

### 1. Créer et accéder à une liste

En Python, on utilise les crochets `[]`.

> **Attention :** Le comptage commence à **0** ! C'est ce qu'on appelle l'indice (index).

```python
langages = ["Python", "Java", "C++", "JavaScript"]

print(langages[0])  # Affiche "Python"
print(langages[2])  # Affiche "C++"
print(langages[-1]) # Affiche le dernier élément ("JavaScript")

```

### 2. Modifier une liste (Les méthodes indispensables)

Les listes sont "mutables", ce qui signifie qu'on peut les transformer en plein vol.

```python
courses = ["Pain", "Lait"]

courses.append("Chocolat")      # Ajoute à la fin
courses.insert(1, "Beurre")     # Ajoute à la position 1
courses.remove("Lait")          # Supprime par valeur
element_supprime = courses.pop(0) # Supprime par position et récupère la valeur

```

### 3. La puissance des listes avec les boucles

C'est le duo gagnant de tout développeur :

```python
prix_ht = [10, 20, 50, 100]
prix_ttc = []

for prix in prix_ht:
    prix_ttc.append(prix * 1.20)

print(prix_ttc) # [12.0, 24.0, 60.0, 120.0]

```

---

# Les Dictionnaires : Le système Clé-Valeur

Si la liste est un tiroir numéroté, le **dictionnaire** est une armoire où chaque objet a une étiquette personnalisée. On n'utilise plus de numéros (index), mais des **clés**.

### 1. Syntaxe et structure

On utilise les accolades `{}` et le format `cle: valeur`.

```python
etudiant = {
    "nom": "Elias",
    "filiere": "Informatique",
    "note": 18,
    "est_inscrit": True
}

print(etudiant["nom"]) # Affiche "Elias"

```

### 2. Pourquoi utiliser un dictionnaire ?

C'est le format idéal pour représenter des objets réels. Dans Django, vous passerez votre temps à manipuler des données sous cette forme (très proche du format **JSON** utilisé sur tout le web).

```python
# Modifier ou ajouter une valeur
etudiant["note"] = 20
etudiant["ville"] = "Dakar"

# Vérifier si une clé existe
if "age" in etudiant:
    print(etudiant["age"])
else:
    print("L'âge n'est pas renseigné.")

```

### 3. Parcourir un dictionnaire

```python
for cle, valeur in etudiant.items():
    print(f"L'info '{cle}' a pour valeur : {valeur}")

```

### Le conseil 

Il faut bien retenir cette différence :

* **Liste `[]**` : Pour une suite d'éléments de même type (ex: liste de noms, liste de prix). L'ordre compte.
* **Dictionnaire `{}**` : Pour décrire un objet complexe avec des propriétés différentes (ex: un utilisateur, une voiture, un article de blog).

---

### Mini-TP

Créer une liste contenant trois dictionnaires. Chaque dictionnaire représente un étudiant avec un `nom` et une `moyenne`.

**Objectif :** Faire une boucle pour afficher le nom de chaque étudiant et dire s'il passe en classe supérieur (moyenne >= 10).

Oups ! Vous avez tout à fait raison. On ne peut pas parler des collections en Python sans mentionner les **Tuples**. Ils ressemblent aux listes, mais avec une différence philosophique (et technique) majeure : ils sont **immuables**.

Voici le complément pédagogique à ajouter dans votre cours (vous pouvez l'insérer dans `src/python/listes.md` ou créer un fichier dédié `src/python/tuples.md`).

---

### Les Tuples

Si une **Liste** est un carnet sur lequel on peut écrire, effacer et raturer, un **Tuple** est une gravure dans le marbre. Une fois créé, on ne peut plus le modifier.

### 1. Syntaxe

On utilise les parenthèses `()` au lieu des crochets.

```python
coordonnees_gps = (14.6937, -17.4441) # Dakar
jours_de_la_semaine = ("Lundi", "Mardi", "Mercredi", "Jeudi", "Vendredi", "Samedi", "Dimanche")

```

### 2. Pourquoi utiliser un Tuple plutôt qu'une Liste ?

C'est la question que vous vous posez ! Voici les 3 raisons :

1. **Sécurité :** Si vous avez des données qui ne doivent jamais changer (les jours de la semaine, les réglages d'une application, des coordonnées), le Tuple garantit qu'aucun bug dans le code ne viendra modifier ces valeurs par erreur.
2. **Performance :** Python traite les Tuples plus rapidement que les Listes. Pour des milliers de données constantes, c'est un gain d'énergie.
3. **Utilisation comme Clé :** Un Tuple peut être utilisé comme **clé dans un dictionnaire**, alors qu'une Liste ne le peut pas (car elle est instable).

### 3. La particularité du Tuple

**L'Immuabilité en action**

Essayez de faire ceci dans votre terminal :

```python
mon_tuple = (1, 2, 3)
mon_tuple[0] = 10  # ❌ ERREUR : TypeError

```

Python va vous envoyer un message d'erreur clair : *"tuple object does not support item assignment"*. 

C'est sa façon de dire : "Je t'avais dit de ne pas y toucher !"

### 4. Le "Packing" et "Unpacking"

```python
# On "emballe" des données dans un tuple
personne = ("Elias", 25, "Dakar")

# On "déballe" le tuple dans des variables distinctes
nom, age, ville = personne

print(nom)  # "Elias"
print(ville) # "Dakar"

```


### Résumé 

| Collection | Symbole | Modifiable ? | Usage principal |
| --- | --- | --- | --- |
| **Liste** | `[]` | ✅ Oui | Séries d'éléments qui évoluent (ex: panier d'achat). |
| **Tuple** | `()` | ❌ Non | Données constantes, sécurisées (ex: config, coordonnées). |
| **Dictionnaire** | `{}` | ✅ Oui | Objets avec propriétés nommées (ex: profil utilisateur). |
