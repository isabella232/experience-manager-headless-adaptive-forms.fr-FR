---
title: Créer un premier formulaire adaptatif découplé
description: Créer un premier formulaire adaptatif découplé
keywords: découplé, formulaire adaptatif
hide: true
exl-id: 99985fed-4a34-47d6-bb6f-79f81e1cd71b
source-git-commit: 41286ff4303e0f4d404deb113fd59d1499768da5
workflow-type: ht
source-wordcount: '1560'
ht-degree: 100%

---

# Créer votre premier formulaire adaptatif découplé

Les formulaires adaptatifs découplés Adobe Experience Manager permettent de créer des applications de formulaires à l’aide de bibliothèques d’interface utilisateur front-end, comme React par exemple, et d’utiliser le SDK Web pour des fonctionnalités telles que la gestion du statut, la validation et les intégrations avec d’autres points de contact.

Prenons l’exemple suivant : l’organisation We.Org cherche à migrer son parcours d’inscription des clients en ligne. L’utilisation d’Angular pour créer des solutions front-end n’a plus de secret pour leur équipe de développement. Elle cherche à créer une interface personnalisée tout en confiant la validation des formulaires et les signatures électroniques à des solutions spécialisées.

Les formulaires adaptatifs découplés Adobe Experience Manager permettent aux entreprises de créer des formulaires en s’appuyant sur leurs compétences en matière de langages front-end, tout en prenant en charge l’utilisation des fonctionnalités back-end pour créer une expérience de formulaires à l’échelle de l’entreprise.

<!-- >>[!VIDEO](https://video.tv.adobe.com/v/341011/) -->

<!--  ![Create a Headless adaptive form](/help/assets/headless-forms.png) -->

## Avant de commencer

* Configurez l’[environnement de développement](setup-development-environment.md) pour créer et tester un formulaire adaptatif découplé sur votre machine locale.
* Les logiciels suivants doivent être installés sur votre machine de développement locale :
   * [Java Development Kit 11](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?1_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3AsoftwareType&amp;1_group.propertyvalues.operation=equals&amp;1_group.propertyvalues.0_values=software-type%3Atooling&amp;fulltext=Oracle%7E+JDK%7E+11%7E&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=14).
   * [Dernière version de Git](https://git-scm.com/downloads). Si vous découvrez Git, consultez [Installer Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
   * [Node.js 16.13.0 ou version ultérieure](https://nodejs.org/en/download/). Si vous découvrez Node.js pour la première fois, consultez [Comment installer Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).
   * [Maven 3.6 ou version ultérieure](https://maven.apache.org/download.cgi). Si vous découvrez Maven pour la première fois, consultez [Installer Apache Maven](https://maven.apache.org/install.html).


## Utiliser le projet d’archétype pour créer un formulaire adaptatif découplé

Le projet d’archétype est un modèle Maven. Il permet de créer un projet basique, fondé sur les bonnes pratiques, pour commencer à utiliser les formulaires adaptatifs découplés. Il comprend également les fonctionnalités de formulaires adaptatifs découplés pour les environnements de développement Forms as a Cloud Service et local. Pendant la phase Beta, la création ou le déploiement du projet basé sur l’archétype 37 ou version ultérieure est requis. Après la phase Beta, le projet n’est nécessaire que pour les personnalisations.

Pour créer et générer votre premier formulaire adaptatif découplé, procédez comme suit :

1. [Créer et déployer le projet AEM basé sur l’archétype](#create-an-archetype-based-project)
1. [Déployer le projet dans le SDK AEM](#deploy-the-project-to-a-local-development-environment)
1. [Créer le schéma JSON du formulaire adaptatif découplé et le télécharger dans votre instance SDK AEM](#create-add-json-representation-of-headless-adaptive-forms)
1. [Créer le formulaire adaptatif basé sur le modèle vierge avec composants principaux](#create-adaptive-form-with-blank-with-core-components-template)


### 1. Créer et déployer le projet AEM basé sur l’archétype {#create-an-archetype-based-project}

Selon le système d’exploitation, exécutez la commande ci-dessous pour créer un projet Experience Manager Forms as a Cloud Service. Utilisez l’archétype version 37 ou ultérieure. Consultez la [documentation de l’archétype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) pour obtenir la dernière version.

**Microsoft Windows**

1. Ouvrez l’invite de commandes avec les privilèges d’administrateur (exécutez l’invite de commande ou un shell Bash en tant qu’administrateur).
1. Exécutez la commande suivante :

   ```shell
     mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
     -D archetypeGroupId=com.adobe.aem ^
     -D archetypeArtifactId=aem-project-archetype ^
     -D archetypeVersion=37 ^
     -D appTitle=myheadlessform ^
     -D appId=myheadlessform ^
     -D groupId=com.myheadlessform ^
     -D includeFormsenrollment="y" ^
     -D includeFormsheadless="y" 
   ```

   * Définissez `appTitle` pour définir le titre et les groupes de composants.
   * Définissez `appId` pour définir l’artifactId Maven, les noms des dossiers de composants, de configurations et de contenu, ainsi que les noms des bibliothèques clientes.
   * Définissez `groupId` pour définir le groupId Maven et le package source Java.
   * Utilisez l’option `includeFormsenrollment=y` pour inclure des configurations, des thèmes, des modèles, des composants principaux et des dépendances spécifiques à Forms, nécessaires à la création de formulaires adaptatifs.
   * Utilisez l’option `includeFormsheadless=y` afin d’ajouter les composants principaux Forms et les dépendances nécessaires pour inclure la fonctionnalité de formulaires adaptatifs découplés. Lors de l’activation de cette option, les éléments suivants sont inclus :
      * Le modèle **Vierge avec composants principaux** avec les [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr).
      * Un module front-end React, `ui.frontend.react.forms.af`. Cela vous permet d’effectuer le rendu du formulaire adaptatif découplé dans une application React.


**Apple macOS ou Linux** :

1. Ouvrez le terminal en tant qu’utilisateur root. Vous pouvez ainsi exécuter des commandes avec des privilèges d’administrateur. Vous pouvez également utiliser la commande `sudo root` après avoir ouvert la fenêtre du terminal pour exécuter des commandes avec des privilèges d’administrateur.
1. Exécutez la commande suivante :

   ```shell
     mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
     -D archetypeGroupId=com.adobe.aem \
     -D archetypeArtifactId=aem-project-archetype \
     -D archetypeVersion=37 \
     -D appTitle=myheadlessform \
     -D appId=myheadlessform \
     -D groupId=com.myheadlessform \
     -D includeFormsenrollment="y" \
     -D includeFormsheadless="y"  
   ```

   * Définissez `appTitle` pour définir le titre et les groupes de composants.
   * Définissez `appId` pour définir l’artifactId Maven, les noms des dossiers de composants, de configurations et de contenu, ainsi que les noms des bibliothèques clientes.
   * Définissez `groupId` pour définir le groupId Maven et le package source Java.
   * Utilisez l’option `includeFormsenrollment=y` pour inclure des configurations, des thèmes, des modèles, des composants principaux et des dépendances spécifiques à Forms, nécessaires à la création de formulaires adaptatifs.
   * Utilisez l’option `includeFormsheadless=y` afin d’ajouter les composants principaux Forms et les dépendances nécessaires pour inclure la fonctionnalité de formulaires adaptatifs découplés. Lors de l’activation de cette option, les éléments suivants sont inclus :
      * Le modèle **Vierge avec composants principaux** avec les [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr).
      * Un module front-end React, `ui.frontend.react.forms.af`. Cela vous permet d’effectuer le rendu du formulaire adaptatif découplé dans une application React.

Une fois la commande exécutée, un dossier de projet portant le nom spécifié dans la propriété `appID` est créé. Par exemple, si vous utilisez `appID` avec la valeur `myheadlessform`, le dossier `myheadlessform` est créé. Il contient le projet basé sur l’archétype.


### 2. Déployer le projet dans le SDK AEM {#deploy-the-project-to-a-local-development-environment}

Lorsque vous déployez le projet sur votre instance SDK AEM, votre environnement de développement reçoit la fonctionnalité de formulaires adaptatifs découplés, le modèle **Vierge avec composants principaux** et les autres ressources du projet. <!-- Deploy the project to your local development environment to locally create Headless Adaptive Forms. or deploy directly to your Forms as a Cloud Service environment. !--> Pour effectuer un déploiement sur votre instance SDK AEM :

1. Ouvrez l’invite de commandes. Sous Windows, ouvrez l’invite de commandes avec les droits d’administrateur (exécutez l’invite de commande ou un [shell Bash Git](https://khushwantsehgal.wordpress.com/2022/06/29/check-if-git-bash-is-running-in-administrator-mode/) en tant qu’administrateur).

1. Accédez au répertoire du projet créé à l’étape précédente. Par exemple, `/myheadlessform`.

   ![project-directory](assets/project-directory.png)

1. Exécutez la commande suivante :

   ```shell
   mvn -PautoInstallPackage clean install
   ```

   Attendez que le message « BUILD SUCCESS » s’affiche.
   ![Projet déployé avec succès](assets/project-deployed-successfully.png).

   La résolution des dépendances et le déploiement du projet peuvent prendre du temps. En cas d’échec du déploiement du projet, consultez la section de [dépannage](troubleshooting.md) pour les problèmes courants et leur résolution.


<!-- *  To learn how to deploy code to AEM as a Cloud Service, see the video in [Deploying to AEM as a Cloud Service]https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=en#coding-against-the-right-aem-version) article : -->


### 3. Créer le schéma JSON du formulaire adaptatif découplé et le télécharger dans votre instance SDK AEM {#create-add-json-representation-of-headless-adaptive-forms}

Un formulaire adaptatif découplé est représenté sous la forme d’un fichier JSON. Consultez un exemple de formulaire dans le [storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--contact) ou utilisez l’exemple de formulaire inclus dans le projet d’archétype à l’adresse `[Archetype Project]\ui.content\src\main\content\jcr_root\content\dam\myheadlessform\af_model_sample.json`. Ce document utilise le formulaire d’[introduction](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) du storybook. Il s’agit d’un formulaire à champ unique qui vous permet de commencer rapidement à utiliser le formulaire adaptatif découplé. <!-- The [specifications](/help/assets/Headless-Adaptive-Form-Specification.pdf) document provides detailed information about various components, rules, and constraints for Headless Adaptive Forms -->

Pour créer et charger le schéma, procédez comme suit :

1. Créez un fichier de texte brut doté de l’extension `.json`. Par exemple, `myfirstform.json`. Vous pouvez créer le fichier n’importe où sur votre système de fichiers ou dans votre projet AEM basé sur l’archétype à l’adresse `\<project-name>\ui.content\src\main\content\jcr_root\content\dam\myheadlessform\<formname>.json`.
1. Ajoutez le contenu JSON suivant à votre fichier `.json` et enregistrez-le :

   ```JSON
   {
     "adaptiveform": "0.10.0",
     "items": [
       {
         "fieldType": "text-input",
         "label": {
           "value": "Enter your Name"
         },
         "name": "textInput"
       }
     ],
     "metadata": {
       "grammar": "json-formula-1.0.0",
       "version": "1.0.0"
     }
   }
   ```

   Un champ unique est alors ajouté au formulaire :

   ![Hello World](assets/introduction.png)

1. Connectez-vous à l’[instance SDK AEM locale](setup-development-environment.md#setup-author-instance)
1. Accédez à Adobe Experience Manager > Formulaires > Formulaires et documents. Appuyez sur Créer > Chargement de fichier.
1. Sélectionnez le fichier `.json` créé à l’étape 2 et téléchargez-le. Vous êtes fin prêt à créer le formulaire adaptatif découplé. Si vous enregistrez le fichier .json dans votre projet AEM basé sur l’archétype à l’adresse `\<project-name>\ui.content\src\main\content\jcr_root\content\dam\myheadlessform\<formname>.json`. Exécutez `mvn -PautoInstallPackage clean install` pour déployer le projet sur votre SDK AEM et le fichier `<formname>.json` avec lui.

En cas d’échec du chargement du fichier `.json`, assurez-vous que le [projet d’archétype AEM a été déployé correctement](#deploy-the-project-to-a-local-development-environment).

<!-- 1. Open the [contact form](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--contact) and tap the [![Raw](assets/raw.png)](faq.md#storybook-example) icon on bottom-right side of the Storybook page to view the source code of the headless . 

You can use [Adaptive Forms builder extension for Visual Studio Code](/help/setup-development-environment.md#microsot-visual-studio-code-extension-for-headless-adaptive-forms) to build a JSON schema of your Headless Adaptive Forms. 

You can see [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) for sample JSON schemas and list of components, attributes, and properties. You can also see the [specifications document](/help/assets/Headless-Adaptive-Form-Specification.pdf) for detailed information on all the components, constraints, and methods available to define Headless Adaptive Forms.

File extension of a JSON schema of Headless Adaptive Forms is .json. For example, formname.json. Create or add the file to your AEM Archetype based project. For example, `\myheadlessform\ui.content\src\main\content\jcr_root\content\dam\myheadlessform\home-loan.json` -> 

### 3. Deploy the project to a local development environment {#deploy-the-project-to-a-local-development-environment}

You can deploy the project to local development environment. It adds Headless Adaptive Forms functionality, the **Blank with core components** template, JSON schema of form, and other resources included in the project to your development environment. <!-- Deploy the project to your local development environment to locally create Headless Adaptive Forms. or deploy directly to your Forms as a Cloud Service environment. To deploy to your local development environment, use the following command: 

    `mvn -PautoInstallPackage clean install`

If you are on Windows, run the above with Administrative privileges (Run command prompt or [bash shell as an administrator](https://khushwantsehgal.wordpress.com/2022/06/29/check-if-git-bash-is-running-in-administrator-mode/)). For the complete list of commands, see [Building and Installing](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en#building-and-installing).
    
<!-- *  To learn how to deploy code to AEM as a Cloud Service, see the video in [Deploying to AEM as a Cloud Service]https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=en#coding-against-the-right-aem-version) article : -->

### 4. Créer un formulaire adaptatif basé sur le modèle vierge avec composants principaux {#create-adaptive-form-with-blank-with-core-components-template}

1. Connectez-vous à votre [instance SDK AEM](http://localhost:4502/).

1. Accédez à Adobe Experience Manager > Formulaires > Formulaires et documents.

1. Appuyez sur Créer et sélectionner Formulaire adaptatif. Sélectionnez le modèle **Vierge avec composants principaux** et appuyez sur Créer.

   ![Modèle](assets/template.png)

1. Spécifiez les valeurs des champs de propriété suivants. Les champs Titre et Nom sont obligatoires :

   * **Titre** : permet d’indiquer le nom d’affichage du formulaire. Le titre vous permet d’identifier le formulaire dans l’interface utilisateur d’Experience Manager Forms.
   * **Nom** : permet d’indiquer le nom du formulaire. Un nœud portant le nom spécifié est créé dans le référentiel. Lorsque vous commencez à saisir un titre, la valeur du champ Nom est automatiquement générée. Vous pouvez modifier la valeur suggérée. Le champ Nom ne peut contenir que des caractères alphanumériques, des traits d’union et des traits de soulignement. Toutes les entrées non valides sont remplacées par un trait d’union.

1. Appuyez sur Créer. Un formulaire adaptatif est alors créé.

Si vous ne voyez pas le modèle **Vierge avec composants principaux**, assurez-vous que le [projet d’archétype AEM a été déployé correctement](#deploy-the-project-to-a-local-development-environment).

### 5. Configurer le formulaire adaptatif pour utiliser le schéma JSON {#configure-adaptive-form-to-use-the-JSON-representation}

Le formulaire adaptatif créé à l’étape précédente est vierge. Configurez le formulaire adaptatif de façon à utiliser le schéma JSON :

1. Connectez-vous à votre [instance SDK AEM](http://localhost:4502/).

1. Accédez à Adobe Experience Manager > Formulaires > Formulaires et documents. Sélectionnez le formulaire adaptatif créé à l’étape précédente et appuyez sur Modifier. Le formulaire adaptatif s’affiche dans l’éditeur.

1. Appuyez sur le composant Conteneur de formulaires adaptatifs, puis sur Propriétés. L’explorateur de propriétés s’affiche dans la barre latérale.

1. Dans l’explorateur de propriétés, développez l’accordéon BASIC, puis spécifiez le chemin du schéma JSON chargé lors d’une étape précédente pour l’option Chemin d’accès au document d’exécution de formulaire. Le composant Conteneur affiche un rendu du formulaire.

1. Dans l’explorateur de propriétés, développez l’accordéon SUBMISSION et choisissez une action Envoyer pour le formulaire adaptatif. Votre formulaire est prêt à être utilisé dans une application REACT.

1. Pour effectuer le rendu du formulaire, hébergé sur votre machine de développement locale :

   1. Ouvrez le fichier `[Archetype project]\ui.frontend.react.forms.af\.env` et définissez le chemin d’accès au formulaire. Par exemple, /content/forms/af/contact

   1. Ouvrez l’invite de commandes, accédez au projet ui.frontend.react.forms.af et exécutez la commande suivante :

      `npm run start`

   1. Une fois l’opération terminée, ouvrez la page localhost:3000 dans la fenêtre du navigateur pour afficher le formulaire adaptatif découplé.
   1. Pour tester la fonctionnalité d’envoi, connectez-vous à votre serveur AEM Forms, puis utilisez l’option **Prévisualiser le formulaire au format HTML** pour ouvrir le formulaire en mode de prévisualisation.

Le [storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) fournit une liste de composants et de règles pouvant être définis sur différents formulaires adaptatifs découplés, ainsi qu’un exemple de schéma JSON de formulaires adaptatifs découplés. Vous pouvez également consulter le document de [spécifications](/help/assets/Headless-Adaptive-Form-Specification.pdf) pour en savoir plus sur les différentes règles et propriétés liées aux formulaires adaptatifs découplés.
