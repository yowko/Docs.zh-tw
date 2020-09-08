---
title: Visual Basic 中的 XML 常值-LINQ to XML
description: 您可以使用 XML 常值和內嵌運算式，在 Visual Basic 中建立 XML 樹狀結構。 內嵌的運算式可讓您評估運算式，並將運算式的結果插入到 XML 樹狀中。
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: e3b1213672a6a7ddd71fcc38b4502108a6f49881
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552200"
---
# <a name="xml-literals-in-visual-basic-linq-to-xml"></a><span data-ttu-id="dc809-104">Visual Basic 中的 XML 常值 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="dc809-104">XML Literals in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="dc809-105">本文提供有關使用 XML 常值和內嵌運算式在 Visual Basic 中建立 XML 樹狀結構的資訊。</span><span class="sxs-lookup"><span data-stu-id="dc809-105">This article provides information about creating XML trees in Visual Basic using XML literals and embedded expressions.</span></span>

## <a name="example-use-xml-literals-to-create-an-xml-tree"></a><span data-ttu-id="dc809-106">範例：使用 XML 常值建立 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="dc809-106">Example: Use XML literals to create an XML tree</span></span>

<span data-ttu-id="dc809-107">下列範例示範如何 <xref:System.Xml.Linq.XElement> 使用 XML 常值建立，在此案例中為 `contacts` ：</span><span class="sxs-lookup"><span data-stu-id="dc809-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`, with XML literals:</span></span>

```vb
Dim contacts As XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone>206-555-0144</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

## <a name="example-use-xml-literals-to-create-an-xelement-with-simple-content"></a><span data-ttu-id="dc809-108">範例：使用 XML 常值以簡單的內容建立 System.xml.linq.xelement></span><span class="sxs-lookup"><span data-stu-id="dc809-108">Example: Use XML literals to create an XElement with simple content</span></span>

<span data-ttu-id="dc809-109">您可以建立包含簡單內容的 <xref:System.Xml.Linq.XElement>，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc809-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>

```vb
Dim n as XElement = <Customer>Adventure Works</Customer>
Console.WriteLine(n)
```

<span data-ttu-id="dc809-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="dc809-110">This example produces the following output:</span></span>

```xml
<Customer>Adventure Works</Customer>
```

## <a name="example-use-an-xml-literal-to-create-an-empty-element"></a><span data-ttu-id="dc809-111">範例：使用 XML 常值建立空白元素</span><span class="sxs-lookup"><span data-stu-id="dc809-111">Example: Use an XML literal to create an empty element</span></span>

<span data-ttu-id="dc809-112">您可以建立空的 <xref:System.Xml.Linq.XElement>，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc809-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>

```vb
Dim n As XElement = <Customer/>
Console.WriteLine(n)
```

<span data-ttu-id="dc809-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="dc809-113">This example produces the following output:</span></span>

```xml
<Customer />
```

## <a name="use-embedded-expressions-to-create-content"></a><span data-ttu-id="dc809-114">使用內嵌運算式來建立內容</span><span class="sxs-lookup"><span data-stu-id="dc809-114">Use embedded expressions to create content</span></span>

<span data-ttu-id="dc809-115">XML 常值的其中一個重要功能是，這些 XML 常值允許內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="dc809-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="dc809-116">內嵌的運算式可讓您評估運算式，並將運算式的結果插入到 XML 樹狀中。</span><span class="sxs-lookup"><span data-stu-id="dc809-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="dc809-117">如果運算式評估 <xref:System.Xml.Linq.XElement> 的型別，會將項目插入到樹狀中。</span><span class="sxs-lookup"><span data-stu-id="dc809-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="dc809-118">如果運算式評估 <xref:System.Xml.Linq.XAttribute> 的型別，會將屬性插入到樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="dc809-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="dc809-119">您只能將專案和屬性插入樹狀結構中的元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="dc809-119">You can insert elements and attributes into the tree only where they're valid.</span></span>

<span data-ttu-id="dc809-120">請務必注意，只有單一運算式可進入內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="dc809-120">it's important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="dc809-121">您無法內嵌多個語句。</span><span class="sxs-lookup"><span data-stu-id="dc809-121">You can't embed multiple statements.</span></span> <span data-ttu-id="dc809-122">如果運算式的延伸超過單一行，您必須使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="dc809-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>

<span data-ttu-id="dc809-123">如果您使用內嵌的運算式，將現有的節點 (包括項目) 和屬性加入到新的 XML 樹狀結構，而且如果現有的節點已經成為父代，這些節點就會遭到複製。</span><span class="sxs-lookup"><span data-stu-id="dc809-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="dc809-124">新複製的節點會附加到新的 XML 樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="dc809-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="dc809-125">如果現有的節點沒有父代，這些節點只會附加到新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="dc809-125">If the existing nodes aren't parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="dc809-126">本文的最後一個範例將示範這項功能。</span><span class="sxs-lookup"><span data-stu-id="dc809-126">The last example in this article demonstrates this.</span></span>

## <a name="example-use-an-embedded-expression-to-insert-an-element"></a><span data-ttu-id="dc809-127">範例：使用內嵌運算式插入元素</span><span class="sxs-lookup"><span data-stu-id="dc809-127">Example: Use an embedded expression to insert an element</span></span>

<span data-ttu-id="dc809-128">下列範例使用內嵌的運算式，將項目插入到樹狀中：</span><span class="sxs-lookup"><span data-stu-id="dc809-128">The following example uses an embedded expression to insert an element into the tree:</span></span>

```vb
xmlTree1 As XElement = _
    <Root>
        <Child>Contents</Child>
    </Root>
Dim xmlTree2 As XElement = _
    <Root>
        <%= xmlTree1.<Child> %>
    </Root>
Console.WriteLine(xmlTree2)
```

<span data-ttu-id="dc809-129">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="dc809-129">This example produces the following output:</span></span>

```xml
<Root>
  <Child>Contents</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-for-content"></a><span data-ttu-id="dc809-130">範例：將內嵌的運算式用於內容</span><span class="sxs-lookup"><span data-stu-id="dc809-130">Example: Use an embedded expression for content</span></span>

<span data-ttu-id="dc809-131">您可以使用內嵌的運算式提供項目的內容：</span><span class="sxs-lookup"><span data-stu-id="dc809-131">You can use an embedded expression to supply the content of an element:</span></span>

```vb
Dim str As String
str = "Some content"
Dim root As XElement = <Root><%= str %></Root>
Console.WriteLine(root)
```

<span data-ttu-id="dc809-132">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="dc809-132">This example produces the following output:</span></span>

```xml
<Root>Some content</Root>
```

## <a name="example-use-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="dc809-133">範例：在內嵌運算式中使用 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="dc809-133">Example: Use a LINQ query in an embedded expression</span></span>

<span data-ttu-id="dc809-134">您可以使用 LINQ 查詢的結果來提供元素的內容：</span><span class="sxs-lookup"><span data-stu-id="dc809-134">You can use the results of a LINQ query to provide the content of an element:</span></span>

```vb
Dim arr As Integer() = {1, 2, 3}

Dim n As XElement = _
    <Root>
        <%= From i In arr Select <Child><%= i %></Child> %>
    </Root>

Console.WriteLine(n)
```

<span data-ttu-id="dc809-135">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="dc809-135">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Child>3</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-to-provide-node-names"></a><span data-ttu-id="dc809-136">範例：使用內嵌運算式提供節點名稱</span><span class="sxs-lookup"><span data-stu-id="dc809-136">Example: Use an embedded expression to provide node names</span></span>

<span data-ttu-id="dc809-137">您也可以使用內嵌運算式來計算屬性名稱、屬性值、元素名稱和元素值：</span><span class="sxs-lookup"><span data-stu-id="dc809-137">You can also use an embedded expression to calculate attribute names, attribute values, element names, and element values:</span></span>

```vb
Dim eleName As String = "ele"
Dim attName As String = "att"
Dim attValue As String = "aValue"
Dim eleValue As String = "eValue"
Dim n As XElement = _
    <Root <%= attName %>=<%= attValue %>>
        <<%= eleName %>>
            <%= eleValue %>
        </>
    </Root>
Console.WriteLine(n)
```

<span data-ttu-id="dc809-138">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="dc809-138">This example produces the following output:</span></span>

```xml
<Root att="aValue">
  <ele>eValue</ele>
</Root>
```

## <a name="example-use-an-embedded-expression-to-clone-and-attach-nodes"></a><span data-ttu-id="dc809-139">範例：使用內嵌運算式來複製和附加節點</span><span class="sxs-lookup"><span data-stu-id="dc809-139">Example: Use an embedded expression to clone and attach nodes</span></span>

<span data-ttu-id="dc809-140">如先前所述，如果您使用內嵌運算式來加入現有的節點 (包括專案) 和屬性新增至新的 XML 樹狀結構，而且如果加入的節點已經成為父節點，則會複製節點，並將複製附加至新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="dc809-140">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, and if the nodes being added nodes are already parented, the nodes are cloned and the clones are attached to the new XML tree.</span></span> <span data-ttu-id="dc809-141">如果現有的節點不是父節點，這些節點只會附加到新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="dc809-141">If the existing nodes aren't parented, they're simply attached to the new XML tree.</span></span>

<span data-ttu-id="dc809-142">下列程式碼示範將成為父代的項目加入到樹狀結構時，以及將沒有父代的項目加入樹狀結構時的行為。</span><span class="sxs-lookup"><span data-stu-id="dc809-142">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

```vb
' Create a tree with a child element.
Dim xmlTree1 As XElement = _
    <Root>
        <Child1>1</Child1>
    </Root>

' Create an element that's not parented.
Dim child2 As XElement = <Child2>2</Child2>

' Create a tree and add Child1 and Child2 to it.
Dim xmlTree2 As XElement = _
    <Root>
        <%= xmlTree1.<Child1>(0) %>
        <%= child2 %>
    </Root>

' Compare Child1 identity.
Console.WriteLine("Child1 was {0}", _
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _
    "attached", "cloned"))

' Compare Child2 identity.
Console.WriteLine("Child2 was {0}", _
    IIf(child2 Is xmlTree2.Element("Child2"), _
    "attached", "cloned"))
```

<span data-ttu-id="dc809-143">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="dc809-143">This example produces the following output:</span></span>

```output
Child1 was cloned
Child2 was attached
```

## <a name="see-also"></a><span data-ttu-id="dc809-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc809-144">See also</span></span>

- [<span data-ttu-id="dc809-145">功能結構</span><span class="sxs-lookup"><span data-stu-id="dc809-145">Functional construction</span></span>](functional-construction.md)
