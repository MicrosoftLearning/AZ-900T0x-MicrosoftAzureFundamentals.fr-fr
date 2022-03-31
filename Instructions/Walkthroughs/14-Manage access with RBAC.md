---
wts:
  title: 14 - Gérer l’accès avec RBAC (5 minutes)
  module: 'Module 05: Describe identity, governance, privacy, and compliance features'
ms.openlocfilehash: 4d1369307dc306a367a8a4cc532774c08c513e85
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907739"
---
# <a name="14---manage-access-with-rbac-5-min"></a>14 - Gérer l’accès avec RBAC (5 minutes)

Dans cette procédure étape par étape, nous affecterons des rôles de permissions aux ressources et nous afficherons les journaux.

# <a name="task-1-view-and-assign-roles"></a>Tâche 1 : Afficher et attribuer des rôles

Dans cette tâche, nous allons attribuer le rôle de contributeur de machine virtuelle. 

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Groupes de ressources**, puis cliquez sur **+Ajouter +Nouveau +Crér**.

3. Créez un groupe de ressources. Lorsque vous avez terminé, cliquez sur **Créer**. 

    | Paramètre | Valeur |
    | -- | -- |
    | Abonnement | **Utiliser la valeur par défaut fournie** |
    | Resource group | **myRGRBAC** |
    | Région | **(États-Unis) USA Est** |
   

4. Créez **Contrôler + créer** puis cliquez sur **Créer**.

5. **Actualisez** la page du groupe de ressources, puis cliquez sur l’entrée représentant le groupe de ressources nouvellement créé.

6. Cliquez sur le panneau **Contrôle d’accès (IAM)** , puis cliquez sur l’onglet **Rôles**. Faites défiler le grand nombre de définitions de rôles disponibles. Utilisez les icônes d’informations pour vous faire une idée des autorisations de chaque rôle. Notez qu’il existe également des informations sur le nombre d’utilisateurs et de groupes affectés à chaque rôle.
7. 
![image](https://user-images.githubusercontent.com/89808319/144266949-f19d91ab-31d6-4c8b-af36-c00035925cf0.png)

7. Sous l’onglet **Attributions de rôle** du panneau **myRGRBAC - Contrôle d’accès (IAM)** , cliquez sur **+ Ajouter** puis cliquez sur **Ajouter une attribution de rôle**. Recherchez et sélectionnez le rôle Contributeur de machine virtuelle. Passez à l’onglet « Membres » et attribuez l’accès à : Utilisateur, groupe ou principal du service. Cliquez ensuite sur + Sélectionner des membres et tapez votre nom dans la fonction de recherche contextuelle, puis appuyez sur « Sélectionner ». Appuyez ensuite sur « Vérifier et affecter »

    
    ![image](https://user-images.githubusercontent.com/89808319/144266255-3a0f8574-9358-4c21-8f95-3503747e77c8.png)

 

    **Remarque :** Le rôle de contributeur de machine virtuelle permet de gérer des machines virtuelles, mais pas d’accéder à leur système d’exploitation ni de gérer le réseau virtuel et le compte de stockage auxquels ils sont connectés.

  

8. **Rafraîchissez** la page Affectations des rôle et assurez-vous que vous êtes désormais répertorié en tant que contributeur de machine virtuelle. 

    **Remarque** : Cette affectation ne vous octroie en fait aucun privilège supplémentaire, car votre compte a déjà le rôle Propriétaire, qui inclut tous les privilèges associés au rôle Contributeur.

# <a name="task-2-monitor-role-assignments-and-remove-a-role"></a>Tâche 2 : Contrôler les attributions de rôles et supprimer un rôle

Dans cette tâche, nous allons afficher le journal d’activité pour vérifier l’attribution de rôle, puis supprimer le rôle. 

1. Dans le panneau Groupes de ressources myRGRBAC, cliquez sur **Journal d’activité**.

2. Cliquez sur **Ajouter un filtre**, sélectionnez **Opération**, puis **Créer une attribution de rôle**.

    ![Capture d’écran de la page Journal d’activité avec un filtre configuré.](../images/1503.png)

3. Vérifiez que le journal d’activité affiche votre attribution de rôle. 

    **Remarque** : Pouvez-vous comprendre comment supprimer votre attribution de rôle ?

Félicitations ! Vous venez de créer un groupe de ressources, d’y affecter un rôle d'accès et d'afficher les journaux d’activité. 

**Remarque** : Pour éviter des coûts supplémentaires, vous pouvez supprimer ce groupe de ressources. Recherchez des groupes de ressources, cliquez sur votre groupe de ressources, puis sur **Supprimer le groupe de ressources**. Vérifiez le nom du groupe de ressources, puis cliquez sur **Supprimer**. Surveillez les **notifications** pour voir comment se déroule la suppression.

