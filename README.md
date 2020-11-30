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


### 6. Pourquoi l'attribut ```style``` contient deux accolades ?

L’attribut ```style``` contient l'objet litéral en ligne dans la valeur ```prop```.


### 7. Quel est le nom de l'opérateur qui transmet les données du composant App vers le composant User? Pourquoi est-ce dangereux d'abuser de cet opérateur ?

L’opérateur qui transmet des données est props. C’est dangereux d’abuser de ce type d’opérateur car il est non modifiable une fois qu’il est transféré.


### 8. Ajoutez un paragraphe p au composant User pour afficher la date de naissance sous la forme "Né le 27/02/1942" pour un homme ou "Née le 27/02/1942" pour une femme en utilisant une condition ternaire. Copiez le code ajouté dans ce document en guise de réponse.

* App.js
```
function User(props) {
  return (
    <div className="card">
      <div className="card-content">
        <img
          src={props.picture.medium}
          alt={`Profile of ${props.name.first}`}
          style={{ width: "100%" }}
        />
        <div className="container">
          <h4>{props.name.first}</h4>
          <p>
            {props.location.state}, {props.location.country}
          </p>
          <p>
            {props.gender === "male" ? "né" : "née"} le {props.dateOfBirth}
          </p>
        </div>
      </div>
    </div>
  );
}

User.propTypes = {
  gender: PropTypes.string,
  name: PropTypes.shape({
    title: PropTypes.string,
    first: PropTypes.string,
    last: PropTypes.string
  }).isRequired,
  dateOfBirth: PropTypes.string,
  location: PropTypes.object,
  email: PropTypes.string,
  picture: PropTypes.shape({
    medium: PropTypes.string
  })
};
```

* User.json
```
    {
      "gender": "male",
      "name": { "title": "Mr", "first": "Eder", "last": "da Cunha" },
      "dateOfBirth": "27/02/1942",
      "location": {
        "street": { "number": 2090, "name": "Rua Pernambuco " },
        "city": "Araguari",
        "state": "Espírito Santo",
        "country": "Brazil",
        "postcode": 65931,
        "coordinates": { "latitude": "-79.1817", "longitude": "-133.4020" },
        "timezone": {
          "offset": "+2:00",
          "description": "Kaliningrad, South Africa"
        }
      },
```



## Rédaction de tests

### 9. Lisez les [recettes de tests](https://fr.reactjs.org/docs/testing-recipes.html#gatsby-focus-wrapper). Rédigez un test pour vérifier que le composant User contient une image.

```
import React from “react”;
import { render, unmountComponentAtNode} from “react-dom;
import {act} from “react-dom/test-utils”;
import User from “./Users”;

let container = null;
beforeEach(() => {
container = document.createElement(“div”);
document.body.appendChild(container);
});

afterEach(() => {
unmountComponentAtNode(container);
container.remove();
container = null;
});

it(“affiche une image”,(), => {
act(() => {
render(<User  picture=”https://randomuser.me/api/portraits/men/80.jpg” />, container);
});
expect(container.textContent).toBe(“https://randomuser.me/api/portraits/men/80.jpg”);
});

```


### 10. Rédigez un autre test dans lequel vous créez le composant ```User``` avec le ```name``` de votre choix dans le ```props``` et vérifiez que le composant affiche bien le ```name```.

```
import React from “react”;
import { render, unmountComponentAtNode} from “react-dom;
import {act} from “react-dom/test-utils”;
import User from “./Users”;

let container = null;
beforeEach(() => {
container = document.createElement(“div”);
document.body.appendChild(container);
});

afterEach(() => {
unmountComponentAtNode(container);
container.remove();
container = null;
});

it(“devrait afficher le nom”, () => {
const fakeUser = {
name = TristanVarciat”
};
jest.spyOn(global, “fetch”).mockImplementation(() =>
Promise.resolve({
json: () => Promise.resolve(fakeUser)})
);

await act(async() => {
render(<User/>, container);
});

expect(container.querySelector(“h4”).textContent).toBe(fakeUser.name);

global.fetch.mockRestore();
});
```


### 11. Faites un test de "capture d'instantanés" en suivant les indications de la documentation

```
import React from “react”;
import { render, unmountComponentAtNode} from “react-dom;
import {act} from “react-dom/test-utils”;
import User from “./Users”;

let container = null;
beforeEach(() => {
container = document.createElement(“div”);
document.body.appendChild(container);
});

afterEach(() => {
unmountComponentAtNode(container);
container.remove();
container = null;
});

it (“devrait afficher un state”, () => {
act()) => {
render(<Hello  state=”Queensland”/>, container);
});

expect( 
pretty(container.innerHTML)
).toMatchInlineSnapshot();
});
```


### 12. Proposez 3 autres tests

```
import React from “react”;
import { render, unmountComponentAtNode} from “react-dom;
import {act} from “react-dom/test-utils”;
import User from “./Users”;

let container = null;
beforeEach(() => {
container = document.createElement(“div”);
document.body.appendChild(container);
});

afterEach(() => {
unmountComponentAtNode(container);
container.remove();
container = null;
});

it(“devrait afficher le state”, () => {
const fakeUser = {
state=”Queensland”
};
jest.spyOn(global, “fetch”).mockImplementation(() =>
Promise.resolve({
json: () => Promise.resolve(fakeUser)})
);

await act(async() => {
render(<User/>, container);
});

expect(container.querySelector(“p”).textContent).toBe(fakeUser.state);

global.fetch.mockRestore();
});

// Vérifier que le composant affiche bien le pays :
import React from “react”;
import { render, unmountComponentAtNode} from “react-dom;
import {act} from “react-dom/test-utils”;
import User from “./Users”;

let container = null;
beforeEach(() => {
container = document.createElement(“div”);
document.body.appendChild(container);
});
```
