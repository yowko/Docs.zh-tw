---
title: 如何從 XmlReader 建立樹狀結構-LINQ to XML
description: '您可以使用 c # 或 Visual Basic 中的 XmlReader 來讀取 XML 並建立 XML 樹狀結構。 您必須適當地將 XmlReader 放置於元素節點上。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 659135ae9930d4ba63b13e436ebd278807e4256b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552198"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-linq-to-xml"></a>如何從 XmlReader (LINQ to XML) 建立樹狀結構

本文說明如何直接從 <xref:System.Xml.XmlReader> c # 或 Visual Basic 中的來建立 XML 樹狀結構。 若要 <xref:System.Xml.Linq.XElement> 從建立 <xref:System.Xml.XmlReader> ，請將放置在 <xref:System.Xml.XmlReader> 元素節點上。 <xref:System.Xml.XmlReader> 將會略過註解與處理指示，但是，如果 <xref:System.Xml.XmlReader> 定位在文字節點上，則會擲出錯誤。 若要避免這類錯誤，請 <xref:System.Xml.XmlReader> 在從建立 XML 樹狀結構之前，先將放置在元素上 <xref:System.Xml.XmlReader> 。

## <a name="example-load-xelement-object-from-an-xmlreader-object"></a>範例：從 XmlReader 物件載入 System.xml.linq.xelement> 物件

此範例會使用 XML [檔範例 xml 檔：書籍](sample-xml-file-books.md)。

下列程式碼會建立 <xref:System.Xml.XmlReader> 物件、讀取節點，直到它找到第一個元素節點，然後載入 <xref:System.Xml.Linq.XElement> 物件為止。

```csharp
XmlReader r = XmlReader.Create("books.xml");
while (r.NodeType != XmlNodeType.Element)
    r.Read();
XElement e = XElement.Load(r);
Console.WriteLine(e);
```

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

這個範例會產生下列輸出：

```xml
<Catalog>
   <Book id="bk101">
      <Author>Garghentini, Davide</Author>
      <Title>XML Developer's Guide</Title>
      <Genre>Computer</Genre>
      <Price>44.95</Price>
      <PublishDate>2000-10-01</PublishDate>
      <Description>An in-depth look at creating applications
      with XML.</Description>
   </Book>
   <Book id="bk102">
      <Author>Garcia, Debra</Author>
      <Title>Midnight Rain</Title>
      <Genre>Fantasy</Genre>
      <Price>5.95</Price>
      <PublishDate>2000-12-16</PublishDate>
      <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>
   </Book>
</Catalog>
```

## <a name="see-also"></a>另請參閱

- [剖析 XML](parse-string.md)
