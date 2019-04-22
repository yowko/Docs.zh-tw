---
title: 搭配節點 (Visual Basic) 進行程式設計
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: ed7f460b441a5973c33841f1f53ce4679b627071
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817106"
---
# <a name="programming-with-nodes-visual-basic"></a><span data-ttu-id="343d8-102">搭配節點 (Visual Basic) 進行程式設計</span><span class="sxs-lookup"><span data-stu-id="343d8-102">Programming with Nodes (Visual Basic)</span></span>
<span data-ttu-id="343d8-103">必須撰寫程式 (例如，XML 編輯器、轉換系統或報表寫入器) 的 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 開發人員通常需要撰寫的程式可在比項目和屬性更細微的層級上作業。</span><span class="sxs-lookup"><span data-stu-id="343d8-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="343d8-104">他們通常需要在節點層級、管理的文字節點、處理指示與註解上作業。</span><span class="sxs-lookup"><span data-stu-id="343d8-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="343d8-105">這個主題提供一些關於在節點層級進行程式設計的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="343d8-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="343d8-106">節點詳細資料</span><span class="sxs-lookup"><span data-stu-id="343d8-106">Node Details</span></span>  
 <span data-ttu-id="343d8-107">這裡提供程式設計人員在節點層級上作業時應該知道的一些程式設計詳細資料。</span><span class="sxs-lookup"><span data-stu-id="343d8-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="343d8-108">XDocument 之子節點的父屬性設定為 Null</span><span class="sxs-lookup"><span data-stu-id="343d8-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="343d8-109"><xref:System.Xml.Linq.XObject.Parent%2A> 屬性包含父代 <xref:System.Xml.Linq.XElement>，而不包含父節點。</span><span class="sxs-lookup"><span data-stu-id="343d8-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="343d8-110"><xref:System.Xml.Linq.XDocument> 的子節點沒有父代 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="343d8-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="343d8-111">其父代為文件，因此，這些節點的 <xref:System.Xml.Linq.XObject.Parent%2A> 屬性設定為 Null。</span><span class="sxs-lookup"><span data-stu-id="343d8-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="343d8-112">下列範例為其示範：</span><span class="sxs-lookup"><span data-stu-id="343d8-112">The following example demonstrates this:</span></span>  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 <span data-ttu-id="343d8-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="343d8-113">This example produces the following output:</span></span>  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="343d8-114">文字節點可以是相鄰的</span><span class="sxs-lookup"><span data-stu-id="343d8-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="343d8-115">在多個 XML 程式撰寫模型 (Programming Model) 中，相鄰的文字節點永遠會遭到合併。</span><span class="sxs-lookup"><span data-stu-id="343d8-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="343d8-116">這有時候稱為文字節點的正規化。</span><span class="sxs-lookup"><span data-stu-id="343d8-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="343d8-117">不會正規化文字節點。</span><span class="sxs-lookup"><span data-stu-id="343d8-117">does not normalize text nodes.</span></span> <span data-ttu-id="343d8-118">如果您將兩個文字節點加入到相同的項目，則會讓兩個文字節點變成相鄰的。</span><span class="sxs-lookup"><span data-stu-id="343d8-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="343d8-119">不過，如果您新增指定為字串 (而非 <xref:System.Xml.Linq.XText> 節點) 的內容，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 可能會合併字串與相鄰的文字節點。</span><span class="sxs-lookup"><span data-stu-id="343d8-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="343d8-120">下列範例為其示範：</span><span class="sxs-lookup"><span data-stu-id="343d8-120">The following example demonstrates this:</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
' This does not add a new text node.  
xmlTree.Add("new content")  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
'// This does add a new, adjacent text node.  
xmlTree.Add(New XText("more text"))  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
```  
  
 <span data-ttu-id="343d8-121">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="343d8-121">This example produces the following output:</span></span>  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="343d8-122">文字節點可以是空白的</span><span class="sxs-lookup"><span data-stu-id="343d8-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="343d8-123">在某些 XML 程式撰寫模型中，保證文字節點不包含空字串。</span><span class="sxs-lookup"><span data-stu-id="343d8-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="343d8-124">原因是，這種文字節點對於序列化 XML 不會有任何影響。</span><span class="sxs-lookup"><span data-stu-id="343d8-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="343d8-125">不過，因為相同的原因，文字節點可以是相鄰的，如果您藉由將文字節點的值設定為空字串來移除該文字節點中的文字，文字節點本身將不會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="343d8-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 <span data-ttu-id="343d8-126">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="343d8-126">This example produces the following output:</span></span>  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="343d8-127">空文字節點影響序列化</span><span class="sxs-lookup"><span data-stu-id="343d8-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="343d8-128">如果項目僅包含一個空的文字子節點，該項目會以長標記語法序列化：`<Child></Child>`。</span><span class="sxs-lookup"><span data-stu-id="343d8-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="343d8-129">如果項目不包含任何子節點，則該項目會以短標記語法序列化：`<Child />`。</span><span class="sxs-lookup"><span data-stu-id="343d8-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 <span data-ttu-id="343d8-130">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="343d8-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="343d8-131">命名空間為 LINQ to XML 樹狀結構中的屬性</span><span class="sxs-lookup"><span data-stu-id="343d8-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="343d8-132">即使命名空間宣告與屬性具有相同的語法，在某些程式設計介面 (例如，XSLT 和 XPath) 中，命名空間宣告不會被視為屬性。</span><span class="sxs-lookup"><span data-stu-id="343d8-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="343d8-133">不過，在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，命名空間會當做 <xref:System.Xml.Linq.XAttribute> 物件，儲存在 XML 樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="343d8-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="343d8-134">如果您逐一查看包含命名空間宣告之項目的屬性，您將可以看到命名空間宣告，做為所傳回之集合中的其中一個項目。</span><span class="sxs-lookup"><span data-stu-id="343d8-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="343d8-135"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> 屬性會指出屬性是否為命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="343d8-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
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
  
 <span data-ttu-id="343d8-136">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="343d8-136">This example produces the following output:</span></span>  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="343d8-137">XPath 座標軸方法不會傳回 XDocument 的子系空白字元</span><span class="sxs-lookup"><span data-stu-id="343d8-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 <span data-ttu-id="343d8-138">只要文字節點只包含空白字元，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 就允許使用 <xref:System.Xml.Linq.XDocument> 的文字子節點。</span><span class="sxs-lookup"><span data-stu-id="343d8-138">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="343d8-139">不過，XPath 物件模型不包含當做文件子節點的空白字元，因此，當您使用 <xref:System.Xml.Linq.XDocument> 座標軸逐一查看 <xref:System.Xml.Linq.XContainer.Nodes%2A> 的子系時，將不會傳回空白字元文字節點。</span><span class="sxs-lookup"><span data-stu-id="343d8-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="343d8-140">但是，當您使用 XPath 座標軸方法逐一查看 <xref:System.Xml.Linq.XDocument> 的子系時，將不會傳回空白字元文字節點。</span><span class="sxs-lookup"><span data-stu-id="343d8-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes will not be returned.</span></span>  
  
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
  
 <span data-ttu-id="343d8-141">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="343d8-141">This example produces the following output:</span></span>  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="343d8-142">XDeclaration 物件不是節點</span><span class="sxs-lookup"><span data-stu-id="343d8-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="343d8-143">當您逐一查看 <xref:System.Xml.Linq.XDocument> 的子節點時，您將不會看到 XML 宣告物件。</span><span class="sxs-lookup"><span data-stu-id="343d8-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="343d8-144">這是文件的屬性，而不是其子節點。</span><span class="sxs-lookup"><span data-stu-id="343d8-144">It is a property of the document, not a child node of it.</span></span>  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 <span data-ttu-id="343d8-145">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="343d8-145">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a><span data-ttu-id="343d8-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="343d8-146">See also</span></span>

- [<span data-ttu-id="343d8-147">進階的 LINQ to XML 程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="343d8-147">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
