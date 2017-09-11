---
title: "聯結作業 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5b561f66069b042f3216c80c7b8b3a13df63647e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="join-operations-visual-basic"></a><span data-ttu-id="4a068-102">聯結作業 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a068-102">Join Operations (Visual Basic)</span></span>
<span data-ttu-id="4a068-103">A*聯結*的兩個資料來源是指某個資料來源中的物件與另一個資料來源中的共同屬性的物件關聯。</span><span class="sxs-lookup"><span data-stu-id="4a068-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="4a068-104">對於不能直接追蹤目標資料來源彼此之間的關聯性的查詢而言，聯結是很重要的作業。</span><span class="sxs-lookup"><span data-stu-id="4a068-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="4a068-105">在物件導向的程式設計中，這可能表示物件之間的相互關聯沒有模組化，例如單向關聯性的返回方向。</span><span class="sxs-lookup"><span data-stu-id="4a068-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="4a068-106">一個單向關聯性的範例是「客戶」類別，其具有類型「城市」的屬性，但「城市」類別沒有「客戶」物件集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a068-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="4a068-107">若您有「城市」物件清單，且您想要尋找每個城市中的所有客戶，您就可以使用聯結作業來尋找客戶。</span><span class="sxs-lookup"><span data-stu-id="4a068-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="4a068-108">LINQ 架構中提供的聯結方法為<xref:System.Linq.Enumerable.Join%2A>和<xref:System.Linq.Enumerable.GroupJoin%2A>.</xref:System.Linq.Enumerable.GroupJoin%2A> </xref:System.Linq.Enumerable.Join%2A></span><span class="sxs-lookup"><span data-stu-id="4a068-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="4a068-109">這些方法會執行聯結或根據索引鍵相等與否的兩個資料來源的聯結。</span><span class="sxs-lookup"><span data-stu-id="4a068-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="4a068-110">(相較下，Transact-SQL 支援「等於」運算子以外的聯結運算子，例如「小於」運算字)。在關聯式資料庫術語<xref:System.Linq.Enumerable.Join%2A>實作內部聯結，一種聯結中，只有在其他資料集中有相符的物件會傳回。</xref:System.Linq.Enumerable.Join%2A></span><span class="sxs-lookup"><span data-stu-id="4a068-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="4a068-111"><xref:System.Linq.Enumerable.GroupJoin%2A>方法在關聯式資料庫詞彙中，有沒有直接的對等用法，但它會實作內部聯結及左外部聯結的超集。</xref:System.Linq.Enumerable.GroupJoin%2A></span><span class="sxs-lookup"><span data-stu-id="4a068-111">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="4a068-112">左外部聯結是傳回每個元素的第一個 （左） 資料來源的聯結，即使它具有其他資料來源中的任何相關項目。</span><span class="sxs-lookup"><span data-stu-id="4a068-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="4a068-113">以下概念圖示範兩個集合，以及兩個集合中包含在內部聯結或左外部聯結中的項目。</span><span class="sxs-lookup"><span data-stu-id="4a068-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 <span data-ttu-id="4a068-114">![兩個重疊圓形顯示內部/外部。] (../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")</span><span class="sxs-lookup"><span data-stu-id="4a068-114">![Two overlapping circles showing inner&#47;outer.](../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a068-115">方法</span><span class="sxs-lookup"><span data-stu-id="4a068-115">Methods</span></span>  
  
|<span data-ttu-id="4a068-116">方法名稱</span><span class="sxs-lookup"><span data-stu-id="4a068-116">Method Name</span></span>|<span data-ttu-id="4a068-117">描述</span><span class="sxs-lookup"><span data-stu-id="4a068-117">Description</span></span>|<span data-ttu-id="4a068-118">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="4a068-118">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="4a068-119">更多資訊</span><span class="sxs-lookup"><span data-stu-id="4a068-119">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="4a068-120">Join</span><span class="sxs-lookup"><span data-stu-id="4a068-120">Join</span></span>|<span data-ttu-id="4a068-121">根據索引鍵選取器函式聯結兩個序列並擷取值組。</span><span class="sxs-lookup"><span data-stu-id="4a068-121">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`From x In …, y In … Where x.a = y.a`<br /><br /> <span data-ttu-id="4a068-122">-或-</span><span class="sxs-lookup"><span data-stu-id="4a068-122">-or-</span></span><br /><br /> `Join … [As …]In … On …`|<span data-ttu-id="4a068-123"><xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a068-123"><xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="4a068-124"><xref:System.Linq.Queryable.Join%2A?displayProperty=fullName></xref:System.Linq.Queryable.Join%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a068-124"><xref:System.Linq.Queryable.Join%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="4a068-125">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="4a068-125">GroupJoin</span></span>|<span data-ttu-id="4a068-126">根據索引鍵選取器函式聯結兩個序列，並為每個項目的相符結果進行分組。</span><span class="sxs-lookup"><span data-stu-id="4a068-126">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`Group Join … In … On …`|<span data-ttu-id="4a068-127"><xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName></xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a068-127"><xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="4a068-128"><xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName></xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a068-128"><xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a068-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a068-129">See Also</span></span>  
 <span data-ttu-id="4a068-130"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="4a068-130"><xref:System.Linq></span></span>   
<span data-ttu-id="4a068-131"> [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="4a068-131"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="4a068-132"> [匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="4a068-132"> [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="4a068-133"> [制定聯結和交叉乘積查詢](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b) </span><span class="sxs-lookup"><span data-stu-id="4a068-133"> [Formulate Joins and Cross-Product Queries](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b) </span></span>  
<span data-ttu-id="4a068-134"> [Join 子句](../../../../visual-basic/language-reference/queries/join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="4a068-134"> [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) </span></span>  
<span data-ttu-id="4a068-135"> [如何︰ 將內容從不同的檔案 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) </span><span class="sxs-lookup"><span data-stu-id="4a068-135"> [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) </span></span>  
<span data-ttu-id="4a068-136"> [如何︰ 填入物件集合，從多個來源 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)</span><span class="sxs-lookup"><span data-stu-id="4a068-136"> [How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)</span></span>
