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
# <a name="statically-compiled-queries-linq-to-xml"></a><span data-ttu-id="4e689-103">靜態編譯的查詢 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="4e689-103">Statically compiled queries (LINQ to XML)</span></span>

<span data-ttu-id="4e689-104">相較之下，LINQ to XML 最重要的其中一項效能優點， <xref:System.Xml.XmlDocument> 是 LINQ to XML 中的查詢是以靜態方式編譯，而 XPath 查詢則必須在執行時間進行解讀。</span><span class="sxs-lookup"><span data-stu-id="4e689-104">One of the most important performance advantages of LINQ to XML, as compared to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="4e689-105">這項功能內建于 LINQ to XML 中，因此您不需要執行額外的步驟來利用它，但是在選擇這兩項技術時瞭解其差異會很有説明。</span><span class="sxs-lookup"><span data-stu-id="4e689-105">This feature is built into LINQ to XML, so you don't have to perform extra steps to take advantage of it, but it's helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="4e689-106">本文說明差異。</span><span class="sxs-lookup"><span data-stu-id="4e689-106">This article explains the difference.</span></span>

## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="4e689-107">靜態編譯的查詢與 XPath</span><span class="sxs-lookup"><span data-stu-id="4e689-107">Statically compiled queries vs. XPath</span></span>

<span data-ttu-id="4e689-108">下列範例將顯示如何取得具有指定之名稱以及具有指定值之屬性的子代項目。</span><span class="sxs-lookup"><span data-stu-id="4e689-108">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span> <span data-ttu-id="4e689-109">對等的 XPath 運算式是 `//Address[@Type='Shipping']` 。</span><span class="sxs-lookup"><span data-stu-id="4e689-109">The equivalent XPath expression is `//Address[@Type='Shipping']`.</span></span>

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

<span data-ttu-id="4e689-110">編譯器會將此範例中的查詢運算式重寫為以方法為基礎的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="4e689-110">The query expression in this example is rewritten by the compiler to method-based query syntax.</span></span> <span data-ttu-id="4e689-111">下列範例 (使用以方法為基礎的查詢語法所撰寫) 會與先前的範例產生相同的結果：</span><span class="sxs-lookup"><span data-stu-id="4e689-111">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>

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

<span data-ttu-id="4e689-112"><xref:System.Linq.Enumerable.Where%2A> 方法是擴充方法。</span><span class="sxs-lookup"><span data-stu-id="4e689-112">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="4e689-113">如需詳細資訊，請參閱 [ (c # 程式設計手冊) 的擴充方法 ](../../csharp/programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="4e689-113">For more information, see [Extension Methods (C# Programming Guide)](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="4e689-114">由於 <xref:System.Linq.Enumerable.Where%2A> 是擴充方法，所以上述查詢會按照下列方式編譯：</span><span class="sxs-lookup"><span data-stu-id="4e689-114">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>

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

<span data-ttu-id="4e689-115">這則範例會與先前兩則範例產生完全相同的結果。</span><span class="sxs-lookup"><span data-stu-id="4e689-115">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="4e689-116">這表示查詢實際上會編譯成靜態連結方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="4e689-116">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="4e689-117">與 Iterator 的延後執行語意 (Semantics) 結合之後，便可改善效能。</span><span class="sxs-lookup"><span data-stu-id="4e689-117">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="4e689-118">如需反覆運算器的順延強制語義的詳細資訊，請參閱 [延後執行和延遲評估](deferred-execution-lazy-evaluation.md)。</span><span class="sxs-lookup"><span data-stu-id="4e689-118">For more information about the deferred execution semantics of iterators, see [Deferred execution and lazy evaluation](deferred-execution-lazy-evaluation.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4e689-119">這些範例是代表編譯器可能會撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4e689-119">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="4e689-120">實際的實值可能會與這些範例稍有不同，但效能會與這些範例相同或類似。</span><span class="sxs-lookup"><span data-stu-id="4e689-120">The actual implementation might differ slightly from these examples, but the performance will be the same as, or similar to, these examples.</span></span>

## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="4e689-121">使用 Xml 執行 XPath 運算式</span><span class="sxs-lookup"><span data-stu-id="4e689-121">Executing XPath expressions with XmlDocument</span></span>

<span data-ttu-id="4e689-122">下列範例會使用 <xref:System.Xml.XmlDocument> 來達成與先前範例相同的結果：</span><span class="sxs-lookup"><span data-stu-id="4e689-122">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>

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

<span data-ttu-id="4e689-123">此查詢會傳回與使用 LINQ to XML 的範例相同的輸出;唯一的差別是 LINQ to XML 會縮排列印的 XML，而 <xref:System.Xml.XmlDocument> 不是。</span><span class="sxs-lookup"><span data-stu-id="4e689-123">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> doesn't.</span></span>

<span data-ttu-id="4e689-124">不過，此方法 <xref:System.Xml.XmlDocument> 通常不會執行和 LINQ to XML，因為 <xref:System.Xml.XmlNode.SelectNodes%2A> 方法每次呼叫時都必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="4e689-124">However, the <xref:System.Xml.XmlDocument> approach generally doesn't perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following every time it's called:</span></span>

- <span data-ttu-id="4e689-125">剖析包含 XPath 運算式的字串，並將字串分解為標記。</span><span class="sxs-lookup"><span data-stu-id="4e689-125">Parse the string that contains the XPath expression, breaking the string into tokens.</span></span>
- <span data-ttu-id="4e689-126">驗證權杖，以確定 XPath 運算式是有效的。</span><span class="sxs-lookup"><span data-stu-id="4e689-126">Validate the tokens to make sure that the XPath expression is valid.</span></span>
- <span data-ttu-id="4e689-127">將運算式轉譯為內部運算式樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="4e689-127">Translate the expression into an internal expression tree.</span></span>
- <span data-ttu-id="4e689-128">逐一查看節點，根據運算式的評估，適當地選取結果集的節點。</span><span class="sxs-lookup"><span data-stu-id="4e689-128">Iterate through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>

<span data-ttu-id="4e689-129">這點明顯比對應 LINQ to XML 查詢所完成的工作還多。</span><span class="sxs-lookup"><span data-stu-id="4e689-129">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="4e689-130">雖然特定效能差異會因不同類型的查詢而異，不過一般而言，相較於使用 <xref:System.Xml.XmlDocument> 來評估 XPath 運算式，LINQ to XML 查詢會進行較少工作，因此具有較佳的執行效能。</span><span class="sxs-lookup"><span data-stu-id="4e689-130">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>
