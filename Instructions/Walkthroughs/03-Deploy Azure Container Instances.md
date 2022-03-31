---
wts:
  title: 03 - Déployer Azure Container Instances (10 minutes)
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 0616be96840b14f7580c7d2b16cb43b211c6e3a2
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908133"
---
# <a name="03---deploy-azure-container-instances-10-min"></a>03 - Déployer Azure Container Instances (10 minutes)

Dans cette procédure pas à pas, nous allons créer, configurer et déployer un container à l’aide d’ ACI (Azure Container Instances) dans le portail Azure. Le conteneur est une application web Welcome to ACI qui affiche une page HTML statique. 

# <a name="task-1-create-a-container-instance"></a>Tâche 1 : Créer une instance de conteneur 

Dans cette tâche, nous allons créer une nouvelle instance de conteneur pour l’application web.  

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Container instances** puis cliquez sur **+ Ajouter, + Créer, + Nouveau**. 

3. Fournissez les détails de base suivants pour la nouvelle instance de conteneur (laissez les valeurs par défaut pour tous les autres éléments) : 

    | Paramètre| Valeur|
    |----|----|
    | Abonnement | ***Utilisez la valeur par défaut fournie*** |
    | Resource group | **Créer un groupe de ressources** |
    | Nom du conteneur| **mycontainer**|
    | Région | **(États-Unis) USA Est** |
    | Source d’image| **Docker Hub ou autre registre**|
    | Type d’image| **Public**|
    | Image| **mcr.microsoft.com/azuredocs/aci-helloworld**|
    | Type de système d’exploitation| **Linux** |
    | Taille| ***Laissez la valeur par défaut***|


4. Configurez l’onglet Réseaux (remplacez **xxxx** par des lettres et des chiffres afin que le nom soit unique au monde). Laissez la valeur par défaut pour tous les autres paramètres.

    | Paramètre| Valeur|
    |--|--|
    | Étiquette du nom DNS| **mycontainerdnsxxxxx** |

    
    **Remarque** : Votre conteneur sera accessible au public à l’adresse : dns-name-label.region.azurecontainer.io. Si vous recevez le message d’erreur **DNS name label not available** (Étiquette du nom DNS non disponible) à la fin du déploiement, spécifiez une autre étiquette du nom DNS (en remplaçant les valeurs de xxxxx) et procédez à un nouveau déploiement. 

5. Cliquez sur **Examiner et créer** pour lancer le processus de validation automatique.

6. Cliquez sur **Créer** pour créer l’instance de conteneur. 

7. Surveillez la page Déploiement et la page **Notifications**. 


# <a name="task-2-verify-deployment-of-the-container-instance"></a>Tâche 2 : Vérifier le déploiement de l’instance de conteneur

Dans cette tâche, nous vérifierons que l’instance de conteneur est en cours d’exécution, en nous assurant que la page d’accueil s’affiche.

1. Une fois le déploiement terminé, cliquez sur le lien **Accéder à la ressource** sur le panneau de déploiement ou sur le lien vers la ressource dans la zone de notification.

2. Dans le panneau **Aperçu** de **mycontainer**, assurez-vous que le **Statut** de votre conteneur est bien **En cours d’exécution**. 

3. Recherchez le nom de domaine complet (FQDN, Fully Qualified Domain Name).

    ![Capture d’écran du volet de vue d’ensemble du conteneur nouvellement créé dans le portail Azure, avec le nom de domaine complet en surbrillance. ](../images/0202.png)

2. Copiez le nom de domaine complet (FQDN, Fully Qualified Domain Name) du conteneur dans un nouvel onglet du navigateur web et appuyez sur **Entrée**. La page d’accueil doit ensuite s’afficher. 

    ![Capture d’écran du message de bienvenue ACI affiché dans un navigateur web.](../images/0203.png)


**Félicitations !** Vous avez utilisé le portail Azure pour déployer une application dans un conteneur dans Azure Container Instances.

**Remarque** : Pour éviter des coûts supplémentaires, vous pouvez supprimer ce groupe de ressources. Recherchez des groupes de ressources, cliquez sur votre groupe de ressources, puis sur **Supprimer le groupe de ressources**. Vérifiez le nom du groupe de ressources, puis cliquez sur **Supprimer**. Surveillez les **notifications** pour voir comment se déroule la suppression.
