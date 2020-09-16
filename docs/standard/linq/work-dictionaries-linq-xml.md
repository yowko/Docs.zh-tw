---
title: 如何使用 LINQ to XML LINQ to XML 處理字典
description: 您可以將許多種類的資料結構轉換成 XML，也可以將 XML 轉換成結構。 以下是將 Generic 轉換成 XML 和 back 的範例。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: 9f6304dde828b3269f1cf369c3a6f14368676a48
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554483"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml"></a><span data-ttu-id="1fdc2-104">如何使用 LINQ to XML 利用字典</span><span class="sxs-lookup"><span data-stu-id="1fdc2-104">How to work with dictionaries using LINQ to XML</span></span>

<span data-ttu-id="1fdc2-105">將各種種類的資料結構轉換成 XML，然後將 XML 轉換成其他資料結構，通常會很方便。</span><span class="sxs-lookup"><span data-stu-id="1fdc2-105">It's often convenient to convert data structures of various kinds to XML, and then from XML to other data structures.</span></span> <span data-ttu-id="1fdc2-106">本文說明如何將轉換 <xref:System.Collections.Generic.Dictionary%602> 成 XML 和 back。</span><span class="sxs-lookup"><span data-stu-id="1fdc2-106">This article shows a conversion of a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>

## <a name="example-create-a-dictionary-and-convert-its-contents-to-xml"></a><span data-ttu-id="1fdc2-107">範例：建立字典，並將其內容轉換為 XML</span><span class="sxs-lookup"><span data-stu-id="1fdc2-107">Example: Create a Dictionary and convert its contents to XML</span></span>

<span data-ttu-id="1fdc2-108">第一個範例會建立 <xref:System.Collections.Generic.Dictionary%602> ，然後將它轉換為 XML。</span><span class="sxs-lookup"><span data-stu-id="1fdc2-108">This first example creates a <xref:System.Collections.Generic.Dictionary%602>, and then converts it to XML.</span></span>

<span data-ttu-id="1fdc2-109">此範例的 c # 版本會使用一種功能結構，其中查詢會投射新 <xref:System.Xml.Linq.XElement> 的物件，而產生的集合會以引數的形式傳遞至根物件的函式 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="1fdc2-109">This C# version of the example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>

<span data-ttu-id="1fdc2-110">Visual Basic 版本會在內嵌運算式中使用 XML 常值和查詢。</span><span class="sxs-lookup"><span data-stu-id="1fdc2-110">The Visual Basic version uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="1fdc2-111">查詢會投影新的 <xref:System.Xml.Linq.XElement> 物件，然後成為物件的新內容 `Root` <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="1fdc2-111">The query projects new <xref:System.Xml.Linq.XElement> objects which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>

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

<span data-ttu-id="1fdc2-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1fdc2-112">This example produces the following output:</span></span>

```xml
<Root>
  <Child1>Value1</Child1>
  <Child2>Value2</Child2>
  <Child3>Value3</Child3>
  <Child4>Value4</Child4>
</Root>
```

## <a name="example-create-a-dictionary-and-load-it-from-xml-data"></a><span data-ttu-id="1fdc2-113">範例：建立字典並從 XML 資料載入</span><span class="sxs-lookup"><span data-stu-id="1fdc2-113">Example: Create a dictionary and load it from XML data</span></span>

<span data-ttu-id="1fdc2-114">下一個範例會建立字典載入，從 XML 資料載入它。</span><span class="sxs-lookup"><span data-stu-id="1fdc2-114">The next example creates a dictionary loads loads it from XML data.</span></span>

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

<span data-ttu-id="1fdc2-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1fdc2-115">This example produces the following output:</span></span>

```output
Child1:Value1
Child2:Value2
Child3:Value3
Child4:Value4
```

## <a name="see-also"></a><span data-ttu-id="1fdc2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fdc2-116">See also</span></span>

- [<span data-ttu-id="1fdc2-117">投影作業 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="1fdc2-117">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
