---
title: Librairie standard
description: Librairies standard
hide_table_of_contents: true
---

# Kotlin, librairie standard 📘

<Row>

<Column>

:::danger Avant la séance (2h)

1. Lire la documentation de la librairie standard de Kotlin sur les ***[Collections](https://kotlinlang.org/docs/collections-overview.html)***, les ***[List](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-list/)***, les ***[Set](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-set/)*** et les ***[Map](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-map/)*** (max 20 minutes).
2. Regarder les vidéos de théorie.
3. Commencer les exercices de la semaine.
4. Arrêter après 2 heures de travail.

:::

</Column>

<Column>

:::tip Vidéos

<Video url="https://youtu.be/vV_nT5Sj7J4"/>
<Video url="https://youtu.be/5PhJMt4Qwhk"/>
<Video url="https://youtu.be/JEL8ord98nY"/>
<Video url="https://youtu.be/pv-A40Dy-XA"/>
<Video url="https://youtu.be/VB1uKiTiqiw"/>

:::

</Column>

<Column>

:::info À faire pendant la séance

- Compléter les exercices de la semaine.
- Continuer le **[travail pratique](../tp/tp1)** (à remettre bientôt!).

:::

</Column>


</Row>

:::note Exercices

Crée-toi un nouveau projet dans lequel tu pourras créer différents fichiers exécutables pour les exercices.

### Exercice EntrezUnNombre.kt

En utilisant la fonction ***readln()***, crée un programme qui demande à l'utilisateur de taper un mot jusqu'à ce que ce soit un nombre entier (dans la console) :

```text {2,4,6}
Veuillez entrer un nombre :
pipo
Ceci n’est pas un nombre, veuillez entrer un nombre :
popi
Ceci n’est pas un nombre, veuillez entrer un nombre :
123
Merci, votre nombre est 123.
```

### Trace et récursivité

Effectue la trace de la fonction suivante :

```kotlin
fun main() {
    println(factorielle(2))
}
fun factorielle(n: Int): Int {
    if (n == 0) {
        return 1
    } else {
        return n * factorielle(n - 1)
    }
}
```

Après avoir complété ta trace manuelle et ton projet, tu peux (pas obligé) appeler ton prof pour qu'il te montre comment voir les contextes d'exécution (variables) aux différents niveaux dans la pile.

### Exercice EcrireFichier.kt

En utilisant la librairie standard, ton programme doit :

- Créer un fichier vide dans le dossier courant appelé vide.txt.
- Créer un fichier texte contenant ton nom et ton prénom dans le dossier parent du dossier courant.

### Exercice LireFichier.kt

En utilisant la librairie standard, ton programme doit :

- prendre un ou plusieurs noms de fichiers en arguments de ligne de commande;
- afficher le contenu de chaque fichier passé en argument dans la console en les séparant par une ligne de -------------.

### Exercice ListeSimple.kt

Ton programme doit contenir :
- une fonction ***repete(n: Int, nombreFois: Int)*** qui renvoie une liste d'entiers avec tous les nombres de 1 à *n* répétés *nombreFois*.\
Par exemple, pour ***repete(4, 2)***, on doit obtenir **[1, 1, 2, 2, 3, 3, 4, 4]**;
- une fonction ***main*** qui teste la fonction précédente avec plusieurs valeurs de paramètres, et affiche les listes retournées avec *println()*.

### Exercice TriSimple.kt

Ton programme doit contenir :
1. une fonction ***triInverseALaMain(liste: List\<Double\>)*** qui renvoie la liste triée par ordre inverse.\
Par exemple, si on passe **[0.1, 12.34, -0.1234, 3.1416]** on doit obtenir **[3.1416, -0.1234, 12.34, 0.1]**.\
Tu dois utiliser une liste mutable et une boucle;
2. une fonction ***triInverse(liste: List\<Double\>)*** qui fait la même chose, mais sans boucle et en utilisant une méthode de l'objet *List* reçu en paramètre;
3. une fonction ***main*** qui teste les deux fonctions précédentes avec plusieurs listes.

### Exercice TrouvePisCompte.kt

Ton programme doit contenir :
1. une fonction ***trouveALaMain(element: Int, liste: List\<Int\>): Boolean*** qui renvoie si la liste contient l'élément fourni ou pas.\
Tu dois parcourir la liste avec une boucle;
2. une fonction ***trouve(element: Int, liste: List\<Int\>): Boolean*** qui fait la même chose, mais sans boucle et en utilisant une méthode de l'objet *List*;
3. une fonction ***compteALaMain(element: Int, liste: List\<Int\>): Int*** qui renvoie le nombre d'apparitions de l'element dans la liste.\
Tu dois parcourir la liste avec une boucle;
4. une fonction ***compte(element: Int, liste: List\<Int\>): Int*** qui fait la même chose, mais sans boucle et en utilisant une méthode de l'objet *List*;
5. une fonction ***main*** qui teste les 4 fonctions sur plusieurs exemples.

### Exercice Ensemble.kt

Crée un programme pour gérer une liste de mots reçue en ligne de commande.\
Tu dois t'assurer qu’il n’y a pas de doublons (utilise un ***Set***).\
Affiche ensuite les mots triés par ordre alphabétique dans la console.

Par exemple, si ces mots sont passés en ligne commande :

```
on me voit on me voit plus on me voit plus on me voit
```

la console devrait afficher :

```
me
on
plus
voit
```

### Exercice Compteur.kt

En utilisant une ***Map***, crée un programme qui compte les occurences de chacun des mots reçus en ligne de commande.\
Par exemple, si ces mots sont passés en ligne commande :

```
on me voit on me voit plus on me voit plus on me voit
```

ta *Map* devrait contenir :

```kotlin
{on=4, me=4, voit=4, plus=2}
```


:::




<!-- EXERCICES RETIRÉS :

### Exercice TriComparator.kt

Ton programme doit contenir une fonction ***triComplexe(liste: List\<Int\>): List\<Int\>*** qui renvoie la liste, triée selon un ordre un peu complexe :
- si un nombre contient moins de 7 qu'un autre, il doit être avant dans le tri;
- si 2 nombres ont le même nombre de 7, le plus petit devrait être avant dans la liste.

Par exemple, si la fonction reçoit :\
[1234, 747, 77, 1977, -71, 17, 7], elle doit retourner :\
[1234, -**7**1, **7**, 1**7**, **77**, **7**4**7**, 19**77**].

Le ***main*** de ton programme doit tester la fonction précédente avec plusieurs listes.

Tu peux utiliser des boucles si tu veux mais, idéalement, ton programme n'utiliserait que des fonctions de la librairie standard de Kotlin pour effectuer le tri en une seule ligne de code!

### Exercice Liste et références

Crée une classe **Truc** (fichier Truc.kt) avec un constructeur qui reçoit 2 valeurs pour instancier 2 propriétés :

- pipo (un Int);
- popi (une String).

Surcharge la méthode ***toString()*** de la classe Truc pour afficher les valeurs des 2 propriétés.

Crée un fichier exécutable **GererTrucs.kt**, et dans le ***main*** :

1. crée 3 objets de classe Truc dans les variables ***a***, ***b*** et ***c***, avec des valeurs différentes pour chacun;
2. crée une liste **liste1** et mets-y dans cet ordre : **[*a*, *b*, *c*]**;
3. crée une liste **liste2** et mets-y dans cet ordre : **[*b*, *c*, *a*]**;
4. affiche les 2 listes à l'aide de *println()*;
5. modifie les valeurs de l'objet ***a***;
6. réaffiche les 2 listes.

Dans un fichier **Trucs.md** à la racine du projet, réponds à ces questions :
1. L'objet ***a*** dans les listes a-t-il été modifié?
2. Pourquoi?
3. Est-ce une copie de l'objet ***a*** original?

Dans le doute, demande à ton prof.

### Exercice Dictionnaire.kt (optionnel)

On veut garder en mémoire les notes de nos étudiants.\
Après mûre réflexion, on décide d'utiliser comme structure de données un **dictionnaire** (*Map*) avec la note de l'étudiant.e comme clé et son nom de famille comme valeur.

Évalue la solution proposée (bon / pas bon, et pourquoi).

1. Dans le *main*, crée la structure proposée et mets-y les paires suivantes :
   - Sanchez a eu 92%
   - Tremblay a eu 68%
   - Richard a eu 73%
2. Crée une autre fonction qui reçoit une *map* et qui parcourt ses paires (note, etudiant) pour les afficher dans la console, une par ligne.\
   Appelle ta fonction dans la *main*.\
   Le résultat doit ressembler à ceci :
```
NOTES
Sanchez a eu 92%.
Tremblay a eu 68%.
Richard a eu 73%.
```
3. Sur de nouvelles lignes dans ton *main* :
   - Ajoute un nouvel étudiant dans ta *map*, Gino Tremblay, qui a eu 30%.
   - Appelle de nouveau ta fonction pour afficher les notes.
   - Ajoute une nouvelle étudiante, Mauda Sasa, qui a eu 68%.
   - Affiche encore les notes de ta *map*.
- Que s'est-il passé?
- Pourquoi?
- A-t-on bien choisi la paire (clé, valeur) de notre *map*?
- Que proposes-tu? -->


# Kotlin et librairies tierces 📖

<Row>

<Column>

:::danger Avant la séance (2h)

Il existe des milliers de librairies Java pour faire presque tout, qui fonctionnent généralement bien. De nombreuses compagnies tech comme [Google](https://github.com/search?q=topic%3Aandroid+org%3Agoogle+fork%3Atrue&type=repositories), [Twitter](https://github.com/Twitter) ou [Square](https://github.com/search?q=topic%3Aandroid+org%3Asquare+fork%3Atrue&type=repositories) partagent leur librairies.

:::

</Column>

<Column>

:::info À faire pendant la séance

- Demo de MavenRepository: librairie, version
- Exemple de recherche de librairie : exemple de [https://square.github.io](https://square.github.io)
    - Interopérabilité des librairies Java et Kotlin
- Compléter les exercices de la semaine
- **Continuer le [TP1](../tp/tp1)**

**Attention** : une grande partie du travail de ces exercices consiste à faire vos propres recherches. Lorsqu'on commence à utiliser une nouvelle librairie, il est généralement recommandé de commencer en lisant la documentation et les exemples fournis par les développeurs de la librairie.

:::

</Column>

</Row>

:::note Exercices

### Exercice Jsoup

À l'aide de la librairie [Jsoup](https://jsoup.org/), vous devez écrire un petit programme qui prend une url en paramètre, qui télécharge la page web correspondant, puis qui extrait toutes les balises *\<a\>* de la page et affiche leur attribut *href*.

Par exemple, si la page contient

```html
<a href="pipo.html">test</a>
```

le programme devra afficher `test = pipo.html` dans la console.

### Exercice ValidationCourriel

Tu dois trouver une librairie qui valide si un courriel est valide. Écris un programme pour voir si la méthode fournie par la librairie fonctionne sur les exemples suivants:

- Ok : jo@pipo.org
- Ok : ma_mu@m.ca
- Ok : a.a@a.ca
- Ko : a.a@a.aa
- Ko : ab@ab
- Ko : a.b@ab
- Ko : jo

### Exercice SuperListe

On veut comparer les performances de plusieurs implémentations de List quand on parle de performance pour l'insertion.
On souhaite comparer le temps d'exécution nécessaire pour:

- ajouter 100 000 éléments en dernière position dans la liste
- ajouter 100 000 éléments en première position dans la liste
- ajouter 100 000 éléments dans une position au hasard dans la liste

Pour permettre de tester plusieurs listes, on vous recommande de créer une méthode

```java
fun testeCetteListe(liste: MutableList<Int>) {
    val random: Random = Random(1234)
    val a = System.currentTimeMillis()
    // ajouter 100 000 elements en dernière position liste.add(nombre);
    val b = System.currentTimeMillis()
    // ajouter 100 000 elements en première position liste.add(0, nombre);
    val c = System.currentTimeMillis()
    // ajouter 100 000 elements position au hasard liste.add(random.nextInt(liste.size + 1), nombre);
    val d = System.currentTimeMillis()
    // afficher b-a, c-b, d-c qui sont les durées d'exécution en millisecondes
}
```

Le but est de voir quelle liste est la plus performante entre LinkedList, ArrayList et une dernière que vous trouverez dans la librairie suivante : [GapList](http://www.magicwerk.org/page-collections-download.html).

Ainsi, avec un `main` qui appelle la méthode testeCetteListe pour une **LinkedList** puis une **ArrayList** puis une **GapList**, vous aurez une bonne idée des performances respectives.

:::


