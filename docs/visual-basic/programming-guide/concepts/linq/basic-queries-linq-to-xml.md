---
title: "基本查詢 (LINQ to XML) (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: aec6ef60-f6f4-4548-b3db-cf6c94bb0008
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5c558201ad4fdd5412930651fa926f4441b78346
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="basic-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="1daef-102">基本查詢 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1daef-102">Basic Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="1daef-103">本節提供 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 基本查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="1daef-103">This section provides examples of basic [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] queries.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1daef-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="1daef-104">In This Section</span></span>  
  
|<span data-ttu-id="1daef-105">主題</span><span class="sxs-lookup"><span data-stu-id="1daef-105">Topic</span></span>|<span data-ttu-id="1daef-106">描述</span><span class="sxs-lookup"><span data-stu-id="1daef-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1daef-107">如何︰ 尋找具有特定屬性 (Visual Basic) 的項目</span><span class="sxs-lookup"><span data-stu-id="1daef-107">How to: Find an Element with a Specific Attribute (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-an-element-with-a-specific-attribute.md)|<span data-ttu-id="1daef-108">顯示如何尋找其屬性具有特定值的特定項目。</span><span class="sxs-lookup"><span data-stu-id="1daef-108">Shows how to find a particular element that has an attribute that has a specific value.</span></span>|  
|[<span data-ttu-id="1daef-109">如何︰ 尋找具有特定子項目 (Visual Basic) 的項目</span><span class="sxs-lookup"><span data-stu-id="1daef-109">How to: Find an Element with a Specific Child Element (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-an-element-with-a-specific-child-element.md)|<span data-ttu-id="1daef-110">顯示如何尋找其子項目具有特定值的特定項目。</span><span class="sxs-lookup"><span data-stu-id="1daef-110">Shows how to find a particular element that has a child element that has a specific value.</span></span>|  
|[<span data-ttu-id="1daef-111">查詢 XDocument 與查詢 xelement 的比較 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1daef-111">Querying an XDocument vs. Querying an XElement (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-an-xdocument-vs-querying-an-xelement.md)|<span data-ttu-id="1daef-112">說明撰寫查詢，<xref:System.Xml.Linq.XElement>以及撰寫查詢，以<xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument>為基礎的 XML 樹狀結構</xref:System.Xml.Linq.XElement>為基礎的 XML 樹狀結構之間的差異</span><span class="sxs-lookup"><span data-stu-id="1daef-112">Explains the differences between writing queries on an XML tree that is rooted in <xref:System.Xml.Linq.XElement> and writing queries on an XML tree that is rooted in <xref:System.Xml.Linq.XDocument>.</span></span>|  
|[<span data-ttu-id="1daef-113">如何︰ 尋找子系的特定項目名稱 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1daef-113">How to: Find Descendants with a Specific Element Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendants-with-a-specific-element-name.md)|<span data-ttu-id="1daef-114">顯示如何尋找具有特定名稱之項目的所有子代。</span><span class="sxs-lookup"><span data-stu-id="1daef-114">Shows how to find all the descendants of an element that have a specific name.</span></span> <span data-ttu-id="1daef-115">這個範例會使用<xref:System.Xml.Linq.XContainer.Descendants%2A>軸。</xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="1daef-115">This example uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>|  
|[<span data-ttu-id="1daef-116">如何︰ 尋找單一子代使用 Descendants 方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1daef-116">How to: Find a Single Descendant Using the Descendants Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-single-descendant-using-the-descendants-method.md)|<span data-ttu-id="1daef-117">示範如何使用<xref:System.Xml.Linq.XContainer.Descendants%2A>座標軸方法來尋找唯一單一具名項目。</xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="1daef-117">Shows how to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to find a single uniquely named element.</span></span>|  
|[<span data-ttu-id="1daef-118">如何︰ 利用複雜篩選 (Visual Basic) 撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="1daef-118">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md)|<span data-ttu-id="1daef-119">顯示如何使用更複雜的篩選條件撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="1daef-119">Shows how to write a query with a more complex filter.</span></span>|  
|[<span data-ttu-id="1daef-120">如何︰ 篩選選擇性項目 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1daef-120">How to: Filter on an Optional Element (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-an-optional-element.md)|<span data-ttu-id="1daef-121">顯示如何在不規則組織的樹狀中尋找節點。</span><span class="sxs-lookup"><span data-stu-id="1daef-121">Shows how to find nodes in an irregularly shaped tree.</span></span>|  
|[<span data-ttu-id="1daef-122">如何︰ 尋找命名空間 (Visual Basic) 中的所有節點</span><span class="sxs-lookup"><span data-stu-id="1daef-122">How to: Find All Nodes in a Namespace (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-all-nodes-in-a-namespace.md)|<span data-ttu-id="1daef-123">顯示如何尋找特定命名空間中的所有節點。</span><span class="sxs-lookup"><span data-stu-id="1daef-123">Shows how to find all nodes that are in a specific namespace.</span></span>|  
|[<span data-ttu-id="1daef-124">如何︰ 排序項目 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1daef-124">How to: Sort Elements (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-elements.md)|<span data-ttu-id="1daef-125">顯示如何撰寫排序其結果的查詢。</span><span class="sxs-lookup"><span data-stu-id="1daef-125">Shows how to write a query that sorts its results.</span></span>|  
|[<span data-ttu-id="1daef-126">如何︰ 排序多個索引鍵 (Visual Basic) 的項目</span><span class="sxs-lookup"><span data-stu-id="1daef-126">How to: Sort Elements on Multiple Keys (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md)|<span data-ttu-id="1daef-127">顯示如何在多個索引鍵上排序。</span><span class="sxs-lookup"><span data-stu-id="1daef-127">Shows how to sort on multiple keys.</span></span>|  
|[<span data-ttu-id="1daef-128">如何︰ 計算中繼值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1daef-128">How to: Calculate Intermediate Values (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-calculate-intermediate-values.md)|<span data-ttu-id="1daef-129">示範如何使用`Let`子句來計算中的中繼值[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]查詢。</span><span class="sxs-lookup"><span data-stu-id="1daef-129">Shows how to use the `Let` clause to calculate intermediate values in a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query.</span></span>|  
|[<span data-ttu-id="1daef-130">如何︰ 撰寫查詢，以尋找項目根據內容 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1daef-130">How to: Write a Query that Finds Elements Based on Context (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-query-that-finds-elements-based-on-context.md)|<span data-ttu-id="1daef-131">顯示如何根據樹狀中的其他項目選取項目。</span><span class="sxs-lookup"><span data-stu-id="1daef-131">Shows how to select elements based on other elements in the tree.</span></span>|  
|[<span data-ttu-id="1daef-132">如何︰ 偵錯空白查詢結果集 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1daef-132">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md)|<span data-ttu-id="1daef-133">針對預設命名空間中的 XML 偵錯查詢時，顯示適當的修正。</span><span class="sxs-lookup"><span data-stu-id="1daef-133">Shows the appropriate fix when debugging queries on XML that is in a default namespace.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1daef-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1daef-134">See Also</span></span>  
 [<span data-ttu-id="1daef-135">查詢 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1daef-135">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
