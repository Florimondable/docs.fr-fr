---
title: 'Procédure : Utiliser des propriétés indexées dans la programmation COM Interop - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 920b9ad28bb3bd26b7606fba12bdf2e042be49fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509855"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Procédure : Utiliser des propriétés indexées dans la programmation COM Interop (Guide de programmation C#)
Les *propriétés indexées* améliorent la façon dont les propriétés COM avec des paramètres sont consommées dans la programmation C#. Les propriétés indexées fonctionnent avec d’autres fonctionnalités dans Visual C#, comme les [arguments nommés et facultatifs](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), un nouveau type ([dynamique](../../../csharp/language-reference/keywords/dynamic.md)) et [les informations de type incorporées](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), pour améliorer la programmation Microsoft Office.  
  
 Dans les versions antérieures de C#, les méthodes sont accessibles comme des propriétés uniquement si la méthode `get` n’a aucun paramètre et que la méthode `set` a un seul et unique paramètre de valeur. Toutefois, toutes les propriétés COM ne respectent pas ces restrictions. Par exemple, la propriété <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> d’Excel a un accesseur `get`, qui nécessite un paramètre pour le nom de la plage. Dans le passé, parce que vous ne pouviez pas accéder à la propriété `Range` directement, vous deviez utiliser la méthode `get_Range` à la place, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 Les propriétés indexées vous permettent d’écrire ce qui suit à la place :  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  L’exemple précédent utilise également la fonctionnalité des [arguments facultatifs](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), qui vous permet d’omettre `Type.Missing`.  
  
 De même, pour définir la valeur de la propriété `Value` d’un objet <xref:Microsoft.Office.Interop.Excel.Range> dans Visual C# 2008 et les versions antérieures, deux arguments sont nécessaires. L’un fournit un argument pour un paramètre facultatif qui spécifie le type de la valeur de la plage. L’autre fournit la valeur de la propriété `Value`. Les exemples suivants illustrent ces techniques. Les deux définissent la valeur de la cellule A1 sur `Name`.
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 Les propriétés indexées vous permettent d’écrire le code suivant à la place.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 Vous ne pouvez pas créer vos propres propriétés indexées. La fonctionnalité prend uniquement en charge la consommation de propriétés indexées existantes.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant illustre l'exemple complet. Pour plus d’informations sur la configuration d’un projet qui accède à l’API Office, consultez [Guide pratique pour accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a>Voir aussi

- [Arguments nommés et facultatifs](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)
- [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [Guide pratique pour utiliser des arguments nommés et facultatifs dans la programmation Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Guide pratique pour accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)
- [Procédure pas à pas : programmation Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
