---
title: 使用 XPathNavigator 選取 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fea54d36759b12b01fa7a68748d069c7890d84e4
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711320"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="83b78-102">使用 XPathNavigator 選取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="83b78-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="83b78-103"><xref:System.Xml.XPath.XPathNavigator> 類別提供一組方法，可以使用 XPath 運算式選取 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中的一組節點。</span><span class="sxs-lookup"><span data-stu-id="83b78-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="83b78-104">一旦選取，即可重複處理已選取的節點集。</span><span class="sxs-lookup"><span data-stu-id="83b78-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="83b78-105">XPathNavigator 選取方法</span><span class="sxs-lookup"><span data-stu-id="83b78-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="83b78-106"><xref:System.Xml.XPath.XPathNavigator> 類別提供一組方法，可以使用 XPath 運算式選取 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中的一組節點。</span><span class="sxs-lookup"><span data-stu-id="83b78-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="83b78-107"><xref:System.Xml.XPath.XPathNavigator> 類別也提供了一組最佳化方法，可以選取上階節點、子節點及子代節點，其速度比使用 XPath 運算式快。</span><span class="sxs-lookup"><span data-stu-id="83b78-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="83b78-108">若為選取的單一節點，會在 <xref:System.Xml.XPath.XPathNodeIterator> 物件或 <xref:System.Xml.XPath.XPathNavigator> 物件中傳回已選取的節點集。</span><span class="sxs-lookup"><span data-stu-id="83b78-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="83b78-109">使用 XPath 運算式選取節點</span><span class="sxs-lookup"><span data-stu-id="83b78-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="83b78-110">若要使用 XPath 運算式來選取一組節點，請使用下列其中一種選取方法。</span><span class="sxs-lookup"><span data-stu-id="83b78-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="83b78-111">呼叫時，這些方法會傳回一組節點，您可以使用 <xref:System.Xml.XPath.XPathNodeIterator> 物件或 <xref:System.Xml.XPath.XPathNavigator> 物件 (若為選取的單一節點) 來隨意巡覽這些節點。</span><span class="sxs-lookup"><span data-stu-id="83b78-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="83b78-112">使用 <xref:System.Xml.XPath.XPathNodeIterator> 物件來巡覽不會影響用於建立它之 <xref:System.Xml.XPath.XPathNavigator> 物件的位置。</span><span class="sxs-lookup"><span data-stu-id="83b78-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="83b78-113">從 <xref:System.Xml.XPath.XPathNavigator> 方法傳回的 <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> 物件會置於傳回的單一節點上，而且也不會影響用來建立它之 <xref:System.Xml.XPath.XPathNavigator> 物件的位置。</span><span class="sxs-lookup"><span data-stu-id="83b78-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="83b78-114">下列範例顯示如何從 <xref:System.Xml.XPath.XPathNavigator> 物件建立 <xref:System.Xml.XPath.XPathDocument> 物件、如何使用 <xref:System.Xml.XPath.XPathNavigator.Select%2A> 方法來選取 <xref:System.Xml.XPath.XPathDocument> 物件中的節點，以及如何使用 <xref:System.Xml.XPath.XPathNodeIterator> 物件來重複處理已選取的節點。</span><span class="sxs-lookup"><span data-stu-id="83b78-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 <span data-ttu-id="83b78-115">該範例採用 `books.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="83b78-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="83b78-116">最佳化選取方法</span><span class="sxs-lookup"><span data-stu-id="83b78-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="83b78-117"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>、<xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 方法表示一般用來擷取子節點、子代節點及上階節點的 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="83b78-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="83b78-118">這些方法已針對效能最佳化，而且速度比其相對應的 XPath 運算式快。</span><span class="sxs-lookup"><span data-stu-id="83b78-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="83b78-119"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>、<xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> 及 <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> 方法會依據 <xref:System.Xml.XPath.XPathNodeType> 值或要選取之節點的區域名稱及命名空間 URI，來選取上階節點、子節點及子代節點。</span><span class="sxs-lookup"><span data-stu-id="83b78-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="83b78-120">選取的上階節點、子節點及子代節點會在 <xref:System.Xml.XPath.XPathNodeIterator> 物件中傳回。</span><span class="sxs-lookup"><span data-stu-id="83b78-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83b78-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83b78-121">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="83b78-122">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="83b78-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="83b78-123">使用 XPathNavigator 評估 XPath 運算式</span><span class="sxs-lookup"><span data-stu-id="83b78-123">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
- [<span data-ttu-id="83b78-124">使用 XPathNavigator 比對節點</span><span class="sxs-lookup"><span data-stu-id="83b78-124">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
- [<span data-ttu-id="83b78-125">使用 XPath 查詢辨識的節點類型</span><span class="sxs-lookup"><span data-stu-id="83b78-125">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
- [<span data-ttu-id="83b78-126">XPath 查詢和命名空間</span><span class="sxs-lookup"><span data-stu-id="83b78-126">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
- [<span data-ttu-id="83b78-127">編譯 XPath 運算式</span><span class="sxs-lookup"><span data-stu-id="83b78-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
