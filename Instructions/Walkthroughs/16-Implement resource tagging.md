---
wts:
  title: 16 - Implémenter le balisage des ressources (5 minutes)
  module: 'Module 05: Describe identity, governance, privacy, and compliance features'
ms.openlocfilehash: cc7a298eb03be3dfcbcc1c69cfa7409bc94c0640
ms.sourcegitcommit: dfe52fea15c568547ba630e9b337ec8df957ad80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2022
ms.locfileid: "139213863"
---
# <a name="16---implement-resource-tagging-5-min"></a>16 - Implémenter le balisage des ressources (5 minutes)

Au cours de cette procédure pas à pas, nous allons créer une affectation de stratégie qui exige un balisage, créer un compte de stockage et tester le balisage, afficher les ressources avec une balise spécifique et supprimer la stratégie de balisage.

# <a name="task-1-create-a-policy-assignment"></a>Tâche 1 : Créer une affectation de stratégie 

Au cours de cette tâche, nous allons configurer la stratégie **Exiger une balise pour les ressources** et l’assigner à notre abonnement. 

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Stratégie**.

3. Faites défiler vers le bas jusqu’à la section **Création**, cliquez sur **Affectations**, puis sur **Attribuer une stratégie** en haut de la page.

4. Notez que la **Portée** de notre stratégie sera valable au niveau de l’abonnement. 

5. Sous **Informations de base**, sélectionnez les points de suspension affichés en regard de la zone **Définition de la stratégie** (côté droit de la zone de texte). Dans la zone de **Recherche**, entrez la valeur **balise**. Une liste des stratégies associées au mot **balise** s’affiche. Faites défiler jusqu’à trouver la définition **Exiger une étiquette et sa valeur sur les ressources**, cliquez sur celle-ci, puis sur **Sélectionner**.

   ![image](https://user-images.githubusercontent.com/89808319/155607579-d564a43e-a9cd-443d-8482-f47879eff2e9.png)
   
6.  Sous l’onglet **Paramètres**, tapez **Company : Contoso ** pour le nom de la paire clé-valeur de l’étiquette. Cliquez sur **Examiner et créer**, puis sur **Créer**.

  

7. L’affectation de la stratégie **Exiger une étiquette et sa valeur sur les ressources** est à présent en place. Quand une ressource est créée, elle doit inclure une étiquette avec la clé Company : Contoso.
   **Remarque : Vous pouvez être amené à attendre jusqu’à 30 minutes pour que cette stratégie soit appliquée.** 

  ![image](https://user-images.githubusercontent.com/89808319/155607357-556646b6-9ca7-4817-a02e-643869b2c4dd.png)

# <a name="task-2-create-a-storage-account-to-test-the-required-tagging"></a>Tâche 2 : Créer un compte de stockage pour tester le balisage requis

Au cours de cette tâche, nous allons créer des comptes de stockage pour tester le balisage requis. 

1. Dans le portail Azure, dans le panneau **Tous les services**, recherchez et sélectionnez **Comptes de stockage**, puis cliquez sur **+Ajouter +Nouveau +Créer**.

2. Sous l’onglet **Informations de base** du panneau **Créer un compte de stockage**, remplissez les informations suivantes (remplacez **xxxx** dans le nom du compte de stockage par des lettres et des chiffres de sorte que le nom soit unique au monde). Laissez les valeurs par défaut pour tous les autres éléments.

    | Paramètre | Valeur | 
    | --- | --- |
    | Abonnement | **Utiliser la valeur par défaut fournie** |
    | Groupe de ressources | **Créer un groupe de ressources** |
    | Nom du compte de stockage | **compte_stockagexxxx** |
    | Emplacement | **(États-Unis) USA Est** |

3. Cliquez sur **Vérifier + créer**. 

    **Remarque :** Nous effectuons un test pour voir ce qui se passe lorsque la balise n’est pas fournie. Notez que la prise d’effet des stratégies peut parfois prendre jusqu’à 30 minutes.

4. Vous recevrez un message d’échec de validation. Cliquez sur le message **Cliquez ici pour afficher les détails**. Dans le panneau **Erreurs**, sous l’onglet **Sommaire**, notez le message d’erreur indiquant que la ressource a été refusée par la stratégie.

    **Remarque :** Si vous affichez l’onglet Erreur brute, vous verrez le nom de balise spécifique requis. 

    ![Capture d’écran de refus en raison d’une erreur de stratégie.](../images/1704.png)


5. Fermez le volet **Erreur** et cliquez sur **Précédent** (au bas de l’écran). Fournissez les informations de balisage. 

    | Paramètre | Valeur | 
    | --- | --- |
    | Nom de la balise | **Company:Contoso** (peut ne pas se trouver dans la liste déroulante) |

6. Cliquez sur **Examiner et créer** et vérifiez que la validation a réussi. Cliquez sur **Créer** pour déployer le compte de stockage. 

# <a name="task-3-view-all-resources-with-a-specific-tag"></a>Tâche 3 : Afficher toutes les ressources avec une balise spécifique

1. Dans le portail Azure, dans le panneau **Tous les services**, recherchez et sélectionnez **Balises**.

2. Notez toutes les balises et leurs valeurs. Cliquez sur la paire clé-valeur **Company : Contoso**. Un panneau présentant le compte de stockage nouvellement créé s’affiche, à condition que vous ayez inclus la balise lors de son déploiement. 

   ![Capture d’écran des balises avec les options Entreprise et Contoso sélectionnées.](../images/1705.png)

3. Dans le portail, affichez le panneau **Toutes les ressources**.

4. Cliquez sur **Ajouter un filtre** et ajoutez la clé de balise **Entreprise** comme catégorie de filtre. Une fois le filtre appliqué, seul votre compte de stockage est répertorié.

    ![Capture d’écran du filtre Toutes les ressources avec l’option Entreprise activée.](../images/1706.png)

# <a name="task-4-delete-the-policy-assignment"></a>Tâche 4 : Supprimer l’attribution de stratégie

Au cours de cette tâche, nous allons supprimer la stratégie **Exiger une balise pour les ressources** afin de ne pas affecter nos travaux suivants. 

1. Dans le portail, depuis le panneau **Tous les services**, recherchez et sélectionnez **Stratégie**.

2. Cliquez sur l’entrée de stratégie **Exiger une balise sur les ressources**.

3. Cliquez sur **Supprimer l’affectation** dans le menu principal.

4. Confirmez la suppression de l’affectation de stratégie dans la boîte de dialogue **Supprimer l’affectation** en cliquant sur **Oui**.

5. Si vous avez le temps, créez une autre ressource sans balise pour vous assurer que la stratégie n’est plus en vigueur.

Félicitations ! Au cours de cette procédure pas à pas, nous avons créé une affectation de stratégie qui exige un balisage, créé un compte de Ressources(stockage ), testé la stratégie de balisage, affiché les ressources avec une balise spécifique et, enfin, supprimé la stratégie de balisage.


**Remarque** : Pour éviter des coûts supplémentaires, vous pouvez supprimer ce groupe de ressources. Recherchez des groupes de ressources, cliquez sur votre groupe de ressources, puis sur **Supprimer le groupe de ressources**. Vérifiez le nom du groupe de ressources, puis cliquez sur **Supprimer**. Surveillez les **notifications** pour voir comment se déroule la suppression.
