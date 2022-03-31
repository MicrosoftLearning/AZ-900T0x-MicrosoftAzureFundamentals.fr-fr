---
wts:
  title: 06 - Créer une base de données SQL (5 minutes)
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 61a0e7c7b54ed7cd13a9eae427a5b41abc51cffe
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908128"
---
# <a name="06---create-a-sql-database-5-min"></a>06 - Créer une base de données SQL (5 minutes)

Dans cette procédure pas à pas, nous allons créer une base de données SQL dans Azure, puis interroger les données de cette base de données.

# <a name="task-1-create-the-database"></a>Tâche 1 : Créer la base de données 

Dans cette tâche, nous créons une base de données SQL à partir de l’exemple de base de données AdventureWorksLT. 

1. Connectez-vous au portail Azure à l’adresse [ **https://portal.azure.com**](https://portal.azure.com).

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Bases de données SQL**, puis cliquez sur **+ Ajouter, + Créer, + Nouveau**. 

3. Sous l’onglet **Général**, renseignez ces informations.  

    | Paramètre | Valeur | 
    | --- | --- |
    | Abonnement | **Utilisez la valeur par défaut fournie** |
    | Groupe de ressources | **Créer un groupe de ressources** |
    | Nom de la base de données| **db1** | 
    | Serveur | Sélectionnez **Créer** (une nouvelle barre latérale s’ouvre sur la droite)|
    | Nom du serveur | **sqlserverxxxx** (doit être unique) | 
    | Emplacement | **(États-Unis) USA Est** |
    | Méthode d'authentification | **Utilisez l’authentification SQL** |
    | Connexion d’administrateur du serveur | **sqluser** |
    | Mot de passe | **Pa$$w0rd1234** |
    | Cliquez sur  | **OK** |

   ![Capture d’écran du volet Serveur et du volet Nouveau serveur, avec les champs renseignés conformément au tableau et avec les boutons Vérifier + créer et OK mis en surbrillance.](../images/0501.png)

4. Sous l’onglet **Réseaux**, configurez les paramètres suivants (et conservez les valeurs par défaut des autres) 

    | Paramètre | Valeur | 
    | --- | --- |
    | Méthode de connexion | **Point de terminaison public** |    
    | Autoriser les services et les ressources Azure à accéder à ce serveur | **Oui** |
    | Ajouter l’adresse IP actuelle du client | **Non** |
    
   ![Capture d’écran de l’onglet Mise en réseau du panneau Créer une base de données SQL avec les paramètres sélectionnés conformément au tableau et le bouton Examiner et créer activé.](../images/0501b.png)

5. Sous l’onglet **Sécurité**. 

    | Paramètre | Valeur | 
    | --- | --- |
    | Microsoft Defender pour SQL| **Pas maintenant** |
    
6. Sélectionnez l’onglet **Paramètres supplémentaires**. Nous allons utiliser la base de données test AdventureWorksLT.

    | Paramètre | Value | 
    | --- | --- |
    | Données existantes | **Exemple** |

    ![Capture d’écran de l’onglet Paramètres supplémentaires du panneau Créer une base de données SQL avec les paramètres sélectionnés conformément au tableau et le bouton Examiner et créer mis en surbrillance.](../images/0501c.png)

7. Cliquez sur **Examiner et créer** puis cliquez sur **Créer** pour déployer et approvisionner le groupe de ressources, le serveur et la base de données. Le déploiement peut prendre entre 2 et 5 minutes.


# <a name="task-2-test-the-database"></a>Tâche 2 : Tester la base de données.

Dans cette tâche, nous configurons le serveur SQL Server et nous exécutons une requête SQL. 

1. Une fois le déploiement terminé, cliquez sur Accéder à la ressource dans le panneau de déploiement. Une autre alternative consiste à accéder au panneau **Toutes les ressources**, à rechercher et à sélectionner **Bases de données**, puis **Bases de données SQL** et à vérifier que votre nouvelle base de données a bien été créée. Il peut être nécessaire de cliquer sur **Actualiser** pour actualiser la page.

    ![Capture d’écran du serveur et de la base de données SQL qui viennent d’être déployés.](../images/0502.png)

2. Cliquez sur l’entrée **db1** représentant la base de données SQL que vous venez de créer. Dans le panneau db1, cliquez sur **Éditeur de requête (préversion)** .

3. Connectez-vous en tant que **sqluser** avec le mot de passe **Pa$$w0rd1234**.

4. La connexion échouera. Lisez attentivement l’erreur et notez l’adresse IP qui doit être autorisée via le pare-feu. 

    ![Capture d’écran de la page de connexion de l’Éditeur de requêtes avec une erreur d’adresse IP.](../images/0503.png)

5. Revenez dans le panneau **db1** et cliquez sur **Présentation**. 

    ![Capture d’écran de la page du serveur SQL.](../images/0504.png)

6. Dans le panneau **Présentation** de db1, cliquez sur l’option **Définir le pare-feu du serveur** située dans la partie centrale supérieure de l’écran de présentation.

7. Cliquez sur **+ Ajouter une adresse IP de client** (en haut de la barre de menus) pour ajouter l'adresse IP référencée dans le message d’erreur. (Cette zone est parfois renseignée automatiquement. Si ce n’est pas le cas, collez-la dans les champs d’adresse IP). Veillez à **Enregistrer** vos modifications. 

    ![Capture d’écran de la page de paramètres du pare-feu du serveur SQL, avec la nouvelle règle d’adresse IP mise en surbrillance.](../images/0506.png)

8. Revenez au niveau de votre base de données SQL (en faisant glisser la barre de progression inférieure vers la gauche), puis cliquez sur **Éditeur de requête (préversion)** . Réessayez de vous connecter en tant que **sqluser** avec le mot de passe **Pa$$w0rd1234**. Cette fois, la connexion doit réussir normalement. Notez que le déploiement de la nouvelle règle de pare-feu peut prendre quelques minutes. 

9. Une fois la session ouverte, le panneau de requêtes s'affiche. Entrez la requête suivante dans le volet de l’éditeur. 

    ```SQL
    SELECT TOP 20 pc.Name as CategoryName, p.name as ProductName
    FROM SalesLT.ProductCategory pc
    JOIN SalesLT.Product p
    ON pc.productcategoryid = p.productcategoryid;
    ```

    ![Capture d’écran de l’Éditeur de requêtes, avec le volet Requête affiché et les commandes exécutées avec succès.](../images/0507.png)

10. Cliquez sur **Exécuter**, puis examinez les résultats de la requête dans le volet **Résultats**. La requête doit s’exécuter correctement.

    ![Capture d’écran du volet Éditeur de requêtes de la base de données, avec le code SQL exécuté avec succès et la sortie affichée dans le volet Résultats.](../images/0508.png)

Félicitations ! Vous avez créé une base de données SQL dans Azure et interrogé avec succès les données de cette base de données.

**Remarque** : Pour éviter des coûts supplémentaires, vous pouvez supprimer ce groupe de ressources. Recherchez des groupes de ressources, cliquez sur votre groupe de ressources, puis sur **Supprimer le groupe de ressources**. Vérifiez le nom du groupe de ressources, puis cliquez sur **Supprimer**. Surveillez les **notifications** pour voir comment se déroule la suppression.
