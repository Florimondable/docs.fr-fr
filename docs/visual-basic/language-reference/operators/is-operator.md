---
title: Is, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: a78189a6b82100665ac07b9d7c89590613ec1e1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745621"
---
# <a name="is-operator-visual-basic"></a>Is, opérateur (Visual Basic)
Compare deux variables de référence d’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Composants  
 `result`  
 Obligatoire. N’importe quel `Boolean` valeur.  
  
 `object1`  
 Obligatoire. N’importe quel `Object` nom.  
  
 `object2`  
 Obligatoire. N’importe quel `Object` nom.  
  
## <a name="remarks"></a>Notes  
 Le `Is` opérateur détermine si deux références d’objet font référence au même objet. Toutefois, il n’effectue pas de comparaisons de valeurs. Si `object1` et `object2` se rapportent à la même instance d’objet, `result` est `True`; si elles ne le faites pas, `result` est `False`.  
  
 `Is` peut également être utilisé avec le `TypeOf` mot clé pour rendre un `TypeOf`... `Is` expression, qui teste si une variable objet est compatible avec un type de données.  
  
> [!NOTE]
>  Le `Is` clé est également utilisé dans le [sélectionnez... Instruction case](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Is` opérateur pour comparer des paires de références d’objet. Les résultats sont affectés à un `Boolean` valeur indiquant si les deux objets sont identiques.  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 Comme illustré dans l’exemple précédent, vous pouvez utiliser le `Is` opérateur pour tester les deux à liaison anticipée et tardive des objets.  
  
## <a name="see-also"></a>Voir aussi
- [TypeOf (opérateur)](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot (opérateur)](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Opérateurs de comparaison en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
