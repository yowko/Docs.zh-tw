---
title: 如何：使用註釋轉換 XSLT 樣式的 LINQ to XML 樹狀結構 (C#)
ms.date: 07/20/2015
ms.assetid: 12a95902-a6b7-4a1e-ad52-04a518db226f
ms.openlocfilehash: 13b65b5b4e1926910ad68204fdffffd7020f07f2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864348"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-c"></a><span data-ttu-id="2b1c3-102">如何：使用註釋轉換 XSLT 樣式的 LINQ to XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="2b1c3-102">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (C#)</span></span>
<span data-ttu-id="2b1c3-103">附註可用於簡化 XML 樹狀的轉換。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>  
  
 <span data-ttu-id="2b1c3-104">有些 XML 文件為「中央具有混合內容的文件」。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="2b1c3-105">使用這類文件時，您不一定要知道項目子節點的組織結構。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="2b1c3-106">例如，包含文字的節點類似如下：</span><span class="sxs-lookup"><span data-stu-id="2b1c3-106">For instance, a node that contains text may look like this:</span></span>  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 <span data-ttu-id="2b1c3-107">針對任何指定的文字節點，可能會有任何數目的 `<b>` 和 `<i>` 子項目。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="2b1c3-108">這個方法會延伸到數個其他情況：亦即，可以包含各種子項目的頁面，例如，一般段落、分項段落與點陣圖。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-108">This approach extends to a number of other situations, such as pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="2b1c3-109">資料表中的儲存格可能包含文字、下拉式清單或點陣圖。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="2b1c3-110">文件中心 XML 的其中一個主要特性為，您不知道任何特定項目將會有哪個子項目。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>  
  
 <span data-ttu-id="2b1c3-111">如果您要在樹狀結構中，轉換您不一定了解太多您要轉換之項目子系的項目，則使用附註的這個方法是一個有效的方法。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>  
  
 <span data-ttu-id="2b1c3-112">方法的摘要如下：</span><span class="sxs-lookup"><span data-stu-id="2b1c3-112">The summary of the approach is:</span></span>  
  
-   <span data-ttu-id="2b1c3-113">首先，在樹狀結構中，以替代項目附註項目。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-113">First, annotate elements in the tree with a replacement element.</span></span>  
  
-   <span data-ttu-id="2b1c3-114">接著，逐一查看整個樹狀結構，建立您以其附註取代每個項目的新樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="2b1c3-115">這個範本會在名稱為 `XForm` 的函式中，實作反覆運算並建立新的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>  
  
 <span data-ttu-id="2b1c3-116">就細節而言，此方法包含：</span><span class="sxs-lookup"><span data-stu-id="2b1c3-116">In detail, the approach consists of:</span></span>  
  
-   <span data-ttu-id="2b1c3-117">執行一或多個 LINQ to XML 查詢，這些查詢會傳回您要從一個組織結構轉換為另一個組織結構的項目集。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="2b1c3-118">針對查詢中的每個項目，加入新的 <xref:System.Xml.Linq.XElement> 物件做為項目的附註。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="2b1c3-119">這個新項目將會取代已轉換之新樹狀結構中的附註項目。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="2b1c3-120">如本範例的示範，這是容易撰寫的簡單程式碼。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-120">This is simple code to write, as demonstrated by the example.</span></span>  
  
-   <span data-ttu-id="2b1c3-121">加入為附註的新項目可以包含新的子節點；它可以形成具有任何所需組織結構的子樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>  
  
-   <span data-ttu-id="2b1c3-122">有一個特殊規則：如果新項目的子節點位於不同的命名空間中，也就是針對此目的所形成的命名空間 (在此範例中，命名空間為 `http://www.microsoft.com/LinqToXmlTransform/2007`)，則不會將該子項目複製到新的樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="2b1c3-123">但是，如果命名空間為上述的特殊命名空間，而且該項目的區域名稱為 `ApplyTransforms`，則會反覆運算來源樹狀結構中項目的子節點，並複製到新的樹狀結構 (除非附註的子項目會根據這些規則自我轉換) 中。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>  
  
-   <span data-ttu-id="2b1c3-124">這有點類似於 XSL 中的轉換規格。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="2b1c3-125">選取一組節點的查詢類似於範本的 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="2b1c3-126">建立另存為附註之新 <xref:System.Xml.Linq.XElement> 的程式碼類似於 XSL 中的序列建構函式，而 `ApplyTransforms` 項目在功能上則類似於 XSL 中的 `xsl:apply-templates` 項目。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>  
  
-   <span data-ttu-id="2b1c3-127">採取此種方法的其中一個優點是，當您編寫查詢時，您永遠都是在未修改的來源樹狀結構上撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="2b1c3-128">您不必擔心樹狀結構的修改會如何影響您要撰寫的查詢。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>  
  
## <a name="transforming-a-tree"></a><span data-ttu-id="2b1c3-129">轉換樹狀結構</span><span class="sxs-lookup"><span data-stu-id="2b1c3-129">Transforming a Tree</span></span>  
 <span data-ttu-id="2b1c3-130">這個第一個範例會將所有 `Paragraph` 節點重新命名為 `para`。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-130">This first example renames all `Paragraph` nodes to `para`.</span></span>  
  
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
  
// The XForm method, shown later in this topic, accomplishes the transform  
XElement newRoot = XForm(root);  
  
Console.WriteLine(newRoot);  
```  
  
 <span data-ttu-id="2b1c3-131">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2b1c3-131">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a><span data-ttu-id="2b1c3-132">更複雜的轉換</span><span class="sxs-lookup"><span data-stu-id="2b1c3-132">A More Complicated Transform</span></span>  
 <span data-ttu-id="2b1c3-133">下列範例會查詢樹狀結構並計算 `Data` 項目的平均值和總和，然後將它們加入為樹狀結構中的新項目。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>  
  
```csharp  
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
XName at = xf + "ApplyTransforms";  
  
XElement data = new XElement("Root",  
    new XElement("Data", 20),  
    new XElement("Data", 10),  
    new XElement("Data", 3)  
);  
  
// while adding annotations, you can query the source tree all you want,  
// as the tree is not mutated while annotating.  
data.AddAnnotation(  
    new XElement("Root",  
        new XElement(xf + "ApplyTransforms"),  
        new XElement("Average",  
            String.Format("{0:F4}",  
                data  
                .Elements("Data")  
                .Select(z => (Decimal)z)  
                .Average()  
            )  
        ),  
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
  
// The XForm method, shown later in this topic, accomplishes the transform  
XElement newData = XForm(data);  
  
Console.WriteLine("After Transform");  
Console.WriteLine("----------------");  
Console.WriteLine(newData);  
```  
  
 <span data-ttu-id="2b1c3-134">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2b1c3-134">This example produces the following output:</span></span>  
  
```  
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
  
## <a name="effecting-the-transform"></a><span data-ttu-id="2b1c3-135">實行轉換</span><span class="sxs-lookup"><span data-stu-id="2b1c3-135">Effecting the Transform</span></span>  
 <span data-ttu-id="2b1c3-136">`XForm` 這個小函式會從原始的附註樹狀結構建立轉換的新樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>  
  
-   <span data-ttu-id="2b1c3-137">函式的虛擬程式碼相當簡單：</span><span class="sxs-lookup"><span data-stu-id="2b1c3-137">The pseudo code for the function is quite simple:</span></span>  
  
```  
The function takes an XElement as an argument and returns an XElement.   
If an element has an XElement annotation, then  
    Return a new XElement  
        The name of the new XElement is the annotation element's name.  
        All attributes are copied from the annotation to the new node.  
        All child nodes are copied from the annotation, with the  
            exception that the special node xf:ApplyTransforms is  
            recognized, and the source element's child nodes are  
            iterated. If the source child node is not an XElement, it  
            is copied to the new tree. If the source child is an  
            XElement, then it is transformed by calling this function  
            recursively.  
If an element is not annotated  
    Return a new XElement  
        The name of the new XElement is the source element's name  
        All attributes are copied from the source element to the  
            destination's element.  
        All child nodes are copied from the source element.  
        If the source child node is not an XElement, it is copied to  
            the new tree. If the source child is an XElement, then it  
            is transformed by calling this function recursively.  
```  
  
 <span data-ttu-id="2b1c3-138">以下是此函式的實作：</span><span class="sxs-lookup"><span data-stu-id="2b1c3-138">Following is the implementation of this function:</span></span>  
  
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
  
## <a name="complete-example"></a><span data-ttu-id="2b1c3-139">完整範例</span><span class="sxs-lookup"><span data-stu-id="2b1c3-139">Complete Example</span></span>  
 <span data-ttu-id="2b1c3-140">下列程式碼是包含 `XForm` 函式的完整範例。</span><span class="sxs-lookup"><span data-stu-id="2b1c3-140">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="2b1c3-141">此範例包含一些此類型轉換的一般用法：</span><span class="sxs-lookup"><span data-stu-id="2b1c3-141">It includes a few of the typical uses of this type of transform:</span></span>  
  
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
  
 <span data-ttu-id="2b1c3-142">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2b1c3-142">This example produces the following output:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="2b1c3-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="2b1c3-143">See Also</span></span>

- [<span data-ttu-id="2b1c3-144">進階 LINQ to XML 程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="2b1c3-144">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
