---
title: "使用 XPathNavigator 評估 XPath 運算式"
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
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d4515b8ebea338a153319dfd02eab8d389b843b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="602f6-102">使用 XPathNavigator 評估 XPath 運算式</span><span class="sxs-lookup"><span data-stu-id="602f6-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="602f6-103"><xref:System.Xml.XPath.XPathNavigator> 類別提供 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法，以評估 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="602f6-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="602f6-104"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法會使用 XPath 運算式，評估它並根據 XPath 運算式的結果傳回 W3C XPath 型別：Boolean、Number、String 或 Node Set。</span><span class="sxs-lookup"><span data-stu-id="602f6-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="602f6-105">評估方法</span><span class="sxs-lookup"><span data-stu-id="602f6-105">The Evaluate Method</span></span>  
 <span data-ttu-id="602f6-106"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法會使用 XPath 運算式，評估它並傳回具型別的結果：Boolean (<xref:System.Boolean>)、Number (<xref:System.Double>)、String (<xref:System.String>) 或 Node Set (<xref:System.Xml.XPath.XPathNodeIterator>)。</span><span class="sxs-lookup"><span data-stu-id="602f6-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="602f6-107">例如，<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法可用於數學方法。</span><span class="sxs-lookup"><span data-stu-id="602f6-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="602f6-108">下列範例程式碼會計算 `books.xml` 檔案中所有書籍的總價。</span><span class="sxs-lookup"><span data-stu-id="602f6-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 <span data-ttu-id="602f6-109">該範例採用 `books.xml` 檔案做為輸入。</span><span class="sxs-lookup"><span data-stu-id="602f6-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="602f6-110">position 及 last 函式</span><span class="sxs-lookup"><span data-stu-id="602f6-110">position and last Functions</span></span>  
 <span data-ttu-id="602f6-111">會多載 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="602f6-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="602f6-112">其中一個 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法會採用 <xref:System.Xml.XPath.XPathNodeIterator> 物件做為參數。</span><span class="sxs-lookup"><span data-stu-id="602f6-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="602f6-113">此特定 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 方法與僅將 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 物件做為參數的 <xref:System.Xml.XPath.XPathExpression> 方法相同，只是它允許節點集引數來指定要執行評估的目前內容。</span><span class="sxs-lookup"><span data-stu-id="602f6-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="602f6-114">此內容對於 XPath `position()` 及 `last()` 函式是必要的，因為它們相對於目前的內容節點。</span><span class="sxs-lookup"><span data-stu-id="602f6-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="602f6-115">除非是用做位置步驟中的述詞，否則 `position()` 及 `last()` 函式需要節點集的參考以進行評估，否則 `position` 及 `last` 函式會傳回 `0`。</span><span class="sxs-lookup"><span data-stu-id="602f6-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="602f6-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="602f6-116">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="602f6-117">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="602f6-117">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="602f6-118">使用 XPathNavigator 選取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="602f6-118">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="602f6-119">使用 XPathNavigator 比對節點</span><span class="sxs-lookup"><span data-stu-id="602f6-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="602f6-120">使用 XPath 查詢辨識的節點類型</span><span class="sxs-lookup"><span data-stu-id="602f6-120">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="602f6-121">XPath 查詢和命名空間</span><span class="sxs-lookup"><span data-stu-id="602f6-121">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="602f6-122">編譯 XPath 運算式</span><span class="sxs-lookup"><span data-stu-id="602f6-122">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
