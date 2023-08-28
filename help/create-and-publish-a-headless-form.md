---
title: Création et publication d’un formulaire sans affichage avec Adobe Experience Manager Adaptive Forms | Guide pas à pas
description: Découvrez comment créer et publier un formulaire sans interface utilisateur graphique à l’aide de Adobe Experience Manager des formulaires adaptatifs dans ce guide détaillé. Découvrez les avantages d’un fonctionnement sans interface et de simplifier votre processus de création de formulaire dès aujourd’hui. Commencez à créer des formulaires dynamiques et réactifs qui fonctionnent de manière transparente sur tous les appareils avec Adobe Experience Manager Headless Adaptive Forms.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 1%

---



# Création et prévisualisation d’un formulaire sans affichage à l’aide d’une application React {#introduction}

Le kit de démarrage vous permet de commencer rapidement à utiliser une application React. Vous êtes libre de développer et d’utiliser des formulaires adaptatifs sans affichage dans un Angular, Vanilla JS et d’autres environnements de développement de votre choix.

Commencer avec des formulaires adaptatifs sans affichage est assez facile et rapide. Cloner le projet React prêt à l’emploi, installer les dépendances et exécuter le projet. Un formulaire adaptatif sans affichage est intégré à une application React opérationnelle. Vous pouvez utiliser l’exemple de projet de réaction pour créer et tester des formulaires adaptatifs sans affichage avant de les déployer dans un environnement de production.

Commençons par :

>[!NOTE]
>
>
> Ce guide de prise en main utilise une application React. Vous êtes libre d’utiliser la technologie ou le langage de programmation de votre choix pour utiliser des formulaires adaptatifs sans affichage.

## Avant de commencer {#pre-requisites}

Pour créer et exécuter une application React, les éléments suivants doivent être installés sur votre ordinateur :

* Installez le [dernière version de Git](https://git-scm.com/downloads). Si vous découvrez Git, voir [Installation de Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* Installer [Node.js 16.13.0 ou version ultérieure](https://nodejs.org/en/download/). Si vous découvrez Node.js pour la première fois, voir [Comment installer Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).

## Prise en main

Une fois que vous avez satisfait aux exigences, procédez comme suit pour commencer :

1. [Configuration d’un kit de démarrage de formulaires adaptatifs sans affichage](#setup)

1. [Aperçu du formulaire adaptatif sans affichage inclus dans le kit de démarrage](#preview)

1. [Créer et générer votre propre formulaire adaptatif sans affichage](#custom)



## 1. Configuration du kit de démarrage de formulaires adaptatifs sans affichage {#install}

Le kit de démarrage est une application React avec un exemple de formulaire adaptatif sans affichage et les bibliothèques correspondantes. Utilisez le kit pour développer et tester vos formulaires adaptatifs sans affichage et les composants React correspondants. Exécutez les commandes suivantes pour configurer le kit de démarrage de formulaires adaptatifs sans affichage :

1. Ouvrez une invite de commande et exécutez la commande suivante :

   ```shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   La commande crée un répertoire appelé **response-starter-kit-aem-headless-forms** dans votre emplacement actuel et y clone l’application de démarrage React des formulaires adaptatifs sans affichage. Outre les configurations et la liste des dépendances requises pour le rendu du formulaire, le répertoire comprend le contenu important suivant :

   * **Exemple de formulaire**: le kit de démarrage comprend un exemple de formulaire de demande de prêt. Pour afficher le formulaire (définition de formulaire) inclus dans l’application, ouvrez le `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` fichier .
   * **Exemples de composants de réaction**: le kit de démarrage comprend des exemples de composants de réaction pour le texte enrichi et le curseur. Ce guide vous aide à créer vos propres composants personnalisés à l’aide de ces composants de texte enrichi et de curseur.
   * **Mappings.ts**: le fichier mappings.ts vous aide à mapper des composants personnalisés à des champs de formulaire. Par exemple, mappez un champ d’exécution numérique pas à pas avec le composant d’évaluation.
   * **Configurations d’environnement**: les configurations d’environnement vous permettent de choisir de générer un formulaire inclus dans le kit de démarrage ou de récupérer un formulaire à partir d’un serveur AEM Forms.

   ![](/help/assets/getting-started-starter-kit-content.png)

   >[!NOTE]
   >
   > 
   > Les exemples de documents sont basés sur VSCode. Vous êtes libre d’utiliser n’importe quel éditeur de code de texte brut.


1. Accédez au **response-starter-kit-aem-headless-forms** et exécutez la commande suivante pour installer les dépendances :

   ```shell
   npm install
   ```

   La commande télécharge tous les packages et bibliothèques nécessaires pour exécuter et créer l’application, tels que les bibliothèques de formulaires adaptatifs sans affichage (@aemforms/af-response-renderer, @aemforms/af-response-components, @adobe/response-spectre), exécute les validations et conserve les données pour les instances du formulaire.

   ![](/help/assets/install-react-app-starter-kit.png)


## 2. Aperçu du formulaire adaptatif sans affichage {#preview}

Après avoir configuré le kit de démarrage, vous pouvez prévisualiser l’exemple de formulaire adaptatif sans affichage, le remplacer par votre propre formulaire personnalisé. Vous pouvez également configurer le kit de démarrage pour récupérer un formulaire à partir d’un serveur AEM Forms. Pour prévisualiser le formulaire

1. Renommez la variable `env_template` vers `.env` fichier . Assurez-vous également que l’option USE_LOCAL_JSON est définie sur true.

   ![](/help/assets/rename-env-file.png)

   <!-- The options in the .env file help you configure source of the forms definantion (.JSON):
    *  To source forms definantion (.JSON) from an AEM Server, set USE_LOCAL_JSON option to false, use the AEM_URL option to specify URL  of your AEM Server, and set the AEM_FORM_PATH option to path of your adaptive form.
    *  To source forms definantion (.JSON) form-model.json file included in the starter-kit, set USE_LOCAL_JSON option to false. -->

1. Utilisez la commande suivante pour exécuter l’application :

   ```shell
     npm start
   ```


   Cette commande démarre un serveur de développement local et ouvre l’exemple de formulaire adaptatif sans affichage, inclus dans l’application de démarrage, dans votre navigateur web par défaut.

   ![Exemple de formulaire sans affichage](assets/sample-headless-adaptive-form.png)

   Voila ! Vous êtes configuré pour commencer à développer un formulaire adaptatif sans affichage personnalisé.

   <!--  As you know, in a headless form the form data and logic are separate from the presentation layer and can be used by any client that can make HTTP requests, such as a mobile app, a static site, or a different web application. The form is often managed and stored on a server, which serves as the backend for the form. The client sends requests to the server to retrieve the form, submit data, and receive updated form data. This allows for greater flexibility and integration with different technologies. You can store and retrive a Headless adaptive form on an AEM Server  -->

## 3. Créez et générez votre propre formulaire adaptatif sans affichage{#custom}

Un formulaire adaptatif sans affichage représente le formulaire et ses composants, tels que les champs et les boutons, au format JSON (JavaScript Object Notation). L’avantage du format JSON est qu’il peut être facilement analysé et utilisé par divers langages de programmation, ce qui en fait un moyen pratique d’échanger des données de formulaire entre les systèmes. Pour afficher l’exemple de formulaire adaptatif sans affichage fourni avec l’application, ouvrez le `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` fichier .

Créez un formulaire de contact avec quatre champs : &quot;Nom&quot;, &quot;Email&quot;, &quot;Numéro de contact&quot; et &quot;Message&quot;. Les champs sont définis comme des objets (éléments) au sein du JSON, chaque objet (élément) ayant des propriétés telles que le type, l’étiquette, le nom et les propriétés requises. Le formulaire comporte également un bouton de type &quot;submit&quot;. Voici JSON pour le formulaire.


```JSON
{
  "afModelDefinition": {
    "adaptiveform": "0.10.0",
    "items": [
      {
        "fieldType": "text-input",
        "label": {
          "value": "Name"
        },
        "name": "name"
      },
      {
        "fieldType": "text-input",
        "format": "email",
        "label": {
          "value": "Email"
        },
        "name": "email"
      },
      {
        "fieldType": "text-input",
        "format": "phone",
        "pattern": "[0-9]{10}",
        "label": {
          "value": "Contact Number"
        },
        "name": "Phone"
      },
      {
        "fieldType": "multiline-input",
        "label": {
          "value":"Message"
        },
        "name": "message"
      },
      {
        "fieldType": "button",
        "label":{
          "value": "Submit"
        },
        "name":"submit",
        "events":{
          "click": "submitForm()"
        }
      }
    ],
    "action": "https://eozrmb1rwsmofct.m.pipedream.net",
    "description": "Contact Us",
    "title": "Contact Us",
    "metadata": {
      "grammar": "json-formula-1.0.0",
      "version": "1.0.0"
    }
  }
}
```

>[!NOTE]
>
> * L’attribut &quot;afModelDefinition&quot; n’est nécessaire que pour les applications React et ne fait pas partie de la définition du formulaire.
> * Vous pouvez concevoir le formulaire JSON à la main ou utiliser le [AEM éditeur de formulaires adaptatifs (éditeur WYSIWYG de formulaires adaptatifs)](create-a-headless-adaptive-form.md) pour créer et diffuser le formulaire JSON. Dans un environnement de production, vous utilisez AEM Forms pour diffuser le formulaire JSON, et vous en apprendrez davantage ultérieurement.
> * Le tutoriel utilise https://pipedream.com/ pour tester les envois de formulaire. Vous utilisez vos propres points de terminaison ou tiers approuvés par votre entreprise pour recevoir les données d’un formulaire adaptatif sans affichage.


Pour effectuer le rendu du formulaire, remplacez l’exemple de formulaire adaptatif sans affichage JSON `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` avec le fichier JSON ci-dessus, enregistrez le fichier et attendez que le kit de démarrage compile et actualise le formulaire.

![Remplacement de l’exemple de formulaire adaptatif sans affichage JSON `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` avec le formulaire adaptatif JSON personnalisé sans affichage](assets/render-custom-headless-adaptive-form.png)

<!-- Your form is ready. Let's add some validations and make "Name", "Email", and "Message" fields mandatory. -->

Vous avez réussi à rendre le formulaire adaptatif sans affichage.


## Bonus

Définissons le titre de la page web hébergeant le formulaire sur `Contact Us | WKND Adventures and Travel`. Pour modifier le titre, ouvrez le _react-starter-kit-aem-headless-forms/public/index.html_ pour modifier et définir le titre.

![](assets/contact-us-headless-adaptive-forms-updated-title.png)


## Étape suivante

Par défaut, le kit de démarrage utilise [Le spectre de l&#39;Adobe](https://spectrum.adobe.com/) composants pour générer le formulaire. Vous pouvez utiliser pour créer et utiliser vos propres composants ou composants tiers. Par exemple, à l’aide de l’interface utilisateur Google Matériau ou de l’interface utilisateur Chakra.

Allons-y. [Utilisation de l’interface utilisateur de Google Matériau](use-google-material-ui-react-components-to-render-a-headless-form.md) pour générer notre formulaire de contact.




