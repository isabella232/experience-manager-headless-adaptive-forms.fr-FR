---
title: Architecture des formulaires adaptatifs découplés
description: Découvrez l’architecture des formulaires adaptatifs découplés d’AEM Forms et commencez à créer rapidement des formulaires pour diverses plateformes. Cet article décrit le fonctionnement des formulaires adaptatifs découplés et leur intégration à différentes applications afin de simplifier le processus de création de formulaires.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: découplé, formulaire adaptatif, architecture
hide: false
exl-id: ee7096d8-89e2-41e0-85e7-b26457df96fb
source-git-commit: 48ba054d7ef3b4e27e0b4d6026dfc2475917723e
workflow-type: tm+mt
source-wordcount: '893'
ht-degree: 100%

---


# Fonctionnement des formulaires adaptatifs découplés

Un formulaire adaptatif découplé est essentiellement une structure JSON (schéma) composée de champs de formulaire (zone de texte, choix et de nombreux autres champs) et de règles correspondantes (logique conditionnelle) pour ajouter un comportement interactif au formulaire. Vous pouvez utiliser des API REST dans votre application ou site web pour demander la structure JSON hébergée et effectuer le rendu natif de la structure JSON en tant que formulaire dans votre application ou site web. Un seul formulaire adaptatif découplé peut alimenter plusieurs pages web et applications sans qu’il soit nécessaire d’y apporter des modifications spécifiques à l’application ou au site web.

![Fonctionnement des formulaires adaptatifs découplés](/help/assets/how-headless-adaprive-forms-work.png)

## Architecture {#architecture}

Une architecture type de formulaires adaptatifs découplés comprend un serveur Adobe Experience Manager Forms, des formulaires adaptatifs découplés hébergés sur le serveur Adobe Experience Manager Forms et vos applications front-end (site web, application mobile, applications JavaScript, applications conversationnelles, etc.) pour les rendus de formulaire spécifiques à un canal.

L’architecture type d’un déploiement de formulaires adaptatifs découplés ressemble à celle-ci :

![Architecture](/help/assets/headless-af-architecture.png)

<!-- 

You can use the React renderer component shipped with Headless adaptive forms to render an Adaptive Form or build your own custom component to natively render a Headless Form in a website or an application or use any UI framework or programming language to build your own components to render your forms.

A typical Headless adaptive forms architecture constitutes an Adobe Experience Manager Server, JSON structure of forms, various frontend apps for channel-specific form renditions.

![Architecture](/help/assets/headless-af-architecture.png) -->

### Composant d’une mise en œuvre des formulaires adaptatifs découplés

**Serveur Adobe Experience Manager** : en plus de servir d’hôte pour les formulaires adaptatifs découplés, Adobe Experience Manager fournit les fonctionnalités back-end suivantes :

* API RESTful permettant de répertorier, de récupérer, de préremplir, de valider, d’envoyer et de suivre le statut d’envoi des formulaires découplés.
* Éditeur visuel pour développer facilement un formulaire adaptatif découplé.
* Modèle de données de formulaire pour recevoir ou envoyer des données à des sources de données disparates.
* Moteur de workflow pour automatiser les tâches complexes.

**Formulaires adaptatifs découplés** : un formulaire adaptatif découplé est représenté sous la forme d’un fichier .json. La structure JSON définit les composants, les contraintes et la structure d’un formulaire.

**Applications front-end** : les applications front-end telles que les applications monopages, les applications mobiles et les applications JavaScript utilisent des formulaires adaptatifs découplés (la représentation de formulaire JSON) et effectuent le rendu du formulaire sur un client. Vous pouvez utiliser le composant de rendu React fourni avec les formulaires adaptatifs découplés pour effectuer le rendu d’un formulaire adaptatif ou créer votre propre composant personnalisé pour effectuer le rendu natif des formulaires adaptatifs découplés.

<!-- ### Understanding Headless adaptive forms definition -->



### Outils de développement

Au cours d’un cycle de développement type, vous commencez par créer et héberger des formulaires adaptatifs découplés sur le serveur Adobe Experience Manager Forms. Ensuite, vous mappez les composants de l’interface utilisateur ou utilisez une bibliothèque de composants d’interface utilisateur publique, comme Material UI de Google ou Chakra UI, pour appliquer un style à vos formulaires. Lors de la dernière étape, vous récupérez et affichez des formulaires adaptatifs découplés dans votre application (site web, application mobile, applications JavaScript, applications conversationnelles ou de nombreuses autres surfaces).

Les outils suivants permettent de créer et d’intégrer des formulaires adaptatifs découplés à vos applications :

**SDK Web Forms (Runtime côté client)** : le SDK Web Forms est une bibliothèque JavaScript côté client. Le SDK vous permet d’appliquer des validations côté client sur les champs de formulaire et de conserver le statut du formulaire. Il fournit en outre des hooks pour connecter le formulaire à la couche d’interface utilisateur ou au composant de rendu des formulaires adaptatifs. Il permet aux clients et clientes de valider les contraintes appliquées à différents champs d’un formulaire et fournit des hooks pour connecter la structure JSON du formulaire au framework d’interface utilisateur. Le SDK Web Forms comprend les composants suivants :

* **Processeur des règles commerciales**: le processeur des règles de fonctionnement accepte la structure JSON des formulaires en tant qu’entrée, gère le statut des champs de formulaire, exécute les règles et les gestionnaires d’événements présents dans le fichier JSON.
* **React Binder** : fournit des hooks au-dessus du contrôleur pour ajouter un statut aux composants de formulaire. Ce composant est également utile pour préremplir un formulaire.
* **Bibliothèque de composants** : elle fournit des composants React Spectrum et utilise des hooks dans le module React Binder pour ajouter un statut à ces composants.

En plus de fournir les API pour valider les contraintes appliquées aux différents champs d’un formulaire, le SDK Web Forms fournit des hooks pour connecter les formulaires adaptatifs découplés au framework de l’interface utilisateur. Il fournit également React Renderer pour les formulaires adaptatifs découplés pour vous permettre d’intégrer un formulaire adaptatif découplé à votre application. Les composants suivants du SDK web sont disponibles :

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

Tous ces composants sont inclus dans l’archétype AEM. Lorsque vous créez un projet d’archétype AEM 37 ou version ultérieure pour les formulaires adaptatifs découplés, la dernière version des bibliothèques répertoriées ci-dessus est incluse dans le projet.

**Application commencée** : Adobe a également publié une application commencée pour vous aider à démarrer rapidement avec les formulaires adaptatifs découplés.

<!-- **View Library (UI Layer)**: A custom form application built in a front-end language. You can use react, Angular, Flutter, NPM, Vue.js, Ionic, BootStrap, or any other language to built front end. You can also use the Headless adaptive forms Super Component, provided out-of-the-box, inside a react application to render a Headless adaptive form. Headless adaptive forms super component makes use of OOTB react spectrum -based form components to render the Headless adaptive form. 

Core-Components: It enables use to render an Adaptive Form using JSON structure. It uses rule grammar to help create dynamic field interactions. The rule grammar is based on [JSON formula](http://github.com/adobe/json-formula/). You can develop your own renderer or embed the React based Adaptive Forms renderer, provided OOTB, in your front-end app to render the form. -->

**Storybook** : le [storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) donne un aperçu des différents composants des formulaires adaptatifs découplés. Il fournit également la liste de tous les composants pris en charge, leurs propriétés et contraintes correspondantes.

**Extension Visual Studio Code** : l’[extension Visual Studio Code](visual-studio-code-extension-for-headless-adaptive-forms.md) permet de créer une structure JSON valide. Elle assure la prise en charge et la validation IntelliSense pour la structure JSON des formulaires et fournit des fonctions courantes telles que l’ajout, la suppression ou l’attribution d’un nouveau nom aux composants d’une structure JSON.

**Spécifications des formulaires adaptatifs version 2.0** : fournit des informations détaillées sur les composants, contraintes et méthodes disponibles pour définir les formulaires adaptatifs découplés. La spécification est disponible au format [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf).

**API HTTP et JavaScript** : les [API HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) vous permettent de répertorier, de récupérer, de valider, d’envoyer et de suivre le statut d’envoi des formulaires découplés. Les [JS APIs](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) vous aident à utiliser des formulaires adaptatifs découplés avec n’importe quel framework d’interface utilisateur basé sur JavaScript.

**Formule JSON** : il s’agit d’une mise en œuvre de la grammaire des expressions de formulaires qui vous aide à interroger la structure JSON et à créer des règles pour les formulaires adaptatifs découplés La grammaire est un mashup de fonctions et d’opérateurs de type feuille de calcul et [JMESPath](https://jmespath.org/), un langage de requête JSON. Vous pouvez utiliser le [playground](https://opensource.adobe.com/json-formula/dist/index.html) pour découvrir la syntaxe et les fonctionnalités des formules JSON.