# Installation et Configuration

Avant de coder, il nous faut un atelier digne de ce nom. On ne construit pas une Formule 1 avec un tournevis rouillé. Il nous faut deux outils majeurs : **Python** (le moteur) et **VS Code** (votre tableau de bord).

### 1. Installer le moteur : Python

Si vous êtes sur Mac ou Linux, Python est souvent déjà là. Mais attention, on veut la version la plus récente !

* **Windows :** Allez sur [python.org](https://www.python.org/). **TRÈS IMPORTANT :** Cochez la case **"Add Python to PATH"** au début de l'installation. Si vous l'oubliez, votre ordinateur fera semblant de ne pas connaître Python.
* **macOS :** Utilisez l'installateur du site officiel ou passez par `brew install python` si vous êtes déjà un habitué du terminal.
* **Vérification :** Ouvrez votre terminal (ou PowerShell) et tapez :
```bash
python --version

```

*Si vous voyez "Python 3.15.x" (ou plus), vous êtes le roi du pétrole.*

Dans le cas contraire nous allons installer le gestionnaire trés connu de packages **Homebrew** voir la commande à copier dans votre terminal en dessous

```bash 
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

```

Une fois que l'installation est bien effectuée toujours dans le terminal saisir la commande : 

```bash
    brew install python

```

Une fois que le python est installé, nous faisons une petite vérification de routine : 
```bash
    python3 --version

```
NB : Sous MacOS entre les querelles du python natif et les nouvelles versions installées il est recommandé de mettre le "3" devant la commande (python3) et plutard aussi pour la commande pip (pip3) que nous verrons plutard.

### 2. Le tableau de bord : Visual Studio Code (VS Code) 

C'est l'éditeur de texte préféré des développeurs. Il est gratuit, beau, et surtout, il possède des extensions magiques.

1. Téléchargez-le ici : [code.visualstudio.com](https://code.visualstudio.com/).
2. **L'extension indispensable :** Une fois installé, cliquez sur l'icône des carrés à gauche (Extensions), cherchez **"Python"** (par Microsoft) et installez-la. Elle vous aidera à corriger vos fautes de frappe avant même que vous ne lanciez le code.

### 3. Votre premier fichier (Le test de vérité)

1. Créez un dossier nommé `cours_python` sur votre bureau.
2. Ouvrez ce dossier avec VS Code.
3. Créez un nouveau fichier nommé `hello.py`.
4. Écrivez exactement ceci :
```python
print("Si vous voyez ce message, c'est que vous êtes officiellement un futur génie.")

```


5. Cliquez sur la petite flèche "Play" en haut à droite.

> **Note aux étudiants :** Si rien ne s'affiche ou si vous voyez un message d'erreur rouge sang, pas de panique ! Respirez un grand coup, vérifiez vos guillemets, ou appelez-moi à la rescousse.

---

### Environnement virtuel sous Python 

Maintenant que vos outils sont prêts, nous allons voir comment créer un [Environnement Virtuel](/python/venv.md).

C'est comme créer une petite bulle hermétique pour chaque projet afin d'éviter que les bibliothèques d'un projet ne viennent mettre le bazar dans un autre. C'est l'étape que tout le monde oublie, mais pas nous !

