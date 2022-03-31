---
wts:
  title: « 08 - Implémenter Azure Functions (5 minutes) »
  module: 'Module 03: Describe core solutions and management tools'
ms.openlocfilehash: 419d49832a4059e447d2621fe4f209dc5ada2474
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907765"
---
# <a name="08---implement-azure-functions-5-min"></a>« 08 - Implémenter Azure Functions (5 minutes) »

Dans cette procédure pas à pas, nous allons créer une application de fonction pour afficher un message Hello en cas de requête HTTP. 

# <a name="task-1-create-a-function-app"></a>Tâche 1 : Créer une application de fonction 

Dans cette tâche, nous allons créer une application de fonction.

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Dans la **barre de recherche** située en haut du portail, recherchez et sélectionnez **Function App** puis, dans le panneau **Function App**, cliquez sur **+ Ajouter, + Créer, + Nouveau**.

3. Sous l’onglet **Bases** du panneau **Application de fonction**, spécifiez les paramètres suivants (remplacez **xxxx** dans le nom de la fonction par des lettres et des chiffres de façon à ce que le nom soit unique au monde et maintenez les valeurs par défaut de tous les autres paramètres) : 

    | Paramètres | Valeur |
    | -- | --|
    | Abonnement | **Utilisez la valeur par défaut fournie** |
    | Resource group | **Créer un groupe de ressources** |
    | Nom de l’application de fonction | **function-xxxx** |
    | Publier | **Code** |
    | Pile d’exécution | **.NET** |
    | Version | **3.1** |
    | Région | **USA Est** |

    **Remarque** - Veillez à modifier la valeur **xxxx** pour créer un **Nom d’application de fonction** unique

4. Cliquez sur **Examiner et créer** puis, après la validation, cliquez sur **Créer** pour commencer l’approvisionnement et le déploiement de votre nouvelle application de fonction Azure.

5. Attendez la notification indiquant que la ressource a bien été créée.

6. Une fois le déploiement terminé, cliquez sur Accéder à la ressource dans le panneau de déploiement. Une autre alternative consiste à revenir au niveau du panneau **Function App**, à cliquer sur **Actualiser** et à vérifier que la nouvelle application de fonction est effectivement dotée du statut **Running** (En cours d’exécution). 

    ![Capture d’écran de la page Function App avec la nouvelle application de fonction.](../images/0701.png)

# <a name="task-2-create-a-http-triggered-function-and-test"></a>Tâche 2 : Créer une fonction déclenchée par requête HTTP et la tester

Dans cette tâche, nous allons utiliser la fonction Webhook + API pour afficher un message en cas de requête HTTP. 

1. Dans le panneau **Application de fonction**, cliquez sur l’application de fonction nouvellement créée. 

2. Dans le panneau Function App, dans la section **Fonctions**, cliquez sur **Fonctions**, puis sur **+ Ajouter, + Créer, + Nouveau**.

    ![Capture d’écran de l’étape de choix d’un environnement de développement dans les fonctions Azure pour le volet Mise en route de dot net dans le portail Azure. Les éléments d’affichage pour créer une nouvelle fonction dans le portail sont mis en surbrillance. Les éléments en surbrillance sont le développement de l’application de fonction, l’ajout d’une nouvelle fonction dans le portail et le bouton Continuer.](../images/0702.png)

3. La fenêtre contextuelle **Ajouter une fonction** s'affiche dans le volet droit. Dans la section **Sélectionner un modèle**, cliquez sur **Déclencheur HTTP**. Cliquez sur **Ajouter** 

    ![Capture d’écran de l’étape de création d’une fonction dans les fonctions Azure pour le volet Mise en route de dot net dans le portail Azure. La fiche de déclenchement HTTP est en surbrillance pour illustrer les éléments d’affichage utilisés pour ajouter un nouveau webhook à une fonction Azure.](../images/0702a.png)

4. Dans le panneau **HttpTrigger1**, dans la section **Développeur**, cliquez sur **Code + Test**. 

5. Dans le panneau **Code + Test**, examinez le code généré automatiquement et notez que le code est conçu pour exécuter une requête HTTP et des informations de traçage. Notez également que la fonction renvoie un message de type Hello avec un nom. 

    ![Capture d’écran du code de la fonction. Le message de type Hello est en surbrillance.](../images/0704.png)

6. Cliquez sur **Obtenir l’URL de la fonction** dans la partie supérieure de l’éditeur de fonctions. 

7. Assurez-vous que la valeur de la liste déroulante **Clé** est définie sur **Par défaut**, puis cliquez sur **Copier** pour copier l’URL de la fonction. 

    ![Capture d’écran du panneau Obtenir l’URL de la fonction dans l’éditeur de fonction du portail Azure. Les éléments d’affichage du bouton Obtenir l’URL de la fonction, de la liste déroulante Définir la clé et du bouton Copier l’URL sont en surbrillance pour indiquer comment obtenir et copier l’URL de la fonction depuis l’éditeur de fonction.](../images/0705.png)

8. Ouvrez un nouvel onglet de navigateur et collez l’URL de la fonction copiée dans la barre d’adresse de votre navigateur web. Lorsque la page sera demandée, la fonction s’exécutera. Notez le message renvoyé indiquant que la fonction nécessite un nom dans le corps de la demande.

    ![Capture d’écran du message Veuillez indiquer un nom.](../images/0706.png)

9. Ajoutez **&name=*yourname*** à la fin de l’URL.

    **Remarque** : Par exemple, si votre nom est Cindy, l’URL final ressemblera à ceci : `https://azfuncxxx.azurewebsites.net/api/HttpTrigger1?code=X9xx9999xXXXXX9x9xxxXX==&name=cindy`

    ![Capture d’écran d’une URL de fonction en surbrillance et d’un exemple de nom d’utilisateur ajouté dans la barre d’adresse d’un navigateur web. Le message de type Hello et le nom d’utilisateur sont également mis en surbrillance pour illustrer la sortie de la fonction dans la fenêtre principale du navigateur.](../images/0707.png)

10. Lorsque vous appuyez sur Entrée, votre fonction est exécutée et toutes les invocations sont tracées. Pour afficher les traces, retournez dans le panneau **HttpTrigger1 \| Code + test** du portail, puis cliquez sur **Analyser**. Vous pouvez **configurer** Application Insights en sélectionnant le timestamp, puis cliquer sur **Exécuter une requête dans Application Insights**.

    ![Capture d’écran d’un journal d’informations de traçage résultant de l’exécution de la fonction dans l’éditeur de fonction du portail Azure.](../images/0709.png) 

Félicitations ! Vous avez créé une application de fonction pour afficher un message Hello en cas de requête HTTP.  

**Remarque** : Pour éviter des coûts supplémentaires, vous pouvez supprimer ce groupe de ressources. Recherchez des groupes de ressources, cliquez sur votre groupe de ressources, puis sur **Supprimer le groupe de ressources**. Vérifiez le nom du groupe de ressources, puis cliquez sur **Supprimer**. Surveillez les **notifications** pour voir comment se déroule la suppression.
