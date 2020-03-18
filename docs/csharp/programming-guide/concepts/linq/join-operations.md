---
title: Join操作 （C#）
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76868001"
---
# <a name="join-operations-c"></a><span data-ttu-id="5ad53-102">聯結作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="5ad53-102">Join Operations (C#)</span></span>

<span data-ttu-id="5ad53-103">兩個資料來源的「聯結」\*\*，就是某個資料來源中的物件，和另一個資料來源中共用通用屬性的物件的關聯。</span><span class="sxs-lookup"><span data-stu-id="5ad53-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="5ad53-104">對於不能直接追蹤目標資料來源彼此之間的關聯性的查詢而言，聯結是很重要的作業。</span><span class="sxs-lookup"><span data-stu-id="5ad53-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="5ad53-105">在物件導向的程式設計中，這可能表示物件之間的相互關聯沒有模組化，例如單向關聯性的返回方向。</span><span class="sxs-lookup"><span data-stu-id="5ad53-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="5ad53-106">一個單向關聯性的範例是「客戶」類別，其具有類型「城市」的屬性，但「城市」類別沒有「客戶」物件集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="5ad53-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="5ad53-107">若您有「城市」物件清單，且您想要尋找每個城市中的所有客戶，您就可以使用聯結作業來尋找客戶。</span><span class="sxs-lookup"><span data-stu-id="5ad53-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="5ad53-108">LINQ 架構中所提供的 join 方法是 <xref:System.Linq.Enumerable.Join%2A> 和 <xref:System.Linq.Enumerable.GroupJoin%2A>。</span><span class="sxs-lookup"><span data-stu-id="5ad53-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="5ad53-109">這些方法會執行等聯結，或是執行根據其索引鍵相等與否配對兩個資料來源的聯結。</span><span class="sxs-lookup"><span data-stu-id="5ad53-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="5ad53-110">（為了進行比較，Transact-SQL 支援"等於"以外的聯結運算子，例如"小於"運算子。在關係資料庫術語中，<xref:System.Linq.Enumerable.Join%2A>實現內部聯接，即僅返回在其他資料集中具有匹配的物件的聯接類型。</span><span class="sxs-lookup"><span data-stu-id="5ad53-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="5ad53-111"><xref:System.Linq.Enumerable.GroupJoin%2A> 方法從關聯式資料庫觀點來看沒有直接的對應項目，但它會實作內部聯結和左方外部聯結的超集。</span><span class="sxs-lookup"><span data-stu-id="5ad53-111">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="5ad53-112">左方外部聯結是傳回第一個 (左) 資料來源中每個項目的聯結，即使它在其他資料來源中沒有相互關聯的項目也一樣。</span><span class="sxs-lookup"><span data-stu-id="5ad53-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="5ad53-113">以下概念圖示範兩個集合，以及兩個集合中包含在內部聯結或左外部聯結中的項目。</span><span class="sxs-lookup"><span data-stu-id="5ad53-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![顯示內部&#47;外部的兩個重疊圓形。](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="5ad53-115">方法</span><span class="sxs-lookup"><span data-stu-id="5ad53-115">Methods</span></span>  
  
|<span data-ttu-id="5ad53-116">方法名稱</span><span class="sxs-lookup"><span data-stu-id="5ad53-116">Method Name</span></span>|<span data-ttu-id="5ad53-117">描述</span><span class="sxs-lookup"><span data-stu-id="5ad53-117">Description</span></span>|<span data-ttu-id="5ad53-118">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="5ad53-118">C# Query Expression Syntax</span></span>|<span data-ttu-id="5ad53-119">相關資訊</span><span class="sxs-lookup"><span data-stu-id="5ad53-119">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|<span data-ttu-id="5ad53-120">根據索引鍵選取器函式聯結兩個序列並擷取值組。</span><span class="sxs-lookup"><span data-stu-id="5ad53-120">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|<span data-ttu-id="5ad53-121">根據索引鍵選取器函式聯結兩個序列，並為每個項目的相符結果進行分組。</span><span class="sxs-lookup"><span data-stu-id="5ad53-121">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="5ad53-122">查詢運算式語法示例</span><span class="sxs-lookup"><span data-stu-id="5ad53-122">Query expression syntax examples</span></span>
  
### Join  
  
<span data-ttu-id="5ad53-123">下面的示例使用 子`join … in … on … equals …`句根據特定值聯接兩個序列：</span><span class="sxs-lookup"><span data-stu-id="5ad53-123">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

<span data-ttu-id="5ad53-124">下面的示例使用 子`join … in … on … equals … into …`句根據特定值聯接兩個序列，並為每個元素的結果匹配進行分組：</span><span class="sxs-lookup"><span data-stu-id="5ad53-124">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a><span data-ttu-id="5ad53-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ad53-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="5ad53-126">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="5ad53-126">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="5ad53-127">匿名型別</span><span class="sxs-lookup"><span data-stu-id="5ad53-127">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="5ad53-128">制定聯結和交叉乘積查詢</span><span class="sxs-lookup"><span data-stu-id="5ad53-128">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="5ad53-129">聯接子句</span><span class="sxs-lookup"><span data-stu-id="5ad53-129">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- <span data-ttu-id="5ad53-130">[Join通過使用複合鍵](../../../linq/join-by-using-composite-keys.md)</span><span class="sxs-lookup"><span data-stu-id="5ad53-130">[Join by using composite keys](../../../linq/join-by-using-composite-keys.md)</span></span>
- [<span data-ttu-id="5ad53-131">如何從不同檔 （LINQ） （C#） 加入內容</span><span class="sxs-lookup"><span data-stu-id="5ad53-131">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="5ad53-132">排序 join 子句的結果</span><span class="sxs-lookup"><span data-stu-id="5ad53-132">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="5ad53-133">執行自訂聯接操作</span><span class="sxs-lookup"><span data-stu-id="5ad53-133">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="5ad53-134">執行群組聯結</span><span class="sxs-lookup"><span data-stu-id="5ad53-134">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="5ad53-135">執行內部聯結</span><span class="sxs-lookup"><span data-stu-id="5ad53-135">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="5ad53-136">執行左方外部聯結</span><span class="sxs-lookup"><span data-stu-id="5ad53-136">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="5ad53-137">如何從多個源 （LINQ） （C#） 填充物件集合</span><span class="sxs-lookup"><span data-stu-id="5ad53-137">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
