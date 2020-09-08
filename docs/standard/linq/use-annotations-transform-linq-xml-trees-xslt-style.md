---
title: 如何使用批註來轉換 XSLT 樣式的 LINQ to XML 樹狀結構-LINQ to XML
description: 瞭解如何使用批註來轉換以檔為中心並具有混合內容的 XML 檔。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 12a95902-a6b7-4a1e-ad52-04a518db226f
ms.openlocfilehash: 3cecc1b868983f1fa19d29d4bf5e73182a1af295
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552178"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-linq-to-xml"></a><span data-ttu-id="78c87-103">如何使用批註來轉換 XSLT 樣式的 LINQ to XML 樹狀結構 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="78c87-103">How to use annotations to transform LINQ to XML trees in an XSLT style (LINQ to XML)</span></span>

<span data-ttu-id="78c87-104">附註可用於簡化 XML 樹狀的轉換。</span><span class="sxs-lookup"><span data-stu-id="78c87-104">Annotations can be used to facilitate transforms of an XML tree.</span></span>

<span data-ttu-id="78c87-105">部分 XML 檔是「以檔為中心的混合內容」。</span><span class="sxs-lookup"><span data-stu-id="78c87-105">Some XML documents are "document-centric with mixed content."</span></span> <span data-ttu-id="78c87-106">使用這類文件時，您不一定要知道項目子節點的組織結構。</span><span class="sxs-lookup"><span data-stu-id="78c87-106">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="78c87-107">例如，包含文字的節點類似如下：</span><span class="sxs-lookup"><span data-stu-id="78c87-107">For instance, a node that contains text may look like this:</span></span>

```xml
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>
```

<span data-ttu-id="78c87-108">針對任何指定的文字節點，可能會有任何數目的 `<b>` 和 `<i>` 子項目。</span><span class="sxs-lookup"><span data-stu-id="78c87-108">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="78c87-109">這種方法會延伸到其他許多情況，例如可以包含各種子專案的頁面，這些子項目可能是一般段落、點符段落和點陣圖。</span><span class="sxs-lookup"><span data-stu-id="78c87-109">This approach extends to a number of other situations, such as pages that can contain a variety of child elements, which could be regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="78c87-110">資料表中的儲存格可能包含文字、下拉式清單或點陣圖。</span><span class="sxs-lookup"><span data-stu-id="78c87-110">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="78c87-111">以檔為中心的 XML 主要特性之一，就是您不知道任何特定元素將擁有哪個子項目。</span><span class="sxs-lookup"><span data-stu-id="78c87-111">One of the primary characteristics of document-centric XML is that you don't know which child element any particular element will have.</span></span>

<span data-ttu-id="78c87-112">如果您想要轉換樹狀結構中的元素，而不一定知道您想要轉換之專案的子系，則使用批註的這種方法會是有效的。</span><span class="sxs-lookup"><span data-stu-id="78c87-112">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective one.</span></span>

<span data-ttu-id="78c87-113">方法的摘要如下：</span><span class="sxs-lookup"><span data-stu-id="78c87-113">The summary of the approach is:</span></span>

- <span data-ttu-id="78c87-114">首先，在樹狀結構中，以替代項目附註項目。</span><span class="sxs-lookup"><span data-stu-id="78c87-114">First, annotate elements in the tree with a replacement element.</span></span>
- <span data-ttu-id="78c87-115">接著，逐一查看整個樹狀結構，建立您以其附註取代每個項目的新樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="78c87-115">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="78c87-116">本文中的範例會在名為的函式中，執行反覆運算和建立新的樹狀結構 `XForm` 。</span><span class="sxs-lookup"><span data-stu-id="78c87-116">The examples in this article implement the iteration and creation of the new tree in a function named `XForm`.</span></span>

<span data-ttu-id="78c87-117">就細節而言，此方法包含：</span><span class="sxs-lookup"><span data-stu-id="78c87-117">In detail, the approach consists of:</span></span>

- <span data-ttu-id="78c87-118">執行一或多個 LINQ to XML 查詢，這些查詢會傳回您要從一個組織結構轉換為另一個組織結構的項目集。</span><span class="sxs-lookup"><span data-stu-id="78c87-118">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="78c87-119">針對查詢中的每個項目，加入新的 <xref:System.Xml.Linq.XElement> 物件做為項目的附註。</span><span class="sxs-lookup"><span data-stu-id="78c87-119">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="78c87-120">這個新項目將會取代已轉換之新樹狀中的標註項目。</span><span class="sxs-lookup"><span data-stu-id="78c87-120">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="78c87-121">如本範例的示範，這是容易撰寫的簡單程式碼。</span><span class="sxs-lookup"><span data-stu-id="78c87-121">This is simple code to write, as demonstrated by the example.</span></span>
- <span data-ttu-id="78c87-122">新增為批註的新專案可以包含新的子節點。它可形成具有任何所需圖形的子樹。</span><span class="sxs-lookup"><span data-stu-id="78c87-122">The new element that's added as an annotation can contain new child nodes; it can form a subtree with any desired shape.</span></span>
- <span data-ttu-id="78c87-123">有一項特殊的規則：如果新專案的子節點位於不同的命名空間中，則為此用途所組成的命名空間 (在此範例中，會) 命名空間 `http://www.microsoft.com/LinqToXmlTransform/2007` ，然後該子項目不會複製到新的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="78c87-123">There is a special rule: If a child node of the new element is in a different namespace, a namespace that's made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element isn't copied to the new tree.</span></span> <span data-ttu-id="78c87-124">相反地，如果命名空間是上述的特殊命名空間，而專案的區功能變數名稱稱是，則 `ApplyTransforms` 會反復查看來源樹狀結構中專案的子節點，並將其複製到新的樹狀結構 (但批註的子專案會根據這些規則) 來轉換。</span><span class="sxs-lookup"><span data-stu-id="78c87-124">Instead, if the namespace is the above-mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>
- <span data-ttu-id="78c87-125">這有點類似於 XSL 中的轉換規格。</span><span class="sxs-lookup"><span data-stu-id="78c87-125">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="78c87-126">選取一組節點的查詢類似於範本的 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="78c87-126">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="78c87-127">建立 <xref:System.Xml.Linq.XElement> 儲存為批註之新的程式碼類似于 xsl 中的 sequence 函式，而專案 `ApplyTransforms` 則類似于 xsl 中的 `xsl:apply-templates` 元素。</span><span class="sxs-lookup"><span data-stu-id="78c87-127">The code to create the new <xref:System.Xml.Linq.XElement> that's saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>
- <span data-ttu-id="78c87-128">採用這種方法的其中一個優點是，當您在撰寫查詢時，一律是在未修改的來源樹狀結構上撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="78c87-128">One advantage to taking this approach is that, as you formulate queries, you're  always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="78c87-129">您不需要擔心對樹狀結構的修改會如何影響您正在撰寫的查詢。</span><span class="sxs-lookup"><span data-stu-id="78c87-129">You don't need to worry about how modifications to the tree affect the queries that you're writing.</span></span>

## <a name="example-rename-all-paragraph-nodes"></a><span data-ttu-id="78c87-130">範例：重新命名所有段落節點</span><span class="sxs-lookup"><span data-stu-id="78c87-130">Example: Rename all paragraph nodes</span></span>

<span data-ttu-id="78c87-131">此範例會將所有節點重新命名 `Paragraph` 為 `para` 。</span><span class="sxs-lookup"><span data-stu-id="78c87-131">This example renames all `Paragraph` nodes to `para`.</span></span>

```csharp
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";
XName at = xf + "ApplyTransforms";

XElement root = XElement.Parse(@"
<Root>
    <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>
    <Paragraph>More text.</Paragraph>
</Root>");

// replace Paragraph with para
foreach (var el in root.Descendants("Paragraph"))
    el.AddAnnotation(
        new XElement("para",
            // same idea as xsl:apply-templates
            new XElement(xf + "ApplyTransforms")
        )
    );

// The XForm method, shown later in this article, accomplishes the transform
XElement newRoot = XForm(root);

Console.WriteLine(newRoot);
```

```vb
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>
                <Paragraph>More text.</Paragraph>
            </Root>

        ' Replace Paragraph with p.
        For Each el In root...<Paragraph>
            ' same idea as xsl:apply-templates
            el.AddAnnotation( _
                <para>
                    <<%= at %>></>
                </para>)
        Next

        ' The XForm function, shown later in this article, accomplishes the transform
        Dim newRoot As XElement = XForm(root)
        Console.WriteLine(newRoot)
    End Sub
End Module
```

<span data-ttu-id="78c87-132">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="78c87-132">This example produces the following output:</span></span>

```xml
<Root>
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>
  <para>More text.</para>
</Root>
```

## <a name="example-calculate-averages-and-sums-and-add-them-as-new-elements-to-the-tree"></a><span data-ttu-id="78c87-133">範例：計算平均值和總和，並將其新增為樹狀結構中的新元素</span><span class="sxs-lookup"><span data-stu-id="78c87-133">Example: Calculate averages and sums and add them as new elements to the tree</span></span>

<span data-ttu-id="78c87-134">下列範例會計算專案的平均值和總和 `Data` ，並將其加入至樹狀結構中的新元素。</span><span class="sxs-lookup"><span data-stu-id="78c87-134">The following example calculates the average and sum of the `Data` elements and adds them as new elements to the tree.</span></span>

```csharp
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";
XName at = xf + "ApplyTransforms";

XElement data = new XElement("Root",
    new XElement("Data", 20),
    new XElement("Data", 10),
    new XElement("Data", 3)
);

// while adding annotations, you can query the source tree all you want,
// as the tree isn't mutated while annotating.
var avg = data.Elements("Data").Select(z => (Decimal)z).Average();
data.AddAnnotation(
    new XElement("Root",
        new XElement(xf + "ApplyTransforms"),
        new XElement("Average", $"{avg:F4}"),
        new XElement("Sum",
            data
            .Elements("Data")
            .Select(z => (int)z)
            .Sum()
        )
    )
);

Console.WriteLine("Before Transform");
Console.WriteLine("----------------");
Console.WriteLine(data);
Console.WriteLine();
Console.WriteLine();

// The XForm method, shown later in this article, accomplishes the transform
XElement newData = XForm(data);

Console.WriteLine("After Transform");
Console.WriteLine("----------------");
Console.WriteLine(newData);
```

```vb
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    Sub Main()
        Dim data As XElement = _
            <Root>
                <Data>20</Data>
                <Data>10</Data>
                <Data>3</Data>
            </Root>

        ' While adding annotations, you can query the source tree all you want,
        ' as the tree isn't mutated while annotating.
        data.AddAnnotation( _
            <Root>
                <<%= at %>/>
                <Average>
                    <%= _
                        String.Format("{0:F4}", _
                        data.Elements("Data") _
                        .Select(Function(z) CDec(z)).Average()) _
                    %>
                </Average>
                <Sum>
                    <%= _
                        data.Elements("Data").Select(Function(z) CInt(z)).Sum() _
                    %>
                </Sum>
            </Root> _
        )

        Console.WriteLine("Before Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(data)
        Console.WriteLine(vbNewLine)

        ' The XForm function, shown later in this article, accomplishes the transform
        Dim newData As XElement = XForm(data)

        Console.WriteLine("After Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(newData)
    End Sub
End Module
```

<span data-ttu-id="78c87-135">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="78c87-135">This example produces the following output:</span></span>

```output
Before Transform
----------------
<Root>
  <Data>20</Data>
  <Data>10</Data>
  <Data>3</Data>
</Root>

After Transform
----------------
<Root>
  <Data>20</Data>
  <Data>10</Data>
  <Data>3</Data>
  <Average>11.0000</Average>
  <Sum>33</Sum>
</Root>
```

## <a name="example-create-a-new-transformed-tree-from-the-original-annotated-tree"></a><span data-ttu-id="78c87-136">範例：從原始批註樹狀結構建立新的已轉換樹狀結構</span><span class="sxs-lookup"><span data-stu-id="78c87-136">Example: Create a new transformed tree from the original annotated tree</span></span>

<span data-ttu-id="78c87-137">`XForm` 這個小函式會從原始的附註樹狀結構建立轉換的新樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="78c87-137">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span> <span data-ttu-id="78c87-138">以下是此函式的虛擬程式碼：</span><span class="sxs-lookup"><span data-stu-id="78c87-138">The following is pseudocode for this function:</span></span>

> <span data-ttu-id="78c87-139">函數會採用 System.xml.linq.xelement> 作為引數，並傳回 System.xml.linq.xelement>。</span><span class="sxs-lookup"><span data-stu-id="78c87-139">The function takes an XElement as an argument and returns an XElement.</span></span>
>
> <span data-ttu-id="78c87-140">如果專案具有 System.xml.linq.xelement> 注釋，則傳回的 System.xml.linq.xelement> 具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="78c87-140">If an element has an XElement annotation, the returned XElement has these characteristics:</span></span>
>
> - <span data-ttu-id="78c87-141">新 System.xml.linq.xelement> 的名稱是 annotation 元素的名稱。</span><span class="sxs-lookup"><span data-stu-id="78c87-141">The name of the new XElement is the annotation element's name.</span></span>
> - <span data-ttu-id="78c87-142">所有屬性都會從注釋複製到新的節點。</span><span class="sxs-lookup"><span data-stu-id="78c87-142">All attributes are copied from the annotation to the new node.</span></span>
> - <span data-ttu-id="78c87-143">所有子節點都會從批註複製，但特殊節點 xf： ApplyTransforms 會被辨識，而且會反復查看來源元素的子節點。</span><span class="sxs-lookup"><span data-stu-id="78c87-143">All child nodes are copied from the annotation, with the exception that the special node xf:ApplyTransforms is recognized, and the source element's child nodes are iterated.</span></span> <span data-ttu-id="78c87-144">如果來源子節點不是 System.xml.linq.xelement>，則會將它複製到新的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="78c87-144">If the source child node isn't an XElement, it's copied to the new tree.</span></span> <span data-ttu-id="78c87-145">如果來源子系是 System.xml.linq.xelement>，則會以遞迴方式呼叫此函數來轉換它。</span><span class="sxs-lookup"><span data-stu-id="78c87-145">If the source child is an XElement, then it's transformed by calling this function recursively.</span></span>
>
> <span data-ttu-id="78c87-146">否則，傳回的 System.xml.linq.xelement> 會有下列特性：</span><span class="sxs-lookup"><span data-stu-id="78c87-146">Otherwise, the returned XElement has these characteristics:</span></span>
>
> - <span data-ttu-id="78c87-147">新 System.xml.linq.xelement> 的名稱是來源元素的名稱。</span><span class="sxs-lookup"><span data-stu-id="78c87-147">The name of the new XElement is the source element's name.</span></span>
> - <span data-ttu-id="78c87-148">所有屬性都會從來源元素複製到目的地的元素。</span><span class="sxs-lookup"><span data-stu-id="78c87-148">All attributes are copied from the source element to the destination's element.</span></span>
> - <span data-ttu-id="78c87-149">所有子節點都會從來源元素複製。</span><span class="sxs-lookup"><span data-stu-id="78c87-149">All child nodes are copied from the source element.</span></span>
> - <span data-ttu-id="78c87-150">如果來源子節點不是 System.xml.linq.xelement>，則會將它複製到新的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="78c87-150">If the source child node isn't an XElement, it's copied to the new tree.</span></span> <span data-ttu-id="78c87-151">如果來源子系是 System.xml.linq.xelement>，則會以遞迴方式呼叫此函數來轉換它。</span><span class="sxs-lookup"><span data-stu-id="78c87-151">If the source child is an XElement, then it's transformed by calling this function recursively.</span></span>

<span data-ttu-id="78c87-152">以下是此函式的程式碼：</span><span class="sxs-lookup"><span data-stu-id="78c87-152">The following is code for this function:</span></span>

```csharp
// Build a transformed XML tree per the annotations
static XElement XForm(XElement source)
{
    XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";
    XName at = xf + "ApplyTransforms";

    if (source.Annotation<XElement>() != null)
    {
        XElement anno = source.Annotation<XElement>();
        return new XElement(anno.Name,
            anno.Attributes(),
            anno
            .Nodes()
            .Select(
                (XNode n) =>
                {
                    XElement annoEl = n as XElement;
                    if (annoEl != null)
                    {
                        if (annoEl.Name == at)
                            return (object)(
                                source.Nodes()
                                .Select(
                                    (XNode n2) =>
                                    {
                                        XElement e2 = n2 as XElement;
                                        if (e2 == null)
                                            return n2;
                                        else
                                            return XForm(e2);
                                    }
                                )
                            );
                        else
                            return n;
                    }
                    else
                        return n;
                }
            )
        );
    }
    else
    {
        return new XElement(source.Name,
            source.Attributes(),
            source
                .Nodes()
                .Select(n =>
                {
                    XElement el = n as XElement;
                    if (el == null)
                        return n;
                    else
                        return XForm(el);
                }
                )
        );
    }
}
```

```vb
' Build a transformed XML tree per the annotations.
Function XForm(ByVal source As XElement) As XElement
    If source.Annotation(Of XElement)() IsNot Nothing Then
        Dim anno As XElement = source.Annotation(Of XElement)()
        Return _
            <<%= anno.Name.ToString() %>>
                <%= anno.Attributes() %>
                <%= anno.Nodes().Select(Function(n As XNode) _
                    GetSubNodes(n, source)) %>
            </>
    Else
        Return _
            <<%= source.Name %>>
                <%= source.Attributes() %>
                <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>
            </>
    End If
End Function

Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object
    Dim annoEl As XElement = TryCast(n, XElement)
    If annoEl IsNot Nothing Then
        If annoEl.Name = at Then
            Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))
        End If
    End If
    Return n
End Function

Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode
    Dim e2 As XElement = TryCast(n2, XElement)
    If e2 Is Nothing Then
        Return n2
    Else
        Return XForm(e2)
    End If
End Function
```

## <a name="example-show-xform-in-typical-uses-of-this-type-of-transform"></a><span data-ttu-id="78c87-153">範例： `XForm` 在這種類型的轉換中顯示一般用法</span><span class="sxs-lookup"><span data-stu-id="78c87-153">Example: Show `XForm` in typical uses of this type of transform</span></span>

<span data-ttu-id="78c87-154">下列範例包含此函式 `XForm` 和這類轉換的一些典型用法：</span><span class="sxs-lookup"><span data-stu-id="78c87-154">The following example includes the `XForm` function and a few of the typical uses of this type of transform:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Xml;
using System.Xml.Linq;

class Program
{
    static XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";
    static XName at = xf + "ApplyTransforms";

    // Build a transformed XML tree per the annotations
    static XElement XForm(XElement source)
    {
        if (source.Annotation<XElement>() != null)
        {
            XElement anno = source.Annotation<XElement>();
            return new XElement(anno.Name,
                anno.Attributes(),
                anno
                .Nodes()
                .Select(
                    (XNode n) =>
                    {
                        XElement annoEl = n as XElement;
                        if (annoEl != null)
                        {
                            if (annoEl.Name == at)
                                return (object)(
                                    source.Nodes()
                                    .Select(
                                        (XNode n2) =>
                                        {
                                            XElement e2 = n2 as XElement;
                                            if (e2 == null)
                                                return n2;
                                            else
                                                return XForm(e2);
                                        }
                                    )
                                );
                            else
                                return n;
                        }
                        else
                            return n;
                    }
                )
            );
        }
        else
        {
            return new XElement(source.Name,
                source.Attributes(),
                source
                    .Nodes()
                    .Select(n =>
                    {
                        XElement el = n as XElement;
                        if (el == null)
                            return n;
                        else
                            return XForm(el);
                    }
                    )
            );
        }
    }

    static void Main(string[] args)
    {
        XElement root = new XElement("Root",
            new XComment("A comment"),
            new XAttribute("Att1", 123),
            new XElement("Child", 1),
            new XElement("Child", 2),
            new XElement("Other",
                new XElement("GC", 3),
                new XElement("GC", 4)
            ),
            XElement.Parse(
              "<SomeMixedContent>This is <i>an</i> element that " +
              "<b>has</b> some mixed content</SomeMixedContent>"),
            new XElement("AnUnchangedElement", 42)
        );

        // each of the following serves the same semantic purpose as
        // XSLT templates and sequence constructors

        // replace Child with NewChild
        foreach (var el in root.Elements("Child"))
            el.AddAnnotation(new XElement("NewChild", (string)el));

        // replace first GC with GrandChild, add an attribute
        foreach (var el in root.Descendants("GC").Take(1))
            el.AddAnnotation(
                new XElement("GrandChild",
                    new XAttribute("ANewAttribute", 999),
                    (string)el
                )
            );

        // replace Other with NewOther, add new child elements around original content
        foreach (var el in root.Elements("Other"))
            el.AddAnnotation(
                new XElement("NewOther",
                    new XElement("MyNewChild", 1),
                    // same idea as xsl:apply-templates
                    new XElement(xf + "ApplyTransforms"),
                    new XElement("ChildThatComesAfter")
                )
            );

        // change name of element that has mixed content
        root.Descendants("SomeMixedContent").First().AddAnnotation(
            new XElement("MixedContent",
                new XElement(xf + "ApplyTransforms")
            )
        );

        // replace <b> with <Bold>
        foreach (var el in root.Descendants("b"))
            el.AddAnnotation(
                new XElement("Bold",
                    new XElement(xf + "ApplyTransforms")
                )
            );

        // replace <i> with <Italic>
        foreach (var el in root.Descendants("i"))
            el.AddAnnotation(
                new XElement("Italic",
                    new XElement(xf + "ApplyTransforms")
                )
            );

        Console.WriteLine("Before Transform");
        Console.WriteLine("----------------");
        Console.WriteLine(root);
        Console.WriteLine();
        Console.WriteLine();
        XElement newRoot = XForm(root);

        Console.WriteLine("After Transform");
        Console.WriteLine("----------------");
        Console.WriteLine(newRoot);
    }
}
```

```vb
Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports System.Xml
Imports System.Xml.Linq

Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    ' Build a transformed XML tree per the annotations.
    Function XForm(ByVal source As XElement) As XElement
        If source.Annotation(Of XElement)() IsNot Nothing Then
            Dim anno As XElement = source.Annotation(Of XElement)()
            Return _
                <<%= anno.Name.ToString() %>>
                    <%= anno.Attributes() %>
                    <%= anno.Nodes().Select(Function(n As XNode) _
                        GetSubNodes(n, source)) %>
                </>
        Else
            Return _
                <<%= source.Name %>>
                    <%= source.Attributes() %>
                    <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>
                </>
        End If
    End Function

    Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object
        Dim annoEl As XElement = TryCast(n, XElement)
        If annoEl IsNot Nothing Then
            If annoEl.Name = at Then
                Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))
            End If
        End If
        Return n
    End Function

    Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode
        Dim e2 As XElement = TryCast(n2, XElement)
        If e2 Is Nothing Then
            Return n2
        Else
            Return XForm(e2)
        End If
    End Function

    Sub Main()
        Dim root As XElement = _
<Root Att1='123'>
    <!--A comment-->
    <Child>1</Child>
    <Child>2</Child>
    <Other>
        <GC>3</GC>
        <GC>4</GC>
    </Other>
    <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>
    <AnUnchangedElement>42</AnUnchangedElement>
</Root>

        ' Each of the following serves the same semantic purpose as
        ' XSLT templates and sequence constructors.

        ' Replace Child with NewChild.
        For Each el In root.<Child>
            el.AddAnnotation(<NewChild><%= CStr(el) %></NewChild>)
        Next

        ' Replace first GC with GrandChild, add an attribute.
        For Each el In root...<GC>.Take(1)
            el.AddAnnotation(<GrandChild ANewAttribute='999'><%= CStr(el) %></GrandChild>)
        Next

        ' Replace Other with NewOther, add new child elements around original content.
        For Each el In root.<Other>
            el.AddAnnotation( _
                <NewOther>
                    <MyNewChild>1</MyNewChild>
                    <<%= at %>></>
                    <ChildThatComesAfter/>
                </NewOther>)
        Next

        ' Change name of element that has mixed content.
        root...<SomeMixedContent>(0).AddAnnotation( _
                <MixedContent><<%= at %>></></MixedContent>)

        ' Replace <b> with <Bold>.
        For Each el In root...<b>
            el.AddAnnotation(<Bold><<%= at %>></></Bold>)
        Next

        ' Replace <i> with <Italic>.
        For Each el In root...<i>
            el.AddAnnotation(<Italic><<%= at %>></></Italic>)
        Next

        Console.WriteLine("Before Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(root)
        Console.WriteLine(vbNewLine)
        Dim newRoot As XElement = XForm(root)

        Console.WriteLine("After Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(newRoot)
    End Sub
End Module
```

<span data-ttu-id="78c87-155">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="78c87-155">This example produces the following output:</span></span>

```output
Before Transform
----------------
<Root Att1="123">
  <!--A comment-->
  <Child>1</Child>
  <Child>2</Child>
  <Other>
    <GC>3</GC>
    <GC>4</GC>
  </Other>
  <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>
  <AnUnchangedElement>42</AnUnchangedElement>
</Root>

After Transform
----------------
<Root Att1="123">
  <!--A comment-->
  <NewChild>1</NewChild>
  <NewChild>2</NewChild>
  <NewOther>
    <MyNewChild>1</MyNewChild>
    <GrandChild ANewAttribute="999">3</GrandChild>
    <GC>4</GC>
    <ChildThatComesAfter />
  </NewOther>
  <MixedContent>This is <Italic>an</Italic> element that <Bold>has</Bold> some mixed content</MixedContent>
  <AnUnchangedElement>42</AnUnchangedElement>
</Root>
```
