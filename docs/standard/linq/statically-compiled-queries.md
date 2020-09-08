---
title: 靜態編譯的查詢-LINQ to XML
description: 透過靜態編譯，瞭解 LINQ to XML 查詢如何獲得優於的效能優勢。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 53dd47247eae8802dcf8187d0e82eb1c8bead9f9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552252"
---
# <a name="statically-compiled-queries-linq-to-xml"></a>靜態編譯的查詢 (LINQ to XML) 

相較之下，LINQ to XML 最重要的其中一項效能優點， <xref:System.Xml.XmlDocument> 是 LINQ to XML 中的查詢是以靜態方式編譯，而 XPath 查詢則必須在執行時間進行解讀。 這項功能內建于 LINQ to XML 中，因此您不需要執行額外的步驟來利用它，但是在選擇這兩項技術時瞭解其差異會很有説明。 本文說明差異。

## <a name="statically-compiled-queries-vs-xpath"></a>靜態編譯的查詢與 XPath

下列範例將顯示如何取得具有指定之名稱以及具有指定值之屬性的子代項目。 對等的 XPath 運算式是 `//Address[@Type='Shipping']` 。

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    from el in po.Descendants("Address")
    where (string)el.Attribute("Type") == "Shipping"
    select el;

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = From el In po.Descendants("Address")
            Where el.@Type = "Shipping"

For Each el In list1
    Console.WriteLine(el)
Next
```

編譯器會將此範例中的查詢運算式重寫為以方法為基礎的查詢語法。 下列範例 (使用以方法為基礎的查詢語法所撰寫) 會與先前的範例產生相同的結果：

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    po
    .Descendants("Address")
    .Where(el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

 ```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<xref:System.Linq.Enumerable.Where%2A> 方法是擴充方法。 如需詳細資訊，請參閱 [ (c # 程式設計手冊) 的擴充方法 ](../../csharp/programming-guide/classes-and-structs/extension-methods.md)。 由於 <xref:System.Linq.Enumerable.Where%2A> 是擴充方法，所以上述查詢會按照下列方式編譯：

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    System.Linq.Enumerable.Where(
        po.Descendants("Address"),
        el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

這則範例會與先前兩則範例產生完全相同的結果。 這表示查詢實際上會編譯成靜態連結方法呼叫。 與 Iterator 的延後執行語意 (Semantics) 結合之後，便可改善效能。 如需反覆運算器的順延強制語義的詳細資訊，請參閱 [延後執行和延遲評估](deferred-execution-lazy-evaluation.md)。

> [!NOTE]
> 這些範例是代表編譯器可能會撰寫的程式碼。 實際的實值可能會與這些範例稍有不同，但效能會與這些範例相同或類似。

## <a name="executing-xpath-expressions-with-xmldocument"></a>使用 Xml 執行 XPath 運算式

下列範例會使用 <xref:System.Xml.XmlDocument> 來達成與先前範例相同的結果：

```csharp
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");
XmlDocument doc = new XmlDocument();
doc.Load(reader);
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");
foreach (XmlNode n in nl)
    Console.WriteLine(n.OuterXml);
reader.Close();
```

```vb
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")
Dim doc As New Xml.XmlDocument()
doc.Load(reader)
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")
For Each n As Xml.XmlNode In nl
    Console.WriteLine(n.OuterXml)
Next
reader.Close()
```

此查詢會傳回與使用 LINQ to XML 的範例相同的輸出;唯一的差別是 LINQ to XML 會縮排列印的 XML，而 <xref:System.Xml.XmlDocument> 不是。

不過，此方法 <xref:System.Xml.XmlDocument> 通常不會執行和 LINQ to XML，因為 <xref:System.Xml.XmlNode.SelectNodes%2A> 方法每次呼叫時都必須執行下列動作：

- 剖析包含 XPath 運算式的字串，並將字串分解為標記。
- 驗證權杖，以確定 XPath 運算式是有效的。
- 將運算式轉譯為內部運算式樹狀結構。
- 逐一查看節點，根據運算式的評估，適當地選取結果集的節點。

這點明顯比對應 LINQ to XML 查詢所完成的工作還多。 雖然特定效能差異會因不同類型的查詢而異，不過一般而言，相較於使用 <xref:System.Xml.XmlDocument> 來評估 XPath 運算式，LINQ to XML 查詢會進行較少工作，因此具有較佳的執行效能。
