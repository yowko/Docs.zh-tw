---
title: 使用 XPathNavigator 巡覽節點集
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f062f7fd58efe6c350b3a119ec3bdd4d27b896db
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086362"
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="88232-102">使用 XPathNavigator 巡覽節點集</span><span class="sxs-lookup"><span data-stu-id="88232-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="88232-103">您可以使用 <xref:System.Xml.XPath.XPathDocument> 類別的節點集巡覽方法，巡覽 <xref:System.Xml.XmlDocument> 或 <xref:System.Xml.XPath.XPathNavigator> 物件中的節點。</span><span class="sxs-lookup"><span data-stu-id="88232-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="88232-104">您可以巡覽所有節點或由 <xref:System.Xml.XPath.XPathNavigator> 類別的其中一個選取方法傳回的選定節點集。</span><span class="sxs-lookup"><span data-stu-id="88232-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="88232-105">項目節點集巡覽</span><span class="sxs-lookup"><span data-stu-id="88232-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="88232-106"><xref:System.Xml.XPath.XPathNavigator> 類別提供可用於巡覽項目節點的數種方法。</span><span class="sxs-lookup"><span data-stu-id="88232-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="88232-107">下表顯示可用的巡覽方法及其移動方式的說明；但不包括可用於巡覽屬性及命名空間節點的方法。</span><span class="sxs-lookup"><span data-stu-id="88232-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="88232-108">如需有關選取 <xref:System.Xml.XPath.XPathNavigator> 物件中之節點的詳細資訊，請參閱[使用 XPathNavigator 選取、評估與比對 XML 資料](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)。</span><span class="sxs-lookup"><span data-stu-id="88232-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="88232-109">如需有關巡覽屬性和命名空間節點的詳細資訊，請參閱[使用 XPathNavigator 巡覽屬性及命名空間節點](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)。</span><span class="sxs-lookup"><span data-stu-id="88232-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="88232-110">方法</span><span class="sxs-lookup"><span data-stu-id="88232-110">Method</span></span>|<span data-ttu-id="88232-111">描述</span><span class="sxs-lookup"><span data-stu-id="88232-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="88232-112">將 <xref:System.Xml.XPath.XPathNavigator> 移至與指定之 <xref:System.Xml.XPath.XPathNavigator> 相同的位置。</span><span class="sxs-lookup"><span data-stu-id="88232-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="88232-113">將 <xref:System.Xml.XPath.XPathNavigator> 移至目前節點的子節點。</span><span class="sxs-lookup"><span data-stu-id="88232-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="88232-114">將 <xref:System.Xml.XPath.XPathNavigator> 移至目前節點的第一個同層級節點。</span><span class="sxs-lookup"><span data-stu-id="88232-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="88232-115">將 <xref:System.Xml.XPath.XPathNavigator> 移至目前節點的第一個子節點。</span><span class="sxs-lookup"><span data-stu-id="88232-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="88232-116">將 <xref:System.Xml.XPath.XPathNavigator> 移至文件順序中指定的項目。</span><span class="sxs-lookup"><span data-stu-id="88232-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="88232-117">將 <xref:System.Xml.XPath.XPathNavigator> 移至屬性型別為 `ID` 且值符合給定 <xref:System.String> 的節點。</span><span class="sxs-lookup"><span data-stu-id="88232-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="88232-118">將 <xref:System.Xml.XPath.XPathNavigator> 移至目前節點的下一個同層級節點。</span><span class="sxs-lookup"><span data-stu-id="88232-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="88232-119">將 <xref:System.Xml.XPath.XPathNavigator> 移至目前節點的父節點。</span><span class="sxs-lookup"><span data-stu-id="88232-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="88232-120">將 <xref:System.Xml.XPath.XPathNavigator> 移至目前節點的前一個同層級節點。</span><span class="sxs-lookup"><span data-stu-id="88232-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="88232-121">將 <xref:System.Xml.XPath.XPathNavigator> 移至 XML 文件的根節點。</span><span class="sxs-lookup"><span data-stu-id="88232-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="88232-122">註解及處理指示節點巡覽</span><span class="sxs-lookup"><span data-stu-id="88232-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="88232-123">下列 <xref:System.Xml.XPath.XPathNavigator> 類別方法適用於從 XML 文件中的其他節點移至註解或處理指示。</span><span class="sxs-lookup"><span data-stu-id="88232-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="88232-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88232-124">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="88232-125">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="88232-125">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="88232-126">使用 XPathNavigator 導覽屬性和命名空間節點</span><span class="sxs-lookup"><span data-stu-id="88232-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
- [<span data-ttu-id="88232-127">使用 XPathNavigator 擷取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="88232-127">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="88232-128">使用 XPathNavigator 存取強型別 XML 資料</span><span class="sxs-lookup"><span data-stu-id="88232-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
