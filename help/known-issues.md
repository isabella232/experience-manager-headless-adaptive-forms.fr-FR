---
title: Problèmes connus liés aux formulaires adaptatifs découplés
description: Problèmes connus liés aux formulaires adaptatifs découplés
keywords: découplé, formulaire adaptatif, problèmes connus
hide: true
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: ht
source-wordcount: '102'
ht-degree: 100%

---


# Problèmes connus {#known-issues}

* Les modèles d’édition, d’affichage et de données ne sont pas pris en charge. (CQ-4327047)
* La contrainte minItems ne peut pas être modifiée de façon dynamique. (CQ-4342499)
* Les validations au niveau du panneau en cas de violation ne génèrent aucune erreur. (CQ-4342373)
* Les validations de fichiers en cas de violation ne génèrent aucune erreur. (CQ-4342372)
* Les propriétés personnalisées ne sont pas dynamiques. (CQ-4342376)
* La modification dynamique des données du fichier lors d’un événement de modification à l’aide d’expressions conduit à une boucle infinie. (CQ-4342377)
* Le fichier joint ne prend pas en charge le texte d’aide. (CQ-4342370)
* Si la case à cocher obligatoire n’est pas activée lors de l’envoi, cela ne génère pas d&#39;erreur. (CQ-4342371)
* aria-label n’est pas ajouté dans la pièce jointe. (CQ-4341494)
