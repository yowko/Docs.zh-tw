---
title: 預先不可部分完成的 XName 物件-LINQ to XML
description: 瞭解如何在建立具有相同名稱的大量元素時，預先不可部分完成以改善效能。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 97da1e09e246491d8427c7a69953e006c80475a4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552161"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml"></a>XName 物件的預先不可部分完成 (LINQ to XML) 

在 LINQ to XML 中，改善效能的其中一種方式就是預先不可部分完成 <xref:System.Xml.Linq.XName> 物件。 預先不可部分完成是表示，您先指派字串給 <xref:System.Xml.Linq.XName> 物件，然後再使用 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XAttribute> 類別 (Class) 的建構函式 (Constructor) 來建立 XML 樹狀結構。 接著，您會傳遞初始化的 <xref:System.Xml.Linq.XName> 物件，而非將字串傳遞至建構函式 (會使用隱含轉換，從字串轉換成 <xref:System.Xml.Linq.XName>)。

當您建立會重複名稱的大型 XML 樹狀結構時，這可改善效能。 若要這樣做，請在建構 XML 樹狀結構之前宣告並初始化 <xref:System.Xml.Linq.XName> 物件，然後使用 <xref:System.Xml.Linq.XName> 物件，而非指定項目和屬性名稱的字串。 如果您要建立具有相同名稱的大量元素或屬性，這項技術可能會產生顯著的效能提升。

您應該使用自己的案例來測試預先不可部分完成，以便決定是否應該使用此作業。

## <a name="example-create-elements-in-various-ways-with-and-without-pre-atomization"></a>範例：使用和不使用預先不可部分完成的各種方式建立元素

下列範例示範預先不可部分完成。

```csharp
XName Root = "Root";
XName Data = "Data";
XName ID = "ID";

XElement root = new XElement(Root,
    new XElement(Data,
        new XAttribute(ID, "1"),
        "4,100,000"),
    new XElement(Data,
        new XAttribute(ID, "2"),
        "3,700,000"),
    new XElement(Data,
        new XAttribute(ID, "3"),
        "1,150,000")
);

Console.WriteLine(root);
```

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

這個範例會產生下列輸出：

```xml
<Root>
  <Data ID="1">4,100,000</Data>
  <Data ID="2">3,700,000</Data>
  <Data ID="3">1,150,000</Data>
</Root>
```

下列範例顯示命名空間中 XML 檔的相同技術：

```csharp
XNamespace aw = "http://www.adventure-works.com";
XName Root = aw + "Root";
XName Data = aw + "Data";
XName ID = "ID";

XElement root = new XElement(Root,
    new XAttribute(XNamespace.Xmlns + "aw", aw),
    new XElement(Data,
        new XAttribute(ID, "1"),
        "4,100,000"),
    new XElement(Data,
        new XAttribute(ID, "2"),
        "3,700,000"),
    new XElement(Data,
        new XAttribute(ID, "3"),
        "1,150,000")
);

Console.WriteLine(root);
```

```vb
Dim aw As XNamespace = "http://www.adventure-works.com"
Dim root1 As XName = aw + "Root"
Dim data As XName = aw + "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XAttribute(XNamespace.Xmlns + "aw", aw),
                          New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

這個範例會產生下列輸出：

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Data ID="1">4,100,000</aw:Data>
  <aw:Data ID="2">3,700,000</aw:Data>
  <aw:Data ID="3">1,150,000</aw:Data>
</aw:Root>
```

下列範例更類似於您可能會在真實世界中遇到的狀況。 在此範例中，項目的內容是由查詢提供：

```csharp
XName Root = "Root";
XName Data = "Data";
XName ID = "ID";

DateTime t1 = DateTime.Now;
XElement root = new XElement(Root,
    from i in System.Linq.Enumerable.Range(1, 100000)
    select new XElement(Data,
        new XAttribute(ID, i),
        i * 5)
);
DateTime t2 = DateTime.Now;

Console.WriteLine("Time to construct:{0}", t2 - t1);
```

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"

Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root2 As New XElement(root1, From i In Enumerable.Range(1, 100000)
                                 Select New XElement(data, New XAttribute(ID, i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```

上述範例的執行效果優於下列範例，其中的名稱不會預先原子化：

```csharp
DateTime t1 = DateTime.Now;
XElement root = new XElement("Root",
    from i in System.Linq.Enumerable.Range(1, 100000)
    select new XElement("Data",
        new XAttribute("ID", i),
        i * 5)
);
DateTime t2 = DateTime.Now;

Console.WriteLine("Time to construct:{0}", t2 - t1);
```

```vb
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root As New XElement("Root", From i In Enumerable.Range(1, 100000)
                                 Select New XElement("Data", New XAttribute("ID", i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```

## <a name="see-also"></a>另請參閱

- [不可部分完成的 XName 和 XNamespace 物件](atomized-xname-xnamespace-objects.md)
