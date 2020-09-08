---
title: 使用節點進行程式設計-LINQ to XML
description: 瞭解如何在 XML 樹狀結構的節點層級撰寫程式碼。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 8f9d5c8656a06a9b40a3833aaf7e190b9ba3f0a6
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552219"
---
# <a name="programming-with-nodes-linq-to-xml"></a><span data-ttu-id="f57da-103">使用節點進行程式設計 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="f57da-103">Programming with nodes (LINQ to XML)</span></span>

<span data-ttu-id="f57da-104">需要撰寫程式（例如 XML 編輯器、轉換系統或報表寫入器）的 LINQ to XML 開發人員，通常需要的程式碼可在比專案和屬性更精細的細微性層級上運作。</span><span class="sxs-lookup"><span data-stu-id="f57da-104">LINQ to XML developers who need to write programs such as an XML editor, a transform system, or a report writer often need code that works at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="f57da-105">它們通常需要在節點層級工作、操作文位元組點、處理指示和處理批註。</span><span class="sxs-lookup"><span data-stu-id="f57da-105">They often need to work at the node level, manipulating text nodes, processing instructions, and processing comments.</span></span> <span data-ttu-id="f57da-106">本文提供在節點層級進行程式設計的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f57da-106">This article provides information about programming at the node level.</span></span>

## <a name="example-the-parent-property-values-of-the-child-nodes-of-xdocument-are-set-to-null"></a><span data-ttu-id="f57da-107">範例： `Parent` XDocument 子節點的屬性值設定為 `null`</span><span class="sxs-lookup"><span data-stu-id="f57da-107">Example: The `Parent` property values of the child nodes of XDocument are set to `null`</span></span>

<span data-ttu-id="f57da-108"><xref:System.Xml.Linq.XObject.Parent%2A> 屬性包含父代 <xref:System.Xml.Linq.XElement>，而不包含父節點。</span><span class="sxs-lookup"><span data-stu-id="f57da-108">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="f57da-109"><xref:System.Xml.Linq.XDocument> 的子節點沒有父代 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="f57da-109">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="f57da-110">其父系是檔，因此 <xref:System.Xml.Linq.XObject.Parent%2A> 這些節點的屬性會設定為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="f57da-110">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to `null`.</span></span>

<span data-ttu-id="f57da-111">下列範例為其示範：</span><span class="sxs-lookup"><span data-stu-id="f57da-111">The following example demonstrates this:</span></span>

```csharp
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);
Console.WriteLine(doc.Root.Parent == null);
```

```vb
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)
Console.WriteLine(doc.Root.Parent Is Nothing)
```

<span data-ttu-id="f57da-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f57da-112">This example produces the following output:</span></span>

```output
True
True
```

## <a name="example-adding-text-may-or-may-not-create-a-new-text-node"></a><span data-ttu-id="f57da-113">範例：新增文字不一定會建立新的文位元組點</span><span class="sxs-lookup"><span data-stu-id="f57da-113">Example: Adding text may or may not create a new text node</span></span>

<span data-ttu-id="f57da-114">在多個 XML 程式撰寫模型 (Programming Model) 中，相鄰的文字節點永遠會遭到合併。</span><span class="sxs-lookup"><span data-stu-id="f57da-114">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="f57da-115">這有時候稱為文字節點的正規化。</span><span class="sxs-lookup"><span data-stu-id="f57da-115">This is sometimes called normalization of text nodes.</span></span> <span data-ttu-id="f57da-116">LINQ to XML 不會將文位元組點標準化。</span><span class="sxs-lookup"><span data-stu-id="f57da-116">LINQ to XML doesn't normalize text nodes.</span></span> <span data-ttu-id="f57da-117">如果您將兩個文字節點加入到相同的項目，則會讓兩個文字節點變成相鄰的。</span><span class="sxs-lookup"><span data-stu-id="f57da-117">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="f57da-118">但是，如果您將指定的內容新增為字串，而不是 <xref:System.Xml.Linq.XText> 節點，LINQ to XML 可能會合並字串與連續的文位元組點。</span><span class="sxs-lookup"><span data-stu-id="f57da-118">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, LINQ to XML might merge the string with an adjacent text node.</span></span> <span data-ttu-id="f57da-119">下列範例示範此作業。</span><span class="sxs-lookup"><span data-stu-id="f57da-119">The following example demonstrates this.</span></span>

```csharp
XElement xmlTree = new XElement("Root", "Content");

Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());

// this doesn't add a new text node
xmlTree.Add("new content");
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());

// this does add a new, adjacent text node
xmlTree.Add(new XText("more text"));
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());
```

```vb
Dim xmlTree As XElement = <Root>Content</Root>
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())

' This doesn't add a new text node.
xmlTree.Add("new content")
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())

'// This does add a new, adjacent text node.
xmlTree.Add(New XText("more text"))
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())
```

 <span data-ttu-id="f57da-120">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f57da-120">This example produces the following output:</span></span>

```output
1
1
2
```

## <a name="example-setting-a-text-node-value-to-the-empty-string-doesnt-delete-the-node"></a><span data-ttu-id="f57da-121">範例：將文位元組點值設定為空字串並不會刪除節點</span><span class="sxs-lookup"><span data-stu-id="f57da-121">Example: Setting a text node value to the empty string doesn't delete the node</span></span>

<span data-ttu-id="f57da-122">在某些 XML 程式撰寫模型中，保證文字節點不包含空字串。</span><span class="sxs-lookup"><span data-stu-id="f57da-122">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="f57da-123">原因是，這種文字節點對於序列化 XML 不會有任何影響。</span><span class="sxs-lookup"><span data-stu-id="f57da-123">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="f57da-124">不過，基於同樣的原因，如果您將文位元組點的值設定為空字串，就可以從文位元組點移除文字，而不會刪除文位元組點本身。</span><span class="sxs-lookup"><span data-stu-id="f57da-124">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself won't be deleted.</span></span>

```csharp
XElement xmlTree = new XElement("Root", "Content");
XText textNode = xmlTree.Nodes().OfType<XText>().First();

// the following line doesn't cause the removal of the text node.
textNode.Value = "";

XText textNode2 = xmlTree.Nodes().OfType<XText>().First();
Console.WriteLine(">>{0}<<", textNode2);
```

```vb
Dim xmlTree As XElement = <Root>Content</Root>
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()

' The following line doesn't cause the removal of the text node.
textNode.Value = ""

Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()
Console.WriteLine(">>{0}<<", textNode2)
```

<span data-ttu-id="f57da-125">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f57da-125">This example produces the following output:</span></span>

```output
>><<
```

## <a name="example-an-element-with-one-empty-text-node-is-serialized-differently-from-one-with-no-text-node"></a><span data-ttu-id="f57da-126">範例：具有一個空白文位元組點的專案，會以不同于沒有文位元組點的方式進行序列化</span><span class="sxs-lookup"><span data-stu-id="f57da-126">Example: An element with one empty text node is serialized differently from one with no text node</span></span>

<span data-ttu-id="f57da-127">如果專案只包含空白的子文位元組點，則會使用長標記語法進行序列化： `<Child></Child>` 。</span><span class="sxs-lookup"><span data-stu-id="f57da-127">If an element contains only a child text node that's empty, it's serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="f57da-128">如果元素不包含任何子節點，則會使用簡短標記語法進行序列化： `<Child />` 。</span><span class="sxs-lookup"><span data-stu-id="f57da-128">If an element contains no child nodes whatsoever, it's serialized with the short tag syntax: `<Child />`.</span></span>

```csharp
XElement child1 = new XElement("Child1",
    new XText("")
);
XElement child2 = new XElement("Child2");
Console.WriteLine(child1);
Console.WriteLine(child2);
```

```vb
Dim child1 As XElement = New XElement("Child1", _
    New XText("") _
)
Dim child2 As XElement = New XElement("Child2")
Console.WriteLine(child1)
Console.WriteLine(child2)
```

<span data-ttu-id="f57da-129">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f57da-129">This example produces the following output:</span></span>

```xml
<Child1></Child1>
<Child2 />
```

## <a name="example-namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="f57da-130">範例：命名空間是 LINQ to XML 樹狀結構中的屬性</span><span class="sxs-lookup"><span data-stu-id="f57da-130">Example: Namespaces are attributes in the LINQ to XML tree</span></span>

<span data-ttu-id="f57da-131">雖然命名空間宣告與屬性具有相同的語法，但是在某些程式設計介面（例如 XSLT 和 XPath）中，命名空間宣告不會被視為屬性。</span><span class="sxs-lookup"><span data-stu-id="f57da-131">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations aren't considered to be attributes.</span></span> <span data-ttu-id="f57da-132">不過，在 LINQ to XML 中，命名空間會以 <xref:System.Xml.Linq.XAttribute> 物件的形式儲存在 XML 樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="f57da-132">However, in LINQ to XML, namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="f57da-133">如果您逐一查看包含命名空間宣告之專案的屬性，則命名空間宣告是所傳回集合中的其中一個專案。</span><span class="sxs-lookup"><span data-stu-id="f57da-133">If you iterate through the attributes of an element that contains a namespace declaration, the namespace declaration is one of the items in the returned collection.</span></span> <span data-ttu-id="f57da-134"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> 屬性會指出屬性是否為命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="f57da-134">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root
    xmlns='http://www.adventure-works.com'
    xmlns:fc='www.fourthcoffee.com'
    AnAttribute='abc'/>");
foreach (XAttribute att in root.Attributes())
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);
```

```vb
Dim root As XElement = _
<Root
    xmlns='http://www.adventure-works.com'
    xmlns:fc='www.fourthcoffee.com'
    AnAttribute='abc'/>
For Each att As XAttribute In root.Attributes()
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, _
                      att.IsNamespaceDeclaration)
Next
```

<span data-ttu-id="f57da-135">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f57da-135">This example produces the following output:</span></span>

```output
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True
AnAttribute="abc"  IsNamespaceDeclaration:False
```

## <a name="example-xpath-axis-methods-dont-return-the-child-text-nodes-of-xdocument"></a><span data-ttu-id="f57da-136">範例： XPath 座標軸方法不會傳回 XDocument 的子文位元組點</span><span class="sxs-lookup"><span data-stu-id="f57da-136">Example: XPath axis methods don't return the child text nodes of XDocument</span></span>

<span data-ttu-id="f57da-137">LINQ to XML 允許的子文位元組點 <xref:System.Xml.Linq.XDocument> ，只要文位元組點只包含空白字元。</span><span class="sxs-lookup"><span data-stu-id="f57da-137">LINQ to XML allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="f57da-138">不過，XPath 物件模型不包含空白字元做為檔的子節點，因此當您使用軸逐一查看的子系時 <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XContainer.Nodes%2A> ，將會傳回空白字元文位元組點。</span><span class="sxs-lookup"><span data-stu-id="f57da-138">However, the XPath object model doesn't include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="f57da-139">但是，當您使用 XPath 座標軸方法逐一查看的子系時 <xref:System.Xml.Linq.XDocument> ，將不會傳回空白字元文位元組點。</span><span class="sxs-lookup"><span data-stu-id="f57da-139">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes won't be returned.</span></span>

```csharp
// Create a document with some white space child nodes of the document.
XDocument root = XDocument.Parse(
@"<?xml version='1.0' encoding='utf-8' standalone='yes'?>

<Root/>

<!--a comment-->
", LoadOptions.PreserveWhitespace);

// count the white space child nodes using LINQ to XML
Console.WriteLine(root.Nodes().OfType<XText>().Count());

// count the white space child nodes using XPathEvaluate
Console.WriteLine(((IEnumerable)root.XPathEvaluate("text()")).OfType<XText>().Count());
```

```vb
' Create a document with some white space child nodes of the document.
Dim root As XDocument = XDocument.Parse( _
"<?xml version='1.0' encoding='utf-8' standalone='yes'?>" & _
vbNewLine & "<Root/>" & vbNewLine & "<!--a comment-->" & vbNewLine, _
LoadOptions.PreserveWhitespace)

' Count the white space child nodes using LINQ to XML.
Console.WriteLine(root.Nodes().OfType(Of XText)().Count())

' Count the white space child nodes using XPathEvaluate.
Dim nodes As IEnumerable = CType(root.XPathEvaluate("text()"), IEnumerable)
Console.WriteLine(nodes.OfType(Of XText)().Count())
```

<span data-ttu-id="f57da-140">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f57da-140">This example produces the following output:</span></span>

```output
3
0
```

### <a name="the-xml-declaration-node-of-an-xdocument-is-a-property-not-a-child-node"></a><span data-ttu-id="f57da-141">XDocument 的 XML 宣告節點為屬性，而非子節點</span><span class="sxs-lookup"><span data-stu-id="f57da-141">The XML declaration node of an XDocument is a property, not a child node</span></span>

<span data-ttu-id="f57da-142">當您逐一查看的子節點時 <xref:System.Xml.Linq.XDocument> ，您不會看到 XML 宣告物件。</span><span class="sxs-lookup"><span data-stu-id="f57da-142">When you iterate through the child nodes of an <xref:System.Xml.Linq.XDocument>, you won't see the XML declaration object.</span></span> <span data-ttu-id="f57da-143">它是檔的屬性，不是它的子節點。</span><span class="sxs-lookup"><span data-stu-id="f57da-143">It's a property of the document, not a child node of it.</span></span>

```csharp
XDocument doc = new XDocument(
    new XDeclaration("1.0", "utf-8", "yes"),
    new XElement("Root")
);
doc.Save("Temp.xml");
Console.WriteLine(File.ReadAllText("Temp.xml"));

// this shows that there is only one child node of the document
Console.WriteLine(doc.Nodes().Count());
```

```vb
Dim doc As XDocument = _
<?xml version='1.0' encoding='utf-8' standalone='yes'?>
<Root/>

doc.Save("Temp.xml")
Console.WriteLine(File.ReadAllText("Temp.xml"))

' This shows that there is only one child node of the document.
Console.WriteLine(doc.Nodes().Count())
```

<span data-ttu-id="f57da-144">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f57da-144">This example produces the following output:</span></span>

```output
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Root />
1
```
