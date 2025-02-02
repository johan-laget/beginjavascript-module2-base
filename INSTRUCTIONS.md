On va continuer à travailler sur "ADDITION-MASTER ™️" afin d'ajouter une fonctionnalité très importante :

- Le choix de l'opérateur !

Une fois que l'utilisateur aura choisi l'opérateur, on sera capable de lui demander les deux nombres à additionner et de lui donner le résultat en fonction de l'opérateur choisi.

Tu as déjà vu les `if`, donc ça devrait être un peu plus simple cette fois !

## Partie 1 - Choix de l'opérateur

On va commencer par demander à l'utilisateur de choisir l'opérateur qu'il souhaite utiliser.

Pour cela, on va afficher dans la console un message qui décrit, pour chaque opérateur, un nombre :

```bash
1 - Addition
2 - Soustraction
```

(Pour l'instant, on va seulement faire l'addition et la soustraction. On verra pour les autres opérateurs plus tard)

Ensuite, on va demander à l'utilisateur de choisir un nombre entre 1 et 2.

S'il choisit autre chose que 1 ou 2, on va lui dire que son choix n'est pas valide et arrêter le script.

Ensuite, on fait comme ce qu'on avait fait sur l'exercice concernant les nombres, sauf qu'on va utiliser, à la fin, un `switch` !

Ne t'en fais pas... je t'explique comment faire car pour la partie 1, les émojis sont là pour t'aider.

Résultat attendu :

```bash
ADDITION-MASTER ™️
Choose an operator:
1. Addition
2. Soustraction
Enter the operator: 2
Enter the first number: 5
Enter the second number: 5
The result of soustraction is: 0

# Ou avec l'addition
ADDITION-MASTER ™️
Choose an operator:
1. Addition
2. Soustraction
Enter the operator: 1
Enter the first number: 5
Enter the second number: 5
The result of addition is: 10
```

## Partie 2 - Ajout de la multiplication et de la division

Ici, on va ajouter la multiplication et la division. Au début du script, il sera écrit :

```bash
Choose an operator:
1. Addition
2. Soustraction
3. Multiplication
4. Division
```

Il faudra modifier la condition `if` pour vérifier si l'opérateur est valide, en prenant en compte les nouveaux opérateurs (3 et 4).

On rajoute également une condition pour la division qui vérifie que le deuxième nombre n'est pas égal à 0.

Pour cela, dans le `if`, on vérifie que l'opérateur est égal à 4 et que le deuxième nombre est égal à 0, car cette vérification ne se produit QUE pour la division.

Évidemment, il faudra aussi modifier le `switch` final afin de prendre en compte les nouveaux opérateurs.

Résultat attendu :

```bash
ADDITION-MASTER ™️
Choose an operator:
1. Addition
2. Soustraction
3. Multiplication
4. Division
Enter the operator: 4
Enter the first number: 1
Enter the second number: 0

Error: division by 0
```

## Partie 3 - Ajout d'une limite

L'utilisateur est capable de mettre n'importe quel nombre, même un nombre énorme pour l'instant :

````bash
ADDITION-MASTER ™️
Choisis un opérateur :
1. Addition
2. Soustraction
3. Multiplication
4. Division
Enter the operator: 3
Enter the first number: 999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999
Enter the second number: 10
The result of multiplication is: Infinity
```

Dans ce cas-là, la réponse devient "Infinity" car le nombre est trop grand pour être stocké dans une variable.

Ton travail est de rajouter une vérification dans la même condition que `Number.isNaN` pour vérifier que le nombre est plus petit que :

`100000000000000`

Tu devrais modifier le `if` pour rajouter une comparaison entre le nombre et le chiffre ci-dessus. Pour cela, il faut utiliser les opérateurs de comparaison `<` et `>` qui signifient :

- `<` : [plus petit que](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Operators/Less_than)
- `>` : [plus grand que](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Operators/Greater_than)

Je te laisse choisir le bon...

Il faudra également modifier le message d'erreur pour indiquer que le nombre est invalide ou qu'il est plus grand que le nombre inscrit ci-dessus.

## Partie 4 - Et les nombres négatifs ?

Ok... maintenant on a ajouté une limite de `100000000000000` à nos nombres positifs !

Donc si j'écris :

```bash
1000000000000000 // pas validé
-1000000000000000 // validé 🤔
```

Effectivement, il y a un problème, on devrait aussi vérifier que le nombre est plus grand que `-100000000000000` !

Pour cela, il suffit d'une petite modification...

Tu connais la notion de valeur absolue ? C'est la valeur d'un nombre sans prendre en compte le signe.

Avec JavaScript, il est possible de récupérer la valeur absolue :

```js
Math.abs(-10); // 10
Math.abs(10); // 10
```

Modifie la condition pour utiliser la valeur absolue afin que la vérification fonctionne aussi avec les nombres négatifs.

Aussi, déplace notre valeur limite (100000000000000) dans une constantes afin de ne pas dupliquer le code plusieurs et pouvoir facilement le changer.

## Partie 5 - Boucle infinie (bonus)

Pour te plonger dans tes retranchements et pour préparer la suite, on va utiliser une boucle `while` pour te demander de manière infinie quel opérateur tu veux utiliser.

Pour cela, on va créer une boucle `while`. Une boucle `while` prend en paramètre une condition et exécute le code à l'intérieur de la boucle tant que la condition est vraie.

```js
let operator = 0;

while (operator === 0) {
  // code de la boucle
}
```

Traduction : "tant que l'opérateur est égal à 0, exécute ce code"

Donc à l'intérieur de la boucle, on va demander à l'utilisateur de choisir un opérateur et de le stocker dans la variable `operator`, uniquement si l'opérateur est égal à 1, 2, 3 ou 4 !

Dans le cas contraire, on affiche un message d'erreur du style "You can only choose 1, 2, 3 or 4" et on redemande à l'utilisateur de choisir un opérateur, car tant que la variable `operator` n'est pas assignée à un nombre valide, la boucle continue de s'exécuter.

Tu remarqueras que j'utilise `let` ici et non `const`, car on va modifier la valeur de `operator` dans la boucle.

Cet exercice est compliqué car tu ne connais (normalement) pas `while`. Tu vas devoir chercher sur internet comment ça fonctionne et comment l'utiliser.

C'est pour ça que c'est un exercice "bonus" et on verra les boucles dans la suite.

Exemple :

```bash
ADDITION-MASTER ™️
Choose an operator:
1. Addition
2. Soustraction
3. Multiplication
4. Division
Enter the operator: a

Error: operator is not 1, 2, 3 or 4! Retry.
Enter the operator: v

Error: operator is not 1, 2, 3 or 4! Retry.
Enter the operator: c

Error: operator is not 1, 2, 3 or 4! Retry.
Enter the operator: x

Error: operator is not 1, 2, 3 or 4! Retry.
Enter the operator: s

Error: operator is not 1, 2, 3 or 4! Retry.
```
````
