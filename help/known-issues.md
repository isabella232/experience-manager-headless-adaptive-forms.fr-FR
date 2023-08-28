---
title: Problèmes connus des formulaires adaptatifs sans affichage
description: Problèmes connus des formulaires adaptatifs sans affichage
keywords: headless, formulaire adaptatif, problèmes connus
hide: true
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 10%

---


# Problèmes connus {#known-issues}

* Les modèles de modification, d’affichage et de données ne sont pas pris en charge. (CQ-4327047)
* La contrainte minItems ne peut pas être modifiée dynamiquement. (CQ-4342499)
* Les validations au niveau du panneau si elles sont enfreintes ne génèrent aucune erreur. (CQ-4342373)
* Les validations de fichier si enfreintes ne génèrent aucune erreur. (CQ-4342372)
* Les propriétés personnalisées ne sont pas dynamiques. (CQ-4342376)
* La modification dynamique des données de fichier lors de la modification de l’événement à l’aide d’expressions entraîne une boucle infinie. (CQ-4342377)
* La pièce jointe ne prend pas en charge le texte d’aide. (CQ-4342370)
* La case à cocher Requise n’affiche pas d’erreur lors de l’envoi, si elle n’est pas sélectionnée. (CQ-4342371)
* aria-label n’est pas ajouté dans la pièce jointe. (CQ-4341494)
