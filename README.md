# Partie 1 : Initiation

> **Note :** il faut avoir Node.js et npm installés sur la machine.

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

## @Component

Permet de définir les métadonnées associées à un composant Angular, telles que le sélecteur, les fichiers HTML et CSS associés, et d'autres configurations spécifiques au composant. Ces informations aident Angular à comprendre comment créer, afficher et gérer le composant.

## selector :

`selector` est une propriété dans la configuration d'un composant Angular. Elle définit le sélecteur CSS qui identifie une instance du composant dans le HTML parent.

Par exemple:

```ts
selector: "app-root";
```

cela signifie qu'on peut utiliser `<app-root></app-root>` dans le HTML parent pour inclure ce composant.

Le sélecteur est un moyen de "sélectionner" une zone du DOM où le composant doit être rendu.

## templateUrl :

`templateUrl` est une propriété qui spécifie le chemin vers le fichier HTML qui contient le modèle du composant.

L'utilisation de `templateUrl` permet de séparer le HTML du composant du code TypeScript, ce qui peut rendre le code plus lisible et faciliter la maintenance.

Par exemple :

```ts
templateUrl: "./app.component.html";
```

indique qu'il faut utiliser le fichier app.component.html comme modèle pour ce composant.

## styleUrls :

`styleUrls` est une propriété qui spécifie un tableau de chemins vers des fichiers de style (CSS) pour le composant.

Comme pour `templateUrl`, l'utilisation de styleUrls permet de séparer le style du composant du reste du code.

Par exemple :

```ts
styleUrls: ["./app.component.css"];
```

signifie qu'il faut appliquer les styles définis dans le fichier app.component.css au composant.

## \*ngFor :

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

## \*ngIf

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

## @NgModule

Le décorateur `@NgModule` est utilisé pour définir et configurer les modules. Les modules sont des conteneurs logiques qui regroupent des composants, des directives, des pipes et des services associés.

```ts
import { NgModule } from "@angular/core";
import { BrowserModule } from "@angular/platform-browser";
import { AppComponent } from "./app.component";
import { HomeComponent } from "./home/home.component";
import { AboutComponent } from "./about/about.component";
import { AppRoutingModule } from "./app-routing.module";

@NgModule({
  declarations: [
    // Liste des composants, directives et pipes déclarés dans ce module
    AppComponent,
    HomeComponent,
    AboutComponent,
  ],
  imports: [
    // Liste des modules dont ce module dépend
    BrowserModule,
    AppRoutingModule,
  ],
  providers: [
    /* Liste des services disponibles au sein de ce module */
  ],
  bootstrap: [AppComponent], // Composant racine à utiliser lors du démarrage de l'application
})
export class AppModule {}
```

- declarations: Cette propriété est utilisée pour déclarer les composants, directives et pipes qui font partie de ce module. Ces éléments seront disponibles pour être utilisés dans les templates de ce module.

- imports: Cette propriété spécifie la liste des modules dont ce module dépend. Par exemple, le module BrowserModule est nécessaire pour les fonctionnalités de base dans les applications web Angular.

- providers: Cette propriété est utilisée pour spécifier les services qui doivent être disponibles dans ce module. Les services fournissent généralement des fonctionnalités partagées entre différents composants.

- bootstrap: Cette propriété spécifie le composant racine de l'application. C'est le composant qui sera automatiquement instancié et rendu lorsque l'application démarre.

Il est important de noter qu'il y a deux types de modules en Angular : le module de la racine de l'application (généralement nommé AppModule) et les modules de fonctionnalités. Chaque module de fonctionnalités peut avoir son propre décorateur @NgModule avec des propriétés similaires pour définir ses composants, directives, pipes, etc.

## Annotation

- `(click)="share()"`: remplace le `onclick="share()"` du button en javascript

- `app-root` est un terme couramment utilisé pour désigner le composant racine. Lorsque un nouveau projet est crée à l'aide `ng new`, le composant racine par défaut est souvent nommé `AppComponent` et son sélecteur est généralement défini sur `app-root` dans le fichier `app.component.ts`.

# Partie 2 : Routing

Le routage est une fonctionnalité essentielle dans les applications web pour la navigation entre différentes vues ou pages. Dans le contexte d'Angular, le routage est géré par le module de routage intégré.

## Définir un itinéraire

Lors de la configuration du routage dans Angular, "path" fait référence à la partie de l'URL qui est associée à une vue ou un composant particulier. Voici un exemple simple :

```typescript
const routes: Routes = [
  { path: "", component: HomeComponent }, // Le chemin vide correspond à la page d'accueil
  { path: "about", component: AboutComponent }, // Le chemin '/about' correspond à la page "À propos"
  { path: "contact", component: ContactComponent }, // Le chemin '/contact' correspond à la page "Contact"
];
```

Dans cet exemple, chaque objet dans le tableau routes associe un `"path"` à un composant spécifique. Par exemple, lorsque l'URL de l'application est "http://nom-du-projet.com/about", Angular affichera le composant AboutComponent parce que le `"path"` correspondant est `'about'`.

`"path"` peut également inclure des paramètres dynamiques. Par exemple :

```typescript
{ path: 'products/:id', component: ProductDetailComponent }
```

Dans ce cas , `'products/:id'` indique qu'il y aura un paramètre id dans l'URL, et Angular peut extraire la valeur de cet identifiant pour afficher les détails du produit correspondant.

En résumé, `"path"` est utilisé dans la configuration du routage pour associer des URL spécifiques à des composants particuliers de l'application.

## [routerLink]

La directive `[routerLink]` est utilisée dans les templates Angular pour créer des liens de navigation entre différentes vues ou composants dans une application. Elle permet de définir la destination vers laquelle le lien doit rediriger lorsqu'il est cliqué.

- Navigation vers une Route sans Paramètres :

  ```html
  <a [routerLink]="'/home'">Accueil</a> <a [routerLink]="'/about'">À propos</a>
  ```

  Ces liens redirigeront vers les routes correspondantes ('/home' et '/about') lorsque l'utilisateur les cliquera.

- Navigation vers une Route avec Paramètres :

  ```html
  <a [routerLink]="'/product/' + productId">Détails du Produit</a>
  ```

  Ici, productId est une variable du composant qui contient l'identifiant du produit. Lorsque l'utilisateur clique sur le lien, la route /product/:id sera activée, où :id est remplacé par la valeur de productId.

En résumé, [routerLink] est une directive Angular qui simplifie la création de liens de navigation des templates en utilisant le système de routage d'Angular. Cela permet de définir dynamiquement les destinations des liens en fonction de la logique de l'application.

## ActivatedRoute

L'objet `ActivatedRoute` est utilisé pour accéder aux informations de la route active dans votre composant. Il fournit des informations sur la route telle que les paramètres de route, les segments de chemin, les données de route, etc.

```typescript
import { Component } from "@angular/core";
import { ActivatedRoute } from "@angular/router";

@Component({
  selector: "app-product-detail",
  template: `
    <h2>Détails du Produit</h2>
    <p>Identifiant du produit : {{ productId }}</p>
  `,
})
export class ProductDetailComponent {
  productId: string;

  constructor(private route: ActivatedRoute) {
    // Utilisation de ActivatedRoute de manière déclarative
    this.productId = this.route.snapshot.paramMap.get("id");
  }
}
```

Dans cet exemple, le constructeur du composant utilise `ActivatedRoute` pour accéder à la `snapshot` de la route active. La propriété paramMap de la `snapshot` est utilisée pour extraire la valeur de l'identifiant du produit à partir des paramètres de la route.

## route.snapshot

Dans le contexte d'Angular, une snapshot (ou instantané) fait référence à un état figé d'un objet à un moment donné. Pour l'objet ActivatedRoute, la snapshot représente l'état de la route au moment où le composant associé est créé.

L'objet ActivatedRouteSnapshot est une propriété de l'objet ActivatedRoute qui contient une représentation immuable de l'état de la route au moment où le composant est instancié. Voici comment vous pouvez l'utiliser :

```typescript

  constructor(private route: ActivatedRoute) {
    // Accéder à la snapshot de la route
    const snapshot = route.snapshot;

    // Utilisation de la snapshot pour obtenir les paramètres de la route
    this.productId = snapshot.paramMap.get("id");
  }

```

`Route.snapshot` donne accès à la `snapshot` de la route.
utile pour extraire des informations telles que les paramètres de la route (paramMap), les segments de chemin (url), les données associées à la route (data), etc.

La `snapshot` est une représentation figée de l'état de la route au moment de la création du composant. Si la route change après la création du composant, vous devrez utiliser des observables, comme ceux fournis par `ActivatedRoute.paramMap.subscribe()`, pour suivre les changements de la route de manière réactive.

En résumé, la `snapshot` de la route (ActivatedRouteSnapshot) permet d'obtenir des informations immuables sur l'état de la route au moment où le composant est créé.

## router-outlet

Chaque route est associée à un composant particulier. Lorsque l'utilisateur navigue vers une route spécifique, le composant associé à cette route est chargé et son contenu est rendu à l'intérieur du `<router-outlet>`.

Lorsque l'utilisateur navigue vers une route, le composant associé est chargé et son contenu est rendu dynamiquement à l'intérieur de `<router-outlet>`

## Wildcard

L'utilisation de `**` dans la configuration de routes est associée au "wildcard" (joker) et est souvent utilisée pour capturer toutes les routes qui ne correspondent pas aux routes spécifiques définies auparavant. Cela est particulièrement utile lorsque l'on souhaite gérer les routes inexistantes.

```typescript
const routes: Routes = [
  { path: "home", component: HomeComponent },
  { path: "about", component: AboutComponent },
  { path: "products/:id", component: ProductDetailComponent },
  { path: "**", component: PageNotFoundComponent }, // Capture toutes les routes non définies ci-dessus
];
```

Les routes spécifiques sont définies en premier, telles que `'home'`, `'about'`, et `'products/:id'`. Ensuite, la route `'**'` avec le composant PageNotFoundComponent est définie en dernier. Cette route avec `**` est un "catch-all" qui sera activée pour toutes les routes qui n'ont pas trouvé de correspondance dans les routes précédentes.

Si l'utilisateur navigue vers une URL qui n'est pas définie, comme `'/unknown-route'`, la route avec `**` sera activée, et le composant `PageNotFoundComponent` sera affiché.

C'est un moyen puissant de gérer les routes inconnues ou non définies. On peut personnaliser `PageNotFoundComponent` pour afficher un message d'erreur ou rediriger l'utilisateur vers une page d'erreur spécifique.

# Partie 3 : Data

## Service

Un service est une classe qui fournit des fonctionnalités partagées ou des logiques de données à travers différents composants l'application.

```bash
ng generate service nom-du-service
```

Cette commande va créer un nouveau dossier appelé nom-du-service dans le répertoire de l'application et y placer les fichiers nécessaires pour le service. Par défaut, cela inclut :

- Un fichier TypeScript (par exemple, data.service.ts).
- Un fichier de test (par exemple, data.service.spec.ts).

Voici à quoi ressemblerait le fichier TypeScript généré pour le service :

```typescript
import { Injectable } from "@angular/core";

@Injectable({
  providedIn: "root",
})
export class DataService {
  constructor() {}
}
```

La directive `@Injectable({ providedIn: 'root' })` signifie que le service sera injecté au niveau de l'application (root) et sera accessible dans toute l'application. Vous pouvez également fournir un autre module en spécifiant le nom du module à la place de `'root'` si vous souhaitez restreindre la portée du service à un module spécifique.

Après avoir généré le service, on peut l'injecter dans les composants ou autres services en ajoutant le service dans le constructeur :

```typescript
import { Component } from "@angular/core";
import { DataService } from "./path-vers-le-service/data.service";

@Component({
  selector: "app-mon-composant",
  template: ` <div>{{ dataService.getData() }}</div> `,
})
export class MonComposantComponent {
  constructor(private dataService: DataService) {}
}
```

Dans cet exemple, dataService est une instance de DataService injectée dans le composant MonComposantComponent.

En résumé, la commande `ng generate service` simplifie la création de services dans Angular en générant automatiquement les fichiers nécessaires et en configurant le service de manière à ce qu'il soit injecté correctement dans l'application.

## HttpClient

HttpClient est une classe fournie par Angular qui simplifie la gestion des requêtes HTTP dans une application Angular.
Elle est utilisée pour effectuer des requêtes HTTP telles que `GET`, `POST`, `PUT`, `DELETE`, etc., vers un serveur distant.
Elle retourne des objets Observable pour gérer les réponses asynchrones.
La classe HttpClient est généralement injectée dans les services Angular qui sont responsables de l'interaction avec les API distantes.
Exemple d'utilisation dans un service Angular :

```typescript
import { HttpClient } from "@angular/common/http";
import { Observable } from "rxjs";

export class MyService {
  constructor(private http: HttpClient) {}

  getData(): Observable<any> {
    return this.http.get("https://api.example.com/data");
  }
}
```

## HttpClientModule

HttpClientModule est un module Angular qui doit être importé dans le module principal de l'application pour pouvoir utiliser HttpClient.
Il fournit le service HttpClient que les composants et les services de l'application peuvent injecter et utiliser.
Il configure également certains aspects du comportement d'HttpClient, tels que les intercepteurs, qui permettent de traiter les requêtes et les réponses HTTP avant qu'elles n'atteignent le code qui les a initiées.
Exemple d'importation dans le module principal (app.module.ts) :

```typescript
import { BrowserModule } from "@angular/platform-browser";
import { NgModule } from "@angular/core";
import { HttpClientModule } from "@angular/common/http";
import { AppComponent } from "./app.component";

@NgModule({
  declarations: [AppComponent],
  imports: [
    BrowserModule,
    HttpClientModule, // Import du HttpClientModule ici
  ],
  bootstrap: [AppComponent],
})
export class AppModule {}
```

En résumé, `HttpClient` est la classe principale pour effectuer des requêtes HTTP, tandis que `HttpClientModule` est le module qui fournit cette classe et doit être importé pour pouvoir l'utiliser dans une application Angular.

## Les observables

Les observables sont un concept clé dans la programmation réactive et sont largement utilisés dans Angular pour gérer les flux de données asynchrones. Voici quelques points importants à connaître sur les observables en Angular :

- Asynchronicité :

  Les observables sont utilisés pour traiter des opérations asynchrones, telles que les requêtes HTTP, les événements de l'interface utilisateur, les timers, etc.
  Ils permettent de traiter des données au fil du temps plutôt que de manière synchrone.

- RxJS :

  Angular utilise la bibliothèque RxJS (Reactive Extensions for JavaScript) pour implémenter le concept des observables.
  RxJS fournit une API riche pour la manipulation des observables, y compris des opérateurs pour filtrer, mapper, combiner et traiter les données émises par les observables.

- Émission de valeurs :

  Un observable émet des valeurs au fil du temps.
  Ces valeurs peuvent être émises une fois, plusieurs fois, ou même en continu.

- Abonnement :

  Pour réagir aux valeurs émises par un observable, on doit s'abonner à cet observable.
  Un abonnement consiste à fournir une fonction de rappel (callback) qui sera exécutée chaque fois que l'observable émet une nouvelle valeur.

  - Exemple d'abonnement à un observable :

    ```typescript
    import { Observable } from "rxjs";

    const observable = new Observable<number>(observer => {
      observer.next(1);
      observer.next(2);
      observer.complete();
    });

    const subscription = observable.subscribe(
      value => console.log(value), // Callback pour les valeurs émises
      error => console.error(error), // Callback en cas d'erreur
      () => console.log("Observable completed") // Callback lorsque l'observable est complet
    );

    // Output : 1, 2, Observable completed
    ```

- Gestion des erreurs :

  Les observables peuvent émettre des erreurs, et on peut les gérer en fournissant une fonction de gestion des erreurs lors de l'abonnement.
  Exemple avec gestion d'erreur :

  ```typescript
  const observable = new Observable<number>(observer => {
    observer.next(1);
    observer.error("Something went wrong");
  });

  const subscription = observable.subscribe(
    value => console.log(value),
    error => console.error("Error:", error) // Gestion de l'erreur
  );

  // Output : 1, Error: Something went wrong
  ```

- Libération des ressources :

  Les observables peuvent être utilisés pour gérer la libération des ressources, par exemple, en se désabonnant lorsqu'un composant Angular est détruit.

  - Exemple de désabonnement :

    ```typescript
    import { Component, OnDestroy } from "@angular/core";
    import { Observable, Subscription } from "rxjs";

    @Component({
      selector: "app-my-component",
      template: "My Component",
    })
    export class MyComponent implements OnDestroy {
      private subscription: Subscription;

      constructor() {
        const observable = new Observable<number>(observer => {
          this.subscription = observer.subscribe(value => console.log(value));
        });
      }

      ngOnDestroy() {
        // Se désabonner pour éviter les fuites de mémoire
        this.subscription.unsubscribe();
      }
    }
    ```

Les observables offrent une manière puissante de gérer les flux de données asynchrones dans Angular, et la compréhension de leur utilisation est essentielle pour le développement d'applications Angular réactives.

## Asynchrone

En Angular, le mot-clé `async` est couramment utilisé en conjonction avec les observables. Les observables sont souvent utilisés pour gérer des opérations asynchrones, telles que les appels `HTTP` ou d'autres opérations qui peuvent prendre du temps.

Voici comment async est généralement utilisé dans le cadre d'Angular :

- Dans les templates :

  On peut utiliser `async` dans les templates Angular pour traiter des valeurs émises par des observables de manière asynchrone. Par exemple, si on a un observable dans un composant, on peut utiliser l'opérateur `async` dans le template pour gérer la mise à jour automatique de la vue lorsque la valeur de l'observable change :

  ```html
  <div>{{ observableData$ | async }}</div>
  ```

  Dans cet exemple, `observableData$` est un observable, et l'opérateur `async` s'assure que la vue est mise à jour automatiquement chaque fois que de nouvelles données sont émises par l'observable.

- Dans les fonctions asynchrones :

  On peut également utiliser `async` dans les fonctions TypeScript. Par exemple, dans une fonction Angular qui effectue une opération asynchrone, on peut utiliser le mot-clé `async` pour indiquer que la fonction contient des opérations asynchrones et peut renvoyer une promesse :

  ```typescript

  async fetchData(): Promise<void> {
    // Opération asynchrone, par exemple un appel HTTP
    const data = await this.http.get('api/data').toPromise();

    // Suite du traitement après que l'opération asynchrone est terminée
  }
  ```

  L'utilisation de `async` dans ce contexte permet d'utiliser l'opérateur `await` pour attendre que des opérations asynchrones, comme les appels `HTTP`, se terminent.

# Partie 4 : Formulaire

//TODO

## FormBuilder

FormBuilder est une classe fournie par Angular qui fait partie du module @angular/forms. Elle offre des méthodes de commodité pour la création de groupes de contrôles et de contrôles individuels lors de la construction de formulaires réactifs.

L'utilisation de `FormBuilder` simplifie la création de formulaires réactifs en fournissant des fonctions utilitaires pour créer des instances de FormGroup, FormControl, et d'autres éléments du système de formulaires réactifs.

Voici comment on peut utiliser `FormBuilder` pour créer un formulaire réactif :

Importation dans le module @angular/forms :

```typescript
import { FormBuilder, FormGroup, Validators } from "@angular/forms";
```

FormBuilder dans le constructeur du composant :

```typescript
constructor(private fb: FormBuilder) { }
```

FormBuilder pour créer un FormGroup et des FormControl :

```typescript
// Créez un FormGroup avec des FormControl
myForm: FormGroup = this.fb.group({
  name: ["", Validators.required],
  email: ["", [Validators.required, Validators.email]],
  // ... autres contrôles
});
```

`name` et `email` sont des champs du formulaire, et nous avons appliqué des validateurs (comme Validators.required et Validators.email) pour définir les règles de validation.

Le formulaire dans le modèle HTML :

```html
<form
  [formGroup]="myForm"
  (ngSubmit)="onSubmit()">
  <label for="name">Name:</label>
  <input
    type="text"
    id="name"
    formControlName="name" />

  <label for="email">Email:</label>
  <input
    type="email"
    id="email"
    formControlName="email" />

  <!-- ... autres champs de formulaire -->

  <button
    type="submit"
    [disabled]="myForm.invalid">
    Submit
  </button>
</form>
```

L'utilisation de FormBuilder simplifie la syntaxe pour la création de formulaires réactifs, rend le code plus lisible et aide à éviter des erreurs courantes. Elle est particulièrement utile pour les formulaires complexes où plusieurs champs nécessitent des configurations spécifiques.

En Angular, FormGroup et FormControl sont des classes clés du système de formulaires réactifs. Elles sont utilisées pour construire et gérer des formulaires complexes de manière réactive.

- FormGroup

  FormGroup est une classe qui représente un groupe de contrôles dans un formulaire réactif. Un groupe de contrôles est généralement associé à une section spécifique d'un formulaire. Il peut contenir plusieurs instances de FormControl et/ou d'autres groupes de contrôles (FormGroup imbriqués).

  ```typescript
  import { FormBuilder, FormGroup, Validators } from "@angular/forms";

  const formBuilder = new FormBuilder();

  const myForm: FormGroup = formBuilder.group({
    name: ["", Validators.required],
    email: ["", [Validators.required, Validators.email]],
    address: formBuilder.group({
      street: [""],
      city: [""],
      zip: [""],
    }),
  });
  ```

  Dans cet exemple, myForm est une instance de FormGroup contenant trois FormControl (pour name, email, et address) et un FormGroup imbriqué pour l'adresse.

- FormControl

  FormControl est une classe qui représente un contrôle individuel dans un formulaire réactif. Il est responsable de la gestion de la valeur du champ de formulaire, des validations, des états tels que la validité et la saleté, ainsi que des événements liés aux changements de valeur.

  ```typescript
  import { FormControl, Validators } from "@angular/forms";

  const nameControl = new FormControl("", Validators.required);
  const emailControl = new FormControl("", [
    Validators.required,
    Validators.email,
  ]);
  const streetControl = new FormControl("");

  // Utilisation de ces contrôles dans un FormGroup
  const myForm: FormGroup = new FormGroup({
    name: nameControl,
    email: emailControl,
    address: new FormGroup({
      street: streetControl,
      city: new FormControl(""),
      zip: new FormControl(""),
    }),
  });
  ```

  Dans cet exemple, nameControl, emailControl, et streetControl sont des instances de FormControl utilisées dans un FormGroup. Chaque FormControl peut être associé à des validateurs spécifiques, comme Validators.required pour indiquer que le champ ne peut pas être vide.

En résumé, FormGroup représente un groupe de contrôles dans un formulaire, tandis que FormControl représente un contrôle individuel. Ensemble, ils forment la structure de base des formulaires réactifs en Angular.

## onSubmit

`onSubmit` est généralement une méthode définie dans un composant Angular qui est appelée lorsque le formulaire est soumis. Cette méthode contient la logique à exécuter lorsque l'utilisateur clique sur le bouton de soumission du formulaire. Voici un exemple typique de l'utilisation de onSubmit dans un composant Angular avec un formulaire réactif :

```typescript
import { Component } from "@angular/core";
import { FormBuilder, FormGroup, Validators } from "@angular/forms";

@Component({
  selector: "app-my-form",
  template: `
    <form
      [formGroup]="myForm"
      (ngSubmit)="onSubmit()">
      <!-- ... Définition des champs de formulaire ... -->
      <button
        type="submit"
        [disabled]="myForm.invalid">
        Submit
      </button>
    </form>
  `,
})
export class MyFormComponent {
  myForm: FormGroup;

  constructor(private fb: FormBuilder) {
    this.myForm = this.fb.group({
      name: ["", Validators.required],
      email: ["", [Validators.required, Validators.email]],
      // ... autres contrôles
    });
  }

  onSubmit() {
    if (this.myForm.valid) {
      // La logique à exécuter lorsque le formulaire est soumis et est valide
      console.log("Form submitted with values:", this.myForm.value);
    } else {
      // La logique à exécuter si le formulaire n'est pas valide
      console.log("Form is invalid. Please check your inputs.");
    }
  }
}
```

`onSubmit` est déclenché lorsque l'utilisateur clique sur le bouton de soumission du formulaire ((ngSubmit)="onSubmit()").
À l'intérieur de `onSubmit`, on vérifie d'abord si le formulaire est valide en utilisant `this.myForm.valid`.

- Si le formulaire est valide, la logique à exécuter lorsque le formulaire est soumis avec succès est placée à l'intérieur du bloc if.
- Sinon, si le formulaire n'est pas valide, la logique correspondante est placée à l'intérieur du bloc else.

C'est une pratique courante pour gérer la soumission de formulaires dans les applications Angular, que ce soit avec des formulaires réactifs ou des formulaires basés sur le modèle.

- La directive `ngSubmit` est utilisée dans Angular pour écouter l'événement de soumission d'un formulaire. Elle est généralement utilisée dans le contexte de formulaires réactifs ou de formulaires basés sur le modèle.

## Liaison de données bidirectionnelle

La directive `[(ngModel)]` est utilisée dans Angular pour établir une liaison bidirectionnelle entre les propriétés d'un élément du formulaire dans le modèle du composant et la valeur de cet élément dans le modèle du formulaire (la vue). Cela permet une synchronisation automatique des données entre la vue et le modèle du composant.

La plupart du temps, `[(ngModel)]` est utilisé dans le contexte de formulaires basés sur le modèle, une des deux approches de gestion des formulaires en Angular.

Voici comment `[(ngModel)]` est généralement utilisé dans un formulaire :

```html
<form>
  <label for="name">Name:</label>
  <input
    type="text"
    id="name"
    name="name"
    [(ngModel)]="user.name" />

  <label for="email">Email:</label>
  <input
    type="email"
    id="email"
    name="email"
    [(ngModel)]="user.email" />

  <!-- ... autres champs de formulaire ... -->

  <button
    type="submit"
    (click)="onSubmit()">
    Submit
  </button>
</form>
```

- `[(ngModel)]="user.name"` : Cette liaison bidirectionnelle signifie que la propriété name du modèle du composant (généralement définie dans la classe TypeScript associée) est liée à la valeur de l'élément d'entrée avec l'ID name dans la vue.
- `[(ngModel)]="user.email"` : De manière similaire, la propriété email du modèle du composant est liée à la valeur de l'élément d'entrée avec l'ID email.

  <sub>Dans le composant associé :<sub>

  ```typescript
  export class MyFormComponent {
    user = {
      name: "",
      email: "",
    };

    onSubmit() {
      // La logique à exécuter lorsque le formulaire est soumis
      console.log("Form submitted with values:", this.user);
    }
  }
  ```

Dans ce composant, `[(ngModel)]` permet une liaison bidirectionnelle entre les propriétés user.name et user.email du modèle du composant et les champs de formulaire correspondants dans la vue. Lorsque l'utilisateur modifie la valeur dans les champs de formulaire, les propriétés du modèle du composant sont automatiquement mises à jour, et vice versa.
