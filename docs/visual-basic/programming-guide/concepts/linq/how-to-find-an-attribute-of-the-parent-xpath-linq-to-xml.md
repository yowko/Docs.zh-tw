---
title: 如何：尋找父代的屬性 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: c4cb2f2e52aeaa42fd69b83c19c47fd205d48cbc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352950"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a>如何：尋找父系的屬性（XPath-LINQ to XML）（Visual Basic）
這個主題顯示如何導覽到父項目並尋找其屬性。  
  
 XPath 運算式為：  
  
 `../@id`  
  
## <a name="example"></a>範例  
 這個範例會先尋找 `Author` 項目。 接著，它會尋找父項目的 `id` 屬性。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)。  
  
```vb  
Dim books As XDocument = XDocument.Load("Books.xml")  
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()  
  
' LINQ to XML query  
Dim att1 As XAttribute = author.Parent.Attribute("id")  
  
' XPath expression  
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _  
    IEnumerable).Cast(Of XAttribute)().First()  
  
If att1 Is att2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(att1)  
```  
  
 這個範例會產生下列輸出：  
  
```console  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ to XML （Visual Basic）](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
