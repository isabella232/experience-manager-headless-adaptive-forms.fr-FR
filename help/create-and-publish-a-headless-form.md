---
title: Créer et publier un formulaire découplé avec les fomulaires adaptatifs Adobe Experience Manager | Guide pas à pas
description: Découvrez comment créer et publier un formulaire découplé à l’aide des formulaires adaptatifs Adobe Experience Manager dans ce guide pas à pas. Découvrez les avantages du mode découplé et simplifiez votre processus de création de formulaire dès aujourd’hui. Commencez à créer des formulaires dynamiques et réactifs, qui fonctionnent de manière transparente sur tous les appareils, grâce aux formulaires adaptatifs découplés Adobe Experience Manager.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: ht
source-wordcount: '1004'
ht-degree: 100%

---



# Créer et prévisualiser un formulaire découplé à l’aide d’une application React {#introduction}

Le kit de démarrage vous permet de commencer rapidement à l’aide d’une application React. Vous êtes libre de développer et d’utiliser des formulaires adaptatifs découplés dans un environnement de développement Angular, Vanilla JS ou autre de votre choix.

La création de formulaires adaptatifs découplés est simple et rapide. Clonez le projet React prêt à l’emploi, installez les dépendances et exécutez le projet. Vous disposez d’un formulaire adaptatif découplé intégré à une application React opérationnelle. Vous pouvez utiliser l’exemple de projet React pour créer et tester des formulaires adaptatifs découplés avant de les déployer dans un environnement de production.

C’est parti !

>[!NOTE]
>
>
> Ce guide de prise en main utilise une application React. Vous êtes libre d’utiliser la technologie ou le langage de programmation de votre choix dans le cadre des formulaires adaptatifs découplés.

## Avant de commencer {#pre-requisites}

Pour créer et exécuter une application React, les éléments suivants doivent être installés sur votre ordinateur :

* Installez la [dernière version de Git](https://git-scm.com/downloads). Si vous découvrez Git, consultez l’article [Installer Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* Installez [Node.js 16.13.0 ou version ultérieure](https://nodejs.org/en/download/). Si vous découvrez Node.js pour la première fois, consultez [Comment installer Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).

## Prise en main

Une fois les conditions remplies, procédez comme suit pour commencer :

1. [Configurez le kit de démarrage de formulaires adaptatifs découplés.](#setup)

1. [Prévisualisez le formulaire adaptatif découplé inclus dans le kit de démarrage.](#preview)

1. [Créez et générez votre propre formulaire adaptatif découplé.](#custom)



## 1. Configurer le kit de démarrage de formulaires adaptatifs découplés {#install}

Le kit de démarrage est une application React comprenant un exemple de formulaire adaptatif découplé et les bibliothèques correspondantes. Utilisez le kit pour développer et tester vos formulaires adaptatifs découplés et les composants React correspondants. Exécutez les commandes suivantes pour configurer le kit de démarrage de formulaires adaptatifs découplés :

1. Ouvrez une invite de commandes et exécutez la commande suivante :

   ```shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   La commande crée le répertoire **response-starter-kit-aem-headless-forms** dans votre emplacement actuel et y clone l’application de démarrage React des formulaires adaptatifs découplés. Outre les configurations et la liste des dépendances requises pour le rendu du formulaire, le répertoire comprend le contenu important suivant :

   * **Exemple de formulaire** : le kit de démarrage comprend un exemple de formulaire de demande de prêt. Pour afficher le formulaire (définition de formulaire) inclus dans l’application, ouvrez le fichier `/react-starter-kit-aem-headless-forms/form-definations/form-model.json`.
   * **Exemples de composants React** : le kit de démarrage comprend des exemples de composants React pour le texte enrichi et le curseur. Ce guide vous aide à créer vos propres composants personnalisés à l’aide de ces composants de texte enrichi et de curseur.
   * **Mappings.ts** : le fichier mappings.ts vous aide à mapper des composants personnalisés à des champs de formulaire. Par exemple, mappez un champ de défilement numérique avec le composant d’évaluation.
   * **Configurations d’environnement** : les configurations d’environnement vous permettent de rendre un formulaire inclus dans le kit de démarrage ou de récupérer un formulaire à partir d’un serveur AEM Forms.

   ![](/help/assets/getting-started-starter-kit-content.png)

   >[!NOTE]
   >
   > 
   > Les exemples de documents sont basés sur VSCode. Vous êtes libre d’utiliser n’importe quel éditeur de code de texte brut.


1. Accédez au répertoire **response-starter-kit-aem-headless-forms** et exécutez la commande suivante pour installer les dépendances :

   ```shell
   npm install
   ```

   La commande télécharge tous les packages et bibliothèques nécessaires pour exécuter et créer l’application, tels que les bibliothèques de formulaires adaptatifs découplés
l (@aemforms/af-react-renderer, @aemforms/af-react-components, @adobe/react-spectrum), exécute les validations et conserve les données pour les instances du formulaire.

   ![](/help/assets/install-react-app-starter-kit.png)


## 2. Prévisualiser le formulaire adaptatif découplé {#preview}

Une fois que vous avez configuré le kit de démarrage, vous pouvez prévisualiser l’exemple de formulaire adaptatif découplé et le remplacer par votre propre formulaire personnalisé. Vous pouvez également configurer le kit de démarrage pour récupérer un formulaire à partir d’un serveur AEM Forms. Pour prévisualiser le formulaire

1. Renommez le fichier `env_template` en fichier `.env`. Assurez-vous également que l’option USE_LOCAL_JSON est définie sur « true ».

   ![](/help/assets/rename-env-file.png)

   <!-- The options in the .env file help you configure source of the forms definantion (.JSON):
    *  To source forms definantion (.JSON) from an AEM Server, set USE_LOCAL_JSON option to false, use the AEM_URL option to specify URL  of your AEM Server, and set the AEM_FORM_PATH option to path of your adaptive form.
    *  To source forms definantion (.JSON) form-model.json file included in the starter-kit, set USE_LOCAL_JSON option to false. -->

1. Utilisez la commande suivante pour exécuter l’application :

   ```shell
     npm start
   ```


   Cette commande démarre un serveur de développement local et ouvre l’exemple de formulaire adaptatif découplé, inclus dans l’application de démarrage, dans votre navigateur web par défaut.

   ![Exemple de formulaire découplé](assets/sample-headless-adaptive-form.png)

   Le tour est joué ! Vous êtes prêt à commencer à développer un formulaire adaptatif découplé personnalisé.

   <!--  As you know, in a headless form the form data and logic are separate from the presentation layer and can be used by any client that can make HTTP requests, such as a mobile app, a static site, or a different web application. The form is often managed and stored on a server, which serves as the backend for the form. The client sends requests to the server to retrieve the form, submit data, and receive updated form data. This allows for greater flexibility and integration with different technologies. You can store and retrive a Headless adaptive form on an AEM Server  -->

## 3. Créer et générer votre propre formulaire adaptatif découplé{#custom}

Un formulaire adaptatif découplé représente le formulaire et ses composants, tels que les champs et les boutons, au format JSON (JavaScript Object Notation). L’avantage du format JSON est qu’il peut être facilement analysé et utilisé par divers langages de programmation, ce qui en fait un moyen pratique d’échanger des données de formulaire entre systèmes. Pour afficher l’exemple de formulaire adaptatif découplé fourni avec l’application, ouvrez le fichier `/react-starter-kit-aem-headless-forms/form-definations/form-model.json`.

Créez un formulaire de contact comportant quatre champs : Nom, E-mail, N° de contact et Message. Les champs sont définis comme des objets (éléments) au sein de JSON, chaque objet (élément) ayant des propriétés telles que le type, le libellé, le nom et l’exigence. Le formulaire comporte également un bouton de type « envoi ». Voici le code JSON du formulaire.


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
> * L’attribut « afModelDefinition » n’est nécessaire que pour les applications React et ne fait pas partie de la définition du formulaire.
> * Vous pouvez concevoir manuellement le formulaire JSON ou utiliser l’[éditeur de formulaires adaptatifs AEM (éditeur WYSIWYG de formulaires adaptatifs)](create-a-headless-adaptive-form.md) pour créer et diffuser le formulaire JSON. Dans un environnement de production, AEM Forms se charge de la diffusion du formulaire JSON. Nous y reviendrons plus loin dans cet article.
> * Le tutoriel utilise https://pipedream.com/ pour tester les envois de formulaire. Vous utilisez vos propres points d’entrée ou tiers approuvés par votre organisation pour recevoir les données d’un formulaire adaptatif découplé.


Pour effectuer le rendu du formulaire, remplacez l’exemple de formulaire adaptatif découplé JSON `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` par le fichier JSON ci-dessus, enregistrez le fichier et attendez que le kit de démarrage compile et actualise le formulaire.

![Remplacer l’exemple de formulaire adaptatif découplé JSON `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` par le formulaire adaptatif JSON personnalisé découplé](assets/render-custom-headless-adaptive-form.png).

<!-- Your form is ready. Let's add some validations and make "Name", "Email", and "Message" fields mandatory. -->

Vous avez réussi à effectuer le rendu du formulaire adaptatif découplé.


## Bonus

Définissons le titre de la page web hébergeant le formulaire sur `Contact Us | WKND Adventures and Travel`. Pour modifier le titre, ouvrez le fichier _react-starter-kit-aem-headless-forms/public/index.html_ pour modifier et définir le titre.

![](assets/contact-us-headless-adaptive-forms-updated-title.png)


## Étape suivante

Par défaut, le kit de démarrage utilise les composants [Spectrum d’Adobe](https://spectrum.adobe.com/) pour générer le formulaire. Vous pouvez pour créer et utiliser vos propres composants ou des composants tiers. Par exemple, à l’aide de Material UI de Google ou de Chakra UI.

Nous allons [utiliser Material UI de Google](use-google-material-ui-react-components-to-render-a-headless-form.md) pour générer le formulaire de contact.




