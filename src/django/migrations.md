
# Les Migrations : Le Versioning de la Base de Données

Dans le développement web moderne, on ne modifie jamais la base de données à la main (via PHPMyAdmin ou des scripts SQL). On utilise les **Migrations** de Django.

### 1. Pourquoi les migrations ?

Imaginez que vous travaillez en équipe. Vous ajoutez un champ `photo` à votre modèle `Article`. Comment votre collègue peut-il avoir la même modification sur son ordinateur ?

* Sans migrations : Vous devez lui envoyer un script SQL.
* **Avec migrations** : Il lui suffit de récupérer votre code et de taper une commande.

---

### 2. Le cycle de vie d'une modification

Il y a toujours deux étapes indispensables dès que vous touchez au fichier `models.py`.

#### Étape A : `makemigrations` (La photo)

Quand vous tapez cette commande, Django compare vos modèles actuels avec la version précédente. Il crée alors un fichier Python dans le dossier `blog/migrations/`.

```bash
python manage.py makemigrations
#Mac
python3 manage.py makemigrations
```

* **Ce que ça fait** : Ça génère un "plan d'action" (ex: `0001_initial.py`).
* **Ce que ça ne fait pas** : Ça ne touche pas encore à la base de données.

#### Étape B : `migrate` (L'exécution)

C'est ici que le plan est appliqué. Django lit les fichiers de migration qui n'ont pas encore été exécutés et transforme le tout en SQL pour votre base de données.

```bash
python manage.py migrate
#Mac
python3 manage.py migrate
```

* **Ce que ça fait** : Ça crée les tables ou ajoute les colonnes réellement.


### 3. Les situations courantes

#### Ajouter un champ obligatoire

Si vous ajoutez un champ à un modèle qui contient déjà des données, Django va vous poser une question :

> *"You are trying to add a non-nullable field 'auteur' to 'article' without a default..."*

**Pourquoi ?** Parce que pour les articles qui existent déjà, Django ne sait pas quoi mettre dans la colonne "auteur".

* **Option 1** : Donner une valeur par défaut immédiatement dans le terminal.
* **Option 2** : Annuler et ajouter `null=True` ou `default='Anonyme'` dans votre modèle.

#### Voir l'historique

Pour savoir quelles migrations ont été appliquées :

```bash
python manage.py showmigrations
#Mac
python3 manage.py showmigrations
```

Les cases cochées `[X]` sont celles qui sont déjà dans votre base de données.



### 4. Revenir en arrière (Le "Rollback")

C'est la magie des migrations. Si vous avez fait une erreur dans la migration `0005` et que vous voulez revenir à l'état `0004` :

```bash
#Windows
python manage.py migrate blog 0004
#Mac
python3 manage.py migrate blog 0004
```

Django va automatiquement annuler les changements de la migration `0005`.


### Les 3 règles d'or des migrations

1. **Ne supprimez jamais** les fichiers dans le dossier `migrations/` (sauf si vous savez exactement ce que vous faites).
2. **Commitez** vos fichiers de migration sur Git. Ils font partie de votre code source.
3. **Ne modifiez jamais** un fichier de migration existant. Si vous avez fait une erreur, créez-en une nouvelle par-dessus.

---

###  Mini-TP

1. Ajoutez un champ `prix = models.IntegerField()` sans valeur par défaut.
2. Lancez `makemigrations`.
3. Lisez le message de Django et essayez de comprendre l'option 1 (fournir une valeur par défaut temporaire).

