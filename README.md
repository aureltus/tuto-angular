# Partie 1 : Initiation

créer une structure automatiquement,
avec un dossier `src` qui contient `app` et `assets`

Dans `app` il y les `component`

`*ngFor` : boucle pour afficher chaque element

L'`{{ product.name }}`instruction est un exemple de la syntaxe d'interpolation d'Angular. L'interpolation `{{ }}`vous permet de restituer la valeur de la propriété sous forme de texte.

La liaison de propriété `[ ]`vous permet d'utiliser la valeur de la propriété dans une expression de modèle.

`*ngIf` Crée l'élément que si le produit actuel a une description.

`@Component` decorateur

`selecteur`

`app-root`

`(click)="share()"` remplace le onclick du button

ng generate component `name` : créer un dossier avec le html,css et js

```
name.component.ts
name.component.html
name.component.css
```

# Partie 2 : Routing

`path:` définir un itinéraire

[routerLink] La directive `RouterLink` vous aide à personnaliser l'élément d'ancrage. Dans ce cas, l'itinéraire, ou URL, contient un segment fixe, `/products`. Le segment final est variable, insérant la propriété `id` du produit actuel. Par exemple, l'URL d'un produit avec un `id1` serait similaire à https://getting-started-myfork.stackblitz.io/products/1.

`ActivatedRouteest` spécifique à chaque composant chargé par le routeur angulaire. `ActivatedRoutecontient` des informations sur l'itinéraire et les paramètres de l'itinéraire.

En injectant `ActivatedRoute`, vous configurez le composant pour utiliser un service. L’ étape Gestion des données couvre les services plus en détail.

`route.snapshot`

`ActivatedRouteSnapshotcontient` des informations sur l'itinéraire actif à ce moment précis. L'URL qui correspond à l'itinéraire fournit le fichier `productId`. Angular utilise le `productId` pour afficher les détails de chaque produit unique.

# Partie 3 : Data

`ng generate service`

https://angular.io/guide/architecture-services

`HttpClient`

`HttpClientModule`

`async`

# Partie 4 : Formulaire
