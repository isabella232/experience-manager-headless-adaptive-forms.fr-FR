---
title: Créer des formulaire attrayants à l’aide des composants principaux et découplés
seo-title: Build Engaging Forms Using Core Components and Headless
description: Créer des formulaire attrayants à l’aide des composants principaux et découplés
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
exl-id: ef99ffe9-4a37-4f0a-a4d3-78976c92220f
source-git-commit: 428416d61f236396449d26df208bf284a1ad162f
workflow-type: tm+mt
source-wordcount: '2452'
ht-degree: 96%

---

# Créez des formulaires attrayants à l’aide de composants de base et de formulaires adaptatifs découplés sur AEM Forms as a Cloud Service {#build-engaging-forms-using-core-components-and-headless}

## Présentation de l’atelier {#lab-overview}

Dans cet atelier pratique, vous allez apprendre :

Comment utiliser AEM Forms pour créer facilement des formulaires adaptatifs à l’aide des derniers composants principaux conformes à AEM Sites, activer les expériences de capture de données omnicanal en fournissant les formulaires adaptatifs sous forme de formulaires découplés sur le web, les appareils mobiles et les chats. Vous allez également découvrir les bonnes pratiques en matière de style, de personnalisation et de développement front-end.

## Principaux points à retenir {#key-takeaways}

* **Agilité professionnelle** : en tant qu’utilisateur professionnel ou utilisatrice professionnelle, je peux facilement créer une expérience de formulaire pour plusieurs canaux.

* **Puissance du développeur front-end** : en tant que développeur ou développeuse front-end, je peux contrôler l’expérience de l’utilisateur final ou de l’utilisatrice finale à l’aide de formulaires découplés.

* **Vitesse du développeur** : en tant que développeur ou développeuse, je peux personnaliser facilement et systématiquement les composants Sites et Forms.

## Prérequis {#prerequisites}

Pour accéder à cet atelier pratique :

* Installez la [dernière version de Git](https://git-scm.com/downloads). Si vous découvrez Git, consultez l’article [Installer Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* Installez [Node.js 16.13.0 ou version ultérieure](https://nodejs.org/en/download/). Si vous découvrez Node.js, consultez l’article [Comment installer Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs).

* [Activer les composants principaux des formulaires adaptatifs](enable-headless-adaptive-forms-and-core-components-on-forms-cloud-service.md) pour votre environnement AEM Forms AEM Cloud Service.

* Installez [Microsoft Code Visual Studio](https://code.visualstudio.com/download) ou un autre éditeur de texte brut. Les exemples du document utilisent Microsoft Visual Studio Code.



## Leçon 1 {#lesson-1}

### Objectif {#lesson-1-objectives}

Familiarisez-vous avec l’environnement d’AEM Forms as a Cloud Service.

### Contexte de la leçon {#lesson-1-context}

Dans cette leçon, vous vous familiarisez avec l’environnement d’AEM Forms as a Cloud Service en naviguant dans l’interface utilisateur.

### Exercice {#lesson-1-excercise}

1. Ouvrez votre navigateur et saisissez l’URL de l’environnement de création de Cloud Service. Par exemple :
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. Connectez-vous à l’environnement de création de Cloud Service.
   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. Pour accéder à l’interface utilisateur AEM Forms, cliquez sur **Formulaires > Formulaires et documents**.



   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   Ignorez les fenêtres contextuelles liées aux préférences ou aux informations. Tous les formulaires disponibles sont affichés.


## Leçon 2

### Objectif

Créez un formulaire adaptatif à l’aide des derniers composants principaux, puis configurez et soumettez le formulaire.

### Contexte de la leçon

Dans cette leçon, en tant qu’utilisatrice ou utilisateur professionnel, vous allez créer un formulaire adaptatif pour plusieurs canaux tels que le web, les appareils mobiles et les chats à l’aide de la création de formulaires adaptatifs avec des composants principaux standards prêts à l’emploi pour la capture de données.

### Exercice

1. Créez un point d’entrée d’envoi pour le formulaire :

   1. Ouvrez <https://requestbin.com/> dans un nouvel onglet du navigateur.
      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. Cliquez sur **Créer un répertoire bin public** et copiez l’URL du point d’entrée.
      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

1. Créez un formulaire adaptatif à l’aide de l’interface de l’assistant :

   1. Dans l’onglet du navigateur utilisé dans la leçon 1, accédez à l’interface web d’AEM Forms as Cloud Service, puis à Formulaires et Documents.
      ![](/help/assets/screenshot2028114029.png)

   1. Appuyez sur **Créer** et sélectionnez Formulaire adaptatif.
      ![](/help/assets/screenshot2028114629.png)

   1. Sélectionnez le modèle **vierge avec composants principaux** à partir de l’écran de sélection des modèles, comme illustré ci-dessous :
      ![](/help/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. Cliquez sur l’onglet **Style** et sélectionnez le thème **wknd-theme** comme illustré ci-dessous :
      ![](/help/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. Cliquez sur l’onglet **Envoi** et sélectionnez la carte **Envoyer vers le point d’entrée REST**, puis spécifiez le répertoire bin public dans le champ
      **URL de la requête POST** comme illustré ci-dessous :
      ![](/help/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. Cliquez sur **Créer**. Indiquez un nom et un titre pour votre formulaire. Par exemple : **enregistrement**. Cliquez sur **Créer**.

   1. L’éditeur de formulaire adaptatif s’ouvre. Ignorez les fenêtres contextuelles ou les boîtes de dialogue concernant les préférences ou les informations. Cliquez sur l’explorateur de composants sur le rail de gauche et ajoutez less composants **En-tête** et **Pied de page** en haut et en bas du formulaire vierge, respectivement.
      ![](/help/assets/screenshot2028121929.png)

   1. Faites glisser puis déposez des composants à partir du navigateur de composants pour créer un formulaire, comme suit :

      ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}





1. Ajoutez des validations au formulaire :

   1. Cliquez sur le composant **Numéro de téléphone** pour afficher le menu contextuel. Cliquez sur l’**icône Clé à molette** dans le menu pour configurer le champ.

   1. Ouvrez l’**onglet Validations**, marquez le champ comme **Obligatoire**, puis cliquez sur **Terminé**. Le message de réussite s’affiche.
      ![](/help/assets/screenshot2028123529.png){width="50%" align="left"}

      ![](/help/assets/screenshot2028123629.png){width="50%" align="left"}

1. Prévisualisez et soumettez le formulaire.

   1. Cliquez sur **Aperçu** pour prévisualiser le formulaire du point de vue de l’utilisateur final ou de l’utilisatrice finale.

   1. Remplissez le formulaire avec des données factices.

   1. Soumettez le formulaire.
      ![](/help/assets/screenshot2028125729.png)

   1. Dans l’onglet Zone de requêtes, vérifiez les données envoyées.
      ![](/help/assets/screenshot2028125829.png)

1. Ajoutez de l’interactivité au formulaire avec des règles :

   1. Sélectionnez le composant **Cocher la case pour recevoir 5 % de réduction**. Dans la barre d’outils des options, cliquez sur l’icône Règles. L’option Éditeur de règles s’ouvre.

   1. Créez une règle, lorsque l’option **Cochez la case pour recevoir 5 % de réduction.** est sélectionnée, les options d’application de la carte de crédit sont désactivées.

1. Publiez le formulaire.

   1. Ouvrez l’interface de gestion d’AEM Forms, par exemple : `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`, puis sélectionnez le formulaire.

   1. Cliquez sur **Publier**.

      ![](/help/assets/screenshot2028115629.png)

      Le message de réussite s’affiche.

      ![](/help/assets/screenshot2028115729.png)

      L’URL de publication du formulaire est semblable à `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

   1. Pour afficher le formulaire publié, remplacez l’ID de programme (pXXXXXX) et l’ID d’environnement (eXXXXXX) dans l’URL ci-dessus par les ID de votre 
environnement.

## Leçon 3

### Objectif

Mise à jour des styles à l’aide des bonnes pratiques de développement front-end.

### Contexte de la leçon

Dans cette leçon, en tant que développeur ou développeuse front-end, vous apprendrez comment mettre facilement à jour le style du formulaire adaptatif créé précédemment.

### Exercice

Configurez le référentiel local du thème :

1. Ouvrez l’invite de commande ou un shell avec les droits d’administrateur :

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. Dans l’invite de commande, utilisez la commande suivante pour accéder au dossier **c:\git**.

   ```Shell
   cd c:\git
   ```

1. Utilisez la commande suivante pour cloner le code front-end du thème :

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. Utilisez la commande suivante dans l’ordre indiqué pour accéder au répertoire **aem-forms-theme-canvas** et ouvrez Visual Studio Code.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png)

1. Sélectionnez **Approbation des auteurs de tous les fichiers du dossier parent** et cliquez sur **Oui, je fais confiance aux auteurs**.

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. Pour effectuer le rendu du formulaire hébergé dans votre environnement de publication Cloud Service, renommez le fichier `env_template`.  Pour renommer le fichier, cliquez avec le bouton droit de la souris sur le fichier **env_template** et sélectionnez l’option **Renommer**.

   ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. Définissez les valeurs suivantes pour les variables dans le fichier .env et enregistrez le fichier :

   * **AEM_URL** : spécifiez votre environnement de publication Cloud Service. Par exemple, `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM** : spécifiez le chemin du formulaire. Par exemple, si le chemin du formulaire est `/content/forms/af/registration`, la valeur de cette variable sera `registration`.

     ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

1. Créez un utilisateur local dans AEM environnement.

   >[!NOTE]
   > Pour créer un utilisateur local :
   > Accédez à `AEM Home` > `Tools` > `Security` > `Users`
   > Assurez-vous que l’utilisateur est membre du groupe forms-users .


1. Dans la fenêtre de l’invite de commande, exécutez la commande suivante :

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Si vous recevez un message vous demandant de mettre à jour npm via la commande `npm notice Run npm nstall -g npm@9.6.0`, ignorez-le.
   > * N’exécutez pas d’autres commandes npm, sauf si cela est indiqué dans le classeur.

1. Exécutez maintenant la commande suivante pour prévisualiser le formulaire.

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   Une fois la commande ci-dessus exécutée, attendez la `webpack compiled` et vous êtes redirigé vers une page de connexion AEM.

1. Cliquez sur **Connexion locale (tâches d’administration uniquement)** sur la page de connexion AEM.
1. Saisissez les informations d’identification de l’utilisateur local créé et le formulaire s’affiche dans un onglet de navigateur.

   >[!NOTE]
   >
   >Si un écran vierge s’affiche dans le navigateur après l’exécution de la commande `npm run live` pendant plus de 3 à 4 minutes, modifiez `localhost` dans l’URL du navigateur avec 127.0.0.1 et cliquez sur **Entrée**.


   ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}


1. Dans Visual Studio Code, ouvrez le fichier `PROJECT\src\site\_variables.scss`. Vous remarquerez que la couleur `$error` est une nuance de rouge.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. Dans le navigateur, envoyez le formulaire pour afficher la couleur rouge dans le champ **Prénom**.

   ![](/help/assets/screenshot2028120829.png)

1. Définissez la couleur **$error** sur **#5736eb** et enregistrez le fichier.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. Actualisez le navigateur et envoyez le formulaire. Vous remarquerez que la couleur d’erreur du champ Prénom a été modifiée en conséquence.

   ![](/help/assets/screenshot2028121129.png)

1. Dans l’invite de commande, appuyez sur **Ctrl+C**, saisissez **Y**, puis appuyez sur la touche **Entrée** pour arrêter le processus npm. Il est important d’arrêter le serveur npm afin qu’il n’entre pas en conflit avec le prochain ensemble d’exercices.
1. Fermez les fenêtres Visual Studio Code et Invite de commande.

## Leçon 4

### Objectif

Effectuez le rendu du formulaire sur des interfaces web/mobile et d’autres interfaces en tant que formulaire découplé.

### Contexte de la leçon

Dans cette leçon, en tant que développeur ou développeuse front-end, vous apprendrez à effectuer le rendu du formulaire adaptatif créé précédemment en tant que formulaire découplé à l’aide du framework de conception React Spectrum.

### Exercice

Configurez le référentiel local à l’aide du projet de démarrage React :

1. Ouvrez l’invite de commande à l’aide des droits d’administration.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. Dans l’invite de commande, utilisez la commande suivante pour accéder au dossier **c:\git**.

   ```Shell
   cd c:\git
   ```

1. Utilisez la commande suivante pour cloner le projet de démarrage react du formulaire adaptatif :

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028117329.png)

1. Utilisez les commandes suivantes dans l’ordre indiqué pour accéder au répertoire **react-starter-kit-aem-headless-forms** et ouvrez Visual Studio Code.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028117529.png)


   La fenêtre Visual Studio Code s’ouvre.

   ![](/help/assets/screenshot2028117429.png){width="50%" align="left"}

Pour effectuer le rendu du formulaire hébergé dans votre environnement de publication de service cloud :

1. Renommez le fichier env_template en fichier .env. Pour renommer, cliquez avec le bouton droit de la souris sur le fichier **env_template** et sélectionnez l’option **Renommer**.

   ![](/help/assets/screenshot2028117629.png){width="50%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. Définissez les valeurs suivantes pour les variables du fichier .env. Après avoir mis à jour les variables, enregistrez le fichier.

   * **AEM_URL** : spécifiez l’URL de l’environnement de publication du service cloud. Par exemple, `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH** : spécifiez le chemin d’accès au formulaire adaptatif créé dans la leçon précédente. Par exemple, `/content/forms/af/registration/`

     ![](/help/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. Ouvrez la fenêtre de commande, vérifiez que vous vous trouvez dans le répertoire react-starter-kit-aem-headless-forms, puis exécutez la commande suivante :

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. Dans la fenêtre de l’invite de commande, exécutez la commande suivante :

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028118129.png)

   La commande ci-dessus lance un serveur de développement local qui effectue le rendu de la définition de formulaire récupérée à partir d’AEM de manière déouplée à l’aide de la bibliothèque front-end react-spectrum.

   >[!NOTE]
   >
   > 
   > Si un écran vierge s’affiche dans le navigateur après l’exécution de la commande `npm start` pendant plus de 3 à 4 minutes, remplacez `localhost` dans l’URL du navigateur par 127.0.0.1 et appuyez sur **Entrée**.

   ![](/help/assets/screenshot2028118229.png)

Vérifions l’exécution des règles dans ce formulaire découplé :

1. Sélectionnez l’option **Cocher la case pour recevoir 5 % de réduction**. L’option suivante d’utilisation de la carte de crédit est désactivée.

   ![](/help/assets/screenshot2028126229.png)

1. Décochez l’option **Cocher la case pour recevoir 5 % de réduction** pour activer l’option de carte de crédit.

   ![](/help/assets/screenshot2028126329.png)

Modifions le formulaire sur le serveur en tant qu’utilisateur professionnel et affichons les modifications répercutées automatiquement dans le formulaire découplé.

1. Ouvrez l’interface de gestion d’AEM Forms dans le navigateur. Par exemple : [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments).

1. Sélectionnez le formulaire **contactus** et cliquez sur **Modifier.** Cette action ouvre le formulaire dans l’éditeur de formulaires adaptatifs.


1. Sélectionnez le champ **Numéro de téléphone** et cliquez sur l’**icône Modifier (icône de crayon)** dans la barre d’outils. Si la barre d’outils contextuelle ne s’affiche pas, basculez en mode d’édition en cliquant sur le bouton **Modifier** en haut à droite, à gauche du bouton **Aperçu**.

   ![](/help/assets/screenshot2028119629.png)

1. Remplacez le libellé par Numéro de mobile. Cliquez sur n’importe quel espace vide du formulaire pour enregistrer les modifications apportées au formulaire.

   ![](/help/assets/screenshot2028119729.png)

Publions maintenant le formulaire mis à jour pour propager les modifications dans l’environnement de publication.

1. Dans l’onglet de l’interface de gestion d’AEM Forms, sélectionnez le formulaire d’enregistrement, puis cliquez sur **Dépublier**. Si vous ne voyez pas le bouton **Dépublier**, passez à l’étape 3 pour publier directement les modifications.

1. Cliquez sur **Dépublier**. Cliquez sur **Fermer** dans la boîte de dialogue correspondante.

1. Une fois le navigateur actualisé, sélectionnez le formulaire d’enregistrement et cliquez sur **Publier**.

1. Cliquez sur **Publier**. Cliquez sur **Fermer** dans la boîte de dialogue correspondante.

1. Actualisez l’onglet du navigateur avec le formulaire découplé affiché. Notez que le libellé Numéro de téléphone a été remplacé par Numéro mobile.

   ![](/help/assets/screenshot2028120529.png)

1. Ouvrez la fenêtre d’invite de commande utilisée pour démarrer le projet **react-starter-kit-aem-headless-forms**, appuyez sur **Ctrl+C**, puis
saisissez **Y** et appuyez sur la touche Entrée pour terminer le processus npm. Il est important d’arrêter le serveur npm afin qu’il n’entre pas en conflit avec le prochain ensemble d’exercices.

1. Fermez les fenêtres Visual Studio Code et Invite de commande.


## Leçon 5

### Objectif

Effectuez le rendu du formulaire en tant que formulaire découplé à l’aide de l’interface utilisateur Material Google.

### Contexte de la leçon

Dans cette leçon, en tant que développeur ou développeuse front-end, vous apprenez à effectuer le rendu du formulaire adaptatif créé précédemment en tant que formulaire découplé à l’aide de l’interface utilisateur Material Google.

### Exercice

Configurez le référentiel local à l’aide du projet de démarrage de l’interface utilisateur Material :

1. Ouvrez l’invite de commande à l’aide des droits d’administration.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}


1. Dans l’invite de commande, utilisez la commande suivante pour accéder au dossier **c:\git** :

   ```Shell
   cd c:\git
   ```

1. Exécutez les commandes suivantes dans l’ordre indiqué pour créer un dossier nommé mui et accédez au dossier mui à l’aide des commandes suivantes :

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Utilisez la commande suivante pour cloner le projet de démarrage react du formulaire adaptatif :

   ```Shell
   git clone -b mui-lab https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028126529.png)

1. Utilisez la commande suivante dans l’ordre indiqué pour accéder au dossier **react-starter-kit-aem-headless-forms**, puis ouvrez le code dans Visual Studio Code :

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028126829.png)

Pour effectuer le rendu du formulaire hébergé dans votre environnement de publication de service cloud :

1. Renommez le fichier **env_template** en fichier **.env**. Pour renommer, cliquez avec le bouton droit de la souris sur le fichier **env_template**, puis sélectionnez **Renommer**.

   ![](/help/assets/screenshot2028126629.png){width="50%" align="left"}

1. Définissez les valeurs suivantes pour les variables du fichier .env. Après avoir mis à jour les variables, enregistrez le fichier. Appuyez sur **Ctrl + S** pour enregistrer le fichier.

   * **AEM_URL** : spécifiez l’URL de l’environnement de publication Cloud Service. Par exemple, [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH** : spécifiez le chemin d’accès au formulaire adaptatif créé dans la leçon précédente. Par exemple, /content/forms/af/registration/

     ![](/help/assets/screenshot2028126929.png)

1. Ouvrez la fenêtre de commande, assurez-vous que vous êtes au répertoire **react-starter-kit-aem-headless-forms**, puis exécutez la commande suivante :

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. Dans la fenêtre de l’invite de commande, exécutez la commande suivante :

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028127129.png)

   La commande démarre un serveur de développement local et effectue le rendu de la définition de formulaire récupérée à partir d’AEM de façon découplée à l’aide de
la bibliothèque front-end de l’interface utilisateur Material Google.

   >[!NOTE]
   >
   >Si un écran vierge s’affiche dans le navigateur après l’exécution de la commande `npm start` pendant plus de 3 à 4 minutes, modifiez `localhost` dans l’URL du navigateur par 127.0.0.1 et appuyez sur **Entrée**.

   ![](/help/assets/screenshot2028127229.png)

1. Pour évaluer l’exécution de la même logique commercial dans ce rendu de formulaire :

   Sélectionnez **Cocher la case pour recevoir 5 % de réduction**. L’option suivante **Souhaitez-vous demander le formulaire de carte de crédit d’entreprise We.Finance ?** se désactive.

   ![](/help/assets/screenshot2028127329.png){width="50%" align="left"}

## Leçon 6

### Objectif

Créez un autre aspect du formulaire découplé à l’aide des variantes de composants de l’interface utilisateur Material.

### Contexte de la leçon

Dans cette leçon, en tant que développeur ou développeuse front-end, vous apprenez à créer une représentation alternative de différents composants à l’aide de l’interface utilisateur Material pour le formulaire adaptatif créé précédemment par l’utilisatrice ou l’utilisateur professionnel.

### Exercice

Mettez à jour la variante des composants dans le projet découplé. Pour modifier la variante du composant de saisie de texte de l’interface utilisateur Material en `OutlinedInput` :

1. Dans Visual Code, accédez au composant de saisie de texte en ouvrant le fichier `index.tsx` à l’emplacement `src/components/textinput/index.tsx`.

1. Ajoutez `//` au début de la ligne de code 103. Cela convertit la ligne en commentaire.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Ajoutez ce qui suit à la ligne 104 pour utiliser une autre variante du composant, puis enregistrez le fichier. Appuyez sur **CTRL + S** pour enregistrer le fichier.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/screenshot2028127629.png)

   Il est essentiel d’utiliser les majuscules correctement pour la variante « OutlinedInput » pour éviter l’échec de la compilation. La compilation de l’environnement de développement local commence automatiquement dans l’invite de commande. Patientez jusqu’à ce que le message suivant s’affiche.

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Actualisez le navigateur, s’il ne s’actualise pas automatiquement, pour voir le composant Entrée de texte utilisez une autre variante.

   ![](/help/assets/screenshot2028127729.png)


   Cette modification se produit pour les utilisatrices et utilisateurs finaux sans modification de la définition de formulaire sur le serveur AEM Forms et est spécifique
au canal découplé en cours de traitement. Par exemple, le canal Web dans cet atelier.

   ![](/help/assets/screenshot2028127529.png){width="50%" align="left"}


1. Fermez les fenêtres Visual Studio Code et Invite de commande.

## Questions fréquentes

+++ L’assistant de formulaire adaptatif est-il accessible au public ?

Oui, il est disponible avec AEM Forms as a Cloud Service.

+++


+++ Les composants principaux sont-ils accessibles au public ?

Oui, les composants principaux de formulaires adaptatifs sont disponibles avec AEM Forms as a Cloud Service.

+++

+++ Les formulaires découplés sont-ils accessibles au public ?

Oui, les formulaires découplés sont disponibles avec AEM Forms as a Cloud Service.

+++

+++ Les formulaires découplés requièrent-ils une licence distincte ?

Non, les formulaires découplés utilisent la même mesure de valeur de licence et le même nombre d’envois de formulaire.

+++

+++ Les composants principaux et les formulaires découplés sont-ils disponibles avec AEM 6.5 Forms ?

Oui, les composants principaux des formulaires adaptatifs et les formulaires découplés sont disponibles avec AEM Forms 6.5 Service Pack 16 et ses versions ultérieures.

+++


## Étapes suivantes

Maintenant que vous avez appris à créer des formulaires adaptatifs et à les diffuser sur plusieurs canaux à l’aide de formulaires découplés, vous devez essayer de mettre en œuvre vos nouvelles compétences. Amusez-vous et allez de l’avant en créant et en proposant des expériences de capture de données exceptionnelles à vos utilisatrices et utilisateurs finaux, où qu’ils et elles se trouvent, et à grande échelle !

## Ressources

* [Présentation des composants principaux des formulaires adaptatifs](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=fr)

* [Création d’un formulaire adaptatif à l’aide des composants principaux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=fr)

* [Mise à jour de la mise en forme pour le formulaire adaptatif basé sur les composants principaux](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=fr)

* [Formulaires adaptatifs découplés](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=fr)

* [Utilisation du kit de démarrage Headless React](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=fr)
