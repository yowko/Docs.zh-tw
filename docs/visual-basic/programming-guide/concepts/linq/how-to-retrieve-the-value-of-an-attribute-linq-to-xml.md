---
title: 作法：擷取屬性的值 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 48ad3c0ab079012793fd9eea89d52fc3a7b1698f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397800"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>如何：取出屬性的值（LINQ to XML）（Visual Basic）
這個主題顯示如何取得屬性的值。 有兩個主要方式：您可以將 <xref:System.Xml.Linq.XAttribute> 轉型為所需的型別；然後，明確的轉換運算子會將項目或屬性的內容轉換為指定的型別。 或者，您可以使用 <xref:System.Xml.Linq.XAttribute.Value%2A> 屬性。 不過，轉型通常是較好的方法。 如果您將屬性轉換成可為 null 的實值型別，則在抓取可能或可能不存在之屬性的值時，程式碼會比較容易撰寫。 如需這項技術的範例，請參閱[如何：取出元素的值（LINQ to XML）（Visual Basic）](how-to-retrieve-the-value-of-an-element-linq-to-xml.md)。  
  
## <a name="example"></a>範例  
 在 Visual Basic 中，您可以使用整合式屬性 (Attribute) 的屬性 (Property) 來擷取屬性 (Attribute) 的值。  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>範例  
 在 Visual Basic 中，您可以使用整合式屬性 (Attribute) 的屬性 (Property) 來設定屬性 (Attribute) 的值。 此外，如果您使用整合式屬性 (Attribute) 的屬性 (Property) 來設定不存在之屬性 (Attribute) 的值，將會建立這個屬性 (Attribute)。  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a>範例  
 下列範例顯示如何擷取屬性位於命名空間之屬性的值。 如需詳細資訊，請參閱[命名空間總覽（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 這個範例會產生下列輸出：  
  
```console  
abcde  
```  
  
## <a name="see-also"></a>另請參閱

- [LINQ to XML 軸 (Visual Basic)](linq-to-xml-axes.md)
