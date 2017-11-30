---
title: "Procédure pas à pas : Création d’un formulaire maître / détail utilisant deux contrôles de DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0d213d70d6f12cb8b574f07457c1b20317670d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="9ae7b-102">Procédure pas à pas : création d'un formulaire maître/détail qui utilise deux contrôles DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ae7b-102">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="9ae7b-103">Un des scénarios plus courants pour l’utilisation de la <xref:System.Windows.Forms.DataGridView> contrôle est le *maître/détail* formulaire, dans lequel une relation parent/enfant entre deux tables de base de données s’affiche.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-103">One of the most common scenarios for using the <xref:System.Windows.Forms.DataGridView> control is the *master/detail* form, in which a parent/child relationship between two database tables is displayed.</span></span> <span data-ttu-id="9ae7b-104">Sélection de lignes dans la table principale entraîne la table de détail mettre à jour avec les données enfants correspondantes.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-104">Selecting rows in the master table causes the detail table to update with the corresponding child data.</span></span>  
  
 <span data-ttu-id="9ae7b-105">Implémentation d’un formulaire maître/détail est facile à l’aide de l’interaction entre le <xref:System.Windows.Forms.DataGridView> contrôle et le <xref:System.Windows.Forms.BindingSource> composant.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-105">Implementing a master/detail form is easy using the interaction between the <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="9ae7b-106">Dans cette procédure pas à pas, vous allez créer le formulaire à l’aide de deux <xref:System.Windows.Forms.DataGridView> contrôles et deux <xref:System.Windows.Forms.BindingSource> composants.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-106">In this walkthrough, you will build the form using two <xref:System.Windows.Forms.DataGridView> controls and two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="9ae7b-107">L’écran affiche deux tables connexes dans la base de données Northwind SQL Server : `Customers` et `Orders`.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-107">The form will show two related tables in the Northwind SQL Server sample database: `Customers` and `Orders`.</span></span> <span data-ttu-id="9ae7b-108">Lorsque vous avez terminé, vous aurez un formulaire qui affiche tous les clients dans la base de données dans le master <xref:System.Windows.Forms.DataGridView> et toutes les commandes du client sélectionné dans le détail <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-108">When you are finished, you will have a form that shows all the customers in the database in the master <xref:System.Windows.Forms.DataGridView> and all the orders for the selected customer in the detail <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
 <span data-ttu-id="9ae7b-109">Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : créer un maître/détail formulaire à l’aide de deux contrôles DataGridView Windows Forms](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md).</span><span class="sxs-lookup"><span data-stu-id="9ae7b-109">To copy the code in this topic as a single listing, see [How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9ae7b-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9ae7b-110">Prerequisites</span></span>  
 <span data-ttu-id="9ae7b-111">Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9ae7b-111">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="9ae7b-112">Accès à un serveur doté de la base de données Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-112">Access to a server that has the Northwind SQL Server sample database.</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="9ae7b-113">Création du formulaire</span><span class="sxs-lookup"><span data-stu-id="9ae7b-113">Creating the form</span></span>  
  
#### <a name="to-create-a-masterdetail-form"></a><span data-ttu-id="9ae7b-114">Pour créer un formulaire maître/détail</span><span class="sxs-lookup"><span data-stu-id="9ae7b-114">To create a master/detail form</span></span>  
  
1.  <span data-ttu-id="9ae7b-115">Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient deux <xref:System.Windows.Forms.DataGridView> contrôles et deux <xref:System.Windows.Forms.BindingSource> composants.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-115">Create a class that derives from <xref:System.Windows.Forms.Form> and contains two <xref:System.Windows.Forms.DataGridView> controls and two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="9ae7b-116">Le code suivant fournit l’initialisation de base et inclut un `Main` (méthode).</span><span class="sxs-lookup"><span data-stu-id="9ae7b-116">The following code provides basic form initialization and includes a `Main` method.</span></span> <span data-ttu-id="9ae7b-117">Si vous utilisez la [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] concepteur pour créer votre formulaire, vous pouvez utiliser le code généré par concepteur au lieu de ce code, mais veillez à utiliser les noms indiqués dans les déclarations de variables.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-117">If you use the [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] designer to create your form, you can use the designer generated code instead of this code, but be sure to use the names shown in the variable declarations here.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  <span data-ttu-id="9ae7b-118">Implémentez une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-118">Implement a method in your form's class definition for handling the detail of connecting to the database.</span></span> <span data-ttu-id="9ae7b-119">Cet exemple utilise un `GetData` méthode remplit une <xref:System.Data.DataSet> d’objet, ajoute un <xref:System.Data.DataRelation> objet au jeu de données et lie le <xref:System.Windows.Forms.BindingSource> composants.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-119">This example uses a `GetData` method that populates a <xref:System.Data.DataSet> object, adds a <xref:System.Data.DataRelation> object to the data set, and binds the <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="9ae7b-120">Veillez à définir la variable `connectionString` avec une valeur appropriée pour votre base de données.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-120">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9ae7b-121">Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-121">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="9ae7b-122">L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-122">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="9ae7b-123">Pour plus d’informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="9ae7b-123">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  <span data-ttu-id="9ae7b-124">Implémenter un gestionnaire pour de votre formulaire <xref:System.Windows.Forms.Form.Load> événements qui lie la <xref:System.Windows.Forms.DataGridView> des contrôles à la <xref:System.Windows.Forms.BindingSource> composants et appelle le `GetData` (méthode).</span><span class="sxs-lookup"><span data-stu-id="9ae7b-124">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that binds the <xref:System.Windows.Forms.DataGridView> controls to the <xref:System.Windows.Forms.BindingSource> components and calls the `GetData` method.</span></span> <span data-ttu-id="9ae7b-125">L’exemple suivant inclut le code qui se redimensionne <xref:System.Windows.Forms.DataGridView> colonnes pour correspondre les données affichées.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-125">The following example includes code that resizes <xref:System.Windows.Forms.DataGridView> columns to fit the displayed data.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="9ae7b-126">Test de l'application</span><span class="sxs-lookup"><span data-stu-id="9ae7b-126">Testing the Application</span></span>  
 <span data-ttu-id="9ae7b-127">Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-127">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="9ae7b-128">Pour tester le formulaire</span><span class="sxs-lookup"><span data-stu-id="9ae7b-128">To test the form</span></span>  
  
-   <span data-ttu-id="9ae7b-129">Compilez et exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-129">Compile and run the application.</span></span>  
  
     <span data-ttu-id="9ae7b-130">Vous verrez deux <xref:System.Windows.Forms.DataGridView> contrôles au-dessus de l’autre.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-130">You will see two <xref:System.Windows.Forms.DataGridView> controls, one above the other.</span></span> <span data-ttu-id="9ae7b-131">Au-dessus se trouvent les clients de Northwind `Customers` table et en bas sont les `Orders` correspondant au client sélectionné.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-131">On top are the customers from the Northwind `Customers` table, and at the bottom are the `Orders` corresponding to the selected customer.</span></span> <span data-ttu-id="9ae7b-132">Lorsque vous sélectionnez des lignes différentes dans le coin supérieur <xref:System.Windows.Forms.DataGridView>, le contenu de la limite inférieure <xref:System.Windows.Forms.DataGridView> changent en conséquence.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-132">As you select different rows in the upper <xref:System.Windows.Forms.DataGridView>, the contents of the lower <xref:System.Windows.Forms.DataGridView> change accordingly.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9ae7b-133">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="9ae7b-133">Next Steps</span></span>  
 <span data-ttu-id="9ae7b-134">Cette application vous donne une connaissance élémentaire de la <xref:System.Windows.Forms.DataGridView> fonctionnalités du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-134">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="9ae7b-135">Vous pouvez personnaliser l’apparence et le comportement de la <xref:System.Windows.Forms.DataGridView> contrôle de plusieurs manières :</span><span class="sxs-lookup"><span data-stu-id="9ae7b-135">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
-   <span data-ttu-id="9ae7b-136">Modifier les styles de bordure et en-tête.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-136">Change border and header styles.</span></span> <span data-ttu-id="9ae7b-137">Pour plus d’informations, consultez [Comment : modifier la bordure et les Styles de quadrillage dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="9ae7b-137">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="9ae7b-138">Activer ou restreindre l’entrée d’utilisateur à le <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-138">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9ae7b-139">Pour plus d’informations, consultez [Comment : empêcher l’ajout ligne et la suppression dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), et [Comment : rendre en lecture seule les colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9ae7b-139">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="9ae7b-140">Valider l’entrée d’utilisateur pour le <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-140">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9ae7b-141">Pour plus d’informations, consultez [procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9ae7b-141">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="9ae7b-142">Gérer des jeux de données très volumineux à l’aide du mode virtuel.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-142">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="9ae7b-143">Pour plus d’informations, consultez [procédure pas à pas : implémentation du Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9ae7b-143">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="9ae7b-144">Personnaliser l’apparence des cellules.</span><span class="sxs-lookup"><span data-stu-id="9ae7b-144">Customize the appearance of cells.</span></span> <span data-ttu-id="9ae7b-145">Pour plus d’informations, consultez [Comment : personnaliser l’apparence des cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) et [Comment : définir des Styles de cellule par défaut pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9ae7b-145">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ae7b-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ae7b-146">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="9ae7b-147">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ae7b-147">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="9ae7b-148">Guide pratique pour créer un formulaire maître/détail utilisant deux contrôles DataGridView Windows Form</span><span class="sxs-lookup"><span data-stu-id="9ae7b-148">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)  
 [<span data-ttu-id="9ae7b-149">Protection des informations de connexion</span><span class="sxs-lookup"><span data-stu-id="9ae7b-149">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)