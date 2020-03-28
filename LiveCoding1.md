```
Le but de cet exercice est de vous aider à vous familiariser avec les instructions
de base de MongoDB

Nous allons commencer avec un schéma simple :

Un document correspond à un film, qui aura un nom, un réalisateur et une liste
d'acteurs qui ont joué
dans ce film. Un acteur a un nom et un prénom
```

```console
1-Commencez par créer une base de données s'appelant Cinema 
```
*Requête1*

```js
use Cinema
```

```console
2-Insérer le film "Le code magique" réalisé par "Jhon Codeur" dans 
lequel a joué "Didier Drogba", "Pierre Cabantus" et "Lionel Messi"
```
*Requête2*

```js
db.Cinema.insert(
                {nom :"Le code magique", 
                realisateur :"Jhon Codeur",
                acteurs :[
                           {nom :"Drogba", prenom :"Didier"}, 
                           {nom :"Cabantus",prenom :"Pierre"},
                           {nom :"Messi", prenom :"Lionel"}
                         ]
                }
                )
```

```console
3-NanFlix prévoit bientôt de faire un film d'action avec de jeunes personnages
de BD dont SuperSidick.

Le nom du réalisateur et des acteurs qui vont jouer dans le film ne sont pas 
encore connus.

Il nous est toutefois demandé d'ajouter cette information dans notre collection
sachant que le film s'appellera "La bataille front end". On donnera l'_id 1 au film.
```
*Requête3*

```js
 db.Cinema.insert({
                   _id:"1", 
                   nom:"La bataille front end"
                  }
                  )
 ```
 
```console
4-Nous venons d'apprendre que le film sera finalement réalisé par "SORO ibrahim".

Ajoutez le nom du réalisateur aux informations
```
*Requête4*
```js

db.Cinema.update(
                  {
                    _id:"1"
                   }, 
                  { $set:
                        {
                          realisateur:"SORO ibrahim"
                        }
                  }
                  )
```

```console
5-Après les premiers castings, il a été convenu que le personnage de SuperSidick
sera interprété par l'acteur ivoirien Guy Kalou.

Mettez à jour les informations dans la base.
```
*Requête5*
```js

db.Cinema.update(
                 {_id:"1"},
                 {$push:
                        {acteurs:
                              {nom:"Kalou", prenom:"Guy"}
                         }
                  }
                  )
```

```console
6-Ayant du mal à trouver les acteurs adaptés aux personnages, NanFlix
décide d'abandonner le projet.

Nous allons donc retirer ce dernier de notre base de données
```
*Requête6*
```js   
     db.Cinema.remove({_id:"1"})
```
