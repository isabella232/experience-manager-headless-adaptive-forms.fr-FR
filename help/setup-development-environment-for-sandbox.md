---
title: Configuration de l’environnement de développement pour un environnement de test Forms as a Cloud Service
description: Configuration de l’environnement de développement pour un environnement de test Forms as a Cloud Service
hide: true
exl-id: befac9ad-d2c4-4705-96fc-f0ea0ef823b8
source-git-commit: 41286ff4303e0f4d404deb113fd59d1499768da5
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 6%

---

# Configuration de l’environnement de développement pour les formulaires adaptatifs sans affichage sur Cloud Service

<span class="preview"> Ceci est une **TRAVAIL EN COURS** article.</span>


Prêt à créer et tester des formulaires adaptatifs sans affichage sur Cloud Service ? Activez Forms pour votre programme de Cloud Service et commencez.

## Avant de commencer

* Installer [Dernière version de Git](https://git-scm.com/downloads) sur votre ordinateur local. Si vous découvrez Git, voir [Installation de Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git). Vous utilisez le référentiel Git pour transmettre les formulaires et le code personnalisé développés sur votre environnement de développement local à votre environnement de développement de Cloud Service.

* Installer [Node.js 16.13.0 ou version ultérieure](https://nodejs.org/en/download/) sur votre ordinateur local. Si vous découvrez Node.js pour la première fois, voir [Comment installer Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).

* Création d’un programme as a Cloud Service AEM : suivez les étapes 1 à 7 de la [créer un programme](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program) article pour créer un programme pour votre organisation.

* Activer [Canal de version préliminaire pour votre programme Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?cloud-environments).

## Workflow de configuration

Pour activer les formulaires adaptatifs sans affichage sur votre environnement de test as a Cloud Service Forms, activez `Forms - Digital enrolment` pour votre programme AEM Cloud Service, créez un projet basé sur Archetype 37 ou version ultérieure sur votre ordinateur local et poussez-le vers votre environnement Forms as a Cloud Service. Le processus complet est le suivant :

![Processus de configuration d’un environnement de développement pour un environnement de test Forms as a Cloud Service](assets/FORMS-HLAF-SANDBOX-PRODUCTION-ENR.png)

### 1. Activez Forms pour votre programme

<table style="table-layout:auto">
<tr>
  <td>
  1. Connectez-vous à <a href="https://experience.adobe.com/" > https://experience.adobe.com/ </a>  et sélectionnez la variable <b> Experience Manager </b> .
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM programmes as a Cloud Service" src="assets/cloud-manager-experience-manager.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2. Pour la variable <b> Cloud Manager </b> option, cliquez sur <b> Lancez. </b> Une liste des programmes de votre entreprise s’affiche.
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM programmes as a Cloud Service" src="assets/cloud-manager-experience-manager-launch.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    3. Pour votre programme, appuyez sur l’icône ... et sélectionnez l’option <b> Modifier le programme </b> . Une boîte de dialogue s’affiche. 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM programmes as a Cloud Service" src="assets/edit-program.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    4. Dans la boîte de dialogue Modifier le programme, accédez au <b> Onglet Solutions et modules complémentaires </b>, sélectionnez la variable <b> Forms - Inscription numérique </b> et appuyez sur <b> update </b>. 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM programmes as a Cloud Service" src="assets/program-solution-addons.png">
    </a>
    <br>
  </td>
</tr>
</table>

### 2. Cloner le référentiel Git de votre programme sur votre ordinateur local

Chaque programme as a Cloud Service AEM dispose d’un référentiel git. Il vous permet de charger du code personnalisé et des ressources de l’ordinateur local vers votre environnement de Cloud Service. Pendant la configuration, nous utilisons le référentiel Git pour importer du code, des modèles et d’autres informations liés aux formulaires adaptatifs sans affichage dans votre programme de Cloud Service depuis votre ordinateur local. Le clonage du référentiel git du Cloud Service sur votre ordinateur local est la première étape pour apporter du code et du contenu personnalisés de votre ordinateur local à Cloud Service.

>[!INFO]
>
> Vous pouvez toujours valider un référentiel Git sans le cloner. Mais elle a ses propres bizarreries. Donc, nous utilisons l&#39;approche du clonage dans ce document.


Pour cloner le référentiel :

<table style="table-layout:fixed">
<tr>
  <td>
  1. Dans la zone de pipeline de votre programme, appuyez sur <b> Accédez à Informations sur le référentiel. </b> Une boîte de dialogue contenant des informations sur le référentiel s’affiche. 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM programmes as a Cloud Service" src="assets/git-repo.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2. Appuyez sur <b> Générer un mot de passe </b> et copiez la variable <b> URL du référentiel. </b> 
  </td>
  <td>
      <img alt="AEM programmes as a Cloud Service" src="assets/repository-info.png">
    <br>
  </td>
</tr>
<tr>
  <td>
    3. Sur votre ordinateur local, ouvrez l’invite de commande, créez un dossier, exécutez la commande suivante, puis saisissez les informations d’identification du référentiel, puis demandez :
    </br>
    <code> git clone [Repository URL] </code> </br></br>
    Par exemple : </br> 
    <code> git clone https://git.cloudmanager.adobe.com/stage-aemformsdev/khushwantsingh-p45413-uk89613/ </code>

</br> Lorsque vous y êtes invité, obtenez la variable <b> Nom d’utilisateur</b> et <b>Password</b> de la <b>Informations sur le référentiel</b> écran.
</td>
  <td>
     <img alt="AEM programmes as a Cloud Service" src="assets/clone-success.png">
  </td>
</tr>
</table>


### 3. Créez un projet AEM basé sur l’archétype

Le projet d’archetype est un modèle maven. Il crée un projet minimal basé sur les bonnes pratiques pour commencer à utiliser les formulaires adaptatifs sans affichage. Elle comprend également la fonctionnalité de base des formulaires adaptatifs sans affichage pour Forms as a Cloud Service. Il est obligatoire de créer et déployer le projet basé sur l’archétype 37 ou version ultérieure.
®®® Selon le système d’exploitation, exécutez la commande maven pour créer un projet Experience Manager Forms as a Cloud Service. Utilisez l’archétype version 37 ou ultérieure. Voir [Documentation sur l’archétype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) pour trouver la dernière version d’Archetype.

+++ Microsoft® Windows 

1. Ouvrez l’invite de commande avec les privilèges d’administrateur (exécutez l’invite de commande ou bash shell en tant qu’administrateur).
1. Exécutez la commande suivante :

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

™™™ * Set `appTitle` pour définir le titre et les groupes de composants.
* Définir `appId` pour définir l’artifactId Maven, les noms des dossiers de composants, de configurations et de contenu, ainsi que les noms des bibliothèques clientes.
* Définir `groupId` pour définir le groupId Maven et le package source Java™.
* Utilisez l’option `includeFormsenrollment=y` pour inclure des configurations, des thèmes, des modèles, des composants principaux et des dépendances spécifiques à Forms, nécessaires à la création de formulaires adaptatifs.
* Utilisez la variable `includeFormsheadless=y` pour inclure les composants principaux de Forms et les dépendances nécessaires pour inclure la fonctionnalité de formulaires adaptatifs sans affichage. Lors de l’activation de cette option, les éléments suivants sont inclus :\
* Le **Vide avec les composants principaux** modèle avec [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr).
* Un module front React, `ui.frontend.react.forms.af`. Elle vous aide à effectuer le rendu d’un formulaire adaptatif sans affichage dans une application de réaction.

+++®®®


+++ Apple macOS ou Linux®

1. Ouvrez le terminal en tant qu’utilisateur root. Il vous permet d’exécuter des commandes avec des privilèges d’administrateur. Vous pouvez également utiliser `sudo root` après avoir ouvert la fenêtre du terminal pour exécuter des commandes avec des privilèges d’administrateur.
1. Exécutez la commande suivante :

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

™™™ * Set `appTitle` pour définir le titre et les groupes de composants.
* Définir `appId` pour définir l’artifactId Maven, le composant, la configuration, les noms des dossiers de contenu et les noms des bibliothèques clientes.
* Définir `groupId` pour définir le groupId Maven et le package source Java™.
*  Utilisez l’option `includeFormsenrollment=y` pour inclure des configurations, des thèmes, des modèles, des composants principaux et des dépendances spécifiques à Forms, nécessaires à la création de formulaires adaptatifs.
* Utilisez la variable `includeFormsheadless=y` pour inclure les composants principaux de Forms et les dépendances nécessaires pour inclure la fonctionnalité de formulaires adaptatifs sans affichage. Lors de l’activation de cette option, les éléments suivants sont inclus :\
* Le **Vide avec les composants principaux** modèle avec [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr).
* Un module de réaction frontale, `ui.frontend.react.forms.af`. Elle vous aide à effectuer le rendu d’un formulaire adaptatif sans affichage dans une application de réaction.

+++

Une fois la commande terminée, un dossier de projet portant le nom spécifié dans la variable `appID` est créée. Par exemple, si vous utilisez `appID` avec valeur `myheadlessform`, un dossier nommé `myheadlessform` est créée. Il contient le projet basé sur l’archétype.

### 4. Envoyez le projet AEM basé sur l’archétype à votre environnement de Cloud Service.

1. Remplacez le contenu du référentiel git par le contenu d’un projet basé sur Archtype.

   >[!VIDEO](https://video.tv.adobe.com/v/3409809/)

1. Ouvrez une invite de commande, accédez à votre dossier Git Repository et exécutez les commandes ci-dessous dans l’ordre indiqué pour charger le contenu remplacé dans votre environnement de Cloud Service. Vous pouvez également utiliser un éditeur visuel au lieu d’utiliser les commandes ci-dessous pour envoyer du contenu vers le référentiel Cloud Service.

   ```
      git add .
      git commit
      git push origin
   ```

### 5. Exécution du pipeline de génération pour votre programme



<table style="table-layout:auto">
<tr>
  <td>
  1. Connectez-vous à <a href="https://experience.adobe.com/" > https://experience.adobe.com/ </a>  et sélectionnez la variable <b> Experience Manager </b> .
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM programmes as a Cloud Service" src="assets/cloud-manager-experience-manager.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2. Pour la variable <b> Cloud Manager </b> option, cliquez sur <b> Lancez. </b> Une liste des programmes de votre entreprise s’affiche. Ouvrez votre programme. 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM programmes as a Cloud Service" src="assets/cloud-manager-experience-manager-launch.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    3. Pour votre pipeline, appuyez sur l’icône ... et sélectionnez l’option <b> Exécuter </b> . Si vous êtes invité à exécuter le pipeline, appuyez sur <b> Exécuter </b> et attendre le pipeline <b> État </b>  pour passer à <b> Terminé </b>.  
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?#create-program">
      <img alt="AEM programmes as a Cloud Service" src="assets/run-build-pipeline.png">
    </a>
    <br>
  </td>
</tr>
</table>

Désormais, votre environnement est prêt à utiliser des formulaires adaptatifs sans affichage. Vous pouvez désormais charger la définition JSON d’un formulaire dans votre environnement de Cloud Service, créer un formulaire adaptatif sans affichage basé dessus et utiliser la variable [getForm](https://opensource.adobe.com/aem-forms-af-runtime/api/#tag/Get-Form-Definition/operation/getForm) et d’autres API REST pour utiliser le formulaire adaptatif sans affichage dans votre application ou service.
