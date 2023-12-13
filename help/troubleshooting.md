---
title: Résolution des problèmes liés aux formulaires adaptatifs découplés
description: Résolution des problèmes liés aux formulaires adaptatifs découplés
keywords: découplé, formulaire adaptatif, dépannage
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: ht
source-wordcount: '133'
ht-degree: 100%

---

# Résolution des problèmes

## Impossible de déployer le projet d’archétype dans un environnement de développement local

### Problème

Lorsque vous saisissez la commande `mvn -PautoInstallPackage clean install` ou une commande similaire pour déployer un projet d’archétype AEM, le déploiement échoue.

### Raison

Ce problème peut se produire en raison d’une version non prise en charge ou d’une installation endommagée de node.js ou NPM.

### Solution

1. [Supprimez complètement les installations existantes de Node.JS](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/) de votre environnement.

1. Installez Node.JS 16.13.0 ou une version ultérieure avec NPM.

1. Redémarrez votre machine.


## Impossible d’exécuter la commande `mvn clean install`.

### Problème

Lorsque vous saisissez la commande `mvn clean install` ou une commande similaire pour déployer un projet d’archétype AEM, l’exécution de la commande échoue.

### Raison

Ce problème peut se produire si Git n’est pas installé.

### Solution

Téléchargez et installez la [dernière version de Git](https://git-scm.com/downloads). Si vous découvrez Git, consultez [Installer Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
