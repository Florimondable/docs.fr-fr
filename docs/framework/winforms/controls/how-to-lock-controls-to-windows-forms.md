---
title: 'Procédure : Verrouiller les contrôles aux Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: a59e5997104b9438681702d460dd8f6937df41b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741455"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Procédure : Verrouiller les contrôles aux Windows Forms
Lorsque vous concevez l’interface utilisateur (IU) de votre application Windows, vous pouvez verrouiller les contrôles une fois qu’ils sont correctement placés, afin que vous ne pas par inadvertance de déplacer ou de les redimensionner lors de la définition d’autres propriétés.  
  
 En outre, vous pouvez verrouiller et déverrouiller tous les contrôles sur le formulaire à la fois, ce qui est utile pour les formulaires avec de nombreux contrôles, ou vous pouvez déverrouiller des contrôles individuels. Une fois que vous avez passé tous les contrôles où vous le souhaitez sur le formulaire, les verrouiller tout en place pour empêcher un mouvement erroné.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-lock-a-control"></a>Pour verrouiller un contrôle  
  
1.  Dans le **propriétés** fenêtre, cliquez sur le **verrouillé** propriété et sélectionnez `true`. (Double-cliquez sur le nom Active ou désactive le paramètre de propriété.)  
  
     Ou bien, cliquez sur le contrôle et choisissez **verrouille les contrôles**.  
  
    > [!NOTE]
    >  Contrôles de verrouillage empêche les glissé vers une nouvelle taille ou l’emplacement sur l’aire de conception. Toutefois, vous pouvez toujours modifier la taille ou l’emplacement des contrôles au moyen de la **propriétés** fenêtre ou dans le code.  
  
### <a name="to-lock-all-the-controls-on-a-form"></a>Pour verrouiller tous les contrôles sur un formulaire  
  
1.  À partir de la **Format** menu, choisissez **verrouille les contrôles**.  
  
    > [!NOTE]
    >  Cette commande verrouille la taille du formulaire, car un formulaire est un contrôle.  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a>Pour déverrouiller verrouillés tous les contrôles sur un formulaire  
  
1.  À partir de la **Format** menu, choisissez **verrouille les contrôles**.  
  
     Tous les contrôles précédemment verrouillés sur le formulaire sont maintenant déverrouillée.  
  
### <a name="to-unlock-locked-controls-individually"></a>Pour déverrouiller les contrôles verrouillés individuellement  
  
1.  Dans le **propriétés** fenêtre, cliquez sur le **verrouillé** propriété et sélectionnez `false`. (Double-cliquez sur le nom Active ou désactive le paramètre de propriété.)  
  
## <a name="see-also"></a>Voir aussi
- [Contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)
- [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
- [Classement par fonction des contrôles Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
