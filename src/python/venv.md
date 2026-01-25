# Environnements Virtuels (venv)

Imaginez que vous travaillez sur deux projets différents :

1. Un vieux site web qui nécessite la version **1.0** d'une bibliothèque.
2. Un nouveau projet génial qui nécessite la version **3.0** de cette même bibliothèque.

Si vous installez tout directement sur votre ordinateur, c'est la guerre civile. L'un des deux projets ne fonctionnera plus.

La solution ? **L'Environnement Virtuel.** C'est comme créer une petite "bulle" isolée pour chaque projet.

### 1. Pourquoi est-ce indispensable ?

* **Isolation :** Ce qui se passe dans la bulle reste dans la bulle.
* **Propreté :** Votre système reste propre, vous ne l'encombrez pas de milliers de fichiers inutiles.
* **Django :** Pour Django, c'est **obligatoire**. On ne commence jamais un projet Django sans environnement virtuel.

### 2. Comment créer votre "bulle" ?

Ouvrez votre terminal dans le dossier de votre projet et tapez la commande suivante :

**Sur Windows :**

```powershell
python -m venv .venv

```

**Sur macOS / Linux :**

```bash
python3 -m venv .venv

```

*(Ici, `.venv` est simplement le nom du dossier qui contiendra votre environnement. Le point devant permet de le cacher pour ne pas qu'il vous gêne).*

### 3. Activer l'environnement (Entrer dans la bulle)

Créer la bulle ne suffit pas, il faut "entrer" dedans !

* **Sur Windows :**
```powershell
.venv\Scripts\activate

```

* **Sur macOS / Linux :**
```bash
source .venv/bin/activate

```

**Comment savoir si ça marche ?**
Vous devriez voir apparaître `(.venv)` au tout début de votre ligne de commande dans le terminal. Si vous le voyez, félicitations : vous êtes protégé !

### 4. En sortir (Désactiver)

Quand vous avez fini de travailler, tapez simplement :

```bash
deactivate

```

Et hop, vous êtes de retour dans le monde réel.

---

### Le conseil du prof

> Ne commettez jamais l'erreur d'envoyer votre dossier `.venv` sur GitHub ! C'est un dossier très lourd qui contient des fichiers spécifiques à **votre** ordinateur. On utilise un fichier `requirements.txt` pour dire aux autres ce qu'ils doivent installer. Mais on verra ça plus tard...
