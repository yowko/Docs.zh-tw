---
title: 作法：擷取屬性的集合 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: be7abac736f9a70ae3f0c9efe2074cfe79821ddb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397878"
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
  
## <a name="see-also"></a>另請參閱

- [LINQ to XML 軸 (Visual Basic)](linq-to-xml-axes.md)
