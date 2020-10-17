# Ionic

1. Prérequis :
 
npm/NodeJS : https://nodejs.org/en/

2. Installer Ionic 

`npm install -g ionic`

3. Créer une 1ere application 

- Mettez vous dans le dossier ou vous voulez créer l'appli 

`ionic start "nomApp" blank`

- Dans le choix de Framework, choisir "React" 

![](C:\Users\romai\Documents\Cours\IHM\Capture.PNG)

Ionic va vous demander si vous souhaitez créer un compte gratuit, répondez "Non"

4. Lancer l'application 

- **Mettez vous dans le dossier que vous venez de créer** 

`ionic serve`

Pour certain, la page de l'appli s'ouvre automatiquement dans le navigateur. Si ce n'est pas le cas vous pouvez l'ouvrir via http:://localhost:8100

*Astuce : Activez le mode "téléphone" pour mieux visualiser l'application*

Vous pouvez maintenant ouvrir votre environnement de développement et regarder la structure de votre application. 

Tout ce qui nous intéresse se situe dans le dosseir "src"

Dans le sous-dossier "pages" de se trouvent les pages ou onglets de votre application. Nous allons commencer par créer une nouvelle page pour notre application. 

5. Créer 1 nouvelle page 

Sous Angular, Ionic propose des commandes qui crée automatiquement ceux dont on a besoin. 

Malheuresement, ce n'est pas encore le cas sous React

Nous devons donc créer une nouvelle page à la main dans le dossier pages. 

-Créer la page "Profil.tsx"

Vous pouvez copier le contenu de Home.tsx dans Profil.tsx pour allez plus vite. (Dans ce cas, n'oubliez pas de changer le nom de la constante de cette nouvelle page) 

6. Créer les onglets 

La page que vous venez de créer va servir de 2ème onglet à l'application (le 1er étant la page principale). 
Pour relier les pages, il va falloir dans un 1er temps créer 2 boutons qui permettront de switcher entre les 2 onglets (Home et Profil). 
Pour cela, utiliser les components `IonTabs` (https://ionicframework.com/docs/api/tabs)

Les boutons doivent être créée dans la page "App.tsx" pour qu'il soit accessible depuis toutes les pages de l'application. 

*Astuce <IonIcon icon={} /> permet d'avoir accès à tout les icones que propose Ionic. Ceux-ci sont accessibles à cette adresse : https://ionicframework.com/docs/v3/ionicons/*

Pensez à importer les nouveaux components que vous allez utiliser. 
Pour importer les icones : `import { "nomIcon" } from 'ionicons/icons';`

C'est normal si votre appli ne marche pas, il faut d'abord créer les routes des onglets que vous venez créer.

7. Créer les routes 

Une fois les boutons des onglets créée, il va falloir crée les routes pour les relier à leurs onglets. 
Vous pouvez voir que la route pour la page "Home" est déjà créer. Pour la relier au bouton, il suffit d'ajouter `href="/home"` dans la balise `<IonTabButton>`. 
- Grace à cet exemple, créer la route de Profil

Astuce : les components doivent être à l'intérieur de la balise `<IonReactRouter>` tandis que <IonRouterOutlet> et les routes doivent être à l'intérieur du component <IonTab>. 

Vous pouvez voir maintenant sur votre appli que lors de l'appui sur un bouton, l'URL change et correspond bien à la page où vous avez cliquer. 

7. Remplir la page Profil 

`
<IonPage>
    <IonHeader>
      <IonToolbar>
        
      </IonToolbar>
    </IonHeader>
    <IonContent fullscreen className="ion-padding ion-text-center">
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
    
Le <IonHeader> comporte le header de la page tandis que le <IonContent> comporte le corps de la page. 

- Ajouter un titre "Login" à la page de couleur "danger" (https://ionicframework.com/docs/api/title)
- Ajouter un icone "personCircle" sur la page avec un fontSize de 60px.
- Ajouter un input de type "Email" (https://ionicframework.com/docs/api/input)
- Ajouter un input de type "Password"
- Créez un bouton cliquable "LOGIN" (https://ionicframework.com/docs/api/button)

Voila à quoi devrait ressembler votre page : (Insérer photo de la page les amis)
 
8. Créer un menu 

Nous allons maintenant créer un menu à notre application. Pour cela, créer une nouvelle page "Menu.tsx" dans le dossier components. 
Voice le code à mettre dans la page : 

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

On s'intéresse ici au fait que Ionic permettent d'inclure ces components dans nos pages. Dans notre cas, nous allons accéder à ce menu depuis la page "Home"

Importer le component qu'on vient de créer: `import Menu from '../components/Menu';`

- Ajouter le menu que l'on vient de créer dans la toolbar de la page Home 

Astuce : Regarder comment l'autre component ExploreContainer est intégrée. 
Astuce2 : https://ionicframework.com/docs/api/menu-button
Pour cela, Ionic propose la balise <IonMenuButton>

- Utiliser les ions Item pour créer un chemin entre le menu et la page Profil (https://ionicframework.com/docs/api/item)



