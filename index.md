---
title: Instructions hébergées en ligne
permalink: index.html
layout: home
ms.openlocfilehash: c8816b7d9de9c19fbd4c6b3f373d6e4336c6ca5a
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908176"
---
# <a name="content-directory"></a>Répertoire de contenu

Liens hypertextes vers chacune des procédures pas à pas. Les instructeurs peuvent choisir d’utiliser la procédure pas à pas comme démonstration ou en tant que labo pour les participants. 

## <a name="walkthroughs"></a>Procédures pas à pas

{% assign wts = site.pages | where_exp:"page", "page.url contains ’/Instructions/Walkthroughs’" %}
| Module | Procédure pas à pas |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

