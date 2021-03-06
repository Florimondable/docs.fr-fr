---
title: "Procédure : Afficher un contenu ListView à l'aide d'un GridView"
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 0e2b37cb061cc92b34c3a4f94bcd42e8ffc69ab5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606005"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>Procédure : Afficher un contenu ListView à l'aide d'un GridView
Cet exemple montre comment définir un <xref:System.Windows.Controls.GridView> mode d’affichage pour un <xref:System.Windows.Controls.ListView> contrôle.  
  
## <a name="example"></a>Exemple  
 Vous pouvez définir le mode d’affichage d’un <xref:System.Windows.Controls.GridView> en spécifiant <xref:System.Windows.Controls.GridViewColumn> objets. L’exemple suivant montre comment définir <xref:System.Windows.Controls.GridViewColumn> objets lier au contenu de données qui est spécifié pour le <xref:System.Windows.Controls.ListView> contrôle. Cela <xref:System.Windows.Controls.GridView> exemple spécifie trois <xref:System.Windows.Controls.GridViewColumn> objets qui mappent au `FirstName`, `LastName`, et `EmployeeNumber` champs de la `EmployeeInfoDataSource` qui est défini comme le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de la <xref:System.Windows.Controls.ListView> contrôle.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 L’illustration suivante montre comment cet exemple s’affiche.  
  
 ![Sortie de ListView avec GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Vue d’ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)
- [Vue d’ensemble de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)
- [Rubriques de guide pratique](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
