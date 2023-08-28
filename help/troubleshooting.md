---
title: Dépannage de Forms adaptatif sans affichage
description: Dépannage de Forms adaptatif sans affichage
keywords: formulaire adaptatif sans tête, résolution des problèmes
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 7%

---

# Résolution des problèmes

## Impossible de déployer le projet Archetype dans un environnement de développement local

### Problème

Lorsque vous utilisez la variable `mvn -PautoInstallPackage clean install` Pour des commandes similaires afin de déployer un projet AEM Archeype, le déploiement du projet échoue.

### Raison

Cela peut se produire en raison d’une version non prise en charge ou d’une installation corrompue de node.js ou NPM.

### Solution

1. Complètement [supprimer les installations existantes de Node.JS](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/) de votre environnement.

1. Installez Node.JS 16.13.0 ou version ultérieure avec NPM.

1. Redémarrez votre machine.


## La variable `mvn clean install` ne s’exécute pas.

### Problème

Lorsque vous utilisez la variable `mvn clean install` Pour des commandes similaires afin de déployer un projet Archeype AEM, l’exécution de la commande échoue.

### Raison

Cela peut se produire si Git n’est pas installé.

### Solution

Téléchargez et installez le [dernière version de Git](https://git-scm.com/downloads). Si vous découvrez Git, voir [Installation de Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
