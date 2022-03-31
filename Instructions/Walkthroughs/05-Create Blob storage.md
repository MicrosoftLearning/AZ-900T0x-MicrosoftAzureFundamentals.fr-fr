---
wts:
  title: 05 - Créer un stockage d’objets Blob (5 minutes)
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 554a3eb1c95b354e836fe22541f00fa1eb0bc2de
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908093"
---
# <a name="05---create-blob-storage-5-min"></a>05 - Créer un stockage d’objets Blob (5 minutes)

Dans cette procédure pas à pas, nous allons créer un compte de stockage, puis travailler avec des fichiers de stockage d’objets Blob.

# <a name="task-1-create-a-storage-account"></a>Tâche 1 : Créer un compte de stockage 

Dans cette tâche, vous allez créer un nouveau compte de stockage. 

1. Connectez-vous au portail Azure à l’adresse <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Comptes de stockage :** , puis cliquez sur **+ Ajouter, + Créer, + Nouveau**. 

3. Sous l’onglet **Informations de base** du panneau **Créer un compte de stockage**, remplissez les informations suivantes (remplacez **xxxx** dans le nom du compte de stockage par des lettres et des chiffres de sorte que le nom soit unique au monde). Laissez les valeurs par défaut pour tous les autres éléments.

    | Paramètre | Valeur | 
    | --- | --- |
    | Abonnement | **Conservez les valeurs par défaut** |
    | Resource group | **Créer un groupe de ressources** |
    | Nom du compte de stockage | **storageaccountxxxxx** |
    | Emplacement | **(États-Unis) USA Est**  |
    | Performances | **Standard** |
    | Redondance | **Stockage localement redondant (LRS)** |
    
    **Remarque** - Veillez à modifier la valeur **xxxxx** pour créer un **Nom de compte de stockage** unique

5. Cliquez sur **Examiner et créer** pour réviser les paramètres de votre compte de stockage et autoriser Azure à valider la configuration. 

6. Une fois validé, cliquez sur **Créer**. Attendez de recevoir la notification indiquant que le compte a bien été créé. 

7. Sur la page d’accueil, recherchez et sélectionnez **Comptes de stockage** et vérifiez que votre nouveau compte de stockage est répertorié.

    ![Capture d’écran du compte de stockage nouvellement créé dans le portail Azure.](../images/0401.png)

# <a name="task-2-work-with-blob-storage"></a>Tâche 2 : Travailler avec le Stockage Blob

Dans cette tâche, nous allons créer un conteneur blob et charger un fichier d’objets blob. 

1. Cliquez sur le nom du nouveau compte de stockage, faites défiler jusqu’à la section **Stockage de données** dans le menu de gauche, puis cliquez sur **Conteneurs**.

2. Cliquez sur **Conteneur** et complétez les informations. Utilisez les icônes Information pour en savoir plus. Une fois que vous avez terminé, cliquez sur **Créer**.


    | Paramètre | Valeur |
    | --- | --- |
    | Nom | **conteneur1**  |
    | Niveau d'accès public| **Privé (aucun accès anonyme)** |
  

    ![Capture d’écran du conteneur d’objets blob nouvellement créé dans le compte de stockage du portail Azure.](../images/0402.png)

4. Ouvrez une nouvelle fenêtre de navigateur et ouvrez **Bing** pour recherchez une image de fleur. Cliquez avec le bouton droit sur l’image et enregistrez-la dans votre machine virtuelle. 

6. Revenez dans le portail, cliquez sur **conteneur1**, puis sélectionnez **Télécharger**.

5. Cliquez sur Parcourir pour retrouver le fichier image que vous venez d’enregistrer sur votre ordinateur local. Sélectionnez-le puis cliquez sur Télécharger.

   
6. Cliquez sur la flèche **Avancée**, laissez les valeurs par défaut mais passez en revue les options disponibles, puis cliquez sur **Charger**.

    **Remarque** : Vous pouvez charger autant de blobs que vous le souhaitez de cette façon. De nouveaux blobs seront répertoriés dans le conteneur.

7. Une fois le fichier chargé, cliquez avec le bouton droit sur le fichier et notez les options comprenant Afficher/modifier, Télécharger, Propriétés et Supprimer. 

8. Si vous avez le temps, vérifiez les options Fichiers, Tables et Files d'attente.

# <a name="task-3-monitor-the-storage-account"></a>Tâche 3 : Surveiller le compte de stockage

1. Revenez dans le panneau Compte de stockage et cliquez sur **Diagnostiquer et résoudre les problèmes**. 

2. Découvrez certains des problèmes de stockage les plus courants. Vous remarquerez la présence de plusieurs utilitaires de résolution de problèmes.

3. Dans le panneau du compte de stockage, défilez vers le bas jusqu’à la section **Surveillance**, puis cliquez sur **Insights**. Notez qu’il existe des informations sur les pannes, les performances, la disponibilité et la capacité. Vos informations seront différentes.

    ![Capture d’écran de la page Informations du compte de stockage.](../images/0403.PNG)

Félicitations ! Vous avez créé un compte de stockage, puis travaillé avec des objets blob de stockage.

**Remarque** : Pour éviter des coûts supplémentaires, vous pouvez supprimer ce groupe de ressources. Recherchez des groupes de ressources, cliquez sur votre groupe de ressources, puis sur **Supprimer le groupe de ressources**. Vérifiez le nom du groupe de ressources, puis cliquez sur **Supprimer**. Surveillez les **notifications** pour voir comment se déroule la suppression.
