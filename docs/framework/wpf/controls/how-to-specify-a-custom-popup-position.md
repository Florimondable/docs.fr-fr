---
title: 'Procédure : Spécifier une position de menu contextuel personnalisée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: b61ab6ab02d65d0549941b0055f7aef480d7d644
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726791"
---
# <a name="how-to-specify-a-custom-popup-position"></a>Procédure : Spécifier une position de menu contextuel personnalisée
Cet exemple montre comment spécifier un emplacement personnalisé pour un <xref:System.Windows.Controls.Primitives.Popup> contrôler quand le <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété est définie sur <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.  
  
## <a name="example"></a>Exemple  
 Lorsque le <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété est définie sur <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, le <xref:System.Windows.Controls.Primitives.Popup> appelle une instance définie de la <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> déléguer. Ce délégué retourne un jeu de points possibles qui sont par rapport à l’angle supérieur gauche de la zone cible et le coin supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>. Le <xref:System.Windows.Controls.Primitives.Popup> placement se produit au point qui fournit la meilleure visibilité.  
  
 L’exemple suivant montre comment définir la position d’un <xref:System.Windows.Controls.Primitives.Popup> en définissant le <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Il montre également comment créer et affecter un <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> délégué afin de positionner le <xref:System.Windows.Controls.Primitives.Popup>.  Le délégué de rappel retourne deux <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objets.  Si le <xref:System.Windows.Controls.Primitives.Popup> est masqué par un bord d’écran à la première position, le <xref:System.Windows.Controls.Primitives.Popup> est placé à la deuxième position.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Pour obtenir un exemple complet, consultez [positionnement de Popup, exemple](https://go.microsoft.com/fwlink/?LinkID=160032).  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.Windows.Controls.Primitives.Popup>
- [Vue d’ensemble de Popup](../../../../docs/framework/wpf/controls/popup-overview.md)
- [Rubriques de guide pratique](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
