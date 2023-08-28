---
title: Architecture des formulaires adaptatifs sans affichage
description: Découvrez l’architecture d’AEM Forms Headless Adaptive Forms et comment elle peut vous aider à créer rapidement des formulaires pour diverses plateformes. Cet article fournit des informations sur le fonctionnement de Headless Adaptive Forms et sur la manière dont ils peuvent être intégrés à différentes applications afin de simplifier le processus de création de formulaires.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, formulaire adaptatif, architecture
hide: false
exl-id: ee7096d8-89e2-41e0-85e7-b26457df96fb
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%

---


# Fonctionnement du formulaire adaptatif sans affichage

Un formulaire adaptatif sans affichage est essentiellement une structure JSON (schéma) composée de champs de formulaire (zone de texte, choix et de nombreux autres champs) et de règles correspondantes (logique conditionnelle) pour ajouter un comportement interactif au formulaire. Vous pouvez utiliser des API REST dans votre application ou site web pour demander la structure JSON hébergée et effectuer le rendu natif de la structure JSON en tant que formulaire dans votre application ou site web. Un seul formulaire adaptatif sans en-tête peut servir plusieurs pages web et applications sans y apporter de modifications spécifiques aux applications ou aux sites web.

![Fonctionnement du formulaire adaptatif sans affichage](/help/assets/how-headless-adaprive-forms-work.png)

## Architecture {#architecture}

Une architecture type de formulaires adaptatifs sans affichage constitue un serveur Adobe Experience Manager Forms, des formulaires adaptatifs sans affichage hébergés sur le serveur Adobe Experience Manager Forms et vos applications frontales (site web, application mobile, applications JavaScript, applications de conversation, etc.) pour les rendus de formulaire spécifiques à un canal.

L’architecture type d’un déploiement de formulaires adaptatifs sans affichage ressemble à ce qui suit :

![Architecture](/help/assets/headless-af-architecture.png)

<!-- 

You can use the React renderer component shipped with Headless adaptive forms to render an Adaptive Form or build your own custom component to natively render a Headless Form in a website or an application or use any UI framework or programming language to build your own components to render your forms.

A typical Headless adaptive forms architecture constitutes an Adobe Experience Manager Server, JSON structure of forms, various frontend apps for channel-specific form renditions.

![Architecture](/help/assets/headless-af-architecture.png) -->

### Composant d’une implémentation de formulaires adaptatifs sans affichage

**Serveur Adobe Experience Manager**: en plus de servir d’hôte pour les formulaires adaptatifs sans affichage, Adobe Experience Manager fournit les fonctionnalités principales suivantes :

* API RESTful permettant de répertorier, récupérer, préremplir, valider, envoyer et suivre l’état d’envoi des formulaires sans en-tête.
* Éditeur visuel pour développer facilement un formulaire adaptatif sans affichage.
* Modèle de données Forms pour recevoir ou envoyer des données à des sources de données disparates.
* Moteur de workflow pour automatiser les tâches complexes.

**Formulaires adaptatifs sans affichage**: un formulaire adaptatif sans affichage est représenté sous la forme d’un fichier .json. La structure JSON définit les composants, contraintes et structure d’un formulaire.

**Applications front-end**: applications front-end telles que SPA (applications d’une seule page), applications mobiles, applications JavaScript, utilisent des formulaires adaptatifs sans affichage (la représentation de formulaire JSON) et effectuent le rendu du formulaire sur un client. Vous pouvez utiliser le composant de rendu React fourni avec les formulaires adaptatifs sans affichage pour effectuer le rendu d’un formulaire adaptatif ou créer votre propre composant personnalisé pour effectuer le rendu natif des formulaires adaptatifs sans affichage.

<!-- ### Understanding Headless adaptive forms definition -->



### Outils de développement

Dans un cycle de développement type, vous commencez par créer et héberger des formulaires adaptatifs sans affichage sur le serveur Adobe Experience Manager Forms. Dans la seconde étape, vous mappez les composants de l’interface utilisateur ou utilisez une bibliothèque de composants de l’interface utilisateur publique, comme l’interface utilisateur Google Matériau ou l’interface utilisateur Chakra, pour appliquer un style à vos formulaires. Lors de la dernière étape, vous récupérez et affichez des formulaires adaptatifs sans affichage dans votre application (site Web, application mobile, applications JavaScript, applications de conversation ou de nombreuses autres surfaces).

Les outils suivants vous aident à créer et à intégrer des formulaires adaptatifs sans affichage à vos applications :

**SDK Web Forms (Runtime côté client)**: le SDK Web de Forms est une bibliothèque JavaScript côté client. Il vous permet d’appliquer des validations côté client sur les champs de formulaire, de conserver l’état du formulaire et fournit des crochets pour connecter le formulaire à la couche d’interface utilisateur ou au composant de formulaire adaptatif rendu. Il permet aux clients de valider les contraintes appliquées aux différents champs d’un formulaire et crochets pour connecter la structure JSON du formulaire à la structure de l’interface utilisateur. Le SDK Web de Forms comporte les composants suivants :

* **Responsable des règles métier**: le processeur des règles de fonctionnement accepte la structure JSON des formulaires en tant qu’entrée, gère l’état des champs de formulaire, exécute les règles et les gestionnaires d’événements présents dans le fichier JSON.
* **Binder React**: fournit des points d’extension au-dessus du contrôleur pour ajouter un état aux composants de formulaire. Il est également utile pour préremplir un formulaire.
* **Bibliothèque de composants**: il fournit des composants React Spectrum et utilise des crochets dans le module React Binder pour ajouter un état à ces composants.

En plus de fournir les API pour valider les contraintes appliquées aux différents champs d’un formulaire, le SDK Web de Forms fournit des hooks pour connecter les formulaires adaptatifs sans affichage à la structure de l’interface utilisateur. Il fournit également des &#x200B; de rendu React pour les formulaires adaptatifs sans affichage afin de vous aider à intégrer un formulaire adaptatif sans affichage à votre application. Les composants suivants du SDK Web sont disponibles :

* **[@aemforms/af-response-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-response-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

Tous ces composants sont inclus dans AEM Archetype. Lorsque vous créez un projet AEM Archetype 37 ou version ultérieure pour les formulaires adaptatifs sans affichage, la dernière version des bibliothèques répertoriées ci-dessus est incluse dans le projet.

**Application lancée**: Adobe a également lancé une application pour vous aider à démarrer rapidement avec les formulaires adaptatifs sans affichage.

<!-- **View Library (UI Layer)**: A custom form application built in a front-end language. You can use react, Angular, Flutter, NPM, Vue.js, Ionic, BootStrap, or any other language to built front end. You can also use the Headless adaptive forms Super Component, provided out-of-the-box, inside a react application to render a Headless adaptive form. Headless adaptive forms super component makes use of OOTB react spectrum -based form components to render the Headless adaptive form. 

Core-Components: It enables use to render an Adaptive Form using JSON structure. It uses rule grammar to help create dynamic field interactions. The rule grammar is based on [JSON formula](http://github.com/adobe/json-formula/). You can develop your own renderer or embed the React based Adaptive Forms renderer, provided OOTB, in your front-end app to render the form. -->

**Storybook**: [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) offre un aperçu des différents composants des formulaires adaptatifs sans affichage. Il fournit également une liste de tous les composants pris en charge, leurs propriétés correspondantes et les contraintes.

**Extension Visual Studio Code**: [Extension Visual Studio Code](visual-studio-code-extension-for-headless-adaptive-forms.md) pour créer une structure JSON valide. Elle fournit la prise en charge et la validation d’IntelliSense pour la structure JSON des formulaires, ainsi que des fonctions courantes telles que l’ajout, la suppression ou le changement de nom des composants d’une structure JSON.

**Spécifications de la version 2.0 d’Adaptive Forms**: la spécification Adaptive Forms version 2.0 fournit des informations détaillées sur tous les composants, contraintes et méthodes disponibles pour définir les formulaires adaptatifs sans affichage. La spécification est disponible dans [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf) format.

**API HTTP et JavaScript**: [API HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) vous permettent de répertorier, récupérer, valider, envoyer et suivre l’état d’envoi des formulaires sans interface utilisateur. [API JS](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) vous aide à utiliser des formulaires adaptatifs sans affichage avec n’importe quelle structure d’interface utilisateur basée sur JavaScript.

**Formule JSON**: il s’agit d’une implémentation de la grammaire des expressions de formulaires qui vous aide à interroger la structure JSON et à créer des règles pour les formulaires adaptatifs sans affichage. La grammaire est un ensemble de fonctions et d’opérateurs de type feuille de calcul et [JMESPath](https://jmespath.org/) un langage de requête JSON. Vous pouvez utiliser la variable [playground](https://opensource.adobe.com/json-formula/dist/index.html) pour explorer la syntaxe et les fonctionnalités de la formule JSON.