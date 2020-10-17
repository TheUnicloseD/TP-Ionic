# Ionic

1. Prérequis :
 
npm/NodeJS : https://nodejs.org/en/

2. Installer Ionic 

`npm install -g ionic`

3. Créer une 1ere application 

**Mettez vous dans le dossier ou vous voulez créer l'appli** 

`ionic start nomApp blank`

**Dans le choix de Framework, choisir "React"** 

![alt tag](https://user-images.githubusercontent.com/47526337/96346560-abe84280-109c-11eb-8148-407867a6d66a.PNG)

Pour certain, Ionic va vous demander si vous souhaitez créer un compte gratuit. Dans ce cas, répondez "Non"

4. Lancer l'application 

**Mettez vous dans le dossier que vous venez de créer** 

`ionic serve`

Pour certain, la page de l'appli s'ouvre automatiquement dans le navigateur. Si ce n'est pas le cas vous pouvez l'ouvrir via http:://localhost:8100

*Astuce : Activez le mode "téléphone" dans votre navigateur pour mieux visualiser l'application*

**Vous pouvez maintenant ouvrir votre environnement de développement et regarder la structure de votre application.** 

Tout ce qui nous intéresse se situe dans le dossier "src"

Dans le sous-dossier "pages" se trouvent les pages ou onglets de votre application. Nous allons commencer par créer une nouvelle page pour notre application. 

5. Créer une nouvelle page. 

Sous Angular, Ionic propose des commandes qui crée automatiquement ce dont on a besoin. 

Malheuresement, ce n'est pas encore le cas sous React

Nous devons donc créer une nouvelle page à la main dans le dossier "pages". 

-Créer la page "Profil.tsx"

Vous pouvez copier le contenu de Home.tsx dans Profil.tsx pour allez plus vite. (Dans ce cas, n'oubliez pas de changer le nom de la constante et de l'export de cette nouvelle page).

6. Créer les onglets 

La page que vous venez de créer va servir de 2ème onglet à l'application (le 1er étant la page "Home").

Pour relier les 2 pages, il va falloir dans un 1er temps créer 2 boutons qui permettront de switcher entre les 2 onglets (Home et Profil). 

Pour cela, nous allons utiliser les components `IonTabs` (https://ionicframework.com/docs/api/tabs)

Les boutons doivent être créée dans la page "App.tsx" pour qu'ils soient accessibles depuis toutes les pages de l'application.

Dans un premier temps, importer les components dont nous allons avoir besoin : `import { IonApp, IonRouterOutlet, IonTabs, IonTabBar, IonTabButton, IonIcon, IonLabel, IonBadge } from '@ionic/react';`

- Créer les 2 boutons "Home" et "Profil" grâce aux components importé ci-dessus. Ajouter un icone adapté au nom de chaque page

*Astuce <IonIcon icon={} /> permet d'utiliser tout les icones que propose Ionic. Ceux-ci sont accessibles à cette adresse : https://ionicframework.com/docs/v3/ionicons/*

**Pensez à importer les nouveaux icones que vous allez utiliser :** `import { nomIcon } from 'ionicons/icons';`

**Ne vous inquiétez si vous voyer cette erreur, cela est normal ! En effet, pour fonctionner, les boutons doivent être relié à leurs pages respectives pour fonctionner ! Vous pouvez donc passer à la question suivante !**

![alt tag](https://user-images.githubusercontent.com/47526337/96346921-b0adf600-109e-11eb-8cc4-b42f0e87b2c6.png)

7. Créer les routes 

Une fois les boutons créee, il va falloir les reliers à leurs onglets respectifs en utilisant des routes 
. 
Vous pouvez voir que la route pour la page "Home" est déjà créer. Pour la relier à son bouton que vous venez de créee, il suffit d'ajouter `href="/home"` dans la balise `<IonTabButton>`.

- Grace à cet exemple, créer la route du bouton Profil. 

*Astuce : les components `<IonTabs>` doivent être à l'intérieur de la balise `<IonReactRouter>` tandis que `<IonRouterOutlet>` et les routes doivent être à l'intérieur du component `<IonTabs>`.* 

Vous pouvez voir maintenant sur votre appli que lors de l'appui sur un des bouton, l'URL change et correspond bien à la page où vous avez cliquer. 

8. Remplir la page Profil

Importer les components dont vous allez avoir besoin : 
`import { IonContent, IonHeader, IonGrid, IonAlert, IonPage,IonButton, IonTitle, IonToolbar,IonIcon,IonRow,IonCol,IonItem,IonInput,IonLabel } from '@ionic/react';`
`import React, { useState } from 'react';`
`import { personCircle } from 'ionicons/icons';`

Copier ce code dans votre page Profil.tsx à la place du code existant :
`
<IonPage>
    <IonHeader>
      <IonToolbar>
      </IonToolbar>
    </IonHeader>
    <IonContent fullscreen>
    <IonGrid>
     <IonRow>
       <IonCol>
       </IonCol>
     </IonRow>
     <IonRow>
      <IonCol>
        <IonItem>
        </IonItem>
       </IonCol>
      </IonRow>
      <IonRow> 
       <IonCol>
        <IonItem>   
        </IonItem>
       </IonCol>
      </IonRow>
      <IonRow>
       <IonCol>
       </IonCol>
        </IonRow>
     </IonGrid>
    </IonContent>
    </IonPage>
    `
    
Les components <IonGrid>,<IonCol> et <IonRow> permettent de présenter la page comme-ci : 

![alt tag](https://user-images.githubusercontent.com/47526337/96347644-64b18000-10a3-11eb-905d-71bdb117a287.PNG)

Dans notre cas vous pouvez voir que nous avons 4 lignes qui ont chacune 1 colonne.

- Ajouter un titre "Login" à l'interieur de la toolbar  (https://ionicframework.com/docs/api/title)
- Ajouter un icone "personCircle" dans la première ligne d'une taille "large".
- Ajouter un input de type "Email" dans la deuxième ligne. (https://ionicframework.com/docs/api/input)
- Ajouter un input de type "Password" dans la troisième ligne.
- Créez un bouton cliquable "LOGIN" dans la quatrième ligne (https://ionicframework.com/docs/api/button)

Voila à quoi devrait ressembler votre page : 

![alt tag](https://user-images.githubusercontent.com/47526337/96347645-654a1680-10a3-11eb-8873-b5fdb11924aa.png)
 
9. Créer un menu 

Nous allons maintenant créer un components "menu" à notre application. Pour cela, créer une nouvelle page "Menu.tsx" dans le dossier components. 
Voici le code à mettre dans la page : 

`
import React from 'react';
import { IonMenu, IonHeader, IonToolbar, IonTitle, IonContent, IonList, IonItem, IonRouterOutlet } from '@ionic/react';

export const Menu: React.FC = () => (
  <>
    <IonMenu side="start" menuId="first" contentId="content1">
      <IonHeader>
        <IonToolbar color="primary">
          <IonTitle>Start Menu</IonTitle>
        </IonToolbar>
      </IonHeader>
      <IonContent>
        <IonList>
          <IonItem>Profil</IonItem>
          <IonItem>Page 3 </IonItem>
          <IonItem>Page 4</IonItem>
          <IonItem>Page 5</IonItem>
          <IonItem>Page 6</IonItem>
        </IonList>
      </IonContent>
    </IonMenu>
    <IonRouterOutlet id="content1"></IonRouterOutlet>
 </>
);

export default Menu;
`

On s'intéresse ici au fait que Ionic permette d'inclure des components dans une page. Dans notre cas, nous allons accéder à ce menu depuis la page "Home"

Importer le component qu'on vient de créer dans "Home.tsx": `import Menu from '../components/Menu';`
Importer les components dont nous allons avoir besoin : `import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar,IonMenuButton,IonButtons,IonRouterOutlet } from '@ionic/react';`

- Ajouter le bouton du menu que l'on vient de créer dans la toolbar de la page Home.

Pour cela, Ionic propose la balise <IonMenuButton> (https://ionicframework.com/docs/api/buttons)

*Astuce : Regardez comment l'autre component "ExploreContainer" est intégrée.*

- Utiliser les ions Item pour créer un chemin entre le menu et la page Profil (https://ionicframework.com/docs/api/item)
*Astuce : Cela marche à l'aide des routes que l'on a crée plûs tot dans le TP. 

Si cela marche, vous devriez avoir accès à la page "Profil" en cliquant sur le bouton Profil de votre menu que vous venez d'integrer à votre page Home.


**Merci à vous pour votre Participation !**



