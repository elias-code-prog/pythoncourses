# Les Conditions (If, Elif, Else)

Jusqu'à présent, nos programmes lisaient les lignes de code une par une, comme une recette de cuisine. Mais dans la vraie vie, on prend des décisions : *"S'il pleut, je prends un parapluie, sinon je mets mes lunettes de soleil."*

En Python, on utilise les instructions `if`, `elif` et `else`.

### 1. La syntaxe de base

La règle d'or en Python : **N'oubliez jamais les deux points (`:`) et l'indentation (le décalage vers la droite).**

```python
age = 20

if age >= 18:
    print("Accès autorisé : Vous êtes majeur.")
else:
    print("Accès refusé : Il faut encore manger de la soupe.")

```

### 2. Les opérateurs de comparaison

Pour comparer des valeurs, on utilise ces symboles :

* `==` : Est égal à (attention, ne pas confondre avec `=` qui sert à donner une valeur).
* `!=` : Est différent de.
* `>` / `<` : Supérieur / Inférieur.
* `>=` / `<=` : Supérieur ou égal / Inférieur ou égal.

### 3. Gérer plusieurs choix avec `elif`

Si vous avez plus de deux options, on utilise `elif` (contraction de *else if*).

```python
note = 15

if note >= 18:
    print("Excellent !")
elif note >= 14:
    print("Très bien.")
elif note >= 10:
    print("Passable.")
else:
    print("On se revoit au rattrapage ?")

```

### 4. Combiner les conditions (And, Or, Not)

Parfois, une seule condition ne suffit pas.

* `and` : Les deux doivent être vraies.
* `or` : Au moins une des deux doit être vraie.
* `not` : L'inverse de la condition.

```python
argent = 50
est_majeur = True

if argent >= 20 and est_majeur:
    print("Tu peux acheter ce jeu vidéo.")

```

---

### Le piège classique : L'Indentation

En Python, l'espace au début de la ligne n'est pas là pour faire joli. C'est lui qui dit à Python : *"Ce code appartient au bloc IF"*. Si vous l'oubliez, vous aurez une `IndentationError`.

> **Astuce du prof :** Si vous avez un doute, appuyez sur la touche **Tab** de votre clavier au début de la ligne.

---

### Mini-TP

Créez un petit script de sécurité pour un parc d'attraction. Le programme doit demander :

1. La taille de l'utilisateur (en cm).
2. Si l'utilisateur a un ticket (True/False).

**Condition :** On ne peut monter dans l'attraction que si on mesure plus de 140cm ET qu'on ait un ticket.
