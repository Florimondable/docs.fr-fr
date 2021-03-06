---
title: "'<typename>' est un type délégué"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 4278ea0fc6a8dc2c6a90b720d2da70b1c26f2a17
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283450"
---
# <a name="typename-is-a-delegate-type"></a>'\<nom_type >' est un type délégué
'\<nom_type >' est un type délégué. Une construction déléguée accepte une seule expression AddressOf comme une liste d’arguments. Une expression AddressOf peut souvent être utilisée au lieu d’une construction de délégué.  
  
 Un `New` clause création d’une instance d’une classe déléguée fournit une liste d’arguments non valide au constructeur délégué.  
  
 Vous pouvez fournir une seule `AddressOf` expression lors de la création d’une nouvelle instance de délégué.  
  
 Cette erreur peut se produire si vous ne passez pas d’arguments au constructeur délégué, si vous passez plusieurs arguments, ou si vous passez un argument unique qui n’est pas valide `AddressOf` expression.  
  
 **ID d’erreur :** BC32008  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Utiliser une seule `AddressOf` expression dans la liste d’arguments pour la classe déléguée dans le `New` clause.  
  
## <a name="see-also"></a>Voir aussi
- [New (opérateur)](../../../visual-basic/language-reference/operators/new-operator.md)
- [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Guide pratique pour Appeler une méthode déléguée](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
