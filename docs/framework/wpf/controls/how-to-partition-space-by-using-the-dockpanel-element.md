---
title: "Procédure : Partitionner l'espace à l'aide de l'élément DockPanel"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], partitioning space
- partitioning space [WPF]
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
ms.openlocfilehash: 8b79b89e512ec9da27774188aeaeed8ebd5b1153
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577657"
---
# <a name="how-to-partition-space-by-using-the-dockpanel-element"></a>Procédure : Partitionner l'espace à l'aide de l'élément DockPanel
L’exemple suivant crée un simple [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] framework à l’aide un <xref:System.Windows.Controls.DockPanel> élément. Le <xref:System.Windows.Controls.DockPanel> partitionne l’espace disponible pour ses éléments enfants.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le <xref:System.Windows.Controls.DockPanel.Dock%2A> propriété, qui est une propriété jointe, pour ancrer deux identiques <xref:System.Windows.Controls.Border> éléments à la <xref:System.Windows.Controls.Dock.Top> de l’espace partitionné. Une troisième <xref:System.Windows.Controls.Border> élément est ancré à le <xref:System.Windows.Controls.Dock.Left>, sa largeur est définie sur 200 pixels. Une quatrième <xref:System.Windows.Controls.Border> est ancré à le <xref:System.Windows.Controls.Dock.Bottom> de l’écran. La dernière <xref:System.Windows.Controls.Border> élément remplit automatiquement l’espace restant.  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  Par défaut, le dernier enfant d’un <xref:System.Windows.Controls.DockPanel> élément remplit l’espace non alloué restant. Si ce comportement ne vous convient pas, définissez `LastChildFill="False"`.  
  
 L’application compilée produit une nouvelle IU qui ressemble à ceci :  
  
 ![Scénario classique d’utilisation de l’élément DockPanel.](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.Windows.Controls.DockPanel>
- [Vue d’ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)
