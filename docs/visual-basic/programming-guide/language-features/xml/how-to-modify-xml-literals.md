---
title: 'Procédure : Modifier des littéraux XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 7a01fdc9d0541b5d277c2f283e25e9a1cef3b862
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636337"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>Procédure : Modifier des littéraux XML (Visual Basic)
Visual Basic offre des moyens pratiques de modifier des littéraux XML. Vous pouvez ajouter ou supprimer des éléments et attributs, et vous pouvez également remplacer un élément existant par un nouvel élément XML. Cette rubrique fournit plusieurs exemples montrant comment modifier un littéral XML existant.  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a>Pour modifier la valeur d’un littéral XML  
  
1.  Pour modifier la valeur d’un littéral XML, obtenez une référence au document XML littéral et définissez le `Value` propriété la valeur souhaitée.  
  
     L’exemple de code suivant met à jour la valeur de tous les \<prix > éléments dans un document XML.  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     Ce qui suit montre l’exemple de source XML et XML modifié à partir de cet exemple de code.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>47.20</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>48.25</Price>  
      </Book>  
    </Catalog>  
    ```  
  
    > [!NOTE]
    >  Le `Value` propriété fait référence au premier élément XML dans une collection. S’il existe plus d’un élément qui porte le même nom dans une collection, définissant le `Value` propriété affecte uniquement le premier élément dans la collection.  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a>Pour ajouter un attribut à un littéral XML  
  
1.  Pour ajouter un attribut à un littéral XML, tout d’abord obtenir une référence au littéral XML. Vous pouvez ensuite ajouter un attribut en ajoutant une nouvelle propriété de l’axe d’attribut XML. Vous pouvez également ajouter un nouveau <xref:System.Xml.Linq.XAttribute> objet pour le littéral à l’aide de XML le <xref:System.Xml.Linq.XContainer.Add%2A> (méthode). L’exemple suivant montre les deux options.  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     Ce qui suit montre l’exemple de source XML et XML modifié à partir de cet exemple de code.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
    ```  
  
     Pour plus d’informations sur les propriétés de l’axe d’attribut XML, consultez [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).  
  
### <a name="to-add-an-element-to-an-xml-literal"></a>Pour ajouter un élément à un littéral XML  
  
1.  Pour ajouter un élément à un littéral XML, tout d’abord obtenir une référence au littéral XML. Vous pouvez ensuite ajouter un nouveau <xref:System.Xml.Linq.XElement> objet en tant que le dernier sous-élément de l’élément à l’aide de la <xref:System.Xml.Linq.XContainer.Add%2A> (méthode). Vous pouvez ajouter un nouveau <xref:System.Xml.Linq.XElement> objet sous la forme du premier sous-élément à l’aide de la <xref:System.Xml.Linq.XContainer.AddFirst%2A> (méthode).  
  
     Pour ajouter un nouvel élément dans un emplacement spécifique par rapport à d’autres sous-éléments, tout d’abord obtenir une référence à un sous-élément adjacent. Vous pouvez ensuite ajouter le nouveau <xref:System.Xml.Linq.XElement> objet avant le sous-élément adjacent à l’aide de la <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> (méthode). Vous pouvez également ajouter le nouveau <xref:System.Xml.Linq.XElement> objet après le sous-élément adjacent à l’aide de la <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> (méthode).  
  
     L’exemple suivant montre des exemples de chacune de ces techniques.  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     Ce qui suit montre l’exemple de source XML et XML modifié à partir de cet exemple de code.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331">  
        <Publisher>Microsoft Press</Publisher>  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
        <PublishDate>2005-2-14</PublishDate>  
      </Book>  
      <Book id="bk999"></Book>  
    </Catalog>  
    ```  
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>Pour supprimer un élément ou attribut d’un littéral XML  
  
1.  Pour supprimer un élément ou un attribut d’un littéral XML, obtenez une référence à l’élément ou un attribut et un appel de la `Remove` méthode, comme indiqué dans l’exemple suivant.  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     Ce qui suit montre l’exemple de source XML et XML modifié à partir de cet exemple de code.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
      <Book id="bk999"></Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book></Catalog>  
    ```  
  
     Pour supprimer tous les éléments ou attributs à partir d’un littéral XML, obtenez une référence au littéral XML et appelez le <xref:System.Xml.Linq.XElement.RemoveAll%2A> (méthode).  
  
### <a name="to-modify-an-xml-literal"></a>Pour modifier un littéral XML  
  
1.  Pour modifier le nom d’un élément XML, tout d’abord obtenir une référence à l’élément. Vous pouvez ensuite créer un nouveau <xref:System.Xml.Linq.XElement> objet qui dispose d’un nouveau nom et passer le nouveau <xref:System.Xml.Linq.XElement> de l’objet à la <xref:System.Xml.Linq.XNode.ReplaceWith%2A> méthode existants <xref:System.Xml.Linq.XElement> objet.  
  
     Si l’élément que vous remplacez comporte des sous-éléments qui doivent être conservés, définissez la valeur de la nouvelle <xref:System.Xml.Linq.XElement> de l’objet à le <xref:System.Xml.Linq.XContainer.Nodes%2A> propriété de l’élément existant. Cela définit la valeur du nouvel élément au document XML interne de l’élément existant. Sinon, vous pouvez définir la valeur du nouvel élément à la `Value` propriété de l’élément existant.  
  
     L’exemple de code suivant remplace tous les \<Description > éléments avec un \<abstraite > élément. Le contenu de la \<Description > élément est conservé dans le nouveau \<abstraite > élément à l’aide de la <xref:System.Xml.Linq.XContainer.Nodes%2A> propriété de la \<Description > <xref:System.Xml.Linq.XElement> objet.  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     Ce qui suit montre l’exemple de source XML et XML modifié à partir de cet exemple de code.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
        <Description>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Description>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
        <Description>  
          Get the expert insights, practical code samples, and best  
          practices you need to advance your expertise with   
          <technology>Visual Basic .NET</technology>.   
          Learn how to create faster, more reliable applications  
          based on professional, pragmatic guidance by today's top  
          <audience>developers</audience>.  
        </Description>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <MSRP>44.95</MSRP>    <Abstract>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Abstract>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <MSRP>45.95</MSRP>    <Abstract>  
          Get the expert insights, practical code samples, and best  
          practices you need to advance your expertise with   
          <technology>Visual Basic .NET</technology>.   
          Learn how to create faster, more reliable applications  
          based on professional, pragmatic guidance by today's top  
          <audience>developers</audience>.  
        </Abstract>  
      </Book>  
    </Catalog>  
    ```  
  
## <a name="see-also"></a>Voir aussi
- [Manipulation de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Guide pratique pour Charger XML à partir d’un fichier, une chaîne ou un Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
