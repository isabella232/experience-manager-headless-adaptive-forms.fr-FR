---
title: Questions fréquemment posées
description: Questions fréquemment posées
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, formulaire adaptatif, FAQ
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 2%

---

# Questions fréquentes {#headless-adaptive-forms-faq}

## Dois-je savoir à React.js comment utiliser des formulaires adaptatifs sans affichage ?

Vous pouvez utiliser n’importe quelle structure, bibliothèque ou langue pour générer des formulaires adaptatifs sans affichage et utiliser nos API REST pour valider et envoyer les formulaires. La bibliothèque AF-core, fournie prête à l’emploi, est indépendante du framework. Les bibliothèques React-Render et React-componet, fournies prêtes à l’emploi, sont à votre disposition. Vous pouvez développer vos propres composants et ne vous y limitez pas.

<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## Ai-je besoin de l’environnement de test as a Cloud Service Forms pour utiliser des formulaires adaptatifs sans affichage ?

Vous pouvez utiliser l’application de démarrage pour commencer à développer et à mettre en forme vos formulaires adaptatifs sans affichage. Vous avez besoin d’Forms as a Cloud Service pour héberger et diffuser des formulaires adaptatifs sans affichage ainsi que des fonctionnalités de formulaires d’arrière-plan.

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## Où obtenir un aperçu d’un formulaire adaptatif sans affichage ? {#storybook-example}

Vous pouvez utiliser l’application de démarrage pour afficher et prévisualiser un formulaire adaptatif sans affichage personnalisé. Vous pouvez également modifier une [storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) exemple pour prévisualiser un formulaire adaptatif sans affichage.

![](/help/assets/storybook-example.png)

## Est-il possible d’utiliser des formulaires adaptatifs sans affichage avec des structures personnalisées ?

Les formulaires adaptatifs sans affichage sont basés sur [spécification standard](/help/assets/Headless-Adaptive-Form-Specification.pdf). Vous pouvez étendre la spécification pour l’utiliser pour créer des composants personnalisés. Par exemple, des composants pour l’interface utilisateur de Chakra, Vue.js, etc.

## Les formulaires adaptatifs sans affichage prennent-ils en charge les champs en cascade ?

Dans les champs en cascade, le contenu du second champ dépend du contenu choisi dans le premier champ. La variable [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour—options&amp;args=formJson.items[0].fieldType:drop;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down) fournit un exemple de champs en cascade.

## Les formulaires adaptatifs sans affichage permettent-ils de préremplir des formulaires avec des données personnalisées ?

Les formulaires adaptatifs sans affichage permettent de préremplir des formulaires avec des données personnalisées. La variable [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data) fournit un exemple de préremplissage d’un formulaire adaptatif sans affichage.

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## Puis-je utiliser des formulaires adaptatifs sans affichage avec des SPA d’Angular ?

Vous pouvez utiliser le SDK Web pour intégrer des formulaires adaptatifs sans affichage à des SPA d’Angular. Elle est indépendante de tout cadre. Vous pouvez utiliser le SDK React comme référence.

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## Existe-t-il un module externe permettant de faciliter le développement pour les AF sans affichage ?

Oui, une extension est disponible pour Microsoft Visual Studio Code. Il offre un moyen pratique de créer manuellement les formulaires adaptatifs sans affichage JSON.

## Un formulaire adaptatif sans affichage peut-il se connecter à un système de gestion de la relation client pour lire ou écrire des données ?

Vous pouvez utiliser Microsoft Dynamics et Salesforce pour envoyer ou préremplir un formulaire adaptatif sans affichage. Outre les formulaires adaptatifs sans affichage, les formulaires adaptatifs prennent en charge l’envoi ou le préremplissage à l’aide de points de fin REST, de courriers électroniques et d’actions d’envoi personnalisées.
