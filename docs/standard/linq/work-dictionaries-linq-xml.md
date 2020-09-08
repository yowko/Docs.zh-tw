---
title: 如何使用 LINQ to XML LINQ to XML 處理字典
description: 您可以將許多種類的資料結構轉換成 XML，也可以將 XML 轉換成結構。 以下是將 Generic 轉換成 XML 和 back 的範例。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: ea61a79549488765526f45852dae7a4df7cacb64
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552202"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml"></a>如何使用 LINQ to XML 利用字典

將各種種類的資料結構轉換成 XML，然後將 XML 轉換成其他資料結構，通常會很方便。 本文說明如何將轉換 <xref:System.Collections.Generic.Dictionary%602> 成 XML 和 back。

## <a name="example-create-a-dictionary-and-convert-its-contents-to-xml"></a>範例：建立字典，並將其內容轉換為 XML

第一個範例會建立 <xref:System.Collections.Generic.Dictionary%602> ，然後將它轉換為 XML。

此範例的 c # 版本會使用一種功能結構，其中查詢會投射新 <xref:System.Xml.Linq.XElement> 的物件，而產生的集合會以引數的形式傳遞至根物件的函式 <xref:System.Xml.Linq.XElement> 。

Visual Basic 版本會在內嵌運算式中使用 XML 常值和查詢。 查詢會投影新的 <xref:System.Xml.Linq.XElement> 物件，然後成為物件的新內容 `Root` <xref:System.Xml.Linq.XElement> 。

```csharp
Dictionary<string, string> dict = new Dictionary<string, string>();
dict.Add("Child1", "Value1");
dict.Add("Child2", "Value2");
dict.Add("Child3", "Value3");
dict.Add("Child4", "Value4");
XElement root = new XElement("Root",
    from keyValue in dict
    select new XElement(keyValue.Key, keyValue.Value)
);
Console.WriteLine(root);
```

```vb
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()
dict.Add("Child1", "Value1")
dict.Add("Child2", "Value2")
dict.Add("Child3", "Value3")
dict.Add("Child4", "Value4")
Dim root As XElement = _
    <Root>
        <%= From keyValue In dict _
            Select New XElement(keyValue.Key, keyValue.Value) %>
    </Root>
Console.WriteLine(root)
```

這個範例會產生下列輸出：

```xml
<Root>
  <Child1>Value1</Child1>
  <Child2>Value2</Child2>
  <Child3>Value3</Child3>
  <Child4>Value4</Child4>
</Root>
```

## <a name="example-create-a-dictionary-and-load-it-from-xml-data"></a>範例：建立字典並從 XML 資料載入

下一個範例會建立字典載入，從 XML 資料載入它。

```csharp
XElement root = new XElement("Root",
    new XElement("Child1", "Value1"),
    new XElement("Child2", "Value2"),
    new XElement("Child3", "Value3"),
    new XElement("Child4", "Value4")
);

Dictionary<string, string> dict = new Dictionary<string, string>();
foreach (XElement el in root.Elements())
    dict.Add(el.Name.LocalName, el.Value);
foreach (string str in dict.Keys)
    Console.WriteLine("{0}:{1}", str, dict[str]);
```

```vb
Dim root As XElement = _
        <Root>
            <Child1>Value1</Child1>
            <Child2>Value2</Child2>
            <Child3>Value3</Child3>
            <Child4>Value4</Child4>
        </Root>

Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)
For Each el As XElement In root.Elements
    dict.Add(el.Name.LocalName, el.Value)
Next
For Each str As String In dict.Keys
    Console.WriteLine("{0}:{1}", str, dict(str))
Next
```

這個範例會產生下列輸出：

```output
Child1:Value1
Child2:Value2
Child3:Value3
Child4:Value4
```

## <a name="see-also"></a>另請參閱

- [投影和轉換 (LINQ to XML)  (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
