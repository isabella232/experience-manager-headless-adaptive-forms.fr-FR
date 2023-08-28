---
title: Configuration de l’environnement de développement pour AEM formulaires adaptatifs sans affichage
description: Configuration de l’environnement de développement pour AEM formulaires adaptatifs sans affichage
hide: true
exl-id: fd92f057-1217-42f8-a454-1bc7e3827e01
source-git-commit: 41286ff4303e0f4d404deb113fd59d1499768da5
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 10%

---


# Configuration d’un environnement de développement local {#headless-adaptive-forms-setup-development-environment}

Vous pouvez configurer un environnement de développement local pour créer et tester des formulaires adaptatifs sans affichage sur votre ordinateur local. L’environnement de développement se compose du SDK AEM et de l’archive de fonctionnalités AEM Forms installés sur AEM SDK.
<!--
 After a Headless adaptive form or related assets are ready on the local development environment, you can deploy the Headless adaptive form application to your publishing environment. -- >

You require knowledge to build application using react, Git, and Maven to use Headless adaptive forms.

<!-- 

### Download the latest version of AEM as a Cloud Service SDK or Forms feature archive (AEM Forms add-on) from Software Distribution {#software-distribution}

To download the supported version of Adobe Experience Manager as a Cloud Service SDK or Forms feature archive (AEM Forms add-on):

1. Log in to [Software Distribution](https://experience.adobe.com/#/downloads) portal with your Adobe ID.

    >[!NOTE]
    >
    > Your Adobe Organization must be provisioned for AEM as a Cloud Service to download the AEM as a Cloud Service SDK.

1. Navigate to the **[!UICONTROL AEM as a Cloud Service]** tab.
1. Sort by published date in descending order.
1. Click on the latest Adobe Experience Manager as a Cloud Service SDK or Forms feature archive (AEM Forms add-on).
1. Review and accept the EULA. Tap the **[!UICONTROL Download]** button. -->

## Configuration requise {#headless-adaptive-forms-system-requirements}

Pour installer AEM SDK, votre ordinateur local doit répondre aux exigences minimales suivantes :

* [Java Development Kit 11](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?1_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3AsoftwareType&amp;1_group.propertyvalues.operation=equals&amp;1_group.propertyvalues.0_values=software-type%3Atooling&amp;fulltext=Oracle%7E+JDK%7E+11%7E&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=14)
* [Dernière version de Git](https://git-scm.com/downloads). Si vous découvrez Git, voir [Installation de Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
* [Node.js 16.13.0 ou version ultérieure](https://nodejs.org/en/download/). Si vous découvrez Node.js pour la première fois, voir [Comment installer Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).
* [Maven 3.6 ou version ultérieure](https://maven.apache.org/download.cgi). Si vous découvrez Maven pour la première fois, voir [Installation d’Apache Maven](https://maven.apache.org/install.html).

## Configuration de l’environnement de développement {#headless-adaptive-forms-procedure-to-setup-development-environment}

Pour configurer un nouvel environnement de développement local et l’utiliser pour développer et tester des formulaires adaptatifs sans affichage :

1. [Configuration AEM SDK as a Cloud Service](#setup-author-instance).
1. [Ajout d’une archive AEM Forms (module complémentaire AEM Forms Cloud Service) au SDK AEM](#add-forms-archive).

<!--

1. (Optional) [Add Forms-specific users to your local Author instance](#configure-users-and-permissions).
1. (Optional) Install [Adaptive forms builder extension for Microsoft Visual Studio Code](#microsoft-visual-studio-code-extension-for-headless-adaptive-forms). 

-->

### 1. Configuration AEM SDK as a Cloud Service {#setup-author-instance}

AEM SDK as a Cloud Service (AEM SDK) fournit aux développeurs une expérience locale pour créer et tester des formulaires adaptatifs sans affichage. Vous pouvez utiliser le SDK as a Cloud Service AEM pour créer et prévisualiser des formulaires adaptatifs sans affichage, ce qui vous permet d’effectuer la plupart des validations liées au développement localement. Pour configurer une instance d’auteur locale :

1. [Télécharger](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?lang=fr) la plus récente [!DNL Adobe Experience Manager] SDK as a Cloud Service. Utilisez la colonne Date de publication pour trier et localiser facilement le dernier SDK.
Il est au format .zip. La version prise en charge est aem-sdk-2022.7.8085.20220725T140323Z-220700.zip et versions ultérieures.

   ![Téléchargement du SDK AEM Cloud Service à partir du portail de distribution de logiciels](assets/software-distribution.png)


1. Extrayez le fichier .zip téléchargé dans un répertoire de votre ordinateur local.
1. Créez un répertoire sur votre ordinateur local qui servira d’emplacement d’installation pour l’instance de création. Par exemple, `~/aem-sdk/author`.
1. Copiez le fichier .jar des fichiers du SDK extraits vers l’emplacement d’installation et renommez le fichier en `aem-author-p4502.jar`. La variable `p4502` string dans le nom du fichier spécifie le numéro de port à utiliser. Vous pouvez également spécifier un autre numéro de port.

   >[!NOTE]
   >
   > Ne double-cliquez pas sur le fichier .jar pour le démarrer. Cela se traduit par une [error](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html?lang=en#troubleshooting-double-click).

1. Ouvrez l’invite de commande :
   * Sous Windows, utilisez le **Exécuter en tant qu’administrateur** pour ouvrir l’invite de commande en mode élevé.
   * Sous Linux, veillez à ouvrir la fenêtre de terminal en tant qu’utilisateur root.

1. Accédez à l’emplacement d’installation contenant le fichier .jar copié, puis exécutez la commande suivante :

   `java -jar aem-author-p4502.jar -r prerelease`

   ![Téléchargement du SDK AEM Cloud Service à partir du portail de distribution de logiciels](assets/install-sdk.png)

   * La variable `-r prerelease` switch active les fonctionnalités disponibles uniquement dans les programmes de version préliminaire et de version limitée.
   * Vous pouvez utiliser `admin` comme nom d’utilisateur et mot de passe pour le développement local afin de réduire la charge cognitive.

   Une fois l’AEM lancée, la page de connexion s’ouvre dans un navigateur web. Vous pouvez également ouvrir la page de connexion de l’instance AEM SDK à l’adresse `http://localhost:<port>` dans votre navigateur web. Par exemple : [http://localhost:4502](http://localhost:4502).

1. Connectez-vous à votre instance de création Appuyez sur le bouton ![help](/help/assets/Help-icon.svg) , appuyez sur À propos de Adobe Experience Manager et assurez-vous que le numéro de version comprend le postfix PRERELEASE .

   ![help](/help/assets/prerelease.png)

Si vous ne voyez pas le correctif de version préliminaire, arrêtez le serveur, supprimez la variable `[AEM SDK installation]/crx-quickstart folder`, puis redémarrez le fichier AEM SDK .jar avec `-r prerelease` changer. Pour plus d’options, voir [Dépannage](/help/troubleshooting.md).

### 2. Ajout d’une archive AEM Forms (module complémentaire AEM Forms Cloud Service) au SDK AEM {#add-forms-archive}

L’archive de fonctionnalités as a Cloud Service d’AEM Forms (module complémentaire AEM Forms Cloud Service) fournit des outils pour créer des formulaires adaptatifs sans affichage dans un environnement de développement local. Pour installer l’archive de fonctionnalités :

1. Téléchargez et extrayez la dernière version [!DNL AEM Forms] archive de fonctionnalités (module complémentaire AEM Forms) depuis [Distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?fulltext=AEM*+Forms*+add*+on*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=20). Utilisez la colonne Date de publication pour trier et localiser facilement le dernier SDK. La version prise en charge est aem-forms-addon-2022.07.06.02-220600 et versions ultérieures.

1. Accédez au répertoire crx-quickstart/install. Si le dossier n’existe pas, créez-le.
1. Arrêtez votre instance AEM SDK. Vous pouvez arrêter la fenêtre d’invite de commande qui s’exécute AEM instance SDK pour arrêter AEM.
1. Copiez le [!DNL AEM Forms] archive des fonctionnalités de module complémentaire à partir d’un fichier, `aem-forms-addon-<version>.far`, extrait à l’étape 1 dans le dossier d’installation.
1. Utilisez la commande suivante pour redémarrer l’instance AEM SDK :

   `java -jar aem-author-p4502.jar -r prerelease`

<!-- 

### 3. (Optional) Configure users and permissions {#configure-users-and-permissions}

Create seperate user accounts for Form Developer, Form Practitioner, and end users. These account help you test Headless adaptive forms for various types of users. To create a user account and add roles to the account:

1. Login to your AEM SDK instance.
1. Go to Tools > Security > Users and tap Create. The Create New User wizard opens.
1. In the details tab, specify an ID and Password. All other fields are optional. It is recommended to provide name and an email address.
1. In the Groups tab, search and select user-groups for a user depending on their role. The table below lists all types of users and pre-defined groups for each type of forms users based on their role:
  
    | User Type | AEM Group |
    |---|---|
    | Form developer | [!DNL forms-users] (AEM Forms Users), [!DNL template-authors], [!DNL workflow-users], [!DNL workflow-editors], and [!DNL fdm-authors]  |
    | Customer Experience Lead or UX Designer| [!DNL forms-users], [!DNL template-authors]|
    | AEM administrator | [!DNL aem-administrators], [!DNL fd-administrators] |
    | End user| When a user must log in to view and submit an Adaptive Form, add such users to [!DNL forms-users] group. </br> When no user authentication is required to access Adaptive Forms, do not assign any group to such users.|

<!-- ### 4. (Optional) Install Visual Studio Code extension for Headless adaptive forms {#microsoft-visual-studio-code-extension-for-headless-adaptive-forms}

You can use any IDE for developing Headless adaptive forms. Adobe provides an extension for Microsoft&reg;reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms. The extension adds adaptive forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. To use the extension: 

1. Ensure [Microsoft Visual Studio Code 1.62.0 or later](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version) is installed. If you have an older version or no version installed, download the latest version from [Microsoft Website](https://code.visualstudio.com/docs/setup/setup-overview)
   >[!NOTE]
   >
   >
   > To use Visual Studio from command line on macOS, see [Launching from the command line](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).

1. Download the [Adaptive forms builder extension](/help/assets/adaptive-form-builder-0.12.0.vsix).

1. Navigate the directory containing the *adaptive-form-builder-[version].vsix* file.

1. Run the following command or see [Install from a VSIX](https://code.visualstudio.com/docs/editor/extension-marketplace#_install-from-a-vsix) article for detailed instructions to install a Visual Studio Code extension from a VSIX file:

    `code -–install-extension adaptive-form-builder-[version].vsix`

    </br> Replace the [version] with actual version of the extension. For example, `code -–install-extension adaptive-form-builder-0.12.0.vsix`

    </br> 

    ![Installing extension](/help/assets/install-extension.png)

<!-- ## Create and setup a react app

Adaptive forms renderer component is a react based component. It requires a react app to run and render a Headless adaptive form. To create and setup react app:

1. Open terminal in Visual Studio code and run the following command to create a react app and installs all related dependencies:

    ```shell
    npx create-react-app [react-app-name] --scripts-version 4.0.3 --template typescript
    ```

    Where [react-app-name] represents name of the project, script version is 4.0.3, and template of type typescript. For example, the following command creates a react app named *headless-forms-demo*.

    ```shell
    npx create-react-app headless-forms-demo --scripts-version 4.0.3 --template typescript
    ```

    It may take some time to create the react app and install all the dependencies. The command creates an empty react app with latest version of react and react-dom dependencies. It does not have any artifacts related to adaptive forms renderer component.

1. Adaptive forms renderer component is based on react spectrum and requires react 16.0.0 and react-dom 16.0.0. To install react 16.0.0 and related dependencies:
    1. Open the Visual Studio code terminal Window or command prompt.
    1. Navigate to the directory of react project.  
    1. Run the following command:

        ```shell
        npm install --save react@16.0.0 react-dom@16.14.0 -force
        ```

1. Run the following command to install adaptive forms renderer component related dependencies:

    ```shell
    npm i --save @aemforms/forms-super-component @aemforms/forms-react-core-components @aemforms/forms-super-component @adobe/react-spectrum @react/react-spectrum
    ```

<!-- 1. Install dependencies for adaptive forms renderer component. Packages for these dependencies are available in Adobe Artifactory. To authenticate with Adobe Artifactory and install dependencies for adaptive forms renderer component:

    1. Create environment variables ARTIFACTORY_USER and ARTIFACTORY_API_TOKEN. The ARTIFACTORY_USER stores Adobe LDAP username and ARTIFACTORY_API_TOKEN stores your [Adobe Artifactory token](https://wiki.corp.adobe.com/display/Artifactory/API+Keys)

    1. Run the following command to set NPM_TOKEN and NPM_EMAIL tokens:

        ```shell

        auth=$(curl -s -u${ARTIFACTORY_USER}:${ARTIFACTORY_API_TOKEN} https://artifactory.corp.adobe.com/artifactory/api/npm/auth)
        export NPM_TOKEN=$(echo "${auth}" | grep "_auth" | awk -F " " '{ print $3 }')
        export NPM_EMAIL=$(echo "${auth}" | grep "email" | awk -F " " '{ print $3 }')
        ```

        These tokens are required to communicated with Adobe Artifactory.

    1. Create a .npmrc file in the react project.

        ![.npmrc file](/help/assets/npmrc.png)

    1. Add the following code to the file:

        ```shell
        @aemforms:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-aem-release/
        @react:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-react-release/
        @quarry:registry=https://artifactory.corp.adobe.com/artifactory/api/npm/npm-adobe-release-local/
        //artifactory.corp.adobe.com/artifactory/api/npm/npm-adobe-release-loca/:_auth=${NPM_TOKEN}
        //artifactory.corp.adobe.com/artifactory/api/npm/npm-aem-release/:_auth=${NPM_TOKEN}
        //artifactory.corp.adobe.com/artifactory/api/npm/npm-react-release/:_auth=${NPM_TOKEN}
        _auth=${NPM_TOKEN}
        email=${NPM_EMAIL}
        always-auth=true
        ```

        It defines the antifactory repositories to use for Headless adaptive forms, react, and quarry related scope.
    1. Run the following command to install adaptive forms renderer component related dependencies:

    ```shell
    npm i --save @aemforms/crispr-react-bindings @aemforms/crispr-react-core-components @adobe/react-spectrum @react/react-spectrum
    ```
 
-->
Votre environnement local est prêt. Vous pouvez créer un formulaire adaptatif sans affichage.
