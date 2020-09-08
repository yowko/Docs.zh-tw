---
title: 功能結構-LINQ to XML
description: LINQ to XML 提供功能結構，可讓您在單一語句中建立 XML 樹狀結構。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: bcdc153d7f60cfb165dcb741d62b6af5c07a148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552165"
---
# <a name="functional-construction-linq-to-xml"></a>功能結構 (LINQ to XML) 

LINQ to XML 提供了一種強大的方式來建立稱為「 *功能結構*」的 XML 元素。 功能結構可讓您在單一語句中建立 XML 樹狀結構。

在功能結構中使用 LINQ to XML 程式設計介面的幾個主要功能：

- <xref:System.Xml.Linq.XElement> 建構函式會針對內容採用各種引數類型。 例如，您可以傳遞變成子項目的其他 <xref:System.Xml.Linq.XElement> 物件。 您可以傳遞變成項目屬性的 <xref:System.Xml.Linq.XAttribute> 物件。 或者，您可以傳遞轉換成字串的其他類物件型，然後變成項目的文字內容。
- <xref:System.Xml.Linq.XElement> 建構函式會採用 `params` 類型的 <xref:System.Object> 陣列，讓您可以將任何數目的物件傳遞到建構函式。 這可讓您建立包含複雜內容的項目。
- 如果物件實作 <xref:System.Collections.Generic.IEnumerable%601>，系統列舉物件中的集合，並加入集合中的所有項目。 如果集合包含 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 物件，系統會個別加入集合中的每個項目。 這點很重要，因為它可讓您將 LINQ 查詢的結果傳遞給函式。

## <a name="example-create-an-xml-tree"></a>範例：建立 XML 樹狀結構

您可以使用功能結構來撰寫程式碼，以建立 XML 樹狀結構。 以下是一個範例：

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

## <a name="example-create-an-xml-tree-using-linq-query-results"></a>範例：使用 LINQ 查詢結果建立 XML 樹狀結構

當您建立 XML 樹狀結構時，這些功能也可讓您撰寫使用 LINQ 查詢結果的程式碼，如下列範例所示：

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

在 Visual Basic 中，您可以使用 XML 常值來完成相同的動作：

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where CInt(el) > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

這個範例會產生下列輸出：

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="see-also"></a>另請參閱

- [在 C 中建立 XML 樹狀結構#](create-xml-trees.md)
- [Visual Basic 中的 XML 常值](xml-literals.md)
