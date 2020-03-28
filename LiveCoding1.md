```
Le but de cet exercice est de vous aider à vous familiariser avec les instructions de base de MongoDB

Nous allons commencer avec un schéma simple :

Un document correspond à un film, qui aura un nom, un réalisateur et une liste d'acteurs qui ont joué dans ce film. Un acteur a un nom et un prénom
```

1-Commencez par créer une base de données s'appelant Cinema 

2-Insérer le film "The godfather" réalisé par "Francis Ford Coppola" dans lequel a joué "Marlon Brando", "Al Pacino" et "Robert Duvall"

Requête2 : 

```js
db.Cinema.insert({nom :"The godfather", realisateur :"Francis Ford Coppola", acteurs :[{nom :"Pacino", prenom :"Al"}, {nom :"Brando",prenom :"Marlon"}, {nom :"Duvall", prenom :"Robert"}]})
```

3-Marvel prévoit bientôt de faire un film d'avengers avec de jeunes personnages de BD dont Kamala Khan.

Le nom du réalisateur et des acteurs qui vont jouer dans le film ne sont pas encore connus.

Il nous est toutefois demandé d'ajouter cette information dans notre collection sachant que le film s'appellera "Young Avengers". On donnera l'_id 1 au film.

Requête3: 
```js
 db.Cinema.insert({_id:"1", nom:"Young Avengers"})
 ```
 
 4-Nous venons d'apprendre que le film sera finalement réalisé par "Joe Johnston".

Ajoutez le nom du réalisateur aux informations
Requête4
```js

db.Cinema.update({_id:"1"}, {$set:{realisateur:"Joe Johnston"}})
```

5-Après les premiers castings, il a été convenu que le personnage de Kamala Khan sera interprété par l'actrice pakistanaise Sanam Jhung.

Mettez à jour les informations dans la base.

Requête 5
```js

db.Cinema.update({_id:"1"}, {$push:{acteurs:{nom:"Jhung", prenom:"Sanam"}}})
```

6-Ayant du mal à trouver les acteurs adaptés aux personnages, Marvel décide d'abandonner le projet.

Nous allons donc retirer ce dernier de notre base de données

Requête 6:
```js   
db.Cinema.remove({_id:"1"})
```
