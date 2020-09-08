---
title: 不可部分完成的 XName 和 XNamespace 物件-LINQ to XML
description: 瞭解相同名稱的不可部分完成的 XName 和 XNamespace 物件如何共用實例。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: bc2be4d408385936598d94d34f9b452d950516d3
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552284"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml"></a><span data-ttu-id="23b60-103"> (LINQ to XML) 的不可部分完成的 XName 和 XNamespace 物件</span><span class="sxs-lookup"><span data-stu-id="23b60-103">Atomized XName and XNamespace objects (LINQ to XML)</span></span>

<span data-ttu-id="23b60-104"><xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 物件是「不可部分完成」\*\* 的物件。也就是說，如果它們包含相同的限定名稱，它們就會參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="23b60-104"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="23b60-105">這會產生查詢的效能優勢：當您比較兩個不可部分完成的名稱是否相等時，基礎中繼語言只需要判斷兩個參考是否指向相同的物件。</span><span class="sxs-lookup"><span data-stu-id="23b60-105">This yields performance benefits for queries: when you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="23b60-106">基礎程式碼不需要執行字串比較，這需要較長的時間。</span><span class="sxs-lookup"><span data-stu-id="23b60-106">The underlying code doesn't have to do string comparisons, which would take longer.</span></span>

## <a name="atomization-semantics"></a><span data-ttu-id="23b60-107">不可部分完成語義</span><span class="sxs-lookup"><span data-stu-id="23b60-107">Atomization semantics</span></span>

<span data-ttu-id="23b60-108">不可部分完成表示如果兩個 <xref:System.Xml.Linq.XName> 物件具有相同的本機名稱，而且它們在相同的命名空間中，它們就會共用相同的實例。</span><span class="sxs-lookup"><span data-stu-id="23b60-108">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they're in the same namespace, they share the same instance.</span></span> <span data-ttu-id="23b60-109">同樣地，如果兩個 <xref:System.Xml.Linq.XNamespace> 物件具有相同的命名空間 URI，它們就會共用相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="23b60-109">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>

<span data-ttu-id="23b60-110">若要讓某個類別 (Class) 啟用不可部分完成的物件，此類別的建構函式 (Constructor) 必須是私用 (Private) 而非公用 (Public)。</span><span class="sxs-lookup"><span data-stu-id="23b60-110">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="23b60-111">這是因為如果建構函式為公用，您就可以建立非不可部分完成的物件。</span><span class="sxs-lookup"><span data-stu-id="23b60-111">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="23b60-112"><xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 類別會實作隱含轉換運算子，將字串轉換成 <xref:System.Xml.Linq.XName> 或 <xref:System.Xml.Linq.XNamespace>。</span><span class="sxs-lookup"><span data-stu-id="23b60-112">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="23b60-113">這就是您取得這些物件之執行個體的方式。</span><span class="sxs-lookup"><span data-stu-id="23b60-113">This is how you get an instance of these objects.</span></span> <span data-ttu-id="23b60-114">因為無法存取函式，所以您無法使用函式來取得實例。</span><span class="sxs-lookup"><span data-stu-id="23b60-114">You can't get an instance by using a constructor, because the constructor is inaccessible.</span></span>

<span data-ttu-id="23b60-115"><xref:System.Xml.Linq.XName><xref:System.Xml.Linq.XNamespace>此外，也會執行相等和不等比較運算子，以判斷要比較的兩個物件是否為相同實例的參考。</span><span class="sxs-lookup"><span data-stu-id="23b60-115"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, which determine whether the two objects being compared are references to the same instance.</span></span>

## <a name="example-create-objects-and-show-that-identical-names-share-an-instance"></a><span data-ttu-id="23b60-116">範例：建立物件，並顯示相同的名稱共用實例</span><span class="sxs-lookup"><span data-stu-id="23b60-116">Example: Create objects and show that identical names share an instance</span></span>

<span data-ttu-id="23b60-117">下列程式碼會建立一些 <xref:System.Xml.Linq.XElement> 物件，並且示範相同的名稱會共用相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="23b60-117">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>

```csharp
XElement r1 = new XElement("Root", "data1");
XElement r2 = XElement.Parse("<Root>data2</Root>");

if ((object)r1.Name == (object)r2.Name)
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");
else
    Console.WriteLine("Different");

XName n = "Root";

if ((object)n == (object)r1.Name)
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");
else
    Console.WriteLine("Different");
```

```vb
Dim r1 As New XElement("Root", "data1")
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")

If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")
Else
    Console.WriteLine("Different")
End If

Dim n As XName = "Root"

If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")
Else
    Console.WriteLine("Different")
End If
```

<span data-ttu-id="23b60-118">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="23b60-118">This example produces the following output:</span></span>

```output
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

<span data-ttu-id="23b60-119">如先前所述，不可部分完成之物件的優點在於，當您使用其中一個採取 <xref:System.Xml.Linq.XName> 當做參數的座標軸方法時，此座標軸方法只需要判斷兩個名稱是否參考相同的執行個體，即可選取所需的項目。</span><span class="sxs-lookup"><span data-stu-id="23b60-119">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>

<span data-ttu-id="23b60-120">下列範例會將 <xref:System.Xml.Linq.XName> 傳遞至 <xref:System.Xml.Linq.XContainer.Descendants%2A> 方法呼叫，而且這樣做會由於不可部分完成模式而具有較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="23b60-120">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("C1", 1),
    new XElement("Z1",
        new XElement("C1", 2),
        new XElement("C1", 1)
    )
);

var query = from e in root.Descendants("C1")
            where (int)e == 1
            select e;

foreach (var z in query)
    Console.WriteLine(z);
```

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e

For Each z As var In query
    Console.WriteLine(z)
Next
```

<span data-ttu-id="23b60-121">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="23b60-121">This example produces the following output:</span></span>

```xml
<C1>1</C1>
<C1>1</C1>
```
