---
title: "聯結作業 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 00ff7cd6547c7472afd81fb227158cfe0df51ab4
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="join-operations-c"></a><span data-ttu-id="2b3fd-102">聯結作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="2b3fd-102">Join Operations (C#)</span></span>
<span data-ttu-id="2b3fd-103">兩個資料來源的「聯結」**，就是某個資料來源中的物件，和另一個資料來源中共用通用屬性的物件的關聯。</span><span class="sxs-lookup"><span data-stu-id="2b3fd-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="2b3fd-104">對於不能直接追蹤目標資料來源彼此之間的關聯性的查詢而言，聯結是很重要的作業。</span><span class="sxs-lookup"><span data-stu-id="2b3fd-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="2b3fd-105">在物件導向的程式設計中，這可能表示物件之間的相互關聯沒有模組化，例如單向關聯性的返回方向。</span><span class="sxs-lookup"><span data-stu-id="2b3fd-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="2b3fd-106">一個單向關聯性的範例是「客戶」類別，其具有類型「城市」的屬性，但「城市」類別沒有「客戶」物件集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="2b3fd-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="2b3fd-107">若您有「城市」物件清單，且您想要尋找每個城市中的所有客戶，您就可以使用聯結作業來尋找客戶。</span><span class="sxs-lookup"><span data-stu-id="2b3fd-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="2b3fd-108">LINQ 架構中提供的聯結方法為 <xref:System.Linq.Enumerable.Join%2A> 及 <xref:System.Linq.Enumerable.GroupJoin%2A>。</span><span class="sxs-lookup"><span data-stu-id="2b3fd-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="2b3fd-109">這些方法會執行等聯結，或是執行根據其索引鍵相等與否配對兩個資料來源的聯結。</span><span class="sxs-lookup"><span data-stu-id="2b3fd-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="2b3fd-110">(相較下，Transact-SQL 支援「等於」運算子以外的聯結運算子，例如「小於」運算字)。從關聯式資料庫觀點來看，<xref:System.Linq.Enumerable.Join%2A> 會實作內部聯結，在這種聯結中，只會傳回在其他資料集中有相符項目的物件。</span><span class="sxs-lookup"><span data-stu-id="2b3fd-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="2b3fd-111"><xref:System.Linq.Enumerable.GroupJoin%2A> 方法從關聯式資料庫觀點來看沒有直接的對應項目，但它會實作內部聯結和左方外部聯結的超集。</span><span class="sxs-lookup"><span data-stu-id="2b3fd-111">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="2b3fd-112">左方外部聯結是傳回第一個 (左) 資料來源中每個項目的聯結，即使它在其他資料來源中沒有相互關聯的項目也一樣。</span><span class="sxs-lookup"><span data-stu-id="2b3fd-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="2b3fd-113">以下概念圖示範兩個集合，以及兩個集合中包含在內部聯結或左外部聯結中的項目。</span><span class="sxs-lookup"><span data-stu-id="2b3fd-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 <span data-ttu-id="2b3fd-114">![顯示內部&#47;外部的兩個重疊圓形。](../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")</span><span class="sxs-lookup"><span data-stu-id="2b3fd-114">![Two overlapping circles showing inner&#47;outer.](../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b3fd-115">方法</span><span class="sxs-lookup"><span data-stu-id="2b3fd-115">Methods</span></span>  
  
|<span data-ttu-id="2b3fd-116">方法名稱</span><span class="sxs-lookup"><span data-stu-id="2b3fd-116">Method Name</span></span>|<span data-ttu-id="2b3fd-117">描述</span><span class="sxs-lookup"><span data-stu-id="2b3fd-117">Description</span></span>|<span data-ttu-id="2b3fd-118">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="2b3fd-118">C# Query Expression Syntax</span></span>|<span data-ttu-id="2b3fd-119">更多資訊</span><span class="sxs-lookup"><span data-stu-id="2b3fd-119">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="2b3fd-120">Join</span><span class="sxs-lookup"><span data-stu-id="2b3fd-120">Join</span></span>|<span data-ttu-id="2b3fd-121">根據索引鍵選取器函式聯結兩個序列並擷取值組。</span><span class="sxs-lookup"><span data-stu-id="2b3fd-121">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<span data-ttu-id="2b3fd-122"><xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2b3fd-122"><xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="2b3fd-123"><xref:System.Linq.Queryable.Join%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2b3fd-123"><xref:System.Linq.Queryable.Join%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="2b3fd-124">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="2b3fd-124">GroupJoin</span></span>|<span data-ttu-id="2b3fd-125">根據索引鍵選取器函式聯結兩個序列，並為每個項目的相符結果進行分組。</span><span class="sxs-lookup"><span data-stu-id="2b3fd-125">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<span data-ttu-id="2b3fd-126"><xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2b3fd-126"><xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="2b3fd-127"><xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2b3fd-127"><xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b3fd-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b3fd-128">See Also</span></span>  
 <span data-ttu-id="2b3fd-129"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="2b3fd-129"><xref:System.Linq></span></span>   
<span data-ttu-id="2b3fd-130"> [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="2b3fd-130"> [Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="2b3fd-131"> [匿名型別](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="2b3fd-131"> [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
<span data-ttu-id="2b3fd-132"> [制定聯結和交叉乘積查詢](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b) </span><span class="sxs-lookup"><span data-stu-id="2b3fd-132"> [Formulate Joins and Cross-Product Queries](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b) </span></span>  
<span data-ttu-id="2b3fd-133"> [join 子句](../../../../csharp/language-reference/keywords/join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="2b3fd-133"> [join clause](../../../../csharp/language-reference/keywords/join-clause.md) </span></span>  
<span data-ttu-id="2b3fd-134"> [如何：使用複合索引鍵執行聯結](../../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md) </span><span class="sxs-lookup"><span data-stu-id="2b3fd-134"> [How to: Join by Using Composite Keys](../../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md) </span></span>  
<span data-ttu-id="2b3fd-135"> [如何：從不同的檔案聯結內容 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) </span><span class="sxs-lookup"><span data-stu-id="2b3fd-135"> [How to: Join Content from Dissimilar Files (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) </span></span>  
<span data-ttu-id="2b3fd-136"> [如何：排序 Join 子句的結果](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="2b3fd-136"> [How to: Order the Results of a Join Clause](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md) </span></span>  
<span data-ttu-id="2b3fd-137"> [如何：執行自訂聯結作業](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md) </span><span class="sxs-lookup"><span data-stu-id="2b3fd-137"> [How to: Perform Custom Join Operations](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md) </span></span>  
<span data-ttu-id="2b3fd-138"> [如何：執行群組聯結](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md) </span><span class="sxs-lookup"><span data-stu-id="2b3fd-138"> [How to: Perform Grouped Joins](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md) </span></span>  
<span data-ttu-id="2b3fd-139"> [如何：執行內部聯結](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md) </span><span class="sxs-lookup"><span data-stu-id="2b3fd-139"> [How to: Perform Inner Joins](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md) </span></span>  
<span data-ttu-id="2b3fd-140"> [如何：執行左方外部聯結](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md) </span><span class="sxs-lookup"><span data-stu-id="2b3fd-140"> [How to: Perform Left Outer Joins](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md) </span></span>  
<span data-ttu-id="2b3fd-141"> [如何：從多個來源填入物件集合 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)</span><span class="sxs-lookup"><span data-stu-id="2b3fd-141"> [How to: Populate Object Collections from Multiple Sources (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)</span></span>
