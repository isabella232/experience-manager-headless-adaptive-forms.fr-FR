---
title: Extension Visual Studio Code pour les formulaires adaptatifs sans affichage
description: Extension Visual Studio Code pour les formulaires adaptatifs sans affichage
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: sans tête, formulaires adaptatifs, extension Visual Studio Code
hide: false
exl-id: 11960e91-6c09-48d4-9d57-37537f808cd4
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 1%

---

# Extension Microsoft Visual Studio Code pour les formulaires adaptatifs sans affichage

Si vous utilisez Microsoft® Visual Studio Code comme IDE, vous pouvez utiliser l’extension Adaptive Forms pour Microsoft Visual Studio Code. L’extension :

* Ajoute des fonctionnalités IntelliSense pour Forms adaptatif au code Visual Studio
* Permet de valider et de renseigner automatiquement la syntaxe JSON pour les composants de formulaires adaptatifs sans affichage
* Fournit un panneau pour parcourir facilement la structure d’un formulaire adaptatif sans affichage
* Permet de traduire un formulaire adaptatif sans affichage

<!-- 

The extension o easily navigate the structure 

Adobe provides an extension for Microsoft&reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms in Visual Studio Code. The extension adds Adaptive Forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. 

-->

## Conditions préalables requises

* Télécharger et installer [Microsoft Visual Studio Code 1.62.0 ou version ultérieure](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version). Si vous disposez d’une ancienne version ou si aucune version n’est installée, téléchargez la dernière version à partir de [Site web Microsoft](https://code.visualstudio.com/docs/setup/setup-overview). Pour utiliser Visual Studio à partir de la ligne de commande sur Apple macOS, voir [Lancement à partir de la ligne de commande](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).
* Téléchargez la [Extension du créateur de formulaires adaptatifs](/help/assets/adaptive-form-builder-0.12.0.vsix).

## Installation de l’extension

1. Ouvrez une invite de commande et accédez au répertoire contenant le fichier d’extension téléchargé, *adaptive-form-builder-[version].vsix*.

1. Exécutez la commande suivante pour installer l’extension :

   `code -–install-extension adaptive-form-builder-0.12.0.vsix`

   <br>

   ![Installation de l’extension](/help/assets/install-extension.png)


   Pour plus d’informations sur les fichiers .vsix, voir [Aide de Microsoft Visual Studio Code](https://code.visualstudio.com/docs/editor/extension-marketplace#_install-from-a-vsix).
