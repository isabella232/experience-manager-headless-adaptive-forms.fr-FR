---
title: Prise en main d’un Forms adaptatif sans affichage
description: Prise en main d’un Forms adaptatif sans affichage
keywords: sans tête, formulaire adaptatif, tutoriel
hide: true
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 3%

---


# Prise en main d’un Forms adaptatif sans affichage

Ce tutoriel vous fournit une structure de bout en bout pour créer un formulaire adaptatif sans affichage. Le tutoriel est organisé en cas d’utilisation et en plusieurs guides. Chaque guide vous aide à apprendre et à ajouter de nouvelles fonctionnalités au formulaire adaptatif sans affichage créé dans ce tutoriel. Vous disposez d’un formulaire adaptatif sans affichage opérationnel après chaque guide. À la fin de ce didacticiel, vous serez capable de :

* Création d’un formulaire adaptatif sans affichage
* Ajout de règles de fonctionnement à votre formulaire
* Utilisation de l’interface utilisateur matérielle de Google pour appliquer un style au formulaire
* Préremplir le formulaire 
* Incorporer votre formulaire à une page web

Vous allez également créer une compréhension de l’architecture, des artefacts disponibles et de la structure JSON des formulaires adaptatifs sans affichage.

**Le parcours commence par l’apprentissage du cas pratique.**:

Raya Tan, membre du département des affaires étrangères d&#39;un pays connu pour sa beauté naturelle et son économie touristique florissante, supervise la distribution des formulaires de visa aux touristes. Ces formulaires sont disponibles sur le site web du département, sur les applications mobiles natives et au format PDF, avec plusieurs options linguistiques pour le choix des touristes. Cependant, la gestion et la mise à l’échelle de ces formulaires sur différentes plateformes et technologies peut s’avérer difficile.

Afin d’améliorer l’efficacité et la flexibilité de leur processus de demande de visa, le département des affaires étrangères a décidé d’adopter une approche des formulaires adaptatifs sans affichage . Cette architecture découplée sépare le front-end du serveur principal, ce qui permet une plus grande personnalisation et évolutivité. Le service prévoit d’utiliser les composants React de l’interface utilisateur Matériel de Google pour améliorer l’expérience utilisateur des formulaires, tout en utilisant des fonctionnalités principales telles que les signatures numériques, l’intégration des données, la gestion des processus d’entreprise, les documents d’enregistrement et les analyses d’utilisation.

La forme la plus populaire parmi les touristes est le formulaire &quot;Nous contacter&quot;, qui est utilisé pour poser diverses questions et questions. À ce titre, le département des affaires étrangères a choisi de commencer à mettre en oeuvre l’approche des formulaires adaptatifs sans affichage avec ce formulaire. Ce tutoriel vous guidera tout au long du processus de création du formulaire de contact à l’aide de cette nouvelle architecture. Le résultat final ressemblera à ceci :

![Contact US Headless formulaire adaptatif](assets/contact-us-headless-adaptive-forms.png)