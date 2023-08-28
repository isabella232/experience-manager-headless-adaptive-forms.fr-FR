---
title: Activation de Forms adaptatif sans affichage sur AEM Forms as a Cloud Service
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM Forms as a Cloud Service
description: Découvrez comment activer des formulaires adaptatifs sans interface sur AEM Forms as a Cloud Service avec notre guide détaillé. Notre tutoriel vous guide tout au long du processus, ce qui facilite l’activation de cette puissante fonctionnalité pour votre environnement AEM Forms.
seo-description: Learn how to enable headless adaptive forms on AEM Forms as a Cloud Service with our step-by-step guide. Our tutorial walks you through the process, making it easy to enable this powerful feature for your AEM Forms environment.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin
level: Beginner, Intermediate
contentOwner: Khushwant Singh
docset: CloudService
hide: true
hidefromtoc: true
exl-id: 7c545ca6-cb2d-4d28-b9e8-b6efe3faee00
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 7%

---

# Activation de Forms adaptatif sans affichage sur AEM Forms as a Cloud Service {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

L’activation d’une Forms adaptative sans affichage sur AEM Forms as a Cloud Service vous permet de commencer à créer, publier et diffuser des Forms sans affichage à l’aide de vos instances de Cloud Service AEM Forms sur plusieurs canaux. Vous avez besoin de l’environnement de composants principaux de Forms adaptatif activé pour utiliser le Forms adaptatif sans affichage.

## Remarques

* Lorsque vous créez un programme AEM Forms as a Cloud Service, [Les Forms adaptatives sans affichage sont déjà activées pour vos environnements.](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Si vous disposez d’un programme Forms as a Cloud Service plus ancien où les composants principaux sont [not enabled](#enable-components), vous pouvez [ajout de dépendances des composants principaux Forms adaptatifs](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) dans votre référentiel as a Cloud Service AEM et déployez le référentiel dans vos environnements de Cloud Service pour activer le Forms adaptatif sans affichage.

* Si votre environnement de Cloud Service existant propose une option pour [créer un Forms adaptatif basé sur les composants principaux](create-a-headless-adaptive-form.md), les Forms adaptatives sans en-tête sont déjà activées pour votre environnement et vous pouvez utiliser des Forms adaptatives basées sur des composants principaux en tant que formulaires sans en-tête pour des canaux tels que les appareils mobiles, web, les applications natives et les services qui nécessitent une représentation sans en-tête des Forms adaptatifs.


>[!NOTE]
>
>
> Adobe fournit le Forms adaptatif [kit de démarrage (React App)](create-and-publish-a-headless-form.md) pour aider les développeurs à démarrer rapidement avec le développement de Forms adaptatif sans affichage, sans activer Forms adaptatif sans affichage dans l’environnement as a Cloud Service d’AEM Forms. Vous pouvez activer le Forms adaptatif sans affichage dans un environnement Forms as a Cloud Service ultérieurement après une [main-d’oeuvre rapide avec le développement de formulaires sans tête](create-and-publish-a-headless-form.md).

## Activation de Forms adaptatif sans affichage pour un environnement as a Cloud Service AEM Forms

Effectuez les étapes suivantes, dans l’ordre indiqué, pour activer Forms adaptatif sans affichage pour un environnement as a Cloud Service AEM Forms


![](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. Cloner votre référentiel Git as a Cloud Service AEM Forms {#clone-git-repository}

1. Connexion à [Cloud Manager](https://my.cloudmanager.adobe.com/) et sélectionnez votre organisation et votre programme.

1. Accédez au **Pipelines** de votre **Aperçu du programme** , cliquez sur **Accès aux informations sur le référentiel** pour accéder à votre référentiel Git et le gérer. La page comprend les informations suivantes :

   * URL du référentiel Git de Cloud Manager.
   * Informations d’identification du nom d’utilisateur Git Repository (nom d’utilisateur et mot de passe).

   Cliquez sur **Générer un mot de passe** pour afficher ou générer le mot de passe.

1. Ouvrez le terminal ou l’invite de commande sur votre ordinateur local et exécutez la commande suivante :

   ```Shell
   git clone [Git Repository URL]
   ```

   Lorsque vous y êtes invité, saisissez les informations d’identification. Le référentiel est cloné sur votre ordinateur local.


## 2. Ajout de dépendances des composants principaux Forms adaptatifs à votre référentiel Git {#add-adaptive-forms-core-components-dependencies}

1. Ouvrez votre dossier Git Repository dans un éditeur de code de texte brut. Par exemple, VS Code.
1. Ouvrez le fichier `[AEM Repository Folder]\pom.xml` en mode d’édition.
1. Remplacer les versions de la fonction `core.forms.components.version`, `core.forms.components.af.version` et `core.wcm.components.version` composants avec les versions spécifiées dans [documentation des composants principaux](https://github.com/adobe/aem-core-forms-components). Si le composant n’existe pas, ajoutez ces composants.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.forms.components.version>2.0.14</core.formscomponents.version>
       <core.forms.components.af.version>2.0.14</core.forms.components.af.version>  
       <core.wcm.components.version>2.21.2</core.wcmcomponents.version>
   </properties>
   ```

   ![Mentionner la dernière version des composants principaux Forms](/help/assets/latest-forms-component-version.png)

1. Dans la section dependencies de la variable `[AEM Repository Folder]\pom.xml` , ajoutez les dépendances suivantes, puis enregistrez le fichier.

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
           <!-- Forms Core Component Dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
   <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. Ouvrez le fichier `[AEM Repository Folder]/all/pom.xml` pour le modifier. Ajoutez les dépendances suivantes dans la variable `<embeddeds>` et enregistrez le fichier.

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  Remplacer `${appId}` avec votre appId.
   >
   >  Pour rechercher votre `${appId}`, dans la variable `[AEM Repository Folder]/all/pom.xml` , recherchez les `-packages/application/install` terme. Le texte situé avant la balise `-packages/application/install` est votre terme `${appId}`. Par exemple, le code suivant : `myheadlessform` is `${appId}`.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. Dans le `<dependencies>` de la `[AEM Repository Folder]/all/pom.xml` , ajoutez les dépendances suivantes, puis enregistrez le fichier :

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
           </dependency>
               <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
           </dependency>
   ```

1. Ouvrez le `[AEM Repository Folder]/ui.apps/pom.xml` pour édition. Ajoutez la variable `af-core bundle` et enregistrez le fichier.

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >Assurez-vous que les artefacts de composants principaux des formulaires adaptatifs suivants ne sont pas inclus dans votre projet.
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > et
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. Enregistrez et fermez le fichier.

## 3. Mettez à jour le projet pour inclure la dernière version des composants principaux Forms :

1. Ouvrez le [AEM archetype Project Folder]/pom.xml pour modification.


1. Enregistrez et fermez le fichier.

## 4. Validez les mises à jour de votre référentiel Git et exécutez le pipeline pour déployer le référentiel. {#Commit-the-updates-to-your-git-repository}

1. Pour valider du code dans votre référentiel Git :
   1. Ouvrez le terminal ou l’invite de commande.
   1. Accédez à `[AEM Repository Folder]` et exécutez les commandes suivantes dans l’ordre indiqué.

      ```Shell
      git add pom.xml
      git add all/pom.xml
      git add ui.apps/pom.xml
      git commit -m "Added dependencies for Adaptive Forms Core Components"
      git push origin
      ```

1. Une fois les fichiers validés dans le référentiel Git, [Exécution du pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=fr).

   Une fois l’exécution du pipeline terminée, les composants principaux de Forms adaptatif sont activés pour l’environnement correspondant. En outre, un modèle Forms adaptatif (composants principaux) et un thème Canevas 3.0 sont ajoutés à votre environnement Forms as a Cloud Service, ce qui vous permet de personnaliser et de créer des composants principaux basés sur Forms adaptatif.


## Foire aux questions {#faq}

### Que sont les composants principaux ? {#core-components}

La variable [Composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr) sont un ensemble de composants WCM (Web Content Management, gestion de contenu web) normalisés permettant d’AEM accélérer le temps de développement et de réduire les coûts de maintenance de vos sites web.

### Quelles sont toutes les fonctionnalités ajoutées lors de l’activation des composants principaux ? {#core-components-capabilities}

Lorsque les composants principaux de Forms adaptatif sont activés pour votre environnement, un modèle de formulaire adaptatif basé sur les composants principaux vierge et le thème Canevas 3.0 sont ajoutés à votre environnement. Après avoir activé les composants principaux de Forms adaptatif pour votre environnement, vous pouvez :

* Création d’un Forms adaptatif basé sur des composants principaux.
* Créez des modèles de formulaires adaptatifs basés sur des composants principaux.
* Créez des thèmes personnalisés pour les modèles de formulaires adaptatifs basés sur les composants principaux.
* Servez les représentations JSON du formulaire adaptatif basé sur les composants principaux aux canaux tels que les applications mobiles, web, natives et les services qui nécessitent une représentation sans tête d’un formulaire.

### Les composants principaux de Forms adaptatif sont-ils activés pour mon environnement ? {#enable-components}

Pour vérifier que les composants principaux de Forms adaptatif sont activés pour votre environnement :

1. [Clonage de votre référentiel as a Cloud Service AEM Forms](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Ouvrez le `[AEM Repository Folder]/all/pom.xml` du référentiel Git de votre Cloud Service AEM Forms.

1. Recherchez les dépendances suivantes :

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content


   ![localisez l’artefact core-forms-components-af-core dans all/pom.xml](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   Si les dépendances existent, les composants principaux de Forms adaptatif sont activés pour votre environnement.
