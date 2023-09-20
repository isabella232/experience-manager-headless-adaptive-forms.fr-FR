---
title: Configurer l’environnement de développement pour un sandbox Forms as a Cloud Service
description: Configurer l’environnement de développement pour un sandbox Forms as a Cloud Service
hide: true
exl-id: befac9ad-d2c4-4705-96fc-f0ea0ef823b8
source-git-commit: 41286ff4303e0f4d404deb113fd59d1499768da5
workflow-type: ht
source-wordcount: '1248'
ht-degree: 100%

---

# Configurer l’environnement de développement pour les formulaires adaptatifs découplés sur Cloud Service

<span class="preview"> Cet article est **EN COURS D’ÉLABORATION**.</span>


Vous êtes prêt à créer et à tester les formulaires adaptatifs découplés sur Cloud Service ? Activez Forms pour votre programme Cloud Service et le tour est joué !

## Avant de commencer

* Installez la [dernière version de Git](https://git-scm.com/downloads) sur votre machine locale. Si vous découvrez Git, consultez [Installer Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git). Vous utilisez le référentiel Git pour envoyer les formulaires et le code personnalisé développés sur votre environnement de développement local vers l’environnement de développement Cloud Service.

* Installez [Node.js 16.13.0 ou une version ultérieure](https://nodejs.org/en/download/) sur votre machine locale. Si vous découvrez Node.js, consultez [Comment installer Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).

* Créez un programme AEM as a Cloud Service : suivez les étapes 1 à 7 de l’article [Créer un programme](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=fr#create-program) pour créer un programme pour votre organisation.

* Activez le [Canal de version préliminaire pour votre programme Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?cloud-environments?lang=fr).

## Workflow de configuration

Pour disposer des formulaires adaptatifs découplés sur votre sandbox Forms as a Cloud Service, activez la solution `Forms - Digital enrolment` pour votre programme AEM Cloud Service, puis créez un projet basé sur l’archétype 37 ou une version ultérieure sur votre machine locale et déployez-le sur votre environnement Forms as a Cloud Service. Le processus complet est le suivant :

![Workflow de configuration d’un environnement de développement pour un sandbox Forms as a Cloud Service](assets/FORMS-HLAF-SANDBOX-PRODUCTION-ENR.png)

### 1. Activer Forms pour votre programme

<table style="table-layout:auto">
<tr>
  <td>
  1. Connectez-vous à <a href="https://experience.adobe.com/" > https://experience.adobe.com/ </a> et sélectionnez l’option <b> Experience Manager. </b>
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=fr#create-program">
      <img alt="Programmes AEM as a Cloud Service" src="assets/cloud-manager-experience-manager.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2. Pour l’option <b> Cloud Manager, </b> cliquez sur <b> Lancer. </b> Une liste des programmes de votre organisation s’affiche.
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=fr#create-program">
      <img alt="Programmes AEM as a Cloud Service" src="assets/cloud-manager-experience-manager-launch.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    3. Pour votre programme, appuyez sur l’icône ... et sélectionnez l’option <b> Modifier le programme </b>. Une boîte de dialogue s’affiche. 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=fr#create-program">
      <img alt="Programmes AEM as a Cloud Service" src="assets/edit-program.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    4. Dans la boîte de dialogue Modifier le programme, accédez à l’onglet <b> Solutions et modules complémentaires, </b> sélectionnez l’option <b> Forms - Inscription numérique </b> et appuyez sur <b> mettre à jour </b>. 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=fr#create-program">
      <img alt="Programmes AEM as a Cloud Service" src="assets/program-solution-addons.png">
    </a>
    <br>
  </td>
</tr>
</table>

### 2. Cloner le référentiel Git de votre programme sur votre machine locale

Chaque programme AEM as a Cloud Service dispose d’un référentiel Git. Il vous permet de charger du code personnalisé et des ressources de la machine locale vers votre environnement Cloud Service. Pendant la configuration, le référentiel Git est utilisé pour importer du code, des modèles et d’autres informations liés aux formulaires adaptatifs découplés dans votre programme Cloud Service, à partir de votre machine locale. Le clonage du référentiel Git de Cloud Service sur votre machine locale constitue la première étape pour transférer le code et le contenu personnalisés de votre machine locale vers Cloud Service.

>[!INFO]
>
> Vous pouvez toujours valider un référentiel Git sans le cloner. Mais cette méthode présente ses propres spécificités. Dans ce document, l’approche du clonage est donc utilisée.


Pour cloner le référentiel :

<table style="table-layout:fixed">
<tr>
  <td>
  1. Dans la zone de pipeline de votre programme, appuyez sur <b> Accédez aux informations sur le référentiel. </b> Une boîte de dialogue contenant des informations sur le référentiel s’affiche 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=fr#create-program">
      <img alt="Programmes AEM as a Cloud Service" src="assets/git-repo.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2. Appuyez sur <b> Générer un mot de passe </b> et copiez <b> l’URL du référentiel. </b> 
  </td>
  <td>
      <img alt="Programmes AEM as a Cloud Service" src="assets/repository-info.png">
    <br>
  </td>
</tr>
<tr>
  <td>
    3. Sur votre machine locale, ouvrez l’invite de commandes, créez un dossier, exécutez la commande suivante, puis saisissez les informations d’identification du référentiel demandées :
 </br>
 <code> git clone [Repository URL] </code> </br></br>
 Par exemple : </br> 
    <code> git clone https://git.cloudmanager.adobe.com/stage-aemformsdev/khushwantsingh-p45413-uk89613/ </code>

</br> Lorsque vous y êtes invité, obtenez le <b> Nom d’utilisateur</b> et le <b>Mot de passe</b> à partir de l’écran <b>Informations sur le référentiel</b>.
</td>
  <td>
     <img alt="Programmes AEM as a Cloud Service" src="assets/clone-success.png">
  </td>
</tr>
</table>


### 3. Créer un projet basé sur l’archétype AEM

Le projet d’archétype est un modèle Maven. Il permet de créer un projet basique, fondé sur les bonnes pratiques, pour commencer à utiliser les formulaires adaptatifs découplés. Il comprend également la fonctionnalité de base des formulaires adaptatifs découplés pour Forms as a Cloud Service. Il est obligatoire de créer et de déployer le projet basé sur l’archétype 37 ou une version ultérieure.
®®®
Selon le système d’exploitation, exécutez la commande Maven pour créer un projet Experience Manager Forms as a Cloud Service. Utilisez l’archétype version 37 ou ultérieure. Consultez la [documentation de l’archétype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) pour obtenir la dernière version.

+++ Microsoft® Windows

1. Ouvrez l’invite de commandes avec les privilèges d’administrateur (exécutez l’invite de commandes ou un shell Bash en tant qu’administrateur).
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

™™™
* Définissez `appTitle` pour définir le titre et les groupes de composants.
* Définissez `appId` pour définir l’artifactId Maven, les noms des dossiers de composants, de configurations et de contenu, ainsi que les noms des bibliothèques clientes.
* Définissez `groupId` pour définir le groupId Maven et le package source Java™.
* Utilisez l’option `includeFormsenrollment=y` pour inclure des configurations, des thèmes, des modèles, des composants principaux et des dépendances spécifiques à Forms, nécessaires à la création de formulaires adaptatifs.
* Utilisez l’option `includeFormsheadless=y` afin d’ajouter les composants principaux Forms et les dépendances nécessaires pour inclure la fonctionnalité de formulaires adaptatifs découplés. Lors de l’activation de cette option, les éléments suivants sont inclus :\
* Le modèle **Vierge avec composants principaux** avec les [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr).
* Un module front-end React, `ui.frontend.react.forms.af`. Vous pouvez ainsi effectuer le rendu d’un formulaire adaptatif découplé dans une application React.

+++®®®


+++ Apple macOS ou Linux®

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

™™™
* Définissez `appTitle` pour définir le titre et les groupes de composants.
* Définissez `appId` pour définir l’artifactId Maven, les noms des dossiers de composants, de configurations et de contenu, ainsi que les noms des bibliothèques clientes.
* Définissez `groupId` pour définir le groupId Maven et le package source Java™.
* Utilisez l’option `includeFormsenrollment=y` pour inclure des configurations, des thèmes, des modèles, des composants principaux et des dépendances spécifiques à Forms, nécessaires à la création de formulaires adaptatifs.
* Utilisez l’option `includeFormsheadless=y` afin d’ajouter les composants principaux Forms et les dépendances nécessaires pour inclure la fonctionnalité de formulaires adaptatifs découplés. Lors de l’activation de cette option, les éléments suivants sont inclus :\
* Le modèle **Vierge avec composants principaux** avec les [composants principaux](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=fr).
* Un module front-end React, `ui.frontend.react.forms.af`. Vous pouvez ainsi effectuer le rendu d’un formulaire adaptatif découplé dans une application React.

+++

Une fois la commande exécutée, un dossier de projet portant le nom spécifié dans `appID` est créé. Par exemple, si vous utilisez `appID` avec la valeur `myheadlessform`, un dossier nommé `myheadlessform` est créé. Il contient le projet basé sur l’archétype.

### 4. Envoyer le projet basé sur l’archétype AEM à votre environnement Cloud Service

1. Remplacez le contenu du référentiel Git par le contenu d’un projet basé sur l’archétype.

   >[!VIDEO](https://video.tv.adobe.com/v/3409809/)

1. Ouvrez une invite de commandes, accédez au dossier de votre référentiel Git et exécutez les commandes ci-dessous dans l’ordre indiqué pour charger le contenu remplacé dans votre environnement Cloud Service. Vous pouvez également utiliser un éditeur visuel au lieu des commandes ci-dessous pour envoyer le contenu vers le référentiel de Cloud Service.

   ```
      git add .
      git commit
      git push origin
   ```

### 5. Exécuter le pipeline de création pour votre programme



<table style="table-layout:auto">
<tr>
  <td>
  1. Connectez-vous à <a href="https://experience.adobe.com/" > https://experience.adobe.com/ </a> et sélectionnez l’option <b> Experience Manager. </b>
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=fr#create-program">
      <img alt="Programmes AEM as a Cloud Service" src="assets/cloud-manager-experience-manager.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  2. Pour l’option <b> Cloud Manager </b>, cliquez sur <b> Lancer. </b> Une liste des programmes de votre organisation s’affiche. Ouvrez votre programme. 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=fr#create-program">
      <img alt="Programmes AEM as a Cloud Service" src="assets/cloud-manager-experience-manager-launch.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    3. Pour votre pipeline, appuyez sur l’icône ... et sélectionnez l’option <b> Exécuter. </b> Si vous êtes invité à exécuter le pipeline, appuyez sur <b> Exécuter </b> et attendez que le <b> Statut </b> du pipeline passe à <b> Terminé </b>.  
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program.html?lang=fr#create-program">
      <img alt="Programmes AEM as a Cloud Service" src="assets/run-build-pipeline.png">
    </a>
    <br>
  </td>
</tr>
</table>

Votre environnement peut maintenant utiliser des formulaires adaptatifs découplés. Vous pouvez à présent charger la définition JSON d’un formulaire dans votre environnement Cloud Service pour créer un formulaire adaptatif découplé, ainsi qu’utiliser les API [getForm](https://opensource.adobe.com/aem-forms-af-runtime/api/#tag/Get-Form-Definition/operation/getForm) et d’autres API REST pour utiliser le formulaire adaptatif découplé dans votre application ou service.
