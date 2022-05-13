---
wts:
  title: 01 - Créez une machine virtuelle dans le portail (10 min)
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 010d6a19a66f6ac92627720379a4eb850b2ee423
ms.sourcegitcommit: 4a0bfef63f98844f16e2a364d156e96382b8fac5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2022
ms.locfileid: "144556868"
---
# <a name="01---create-a-virtual-machine-in-the-portal-10-min"></a>01 - Créez une machine virtuelle dans le portail (10 min)

Au cours de cette procédure pas à pas, nous allons créer une machine virtuelle dans le portail Azure, nous connecter à cette machine virtuelle, installer le rôle Serveur web et effectuer un test. 

**Remarque** : Au cours de cette procédure pas à pas, prenez le temps de lire les informations en cliquant sur les icônes correspondantes. 

# <a name="task-1-create-the-virtual-machine"></a>Tâche 1 : Créer la machine virtuelle 
1. Connectez-vous au portail Azure : **https://portal.azure.com**

3. Dans le panneau **Tous les services** du menu du portail, recherchez et sélectionnez **Machines virtuelles**, puis cliquez sur **+Créer** et choisissez **+Machine virtuelle Azure** dans le menu déroulant.

4. Sous l’onglet **Informations de base** renseignez les informations suivantes (conservez les valeurs par défaut pour toutes les autres options) :

    | Paramètres | Valeurs |
    |  -- | -- |
    | Abonnement | **Utilisez la valeur par défaut fournie** |
    | Resource group | **Créer un groupe de ressources** |
    | Nom de la machine virtuelle | **myVM** |
    | Région | **(États-Unis) USA Est**|
    | Options de disponibilité | Aucune option de redondance de l'infrastructure requise|
    | Image | **Windows Server 2019 Datacenter - Gen2**|
    | Taille | **Standard D2s v3**|
    | Nom d’utilisateur du compte d’administrateur | **azureuser** |
    | Mot de passe du compte d’administrateur (à taper avec prudence) | **Pa$$w0rd1234**|
    | Règles de trafic entrant pour un port - | ** Autoriser les ports sélectionnés **|
    | Sélectionner des ports d’entrée | **RDP (3389)** et **HTTP (80)**| 

5. Accédez à l’onglet Mise en réseau pour vous assurer que **HTTP (80) et RDP (3389)** sont bien sélectionnés dans la section **Sélectionner les ports d’entrée**.

6. Accédez à l’onglet Gestion. Dans la section **Surveillance**, sélectionnez le paramètre suivant :

    | Paramètres | Valeurs |
    | -- | -- |
    | Diagnostics de démarrage | **Désactiver**|

7. Conservez les autres valeurs par valeur défaut, puis cliquez sur le bouton **Examiner et créer** au bas de la page.

8. Une fois la validation réussie, cliquez sur le bouton **Créer**. Le déploiement de la machine virtuelle peut prendre de cinq à sept minutes.

9. Vous pouvez accéder aux mises à jour sur la page Déploiement et dans la zone **Notifications** (icône représentant une cloche en haut de la barre de menus).

# <a name="task-2-connect-to-the-virtual-machine"></a>Tâche 2 : Se connecter à la machine virtuelle

Dans cette tâche, nous nous connecterons à notre nouvelle machine virtuelle à l'aide du protocole RDP (Remote Desktop Protocol). 

1. Cliquez sur l'icône représentant une cloche dans la barre d'outils bleue supérieure, et sélectionnez « Go to resource » à la fin du déploiement. 

    **Remarque** : Vous pouvez également utiliser le lien **Go to resource** sur la page du déploiement 

2. Sur la machine virtuelle, accédez au panneau **Présentation**, cliquez sur **Connecter** et choisissez **RDP** dans la liste déroulante.

    ![Capture d’écran des propriétés de la machine virtuelle avec le bouton Se connecter activé.](../images/0101.png)

    **Remarque** : Les instructions suivantes indiquent comment vous connecter à votre machine virtuelle à partir d’un ordinateur Windows. Sur un Mac, vous avez besoin d’un client RDP tel que le client Bureau à distance disponible sur le Mac App Store. Sur un ordinateur Linux, vous pouvez utiliser un client RDP open source.

2. Sur la page **Se connecter à la machine virtuelle**, maintenez les options par défaut pour vous connecter à l'adresse IP via le port 3389 et cliquez sur **Télécharger le fichier RDP**. Le téléchargement du fichier est visible en bas à gauche de l’écran.

3. **Ouvrez** le fichier RDP téléchargé (situé dans la partie inférieure gauche de votre machine de labo), puis cliquez sur **Connexion** lorsque vous y serez invité. 

    ![Capture d’écran des propriétés de la machine virtuelle avec le bouton Se connecter activé. ](../images/0102.png)

4. Dans la fenêtre **Sécurité Windows**, ouvrez une session à l'aide des identifiants d’administrateur que vous avez utilisés lors de la création de votre machine virtuelle **azureuser** et du mot de passe **Pa$$w0rd1234**. 

5. Un avertissement de certificat peut s’afficher pendant le processus de connexion. Cliquez sur **Oui** pour créer la connexion et vous connecter à votre machine virtuelle déployée. La connexion doit ensuite aboutir.

    ![Capture d’écran de la boîte de dialogue Avertissement de certificat, signalant à l’utilisateur que le certificat n’est pas approuvé, avec le bouton Oui activé. ](../images/0104.png)

Une nouvelle machine virtuelle (nommée myVM) est initiée dans votre labo. Fermez le Gestionnaire de serveur et les fenêtres contextuelles du tableau de bord (en cliquant sur la croix « x » dans le coin supérieur droit). Vous devez ensuite apercevoir l'arrière-plan de couleur bleue de votre machine virtuelle. **Félicitations !** Vous avez déployé et connecté une machine virtuelle exécutant Windows Server. 

# <a name="task-3-install-the-web-server-role-and-test"></a>Tâche 3 : Installez le rôle serveur web et testez-le

Dans cette tâche, installez le rôle serveur web sur la machine virtuelle que vous venez de créer et vérifiez que la page d’accueil par défaut du serveur IIS est bien affichée. 

1. Dans la machine virtuelle que vous venez d'ouvrir, lancez PowerShell en recherchant **PowerShell** dans la barre de recherche, puis cliquez avec le bouton droit sur **Windows PowerShell** pour activer l’option **Exécuter en tant qu’administrateur**.

    ![Capture d’écran du Bureau de la machine virtuelle avec le bouton Démarrer activé et PowerShell sélectionné avec l’option Exécuter en tant qu’administrateur en surbrillance.](../images/0105.png)

2. Dans PowerShell, installez la fonctionnalité **serveur web** sur la machine virtuelle en exécutant la commande suivante. (Collez la commande et appuyez sur ENTRÉE pour procéder à l'installation).

    ```PowerShell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```
  
3. Une fois l'opération terminée, une invite indiquera **Success** avec la valeur **True**. Il n’est pas nécessaire de redémarrer la machine virtuelle pour terminer l’installation. Fermez la connexion RDP de la machine virtuelle en cliquant sur la croix **x** dans la barre centrale bleue affichée dans la partie supérieure de votre machine virtuelle. Vous pouvez également la réduire en cliquant sur le signe **-** dans la barre centrale bleue affichée dans la partie supérieure de l’écran.

    ![Capture d’écran de l’invite de commandes Windows PowerShell avec la commande Install-WindowsFeature -name Web-Server -IncludeManagementTools exécutée avec succès et le résultat correspondant.](../images/0106.png)

4. Revenez au niveau du portail, naviguez vers le panneau **Présentation** de myVM et cliquez sur le bouton **Cliquez sur le Presse-papiers** pour copier l’adresse IP publique de myVM, puis ouvrez un nouvel onglet du navigateur, collez l'adresse IP publique dans la zone de texte de l’URL et appuyez sur **Entrée** pour y accéder.

    ![Capture d’écran du volet de propriétés de la machine virtuelle du portail Azure, avec l’adresse IP copiée.](../images/0107.png)

5. La page d’accueil par défaut du serveur web IIS s'affiche.

    ![Capture d’écran de la page d’accueil par défaut du serveur web IIS accessible via l’adresse IP publique dans un navigateur web.](../images/0108.png)

**Félicitations !** Vous avez créé une nouvelle machine virtuelle exécutant un serveur web accessible via son adresse IP publique. Si vous aviez une application web à héberger, vous pourriez déployer les fichiers de l’application sur la machine virtuelle et les héberger sur la machine virtuelle déployée pour qu’ils soient accessibles au public.


**Remarque** : Pour éviter des coûts supplémentaires, vous pouvez supprimer ce groupe de ressources. Recherchez des groupes de ressources, cliquez sur votre groupe de ressources, puis sur **Supprimer le groupe de ressources**. Vérifiez le nom du groupe de ressources, puis cliquez sur **Supprimer**. Consultez les **notifications** afin de vérifier que la suppression a bien été effectuée. 
