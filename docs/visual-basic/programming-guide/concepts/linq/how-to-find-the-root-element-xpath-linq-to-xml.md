---
title: 'Procédure : Rechercher l’élément racine (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 72c3aed5-9522-4454-a876-2070aad13f2e
ms.openlocfilehash: 6a08817c16bafb2ba1f91931f9718d6ef5053fb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687334"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-visual-basic"></a>Procédure : Rechercher l’élément racine (XPath-LINQ to XML) (Visual Basic)
Cette rubrique montre comment obtenir l'élément racine avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 L’expression XPath est la suivante :  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Exemple  
 Cet exemple recherche l'élément racine.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```vb  
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim el1 As XElement = po.Root  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1.Name)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a>Voir aussi
- [LINQ to XML pour les utilisateurs de XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
