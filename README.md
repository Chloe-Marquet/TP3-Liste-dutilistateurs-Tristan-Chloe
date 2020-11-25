# TP3-Liste-dutilistateurs-Tristan-Chloe

## Analyse de code


### 1. Quelle ligne charge le fichier JSON dans le code ?
Il s'agit de la ligne ci-dessous dans le fichier App.js

```import users from "./Users.json";```


### 2. Quelle est la structure de données du fichier JSON ?

Ce format provient du monde du JavaScript et représente un objet sous forme de clé/valeur. 
La clé et la valeur sont des chaînes de caractères séparé par ```:``` et chaque paire est séparée de la suivante par une virgule.

Le JSON accepte les types de données suivantes :
* Objet
* Array
* Nombre
* Chaînes de caractères
* ```true```
* ```false```
* ```null```


### 3. Justifiez le User.propTypes. Quelles données ne sont pas prises en compte ?

Le ```User.proptypes``` sert à récupérer les données json du ```users.json```. 
```propTypes``` exporte un ensemble de validateurs qui peuvent être utilisés pour s'assurer que la donnée que vous recevez est valide.

Quand une valeur non valide est fournie à une prop, un message d'avertissement apparaîtra dans la console JavaScript.
```propTypes``` n'est vérifiée qu'en mode développement.

De ce fait on peut afficher à partir de ces données le nom, la localisation, la photo de la personne… Beaucouyp des données json ne sont pas utilisées, on compte parmis elles : street, postcode, coordinates, timezone, username, password…



### 4. Quelles données sont obligatoires pour construire le composant User ?

Le name avec son ```title```, son ```first```, et son ```last``` sont obligatoires car elles contiennent un ```required```.


### 5. A quoi correspond PropTypes.shape ?

Le ```propTypes.shape``` est utilisé pour décrire un objet dont les clés sont connues, en précisant les types de leurs valeurs et peuvent représenter différents types.


### 6. Pourquoi l'attribut contient deux accolades ?

L’attribut contient deux accolades car il contient différentes clés.


### 7. Quel est le nom de l'opérateur qui transmet les données du composant App vers le composant User? Pourquoi est-ce dangereux d'abuser de cet opérateur ?

L’opérateur qui transmet des données est un props. C’est dangereux d’abuser de ce type d’opérateur car il est non modifiable une fois qu’il est transféré.


### 8. Ajoutez un paragraphe p au composant User pour afficher la date de naissance sous la forme "Né le 27/02/1942" pour un homme ou "Née le 27/02/1942" pour une femme en utilisant une condition ternaire. Copiez le code ajouté dans ce document en guise de réponse.

