# Les Dictionnaires (`dict`)

Si une liste est un tiroir numéroté, le **dictionnaire** est une armoire où chaque objet possède une **étiquette personnalisée**. On ne cherche plus par un numéro de position, mais par une **clé**.

### 1. Création et accès

On utilise les accolades `{}` et le format `clé: valeur`.

```python
# Un dictionnaire représentant un smartphone
telephone = {
    "marque": "Apple",
    "modele": "iPhone 15",
    "stockage": 128,
    "est_neuf": True
}

# Accéder à une valeur
print(telephone["marque"])  # Affiche : Apple

```

### 2. Ajouter, Modifier, Supprimer

Les dictionnaires sont très flexibles :

```python
# Modifier une valeur
telephone["stockage"] = 256

# Ajouter une nouvelle clé
telephone["couleur"] = "Noir"

# Supprimer une clé
del telephone["est_neuf"]

# Utiliser .get() pour éviter les erreurs si la clé n'existe pas
version = telephone.get("version_ios", "Inconnu")
print(version) # Affiche "Inconnu" au lieu de faire planter le programme

```

### 3. Parcourir un dictionnaire

C'est une opération très courante pour afficher des données provenant d'une base de données :

```python
for cle, valeur in telephone.items():
    print(f"L'élément {cle} a pour valeur : {valeur}")

```

---

# Les Sets (Ensembles)

Le **Set** est une collection non ordonnée d'éléments **uniques**. Imaginez un sac de billes : l'ordre n'a pas d'importance, mais vous ne pouvez pas avoir deux billes exactement identiques.

### 1. Pourquoi utiliser un Set ?

La force du Set réside dans deux points :

1. **L'unicité :** Il supprime automatiquement les doublons.
2. **La vitesse :** Vérifier si un élément est dans un Set est quasi instantané, même avec des millions d'éléments.

### 2. Création et manipulation

On utilise aussi des accolades `{}`, mais sans les deux points `:` du dictionnaire.

```python
# Création d'un set avec des doublons
fruits = {"pomme", "banane", "orange", "pomme", "banane"}

print(fruits) 
# Affiche : {'orange', 'banane', 'pomme'} (les doublons ont disparu !)

# Ajouter et supprimer
fruits.add("ananas")
fruits.discard("orange")

```

### 3. Les opérations mathématiques

C'est ici que les Sets deviennent très puissants pour comparer des groupes de données :

```python
etudiants_python = {"Alice", "Bob", "Charlie"}
etudiants_django = {"Charlie", "David", "Eve"}

# Qui est inscrit aux DEUX cours ? (Intersection)
print(etudiants_python & etudiants_django) # {'Charlie'}

# Liste de TOUS les étudiants sans doublons (Union)
print(etudiants_python | etudiants_django) # {'Alice', 'Bob', 'Charlie', 'David', 'Eve'}

```

### Résumé

| Structure | Symbole | Doublons ? | Usage |
| --- | --- | --- | --- |
| **Liste** | `[]` | ✅ Oui | Une suite ordonnée d'éléments (ex: classement). |
| **Dictionnaire** | `{}` | 🔑 Clés uniques | Un objet avec des propriétés (ex: profil utilisateur). |
| **Set** | `{}` | ❌ Non | Une collection unique sans ordre (ex: liste d'invités). |


### Mini-TP

Prenons une liste de mots contenant beaucoup de répétitions (ex: `["python", "django", "python", "flask", "django", "python"]`).

1. Utilisez un **Set** pour afficher uniquement les langages uniques.
2. Utilisez un **Dictionnaire** pour compter combien de fois chaque mot apparaît (ex: `{"python": 3, "django": 2...}`).

