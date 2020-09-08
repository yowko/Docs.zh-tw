---
title: 如何取出屬性的值-LINQ to XML
description: 取得屬性的值。 您可以將 System.xml.linq.xattribute> 轉換為所需的型別，或使用 System.xml.linq.xattribute> 屬性。
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 7af3616c9808cad5dfb52f53c74b21a59da5c954
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552701"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml"></a>如何擷取屬性值 (LINQ to XML)

本文說明如何取得屬性的值。 有兩個主要方式：您可以將 <xref:System.Xml.Linq.XAttribute> 轉型為所需的型別；然後，明確的轉換運算子會將項目或屬性的內容轉換為指定的型別。 或者，您可以使用 <xref:System.Xml.Linq.XAttribute.Value%2A> 屬性。 不過，轉型通常是較好的方法。 如果您將屬性轉型為可為 null 的實值型別，則在抓取可能存在或可能不存在之屬性的值時，可以更輕鬆地撰寫程式碼。 如需這項技術的範例，請參閱 [如何取出元素的值](retrieve-value-element.md)。

## <a name="example-use-a-cast-to-retrieve-the-value-of-an-attribute"></a>範例：使用 cast 來取出屬性的值

若要在 c # 中取出屬性的值，請將 <xref:System.Xml.Linq.XAttribute> 物件轉換成所需的型別。 在 Visual Basic 中，您可以使用整合屬性屬性來取得值。

```csharp
XElement root = new XElement("Root",
                    new XAttribute("Attr", "abcde")
                );
Console.WriteLine(root);
string str = (string)root.Attribute("Attr");
Console.WriteLine(str);
```

```vb
Dim root As XElement = <Root Attr="abcde"/>
Console.WriteLine(root)
Dim str As String = root.@Attr
Console.WriteLine(str)
```

這個範例會產生下列輸出：

```output
<Root Attr="abcde" />
abcde
```

## <a name="example-use-a-cast-to-retrieve-from-xml-thats-in-a-namespace"></a>範例：使用轉換從命名空間中的 XML 取出

下列範例示範如何在屬性位於命名空間中時，取得屬性的值。 如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
                    new XAttribute(aw + "Attr", "abcde")
                );
string str = (string)root.Attribute(aw + "Attr");
Console.WriteLine(str);
```

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

```output
abcde
```

## <a name="see-also"></a>另請參閱

- [LINQ to XML 軸總覽](linq-xml-axes-overview.md)
