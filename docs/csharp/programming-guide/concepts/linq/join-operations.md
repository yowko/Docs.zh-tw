---
title: ':::no-loc(Join):::作業（c #）'
description: '兩個數據源的聯結會使物件與跨資料來源共用屬性的物件產生關聯。 瞭解 c # 中 LINQ framework 的聯結方法。'
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- ':::no-loc(Join):::'
- ':::no-loc(GroupJoin):::'
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165691"
---
# <a name="no-locjoin-operations-c"></a><span data-ttu-id="af604-104">:::no-loc(Join):::作業（c #）</span><span class="sxs-lookup"><span data-stu-id="af604-104">:::no-loc(Join)::: Operations (C#)</span></span>

<span data-ttu-id="af604-105">兩個資料來源的「聯結」\*\*，就是某個資料來源中的物件，和另一個資料來源中共用通用屬性的物件的關聯。</span><span class="sxs-lookup"><span data-stu-id="af604-105">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="af604-106">:::no-loc(Join):::在以資料來源為目標的查詢中，對於彼此之間的關聯性無法直接遵循，ing 是一項重要的作業。</span><span class="sxs-lookup"><span data-stu-id="af604-106">:::no-loc(Join):::ing is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="af604-107">在物件導向的程式設計中，這可能表示物件之間的相互關聯沒有模組化，例如單向關聯性的返回方向。</span><span class="sxs-lookup"><span data-stu-id="af604-107">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="af604-108">一個單向關聯性的範例是「客戶」類別，其具有類型「城市」的屬性，但「城市」類別沒有「客戶」物件集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="af604-108">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="af604-109">若您有「城市」物件清單，且您想要尋找每個城市中的所有客戶，您就可以使用聯結作業來尋找客戶。</span><span class="sxs-lookup"><span data-stu-id="af604-109">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="af604-110">LINQ 架構中所提供的 join 方法是 <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> 和 <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A>。</span><span class="sxs-lookup"><span data-stu-id="af604-110">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> and <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A>.</span></span> <span data-ttu-id="af604-111">這些方法會執行等聯結，或是執行根據其索引鍵相等與否配對兩個資料來源的聯結。</span><span class="sxs-lookup"><span data-stu-id="af604-111">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="af604-112">（為了進行比較，Transact-sql 支援 ' equals ' 以外的聯結運算子，例如 ' 小於 ' 運算子）。在關係資料庫詞彙中， <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> 會執行內部聯結，這是一種聯結類型，其中只會傳回在其他資料集中具有相符項的物件。</span><span class="sxs-lookup"><span data-stu-id="af604-112">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="af604-113"><xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> 方法從關聯式資料庫觀點來看沒有直接的對應項目，但它會實作內部聯結和左方外部聯結的超集。</span><span class="sxs-lookup"><span data-stu-id="af604-113">The <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="af604-114">左方外部聯結是傳回第一個 (左) 資料來源中每個項目的聯結，即使它在其他資料來源中沒有相互關聯的項目也一樣。</span><span class="sxs-lookup"><span data-stu-id="af604-114">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="af604-115">以下概念圖示範兩個集合，以及兩個集合中包含在內部聯結或左外部聯結中的項目。</span><span class="sxs-lookup"><span data-stu-id="af604-115">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![顯示內部&#47;外部的兩個重疊圓形。](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="af604-117">方法</span><span class="sxs-lookup"><span data-stu-id="af604-117">Methods</span></span>  
  
|<span data-ttu-id="af604-118">方法名稱</span><span class="sxs-lookup"><span data-stu-id="af604-118">Method Name</span></span>|<span data-ttu-id="af604-119">描述</span><span class="sxs-lookup"><span data-stu-id="af604-119">Description</span></span>|<span data-ttu-id="af604-120">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="af604-120">C# Query Expression Syntax</span></span>|<span data-ttu-id="af604-121">相關資訊</span><span class="sxs-lookup"><span data-stu-id="af604-121">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|:::no-loc(Join):::|<span data-ttu-id="af604-122">:::no-loc(Join):::s 以索引鍵選取器函式為基礎的兩個序列，並會解壓縮值的配對。</span><span class="sxs-lookup"><span data-stu-id="af604-122">:::no-loc(Join):::s two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.:::no-loc(Join):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(Join):::%2A?displayProperty=nameWithType>|  
|:::no-loc(GroupJoin):::|<span data-ttu-id="af604-123">:::no-loc(Join):::以索引鍵選取器函式為基礎的兩個序列，並將每個元素的結果相符專案分組。</span><span class="sxs-lookup"><span data-stu-id="af604-123">:::no-loc(Join):::s two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="af604-124">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="af604-124">Query expression syntax examples</span></span>
  
### :::no-loc(Join):::  
  
<span data-ttu-id="af604-125">下列範例會使用 `join … in … on … equals …` 子句，根據特定值聯結兩個序列：</span><span class="sxs-lookup"><span data-stu-id="af604-125">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[:::no-loc(Join):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(Join):::)]  

### :::no-loc(GroupJoin):::  

<span data-ttu-id="af604-126">下列範例會使用 `join … in … on … equals … into …` 子句，根據特定值聯結兩個序列，並將每個元素的結果相符專案分組：</span><span class="sxs-lookup"><span data-stu-id="af604-126">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[:::no-loc(GroupJoin):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(GroupJoin):::)]  
  
## <a name="see-also"></a><span data-ttu-id="af604-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af604-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="af604-128">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="af604-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="af604-129">匿名類型</span><span class="sxs-lookup"><span data-stu-id="af604-129">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="af604-130">制訂 :::no-loc(Join)::: 和交叉乘積查詢</span><span class="sxs-lookup"><span data-stu-id="af604-130">Formulate :::no-loc(Join):::s and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="af604-131">join 子句</span><span class="sxs-lookup"><span data-stu-id="af604-131">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="af604-132">:::no-loc(Join):::使用複合索引鍵</span><span class="sxs-lookup"><span data-stu-id="af604-132">:::no-loc(Join)::: by using composite keys</span></span>](../../../linq/join-by-using-composite-keys.md)
- [<span data-ttu-id="af604-133">如何從不同的檔案聯結內容（LINQ）（c #）</span><span class="sxs-lookup"><span data-stu-id="af604-133">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="af604-134">排序 join 子句的結果</span><span class="sxs-lookup"><span data-stu-id="af604-134">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="af604-135">執行自訂的聯結作業</span><span class="sxs-lookup"><span data-stu-id="af604-135">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="af604-136">執行群組聯結</span><span class="sxs-lookup"><span data-stu-id="af604-136">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="af604-137">執行內部聯結</span><span class="sxs-lookup"><span data-stu-id="af604-137">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="af604-138">執行左方外部聯結</span><span class="sxs-lookup"><span data-stu-id="af604-138">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="af604-139">如何從多個來源填入物件集合（LINQ）（c #）</span><span class="sxs-lookup"><span data-stu-id="af604-139">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
