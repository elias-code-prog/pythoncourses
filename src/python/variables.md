
# Les Variables et Types de données

En programmation, une **variable**, c'est comme une boîte sur laquelle on colle une étiquette. On met une donnée à l'intérieur, et on utilise l'étiquette pour la retrouver plus tard.

### 1. Créer une variable

En Python, c'est ultra simple. Pas besoin de dire à l'ordinateur quel "type" de boîte c'est, il le devine tout seul (c'est ce qu'on appelle le **typage dynamique**).

```python
nom_du_joueur = "Elias"  # Une chaîne de caractères (String)
score = 100              # Un nombre entier (Integer)
est_en_ligne = True      # Un booléen (Boolean)

```

### 2. Les types de données indispensables

Voici les quatre types que vous allez croiser 99% du temps :

| Type | Nom Python | Exemple | Description |
| --- | --- | --- | --- |
| **Texte** | `str` | `"Salut !"` | Toujours entre guillemets. |
| **Entier** | `int` | `42` | Pour compter des objets. |
| **Décimal** | `float` | `19.99` | Pour les prix (utilisez le point, pas la virgule !). |
| **Booléen** | `bool` | `True` / `False` | Pour répondre par Oui ou Non. |

### 3. Les règles d'or (pour éviter les erreurs inutiles)

1. **Pas d'espaces :** Utilisez l'underscore `_` (le tiret du 8). On écrit `mon_score`, pas `mon score`.
2. **Pas de chiffres au début :** `joueur1` est autorisé, `1joueur` fera exploser votre code.
3. **La casse compte :** `Age` et `age` sont deux boîtes totalement différentes pour Python.

### 4. La magie des f-strings (Affichage)

Pour afficher vos variables dans un message sympa, on utilise les **f-strings**. C'est la méthode la plus moderne et la plus propre :

```python
prenom = "Elias"
tentatives = 3

print(f"Désolé {prenom}, il ne vous reste que {tentatives} essais.")

```

---

###  Le petit TP du chapitre

Essayez d'écrire un script qui demande le nom de l'utilisateur et son âge, puis calcule l'année de sa naissance.

> **Indice :** Pour demander une valeur, on utilise `input()`. Mais attention, `input()` donne toujours du texte (`str`). Pour faire des maths, il faudra transformer l'âge en nombre avec `int()`.
