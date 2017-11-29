---
title: "Comment : ouvrir une boîte de dialogue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d318f35f8f009f0f2c77210ca8b6b29bedfb7619
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-open-a-dialog-box"></a><span data-ttu-id="92b68-102">Comment : ouvrir une boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="92b68-102">How to: Open a Dialog Box</span></span>
<span data-ttu-id="92b68-103">Cet exemple montre comment ouvrir une boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="92b68-103">This example shows how to open a dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92b68-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="92b68-104">Example</span></span>  
 <span data-ttu-id="92b68-105">Une boîte de dialogue est une fenêtre qui est ouvert en instanciant <xref:System.Windows.Window> et en appelant le <xref:System.Windows.Window.ShowDialog%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="92b68-105">A dialog box is a window that is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span> <span data-ttu-id="92b68-106"><xref:System.Windows.Window.ShowDialog%2A>Ouvre une fenêtre et ne retourne pas jusqu'à ce que la nouvelle boîte de dialogue a été fermée.</span><span class="sxs-lookup"><span data-stu-id="92b68-106"><xref:System.Windows.Window.ShowDialog%2A> opens a window and doesn't return until the new dialog box has been closed.</span></span> <span data-ttu-id="92b68-107">Ce type de fenêtre est également appelé un *modale* fenêtre et il restreint l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="92b68-107">This type of window is also known as a *modal* window, and restricts user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="92b68-108">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="92b68-108">.NET Framework Security</span></span>  
 <span data-ttu-id="92b68-109">Appel de <xref:System.Windows.Window.ShowDialog%2A> requiert l’autorisation d’utiliser toutes les fenêtres et événements d’entrée d’utilisateur sans restriction.</span><span class="sxs-lookup"><span data-stu-id="92b68-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b68-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92b68-110">See Also</span></span>  
 [<span data-ttu-id="92b68-111">Retourner un résultat de boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="92b68-111">Return a Dialog Box Result</span></span>](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md)