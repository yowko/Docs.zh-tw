---
title: "編譯 XPath 運算式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f7b812d5d6f75e39e9eebcc003686ff88d009e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="0a7bb-102">編譯 XPath 運算式</span><span class="sxs-lookup"><span data-stu-id="0a7bb-102">Compiled XPath Expressions</span></span>
<span data-ttu-id="0a7bb-103"><xref:System.Xml.XPath.XPathExpression> 物件表示從 <xref:System.Xml.XPath.XPathExpression.Compile%2A> 類別的靜態 <xref:System.Xml.XPath.XPathExpression> 方法或 <xref:System.Xml.XPath.XPathNavigator.Compile%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator> 方法傳回的編譯 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="0a7bb-104">XPathExpression 類別</span><span class="sxs-lookup"><span data-stu-id="0a7bb-104">The XPathExpression Class</span></span>  
 <span data-ttu-id="0a7bb-105">如果會多次使用同一 XPath 查詢，則 <xref:System.Xml.XPath.XPathExpression> 物件所表示的編譯 XPath 查詢會很有用。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="0a7bb-106">例如，多次呼叫 <xref:System.Xml.XPath.XPathNavigator.Select%2A> 方法，而不是每次都使用表示 XPath 查詢的字串時，請使用 <xref:System.Xml.XPath.XPathExpression.Compile%2A> 類別的 <xref:System.Xml.XPath.XPathExpression> 方法或 <xref:System.Xml.XPath.XPathNavigator.Compile%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator> 方法，來編譯並快取 <xref:System.Xml.XPath.XPathExpression> 物件中的 XPath 查詢，以重複使用並提升效能。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="0a7bb-107">編譯後，根據從 XPath 查詢傳回的型別，可能會使用 <xref:System.Xml.XPath.XPathExpression> 物件做為下列 <xref:System.Xml.XPath.XPathNavigator> 類別方法的輸入。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="0a7bb-108">下表說明每個 W3C XPath 傳回型別、其 Microsoft .NET Framework 對等型別，以及與 <xref:System.Xml.XPath.XPathExpression> 物件搭配使用的方法 (根據其傳回型別)。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="0a7bb-109">W3C XPath 傳回型別</span><span class="sxs-lookup"><span data-stu-id="0a7bb-109">W3C XPath Return Type</span></span>|<span data-ttu-id="0a7bb-110">.NET Framework 對等型別</span><span class="sxs-lookup"><span data-stu-id="0a7bb-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="0a7bb-111">描述</span><span class="sxs-lookup"><span data-stu-id="0a7bb-111">Description</span></span>|<span data-ttu-id="0a7bb-112">方法</span><span class="sxs-lookup"><span data-stu-id="0a7bb-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="0a7bb-113">依文件順序建立之不重複節點的未排序集合。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="0a7bb-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> 或 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="0a7bb-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="0a7bb-115">`true` 或 `false` 值。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-115">A `true` or `false` value.</span></span>|<span data-ttu-id="0a7bb-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 或</span><span class="sxs-lookup"><span data-stu-id="0a7bb-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="0a7bb-117">浮點數。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="0a7bb-118">UCS 字元的順序。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
>  <span data-ttu-id="0a7bb-119"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法會接受 XPath 運算式做為它的參數。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="0a7bb-120"><xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> 方法會傳回 <xref:System.Xml.XPath.XPathNavigator> 物件，而不是其中一個 W3C XPath 傳回型別。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="0a7bb-121">ReturnType 屬性</span><span class="sxs-lookup"><span data-stu-id="0a7bb-121">The ReturnType Property</span></span>  
 <span data-ttu-id="0a7bb-122">將 XPath 查詢編譯到 <xref:System.Xml.XPath.XPathExpression> 物件中之後，您可使用 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> 物件的 <xref:System.Xml.XPath.XPathExpression> 屬性來判斷 XPath 查詢傳回的型別。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="0a7bb-123"><xref:System.Xml.XPath.XPathExpression.ReturnType%2A> 屬性會傳回下列其中一個表示 W3C XPath 傳回型別的 <xref:System.Xml.XPath.XPathResultType> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
-   <xref:System.Xml.XPath.XPathResultType.Any>  
  
-   <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
-   <xref:System.Xml.XPath.XPathResultType.Error>  
  
-   <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
-   <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
-   <xref:System.Xml.XPath.XPathResultType.Number>  
  
-   <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="0a7bb-124">下列範例會使用 <xref:System.Xml.XPath.XPathExpression> 物件，從 `books.xml` 檔案傳回號碼及節點集。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="0a7bb-125">將每個 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> 物件的 <xref:System.Xml.XPath.XPathExpression> 屬性及 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 與 <xref:System.Xml.XPath.XPathNavigator.Select%2A> 方法的結果寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Returns a number.  
Dim query1 As XPathExpression = navigator.Compile("bookstore/book/price/text()*10")  
Console.WriteLine(query1.ReturnType)  
  
Dim number As Double = CType(navigator.Evaluate(query1), Double)  
Console.WriteLine(number)  
  
' Returns a node set.  
Dim query2 As XPathExpression = navigator.Compile("bookstore/book/price")  
Console.WriteLine(query2.ReturnType)  
  
Dim nodes As XPathNodeIterator = navigator.Select(query2)  
nodes.MoveNext()  
Console.WriteLine(nodes.Current.Value)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Returns a number.  
XPathExpression query1 = navigator.Compile("bookstore/book/price/text()*10");  
Console.WriteLine(query1.ReturnType);  
  
Double number = (Double)navigator.Evaluate(query1);  
Console.WriteLine(number);  
  
// Returns a node set.  
XPathExpression query2 = navigator.Compile("bookstore/book/price");  
Console.WriteLine(query2.ReturnType);  
  
XPathNodeIterator nodes = navigator.Select(query2);  
nodes.MoveNext();  
Console.WriteLine(nodes.Current.Value);  
```  
  
 <span data-ttu-id="0a7bb-126">該範例採用 `books.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="0a7bb-127">較高效能的 XPath 運算式</span><span class="sxs-lookup"><span data-stu-id="0a7bb-127">Higher Performance XPath Expressions</span></span>  
 <span data-ttu-id="0a7bb-128">為了達到較高的效能，請在查詢中使用可能最適合的 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="0a7bb-129">例如，如果 `book` 節點是 `bookstore` 節點的子節點，且 `bookstore` 節點是 XML 文件中的最上層項目，則使用 XPath 運算式 `/bookstore/book` 會比使用 `//book` 更快速。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="0a7bb-130">`//book` XPath 運算式將掃描 XML 樹狀目錄中的每個節點，以識別符合的節點。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="0a7bb-131">此外，在選取準則很簡單的情況下，使用 <xref:System.Xml.XPath.XPathNavigator> 類別提供之節點集巡覽方法的效能，可能會比 <xref:System.Xml.XPath.XPathNavigator> 類別提供之選取方法的效能高。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="0a7bb-132">例如，如果需要選取目前節點的第一個子節點，則使用 <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> 方法會比使用 `child::*[1]` XPath 運算式及 <xref:System.Xml.XPath.XPathNavigator.Select%2A> 方法更快速。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="0a7bb-133">如需有關節點集巡覽方法<xref:System.Xml.XPath.XPathNavigator>類別，請參閱[節點集巡覽使用 XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)。</span><span class="sxs-lookup"><span data-stu-id="0a7bb-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a7bb-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a7bb-134">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="0a7bb-135">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="0a7bb-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="0a7bb-136">使用 XPathNavigator 選取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="0a7bb-136">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="0a7bb-137">使用 XPathNavigator 評估 XPath 運算式</span><span class="sxs-lookup"><span data-stu-id="0a7bb-137">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="0a7bb-138">使用 XPathNavigator 比對節點</span><span class="sxs-lookup"><span data-stu-id="0a7bb-138">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="0a7bb-139">XPath 查詢中辨識的節點型別</span><span class="sxs-lookup"><span data-stu-id="0a7bb-139">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="0a7bb-140">XPath 查詢及命名空間</span><span class="sxs-lookup"><span data-stu-id="0a7bb-140">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
