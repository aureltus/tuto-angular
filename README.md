# Partie 1 : Initiation

il faut avoir Node.js et npm installés sur la machine.

## Creation du projet

on utilise la commande :

```ts
ng new nom-du-projet
```

Ces action sont réaliser automatiqument:

- Vérification de l'installation d'Angular CLI :

  La première étape consiste à vérifier si Angular CLI est installé sur le système. Si ce n'est pas le cas, la commande peut demander d'installer Angular CLI à l'aide de `npm install -g @angular/cli`.

- Interactivité pour la configuration :

  Ensuite, la commande ng new lance un processus interactif pour permettre de configurer certaines options du projet. Pose des questions, telles que le style de feuille de style à utiliser (CSS, SCSS, etc.), si on veut ajouter Angular Routing, etc.

- Création du projet :

  Une fois les options configurées, Angular CLI crée un nouveau répertoire avec le nom que spécifié(ici nom-du-projet).

  Il génère une structure de fichiers de base pour un projet Angular, y compris des fichiers TypeScript, des fichiers de configuration, des fichiers de test, et des fichiers pour les styles.

- Installation des dépendances :

  Ensuite, Angular CLI utilise npm (Node Package Manager) pour installer toutes les dépendances nécessaires au projet. Cela inclut Angular lui-même, ainsi que d'autres bibliothèques et outils utilisés dans le développement Angular.

- Résumé et instructions :

  Une fois que tout est prêt, Angular CLI affiche un résumé des actions effectuées et fournit des instructions sur la façon de démarrer le serveur de développement.

Après avoir créé le projet, on peut se rendre dans le répertoire du projet en utilisant la commande `"cd nom-du-projet"` et lancer le serveur de développement avec la commande `"ng serve"`. Cela va compiler le projet et le rendre disponible à l'adresse http://localhost:4200/ par défaut.

## `@Component`

Permet de définir les métadonnées associées à un composant Angular, telles que le sélecteur, les fichiers HTML et CSS associés, et d'autres configurations spécifiques au composant. Ces informations aident Angular à comprendre comment créer, afficher et gérer le composant.

## `selector` :

`selector` est une propriété dans la configuration d'un composant Angular. Elle définit le sélecteur CSS qui identifie une instance du composant dans le HTML parent.

Par exemple:

```ts
selector: "app-root";
```

cela signifie qu'on peut utiliser `<app-root></app-root>` dans le HTML parent pour inclure ce composant.

Le sélecteur est un moyen de "sélectionner" une zone du DOM où le composant doit être rendu.

## `templateUrl` :

`templateUrl` est une propriété qui spécifie le chemin vers le fichier HTML qui contient le modèle du composant.

L'utilisation de `templateUrl` permet de séparer le HTML du composant du code TypeScript, ce qui peut rendre le code plus lisible et faciliter la maintenance.

Par exemple :

```ts
templateUrl: "./app.component.html";
```

indique qu'il faut utiliser le fichier app.component.html comme modèle pour ce composant.

## `styleUrls` :

`styleUrls` est une propriété qui spécifie un tableau de chemins vers des fichiers de style (CSS) pour le composant.

Comme pour `templateUrl`, l'utilisation de styleUrls permet de séparer le style du composant du reste du code.

Par exemple :

```ts
styleUrls: ["./app.component.css"];
```

signifie qu'il faut appliquer les styles définis dans le fichier app.component.css au composant.

## `*ngFor` :

C'est une directive structurelle utilisée pour l'itération sur les éléments d'une collection, comme un tableau ou une liste, afin de créer des éléments DOM répétitifs. Elle est souvent utilisée dans les balises HTML pour générer dynamiquement du contenu en fonction des données.

```html
<h2>Liste de noms :</h2>
<ul>
  <li *ngFor="let nom of noms">{{ nom }}</li>
</ul>
```

La syntaxe `{{}}` est utilisée pour incorporer des expressions Angular dans le HTML. Ici, `{{ nom }}` affiche la valeur actuelle de la variable nom à chaque itération de `*ngFor`.

Dans cet exemple, `{{ nom }}` est une expression Angular qui sera remplacée par la valeur actuelle de la variable nom dans le composant. Pour lier cette variable à une propriété d'un élément HTML, on utilisera `[ ]` comme suit :

```html
<input [value]="nom" />
```

Cela liera la valeur de la variable `nom` à la propriété `value` de la balise `<input>`. Ainsi, lorsque la variable nom change dans le composant, la valeur de l'entrée sera mise à jour en conséquence.

## `*ngIf`

`*ngIf` est une directive structurelle en Angular qui est utilisée pour conditionnellement inclure ou exclure des éléments du DOM (Document Object Model) en fonction d'une expression donnée. En d'autres termes, elle permet de rendre un élément HTML présent ou non dans le rendu final de la page en fonction d'une condition.

Voici un exemple simple :

```html
<div *ngIf="isUserLoggedIn; else notLoggedIn">Bienvenue, Utilisateur !</div>
<ng-template #notLoggedIn> Veuillez vous connecter. </ng-template>
```

Dans cet exemple, l'élément `<div>` avec la directive `*ngIf` est affiché uniquement si la variable `isUserLoggedIn` est évaluée à `true`. Sinon, le contenu de la balise `<ng-template>` avec la référence `#notLoggedIn` est affiché. Cela permet de gérer le cas où l'utilisateur n'est pas connecté.

L'utilisation de `*ngIf` est un bon moyen de rendre dynamiquement des parties de l'interface utilisateur en fonction de l'état de l'application.

## Creation de nouvent component :

```ts
ng generate component `name`
```

Cette commande effectuera plusieurs actions :

- Elle créera un dossier avec le nom du composant dans le répertoire où la commande est exécutée.

- À l'intérieur de ce dossier, elle générera les fichiers nécessaires pour le composant, y compris le fichier TypeScript du composant, le fichier HTML associé, les fichiers CSS, etc.

- Elle mettra à jour automatiquement le module Angular (app.module.ts) pour déclarer le nouveau composant.

Cette approche de génération de composants avec Angular CLI est très pratique, car elle suit les conventions d'Angular et vous évite d'avoir à créer manuellement les fichiers et de les configurer.

## Annotation

- `(click)="share()"`: remplace le `onclick="share()"` du button en javascript

- `app-root` est un terme couramment utilisé pour désigner le composant racine. Lorsque un nouveau projet est crée à l'aide `ng new`, le composant racine par défaut est souvent nommé `AppComponent` et son sélecteur est généralement défini sur `app-root` dans le fichier `app.component.ts`.

# Partie 2 : Routing

//TODO

`path:` définir un itinéraire

[routerLink] La directive `RouterLink` vous aide à personnaliser l'élément d'ancrage. Dans ce cas, l'itinéraire, ou URL, contient un segment fixe, `/products`. Le segment final est variable, insérant la propriété `id` du produit actuel. Par exemple, l'URL d'un produit avec un `id1` serait similaire à https://getting-started-myfork.stackblitz.io/products/1.

`ActivatedRouteest` spécifique à chaque composant chargé par le routeur angulaire. `ActivatedRoutecontient` des informations sur l'itinéraire et les paramètres de l'itinéraire.

En injectant `ActivatedRoute`, vous configurez le composant pour utiliser un service. L’ étape Gestion des données couvre les services plus en détail.

`route.snapshot`

`ActivatedRouteSnapshotcontient` des informations sur l'itinéraire actif à ce moment précis. L'URL qui correspond à l'itinéraire fournit le fichier `productId`. Angular utilise le `productId` pour afficher les détails de chaque produit unique.

`<router-outlet></router-outlet>`

`**`

# Partie 3 : Data

//TODO

`ng generate service`

https://angular.io/guide/architecture-services

`HttpClient`

`HttpClientModule`

`async`

# Partie 4 : Formulaire

//TODO

`FormBuilder`

```ts
onSubmit(): void { this.items = this.cartService.clearCart(); console.warn("Your order has been submitted", this.checkoutForm.value); }
```

`[formGroup]`

`ngSubmit`

`formControlName`

`[(ngModel)]` est la syntaxe de liaison de données bidirectionnelle
