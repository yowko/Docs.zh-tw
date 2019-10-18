---
title: 如何：取出屬性的集合（LINQ to XML）（Visual Basic）
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: 7c0f809c5a0707f2e6575cb8bca1b2a312f6daeb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321330"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a>如何：取出屬性的集合（LINQ to XML）（Visual Basic）
本主題說明 <xref:System.Xml.Linq.XElement.Attributes%2A> 方法。 這個方法會擷取項目的屬性。  
  
## <a name="example"></a>範例  
 下列範例顯示如何逐一查看項目之屬性的集合。  
  
```vb  
Dim val = _  
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>  
Dim listOfAttributes As IEnumerable(Of XAttribute) = _  
    From att In val.Attributes() _  
    Select att  
For Each att As XAttribute In listOfAttributes  
    Console.WriteLine(att)  
Next  
```  
  
 此程式碼會產生下列輸出：  
  
```console  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>請參閱

- [LINQ to XML 軸 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
