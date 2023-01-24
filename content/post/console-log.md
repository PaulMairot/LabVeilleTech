+++
author = "Paul Mairot"
title = "Article : Beyond Console.log() – Level up Your Debugging Skills"
date = "2023-01-15"
description = "Différentes techniques de débogage pour améliorer les compétences de développement en JavaScript."
tags = [
    "article",
    "console"
]
+++

Différentes techniques de débogage pour améliorer les compétences de développement en JavaScript.<!--more-->

## Résumé de l'article

L'article "Beyond console.log: Level Up Your Debugging Skills" vise à aider les développeurs à améliorer leurs compétences de débogage en JavaScript. Il explique comment utiliser des outils tels que la console JavaScript, les déclarations de breakpoints, les outils de débogage de navigateur, les outils de débogage de réseau, les outils de débogage de performance et les outils de débogage de source pour résoudre les erreurs et optimiser le code.

La console JavaScript est un outil puissant qui permet de loguer des informations dans la console du navigateur. Il permet de loguer des messages, des objets, des tableaux, etc. Les déclarations de breakpoints permettent de mettre en pause l'exécution du code à un endroit spécifique pour pouvoir inspecter les variables et les propriétés de l'objet. Les outils de débogage de navigateur sont intégrés à la plupart des navigateurs modernes et permettent de déboguer le code JavaScript, d'inspecter les éléments HTML et CSS, de visualiser les requêtes réseau et de mesurer les performances.

[Lien vers l'article complet](https://www.sitepoint.com/beyond-console-log-level-up-your-debugging-skills/)



## Ce que j'ai découvert

Comme beaucoup de monde, je n'utilise partiquement que la simple commande ```console.log()```. Cet article met alors en lumière toutes les autres fonctions de la console. La partie sur ```console.time()``` m'était inconnue et est utile dans nombreux projets.

```javascript
console.time('go');
for(let i = 0; i < 200000; i+=1) {
  let x = Math.random()*2000;
}
console.timeEnd('go'); // go: 11.7861328125 ms
```

## Quand cela me sera-t-il utile ?

Dans tous mes futurs projets, cet article me sera utile lors de la partie de débogage. Celui-ci me permettra de mieux structurer mes commandes console et ainsi optimiser la recherche de bugs éventuels dans mes développment.