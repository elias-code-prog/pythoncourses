# La Gestion des Erreurs (Les Exceptions)

Même avec le meilleur code du monde, des erreurs arriveront : un utilisateur qui tape du texte au lieu d'un nombre, un fichier introuvable, ou une connexion internet qui coupe.

En programmation, on appelle cela des **Exceptions**. Si vous ne les gérez pas, le programme s'arrête brutalement avec un message rouge illisible pour l'utilisateur.

### 1. Le bloc `try ... except`

L'idée est simple : "Essaie (`try`) de faire ça, et si ça plante, fais ceci (`except`) au lieu de mourir."

```python
try:
    nombre = int(input("Entrez un nombre : "))
    resultat = 10 / nombre
    print(f"Le résultat est {resultat}")
except ValueError:
    print("Erreur : Vous devez entrer un chiffre, pas du texte !")
except ZeroDivisionError:
    print("Erreur : Impossible de diviser par zéro, l'univers risquerait d'exploser.")

```

### 2. Capturer n'importe quelle erreur

Si vous ne savez pas quel type d'erreur peut arriver, vous pouvez utiliser `Exception as e`. Cela permet de capturer l'erreur et de l'afficher proprement.

```python
try:
    # Un code potentiellement dangereux
    import bibliotheque_imaginaire
except Exception as e:
    print(f"Oups, quelque chose a mal tourné : {e}")

```

### 3. Les blocs `else` et `finally`

Pour être un vrai pro, on peut ajouter deux étapes supplémentaires :

* **`else`** : S'exécute uniquement si **aucune** erreur n'est survenue dans le `try`.
* **`finally`** : S'exécute **dans tous les cas**, qu'il y ait eu une erreur ou non. Très utile pour fermer un fichier ou une base de données.

```python
try:
    fichier = open("notes.txt", "r")
except FileNotFoundError:
    print("Le fichier n'existe pas.")
else:
    print("Fichier lu avec succès !")
finally:
    print("Nettoyage du système... Fin de l'opération.")

```

### 4. Forcer une erreur avec `raise`

Parfois, on veut volontairement créer une erreur parce qu'une règle métier n'est pas respectée (par exemple, un âge négatif).

```python
age = -5

if age < 0:
    raise ValueError("L'âge ne peut pas être négatif !")

```

### Conseils

Évitez d'utiliser un simple `except:` sans préciser le type d'erreur. C'est comme aller chez le médecin et dire "J'ai mal" sans dire où. Préciser `ValueError` ou `TypeError` permet de savoir exactement ce qui ne va pas et de mieux guider l'utilisateur.

---

### Mini-TP : "La Division Sécurisée"

Créer une fonction `division_securisee(a, b)`.

1. La fonction doit essayer de diviser `a` par `b`.
2. Elle doit gérer l'erreur de division par zéro.
3. Elle doit gérer l'erreur si `a` ou `b` ne sont pas des nombres.
4. Si tout va bien, elle retourne le résultat.

