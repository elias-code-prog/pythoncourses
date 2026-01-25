#  L'Architecture MVT

Contrairement à d'autres frameworks qui utilisent le MVC (Modèle-Vue-Contrôleur), Django utilise le **MVT**. Ne paniquez pas, c'est presque la même chose, mais avec des noms qui décrivent mieux le web moderne.

Voici comment se répartissent les rôles dans votre projet :

### 1. M pour MODÈLE (La Base de Données) 

Le Modèle, c'est la structure de vos données. Au lieu d'écrire du SQL complexe, vous décrivez vos données en pur Python.

* *Exemple :* "Un Article de blog a un titre, un contenu et une date de publication."

### 2. V pour VUE (Le Cerveau) 

C'est ici que réside la logique. La Vue reçoit une requête (ex: "L'utilisateur veut voir l'article n°5"), va demander au **Modèle** de chercher cet article, puis le transmet au **Template**.

* *Exemple :* Une fonction Python qui récupère les données et décide si l'utilisateur a le droit de les voir.

### 3. T pour TEMPLATE (L'Affichage) 

Le Template, c'est du HTML, C'est la structure visuelle de votre page. On y utilise des balises spéciales (le langage de template Django) pour afficher les variables envoyées par la Vue.

* *Exemple :* Une page HTML avec un emplacement vide où le titre de l'article viendra s'insérer dynamiquement.


###  Le cycle d'une requête

Pour bien comprendre, suivons le chemin d'un utilisateur qui veut voir un article :

1. **L'URL (Le facteur)** : L'utilisateur tape `monsite.com/article/5`. Le fichier `urls.py` reçoit l'adresse et dit : *"Ok, c'est pour la Vue numéro 5"*.
2. **La VUE (Le chef d'orchestre)** : Elle prend le relais. Elle dit : *"Hé, le Modèle ! Donne-moi les infos de l'article 5 s'il te plaît"*.
3. **Le MODÈLE (L'archiviste)** : Il fouille dans la base de données, trouve l'article et le redonne à la Vue.
4. **La VUE (Encore elle)** : Elle prend les données et appelle le Template : *"Hé, le Template ! Voici les données, prépare-moi une belle page HTML avec ça"*.
5. **Le TEMPLATE (Le designer)** : Il injecte le titre et le texte dans le HTML et renvoie la page finale au navigateur de l'utilisateur.


### Analogie : Le Restaurant

Si Django était un restaurant :

* **L'URL** : C'est le **Menu**. Vous choisissez ce que vous voulez.
* **La VUE** : C'est le **Serveur**. Il prend votre commande, va voir en cuisine, et vous rapporte votre assiette.
* **Le MODÈLE** : C'est le **Cuisinier**. Il manipule les ingrédients (les données) pour préparer le plat.
* **Le TEMPLATE** : C'est l'**Assiette**. C'est la présentation finale qui rend le plat agréable à manger.

---

### Mini-TP

Imaginez que vous vouliez ajouter une page "Profil Utilisateur" à votre site.

1. Que devriez-vous définir dans le **Modèle** ? (Nom, photo, bio ?)
2. Que ferait la **Vue** ? (Chercher l'utilisateur connecté ?)
3. À quoi ressemblerait le **Template** ? (Une page HTML avec des balises pour afficher le nom ?)
    