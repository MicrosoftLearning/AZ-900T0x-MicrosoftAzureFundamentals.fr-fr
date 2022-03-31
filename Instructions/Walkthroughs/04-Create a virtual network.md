---
wts:
  title: 04 - Créer un réseau virtuel (20 min)
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 08aafa461c0facc43e735bd81ba97aa9650952fa
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907797"
---
# <a name="04---create-a-virtual-network-20-min"></a>04 - Créer un réseau virtuel (20 min)

Dans cette procédure pas à pas, nous allons créer un réseau virtuel, déployer deux machines virtuelles sur ce réseau virtuel, puis les configurer pour permettre à une machine virtuelle d’envoyer une requête ping à l’autre au sein de ce réseau virtuel.

# <a name="task-1-create-a-virtual-network"></a>Tâche 1 : Créer un réseau virtuel 

Dans cette tâche, nous allons créer un réseau virtuel. 

Remarque : Avant de commencer le labo, désactivez le pare-feu public et privé dans votre machine virtuelle en ouvrant le menu Démarrer > Paramètres > Réseau et Internet > Localiser le pare-feu Windows

1. Connectez-vous au portail Azure à l’adresse <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Réseaux virtuels**, puis cliquez sur **+ Ajouter, + Créer, + Nouveau**. 

3. Sous l’onglet **Informations de base** renseignez les informations suivantes (conservez les valeurs par défaut pour toutes les autres options) :

    | Paramètre | Valeur | 
    | --- | --- |
    | Abonnement | **Conserver la valeur par défaut fournie** |
    | Groupe de ressources | **Créer un groupe de ressources** |
    | Nom | **vnet1** |
    | Région | **(États-Unis) USA Est** |
    
   
4. Cliquez sur le bouton **Vérifier + créer**. Assurez-vous que la validation a abouti. Appuyez ensuite sur le bouton Créer pour déployer la ressource.


# <a name="task-2-create-two-virtual-machines"></a>Tâche 2 : Créer deux machines virtuelles

Dans cette tâche, nous allons créer deux machines virtuelles dans le réseau virtuel. 

1. Dans le panneau **Tous les services**, recherchez **Machines virtuelles**, puis cliquez sur **+ Ajouter, + Créer, + Nouveau**, puis, dans la liste déroulante, sélectionnez **Machine virtuelle**. 

2. Sous l’onglet **Informations de base** renseignez les informations suivantes (conservez les valeurs par défaut pour toutes les autres options) :

   | Paramètre | Valeur | 
   | --- | --- |
   | Abonnement | **Utilisez la valeur par défaut fournie** |
   | Resource group |  **Sélectionnez la valeur par défaut dans la liste déroulante** |
   | Nom de la machine virtuelle | **vm1**|
   | Région | **(États-Unis) USA Est** |
   | Image | **Windows Server 2019 Datacenter - Gen2** |
   | Nom d’utilisateur| **azureuser** |
   | Mot de passe| **Pa$$w0rd1234** |
   | Aucun port d’entrée public| Sélectionnez **Autoriser les ports sélectionnés**  |
   | Ports d’entrée sélectionnés| **RDP (3389)** |
   

3. Sélectionnez l’onglet **Réseau**. Vérifiez que la machine virtuelle soit bien placée dans le réseau virtuel **vnet1**. Vérifiez les paramètres par défaut, mais n’apportez aucune autre modification. 

4. Cliquez sur **Vérifier + créer**. Une fois la validation réussie, cliquez sur **Créer**. La durée du déploiement peut varier, mais elle est généralement de trois à six minutes.

5. Surveillez votre déploiement, mais passez à l’étape suivante. 

6. Créez une seconde machine virtuelle en répétant les étapes **2 à 4** ci-dessus. Assurez-vous d’utiliser un autre nom de machine virtuelle, vérifiez si la machine virtuelle est située dans le même réseau virtuel et qu'elle utilise effectivement une nouvelle adresse IP publique :

    | Paramètre | Valeur |
    | --- | --- |
    | Groupe de ressources | **Sélectionnez Par défaut dans la liste déroulante (identique aux tâches 1-3 et 2-2)** |
    | Nom de la machine virtuelle |  **vm2** |
    | Réseau virtuel | **vnet1** |
    | Adresse IP publique | **vm2-ip** |

7. Attendez la fin du déploiement des deux machines virtuelles et le message d'avertissement du statut *running* (en cours d'exécution).

# <a name="task-3-test-the-connection"></a>Tâche 3 : Tester la connexion 

Dans cette tâche, nous allons tâcher de définir si les machines virtuelles peuvent communiquer (ping) les unes avec les autres. Si ce n’est pas le cas,nous créerons une règle pour permettre une connexion ICMP. En règle générale, les connexions ICMP sont automatiquement bloquées.

1. Dans le panneau **Toutes les ressources**, recherchez **vm1**, ouvrez le panneau **Vue d’ensemble** correspondant, puis assurez-vous que son **État** est **En cours d’exécution**. Il peut être nécessaire de cliquer sur **Actualiser** pour actualiser la page.

2. Dans le panneau **Présentation**, cliquez sur **Connecter** puis sélectionnez **RDP** dans la liste déroulante.

    **Remarque** : Les instructions suivantes indiquent comment vous connecter à votre machine virtuelle à partir d’un ordinateur Windows. 

3. Dans le panneau **Connexion avec RDP**, conservez les options par défaut pour vous connecter par adresse IP sur le port 3389 et cliquez sur **Télécharger le fichier RDP**.

4. Ouvrez le fichier RDP téléchargé (situé dans la partie inférieure gauche de votre machine virtuelle), puis cliquez sur **Connexion** lorsque vous y serez invité. 

5. Dans la fenêtre **Sécurité de Windows**, tapez le nom d’utilisateur **azureuser** et le mot de passe **Pa$$w0rd1234**, puis cliquez sur **OK**.

6. Un avertissement de certificat peut s’afficher pendant le processus de connexion. Cliquez sur **Oui** pour créer la connexion et vous connecter à votre machine virtuelle déployée. La connexion doit ensuite aboutir. Fermez les fenêtres contextuelles de Windows Server et du tableau de bord. Vous devriez ensuite apercevoir un arrière-plan Windows de couleur bleue. Vous êtes à présent au niveau de votre machine virtuelle.

7. Dans **les deux** machines virtuelles nouvellement créées, connectez-vous via RDP et désactivez le pare-feu public et privé en ouvrant le menu Démarrer > Paramètres > Réseau et Internet > Localiser le pare-feu Windows.

8. Ouvrez PowerShell dans la machine virtuelle en cliquant sur le bouton **Démarrer** puis, dans la zone de recherche, tapez **PowerShell**, cliquez avec le bouton droit sur **Windows PowerShell** pour **Exécuter en tant qu’administrateur**

9. Dans Powershell, tentez de communiquer (ping) avec vm2 en tapant :

   ```PowerShell
   ping vm2
   ```

 10. Vous devriez obtenir un résultat satisfaisant. Vous avec communiqué (ping) avec VM2 depuis VM1.


**Félicitations !** Vous avec configuré et déployé deux machines virtuelles dans un réseau virtuel et vous les avez connectées entre elles.

**Remarque** : Pour éviter des coûts supplémentaires, vous pouvez supprimer ce groupe de ressources. Recherchez des groupes de ressources, cliquez sur votre groupe de ressources, puis sur **Supprimer le groupe de ressources**. Vérifiez le nom du groupe de ressources, puis cliquez sur **Supprimer**. Surveillez les **notifications** pour voir comment se déroule la suppression.
