---
wts:
  title: « 07 - Implémenter Azure IoT Hub (10 minutes) »
  module: 'Module 03: Describe core solutions and management tools'
ms.openlocfilehash: c2098875e07323c84eac8a405c8a59ad70eaabcd
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908048"
---
# <a name="07---implement-an-azure-iot-hub-10-min"></a>« 07 - Implémenter Azure IoT Hub (10 minutes) »

Dans cette procédure pas à pas, nous allons configurer un nouveau hub IoT Azure dans le portail Azure, puis authentifier une connexion à un appareil IoT à l’aide du simulateur d’appareil Raspberry Pi en ligne. Les données et les messages des capteurs sont transmis du simulateur Raspberry Pi à votre hub IoT Azure. Vous pouvez afficher des mesures pour l’activité de messagerie dans le portail Azure.

# <a name="task-1-create-an-iot-hub"></a>Tâche 1 : Créer un hub IoT 

Dans cette tâche, nous allons créer un hub IoT. 

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **IoT Hub**, puis cliquez sur **+ Ajouter, + Créer, + Nouveau**.

3. Sous l’onglet **Général** du panneau **Hub IoT**, remplissez les champs avec les détails suivants (remplacez **xxxx** dans le nom du compte de stockage par des lettres et des chiffres, de façon à ce que le nom soit unique au monde) :

    | Paramètres | Valeur |
    |--|--|
    | Abonnement | **Utilisez la valeur par défaut fournie** |
    | Groupe de ressources | **Créer un groupe de ressources** |
    | Nom du hub IoT | **my-hub-groupxxxxx** |
    | Région | **USA Est** |

    **Remarque** - Veillez à modifier la valeur **xxxxx** pour créer un **Nom de Hub IoT** unique.

4. Sous l’onglet **Gestion** recherchez **Prix et niveau d’échelle** dans la liste déroulante et définissez sa valeur sur **S1 : Niveau Standard**.

5. Cliquez sur le bouton **Vérifier + créer**.

6. Cliquez sur le bouton **Créer** pour commencer à créer votre nouvelle instance hub IoT Azure.

7. Attendez que l’instance hub IoT Azure soit déployée. 

# <a name="task-2-add-an-iot-device"></a>Tâche 2 : Ajouter un appareil IoT

Dans cette tâche, nous allons ajouter un appareil IoT au hub IoT. 

1. Une fois le déploiement terminé, cliquez sur **Accéder à la ressource** dans le panneau de déploiement. Une autre solution consiste, à partir du panneau **Tous les services**, à rechercher et sélectionner **hub IoT** et à localiser votre nouvelle instance hub IoT

    ![Capture d’écran des notifications de déploiement en cours et de déploiement réussi dans le portail Azure.](../images/0601.png)

2. Pour ajouter un nouvel appareil IoT, faites défiler la liste jusqu’à la section **Gestion des appareils**, puis cliquez sur **Appareils**. Ensuite, cliquez sur **+ Ajouter un appareil**.

    ![Capture d’écran du volet des appareils IoT, mis en surbrillance dans le panneau de navigation du hub IoT, dans le portail Azure. Le bouton Nouveau est mis en surbrillance pour illustrer comment ajouter une nouvelle identité d’appareil IoT au hub IoT.](../images/0602.png)

3. Donnez un nom à votre nouvel appareil IoT, **myRaspberryPi**, puis cliquez sur le bouton **Enregistrer**. Cette opération crée une identité d’appareil IoT dans votre hub IoT Azure.

4. Si vous ne voyez pas votre nouvel appareil, **actualisez** la page Appareils IoT. 

5. Sélectionnez **myRaspberryPi** et copiez la valeur **Chaîne de connexion principale**. Vous utiliserez cette clé dans la tâche suivante pour authentifier une connexion auprès du simulateur Raspberry Pi.

    ![Capture d’écran de la page Chaîne de connexion principale avec icône de copie en surbrillance.](../images/0603.png)

# <a name="task-3-test-the-device-using-a-raspberry-pi-simulator"></a>Tâche 3 : Tester l'appareil à l’aide d’un simulateur Raspberry Pi

Dans cette tâche, nous allons tester notre appareil à l’aide du simulateur Raspberry Pi. 

1. Ouvrez un nouvel onglet dans votre navigateur web et tapez https://aka.ms/RaspPi. Ceci vous dirigera vers un site de simulateur Raspberry Pi. Si vous avez le temps, documentez-vous concernant le simulateur Raspberry Pi. Ensuite, sélectionnez **X** pour fermer la fenêtre contextuelle.

2. Dans la zone de code située sur la partie droite, localisez la ligne contenant « const connectionString = » Remplacez ce code par la chaîne de connexion que vous avez copiée à partir du portail Azure. Notez que la chaîne de connexion comprend les entrées DeviceId (**myRaspberryPi**) et SharedAccessKey.

    ![Capture d’écran de la zone de codage dans le simulateur Raspberry Pi.](../images/0604.png)

3. Cliquez sur **Exécuter** (sous la zone de code) pour exécuter l’application. La sortie de la console doit afficher les données du capteur et les messages qui sont envoyés du simulateur Raspberry Pi à votre hub IoT Azure. Les données et les messages sont envoyés à chaque fois que la LED du simulateur Raspberry Pi clignote. 

    ![Capture d’écran de la console du simulateur Raspberry Pi.  La sortie de la console affiche les données du capteur et les messages envoyés du simulateur Raspberry Pi au hub IoT Azure.](../images/0605.png)

5. Cliquez sur **Arrêter** pour interrompre l’envoi de données.

6. Revenez au Portail Azure.

7. Dans le panneau **Présentation** d’IoT Hub, défilez vers le bas jusque **Utilisation d’IoT Hub** pour afficher son utilisation. Modifiez la plage de temps dans la zone **afficher les dernières données** (show data for last) pour visualiser les données de la dernière heure.

    ![Capture d’écran des mesures dans la zone d’utilisation du hub IoT du portail Azure.](../images/0606.png)


Félicitations ! Vous avez configuré le hub IoT Azure pour collecter les données des capteurs à partir d’un appareil IoT.

**Remarque** : Pour éviter des coûts supplémentaires, vous pouvez supprimer ce groupe de ressources. Recherchez des groupes de ressources, cliquez sur votre groupe de ressources, puis sur **Supprimer le groupe de ressources**. Vérifiez le nom du groupe de ressources, puis cliquez sur **Supprimer**. Surveillez les **notifications** pour voir comment se déroule la suppression.
