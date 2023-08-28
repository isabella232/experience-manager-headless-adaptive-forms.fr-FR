---
title: AEM Aperçu des formulaires adaptatifs sans affichage
description: Présentation des AEM de formulaires adaptatifs sans affichage.
hide: true
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 3%

---


# Notes de mise à jour

Bienvenue dans la version des premiers adopteurs des formulaires adaptatifs sans affichage de Experience Manager. Lisez la suite pour obtenir des ressources et des instructions afin de commencer et tirer le meilleur parti de la version.

Vous pouvez utiliser des formulaires adaptatifs sans affichage Adobe Experience Manager pour créer des applications de formulaires à l’aide de structures d’interface utilisateur frontales telles que React, Angular, etc., et utiliser le SDK Web de Forms adaptatif pour des fonctionnalités telles que la gestion de l’état, la validation et les intégrations à d’autres points de contact.

La première version d’adoption vous permet d’utiliser des formulaires adaptatifs sans affichage dans une [environnement de développement local](setup-development-environment.md). Vous pouvez utiliser l’environnement de développement local pour créer et tester des formulaires adaptatifs sans affichage.

Les formulaires adaptatifs sans affichage reçoivent régulièrement des améliorations. Pour vous tenir au courant des dernières nouveautés, consultez régulièrement cette page. Cette page vous fournit des informations sur les accès anticipés, les dernières versions, les nouvelles fonctionnalités, les améliorations, les correctifs de bogues, les fonctionnalités obsolètes, les instructions spéciales et les plans futurs de modifications.

<!-- 

## July 2022 (v0.22.1)

### New features

* Introduced the `validateFormData` API. It validates all the components against the rules and constraints an returns the list of errors. The validation takes place on the server.
* Introduced the `FormLoad` event.
* Introduced the `importData` and `exportData`.
* You can now dynamically add or remove items, that expect unqiue values, from a repeatable panel. You can use the `minItems` and `maxitems` constraint to set limit of item.
* You can now use constraint to set maximum file upload size, accepted file types, minimum files, and maximum files to upload.

### Improvements and bug fixes

* The service was executing some event handlers twice. The issue is fixed.
* Fixing Data Generation with different values of dataRef, name and type.

<!-- ### React Renderer component -->

## Artefacts disponibles dans une version initiale d’adoption

Dans le parcours pour vous apporter des formulaires adaptatifs Adobe Experience Manager sans affichage, les artefacts suivants sont disponibles dans la version la plus récente de l’adoptant :

### SDK AEM FORMS AS A CLOUD SERVICE

SDK AEM Forms as a Cloud Service pour vous aider à créer, stocker et récupérer des formulaires adaptatifs sans affichage. Il permet également de fournir des services de préremplissage, de validation des règles côté serveur et d’envoi pour les formulaires adaptatifs sans affichage.

### SDK Web Forms

Le SDK Web de Forms fournit les API permettant de valider les contraintes appliquées aux différents champs d’un formulaire et les crochets pour connecter la structure JSON du formulaire à la structure de l’interface utilisateur. Il fournit également des &#x200B; de rendu React pour les formulaires adaptatifs sans affichage afin de vous aider à intégrer un formulaire adaptatif sans affichage à votre application. Les composants suivants du SDK Web sont disponibles :

* **[@aemforms/af-response-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-response-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

<!-- npm i --save @aemforms/af-react-components @aemforms/af-react-renderer @aemforms/af-core -->

#### Storybook

[Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) offre un aperçu des différents composants des formulaires adaptatifs sans affichage. Il fournit également une liste de tous les composants pris en charge, leurs propriétés correspondantes et les contraintes.

### Composant principal Forms

<!-- Forms components are the structural elements that constitute the content of the form being authored. These components provide various form fields and ability to customize those fields. -->

Les composants principaux sont un ensemble de composants WCM (Web Content Management) normalisés qui vous permettent d’accélérer le développement et de réduire les coûts de maintenance de vos formulaires. Le composant Conteneur Forms est un composant principal. Elle vous aide à incorporer et à générer une structure JSON de formulaire adaptatif sans affichage dans l’éditeur Forms adaptatif du SDK as a Cloud Service Forms.

### Spécifications de Forms adaptatif V2

La spécification de formulaires adaptatifs sans affichage fournit des informations détaillées sur tous les composants, contraintes et méthodes disponibles pour définir les formulaires adaptatifs sans affichage. La spécification est disponible dans [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf) format.

### API HTTP et JS

[API HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) vous permettent de répertorier, récupérer, valider, envoyer et suivre l’état d’envoi des formulaires sans interface utilisateur. [API JS](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) vous aide à utiliser des formulaires adaptatifs sans affichage avec n’importe quelle structure d’interface utilisateur basée sur JavaScript.

### Extension Visual Studio Code

[Extension Visual Studio Code](visual-studio-code-extension-for-headless-adaptive-forms.md) pour créer une structure JSON valide. Elle fournit la prise en charge et la validation d’IntelliSense pour la structure JSON des formulaires, ainsi que des fonctions courantes telles que l’ajout, la suppression ou le changement de nom des composants d’une structure JSON.

<!-- ## What's next

The following features would be available in upcoming releases:

* HTTP APIs to invoke a business logic.
* Server-side capabilities (Prefill, server-side validation, generating Document of Record (DoR), Submitting to a Form Data Model or using Form Data Models for creating rules, and more).
* Continuous improvements to specifications and Headless adaptive form runtime.
* Use  Adaptive Forms editor for easier management and authoring Headless adaptive forms.
-->