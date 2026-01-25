
# Les Boucles (For & While)

Pourquoi s'embêter à copier-coller 100 fois la même ligne de code quand on peut demander à Python de le faire pour nous ? Les boucles servent à répéter des actions. C'est le secret de la productivité du développeur (et de sa fainéantise légendaire).

### 1. La boucle `for` : Parcourir une liste

C'est la boucle la plus utilisée. On l'utilise quand on sait d'avance combien de fois on veut répéter quelque chose, ou quand on veut explorer une collection de données.

```python
etudiants = ["Amadou", "Alassane", "Jean", "Elias"]

for nom in etudiants:
    print(f"Bienvenue au cours de Python, {nom} !")

```

**L'outil magique : `range()**`
Si vous voulez juste compter, utilisez `range(début, fin_exclue)` :

```python
for i in range(1, 6):
    print(f"Tentative numéro {i}")
# Affichera 1, 2, 3, 4, 5

```

### 2. La boucle `while` : Tant que...

On l'utilise quand on ne sait pas à l'avance quand l'action va s'arrêter. On continue "tant que" une condition est vraie.

```python
batterie = 10

while batterie > 0:
    print(f"Le téléphone est allumé... Batterie : {batterie}%")
    batterie -= 2  # On baisse la batterie de 2 à chaque tour

print("Le téléphone s'éteint. Au revoir !")

```

### 3. Contrôler vos boucles : `break` et `continue`

Parfois, on a besoin de changer le destin de notre boucle en cours de route :

* **`break`** : On arrête tout et on sort de la boucle immédiatement (comme un bouton d'urgence).
* **`continue`** : On saute l'étape actuelle et on passe directement au tour suivant.

```python
for i in range(1, 11):
    if i == 5:
        continue # On saute le chiffre 5
    if i == 8:
        break    # On arrête tout arrivé à 8
    print(i)

```

---

### Le danger : La Boucle Infinie

Si vous utilisez un `while` et que la condition reste toujours vraie (par exemple, si vous oubliez de baisser la batterie dans l'exemple plus haut), votre ordinateur va travailler jusqu'à la fin des temps (ou jusqu'à ce que vous fassiez `Ctrl + C` dans le terminal).

> **Astuce de prof :** Toujours vérifier qu'il existe une porte de sortie dans vos `while` !

---

### Mini-TP : Le Juste Prix

Écrivez un script qui :

1. Définit un `nombre_mystere = 42`.
2. Utilise une boucle `while` pour demander à l'utilisateur de deviner le nombre.
3. Dit "Plus grand" ou "Plus petit" à chaque essai.
4. S'arrête avec un message de félicitations quand l'utilisateur a trouvé.

