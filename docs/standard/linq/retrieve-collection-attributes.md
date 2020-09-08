---
title: 如何取出屬性的集合-LINQ to XML
description: 瞭解如何使用 System.xml.linq.xelement> 方法來取出專案的屬性。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: a15375ffd6b3af7fb9119e3321495cffa00268e4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552156"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml"></a>如何擷取屬性集合 (LINQ to XML)

本文說明 <xref:System.Xml.Linq.XElement.Attributes%2A> 如何使用方法來取出專案的屬性。

## <a name="example-iterate-through-the-attributes-of-an-element"></a>範例：逐一查看元素的屬性

下列範例顯示如何逐一查看項目之屬性的集合。

```csharp
XElement val = new XElement("Value",
    new XAttribute("ID", "1243"),
    new XAttribute("Type", "int"),
    new XAttribute("ConvertableTo", "double"),
    "100");
IEnumerable<XAttribute> listOfAttributes =
    from att in val.Attributes()
    select att;
foreach (XAttribute a in listOfAttributes)
    Console.WriteLine(a);
```

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

這個範例會產生下列輸出：

```output
ID="1243"
Type="int"
ConvertableTo="double"
```

## <a name="see-also"></a>另請參閱

- [LINQ to XML 軸總覽](linq-xml-axes-overview.md)
