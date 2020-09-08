---
title: 預設命名空間的範圍-LINQ to XML
description: XML 樹狀結構中表示的預設命名空間不在查詢的範圍內。 以下是查詢它們的適當且不適當的方式。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 105309a70e5fbf48c4e595d4064b11fe0378f81e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552820"
---
# <a name="scope-of-default-namespaces-linq-to-xml"></a><span data-ttu-id="dd5dc-104">預設命名空間的範圍 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="dd5dc-104">Scope of default namespaces (LINQ to XML)</span></span>

<span data-ttu-id="dd5dc-105">XML 樹狀結構中表示的預設命名空間不在查詢的範圍內。</span><span class="sxs-lookup"><span data-stu-id="dd5dc-105">Default namespaces as represented in the XML tree aren't in scope for queries.</span></span> <span data-ttu-id="dd5dc-106">如果您有在預設命名空間中的 XML，您必須結合命名空間與區功能變數名稱稱，以建立要在查詢中使用的限定名稱。</span><span class="sxs-lookup"><span data-stu-id="dd5dc-106">If you have XML that's in a default namespace, you must combine a namespace with the local name to make a qualified name to be used in the query.</span></span>

<span data-ttu-id="dd5dc-107">查詢具有預設命名空間的 XML 樹狀結構時，常見的錯誤是將查詢撰寫成 XML 不在命名空間中。</span><span class="sxs-lookup"><span data-stu-id="dd5dc-107">A common mistake in querying an XML tree that has a default namespace is to write the query as if the XML weren't in a namespace.</span></span> <span data-ttu-id="dd5dc-108">第一個範例顯示預設命名空間的一般不適當查詢。</span><span class="sxs-lookup"><span data-stu-id="dd5dc-108">The first example shows a typical improper query of a default namespace.</span></span> <span data-ttu-id="dd5dc-109">第二個範例顯示適當的查詢。</span><span class="sxs-lookup"><span data-stu-id="dd5dc-109">The second shows a proper query.</span></span>

## <a name="example-improper-query-of-xml-in-a-namespace"></a><span data-ttu-id="dd5dc-110">範例：命名空間中的 XML 查詢不正確</span><span class="sxs-lookup"><span data-stu-id="dd5dc-110">Example: Improper query of XML in a namespace</span></span>

<span data-ttu-id="dd5dc-111">此範例示範如何在命名空間中建立 XML，以及傳回空結果集的不適當查詢。</span><span class="sxs-lookup"><span data-stu-id="dd5dc-111">This example shows the creation of XML in a namespace, and an improper query that returns an empty result set.</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements("Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="dd5dc-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="dd5dc-112">This example produces the following output:</span></span>

```output
Result set follows:
End of result set
```

## <a name="example--proper-query-of-xml-in-a-namespace"></a><span data-ttu-id="dd5dc-113">範例：適當地查詢命名空間中的 XML</span><span class="sxs-lookup"><span data-stu-id="dd5dc-113">Example:  Proper query of XML in a namespace</span></span>

<span data-ttu-id="dd5dc-114">此範例示範如何在命名空間中建立 XML 和適當的查詢。</span><span class="sxs-lookup"><span data-stu-id="dd5dc-114">This example shows the creation of XML in a namespace, and a proper query.</span></span>

<span data-ttu-id="dd5dc-115">在 c # 中，正確的方法是宣告和初始化 <xref:System.Xml.Linq.XNamespace> 物件，並在指定物件時使用它 <xref:System.Xml.Linq.XName> 。</span><span class="sxs-lookup"><span data-stu-id="dd5dc-115">In C#, the correct approach is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="dd5dc-116">在這個情況下，<xref:System.Xml.Linq.XContainer.Elements%2A> 方法的引數為 <xref:System.Xml.Linq.XName> 物件。</span><span class="sxs-lookup"><span data-stu-id="dd5dc-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>

<span data-ttu-id="dd5dc-117">使用 Visual Basic 時的正確方法為宣告並初始化全域預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="dd5dc-117">The correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="dd5dc-118">這會將所有 XML 屬性放在預設的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="dd5dc-118">This places all XML properties in the default namespace.</span></span>

<span data-ttu-id="dd5dc-119">程式碼如下：</span><span class="sxs-lookup"><span data-stu-id="dd5dc-119">Here is the code:</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(el.Value)
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="dd5dc-120">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="dd5dc-120">This example produces the following output:</span></span>

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="dd5dc-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd5dc-121">See also</span></span>

- [<span data-ttu-id="dd5dc-122">命名空間總覽</span><span class="sxs-lookup"><span data-stu-id="dd5dc-122">Namespaces overview</span></span>](namespaces-overview.md)
