---
title: "Procédure : Déclencher une animation en cas de modification d'une valeur de propriété"
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
ms.openlocfilehash: 2be85a9ae93d504d98930468ad2e257385e835f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705295"
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>Procédure : Déclencher une animation en cas de modification d'une valeur de propriété
Cet exemple montre comment utiliser un <xref:System.Windows.Trigger> pour démarrer un <xref:System.Windows.Media.Animation.Storyboard> quand une valeur de propriété change. Vous pouvez utiliser un <xref:System.Windows.Trigger> à l’intérieur d’un <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, ou <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un <xref:System.Windows.Trigger> pour animer la <xref:System.Windows.UIElement.Opacity%2A> d’un <xref:System.Windows.Controls.Button> lors de son <xref:System.Windows.UIElement.IsMouseOver%2A> propriété devient `true`.  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 Les animations appliquées par la propriété <xref:System.Windows.Trigger> objets se comportent de façon plus complexe que <xref:System.Windows.EventTrigger> animations ou les animations démarrées à l’aide de <xref:System.Windows.Media.Animation.Storyboard> méthodes.  Elles « effectuent un transfert » avec des animations défini par d’autres <xref:System.Windows.Trigger> objets, mais composent avec <xref:System.Windows.EventTrigger> et animations déclenchées à la méthode.  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.Windows.Trigger>
- [Vue d’ensemble des techniques d’animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
- [Vue d'ensemble des plans conceptuels](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
