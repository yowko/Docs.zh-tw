---
title: Null 比較
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: a9e519fb8b2ca021d66adb23659d83efc571afae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222662"
---
# <a name="null-comparisons"></a><span data-ttu-id="daeeb-102">Null 比較</span><span class="sxs-lookup"><span data-stu-id="daeeb-102">Null Comparisons</span></span>
<span data-ttu-id="daeeb-103">資料來源中的 `null` 值表示該值未知。</span><span class="sxs-lookup"><span data-stu-id="daeeb-103">A `null` value in the data source indicates that the value is unknown.</span></span> <span data-ttu-id="daeeb-104">在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢中，您可以檢查 null 值，以便讓某些計算或比較只會在包含有效或非 null 資料的資料列上執行。</span><span class="sxs-lookup"><span data-stu-id="daeeb-104">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries, you can check for null values so that certain calculations or comparisons are only performed on rows that have valid, or non-null, data.</span></span> <span data-ttu-id="daeeb-105">不過，CLR null 語意 (Semantics) 可能與資料來源的 null 語意不同。</span><span class="sxs-lookup"><span data-stu-id="daeeb-105">CLR null semantics, however, may differ from the null semantics of the data source.</span></span> <span data-ttu-id="daeeb-106">大部分的資料庫都使用三值邏輯來處理 null 比較，</span><span class="sxs-lookup"><span data-stu-id="daeeb-106">Most databases use a version of three-valued logic to handle null comparisons.</span></span> <span data-ttu-id="daeeb-107">也就是針對 null 值的比較不會評估`true`或是`false`，其評估結果為`unknown`。</span><span class="sxs-lookup"><span data-stu-id="daeeb-107">That is, a comparison against a null value does not evaluate to `true` or `false`, it evaluates to `unknown`.</span></span> <span data-ttu-id="daeeb-108">通常，這是 ANSI NULLS 的實作，可是實際情況不一定如此。</span><span class="sxs-lookup"><span data-stu-id="daeeb-108">Often this is an implementation of ANSI nulls, but this is not always the case.</span></span>  
  
 <span data-ttu-id="daeeb-109">根據預設，SQL Server 中 null 等於 null 的比較會傳回 null 值。</span><span class="sxs-lookup"><span data-stu-id="daeeb-109">By default in SQL Server, the null-equals-null comparison returns a null value.</span></span> <span data-ttu-id="daeeb-110">在下列範例中，結果集會排除 `ShipDate` 為 null 的資料列，而 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 陳述式則會傳回 0 個資料列。</span><span class="sxs-lookup"><span data-stu-id="daeeb-110">In the following example, the rows where `ShipDate` is null are excluded from the result set, and the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] statement would return 0 rows.</span></span>  
  
```  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 <span data-ttu-id="daeeb-111">這與 CLR null 語意大不相同，其中 null 等於 null 的比較則是會傳回 true。</span><span class="sxs-lookup"><span data-stu-id="daeeb-111">This is very different from the CLR null semantics, where the null-equals-null comparison returns true.</span></span>  
  
 <span data-ttu-id="daeeb-112">下列 LINQ 查詢是以 CLR 表示，但卻在資料來源中執行。</span><span class="sxs-lookup"><span data-stu-id="daeeb-112">The following LINQ query is expressed in the CLR, but it is executed in the data source.</span></span> <span data-ttu-id="daeeb-113">因為無法保證 CLR 語意在資料來源能被接受，預期的行為是不確定的。</span><span class="sxs-lookup"><span data-stu-id="daeeb-113">Because there is no guarantee that CLR semantics will be honored at the data source, the expected behavior is indeterminate.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a><span data-ttu-id="daeeb-114">索引鍵選擇器</span><span class="sxs-lookup"><span data-stu-id="daeeb-114">Key Selectors</span></span>  
 <span data-ttu-id="daeeb-115">A*索引鍵選取器*是用於標準查詢運算子，以從項目擷取索引鍵的函式。</span><span class="sxs-lookup"><span data-stu-id="daeeb-115">A *key selector* is a function used in the standard query operators to extract a key from an element.</span></span> <span data-ttu-id="daeeb-116">在索引鍵選擇器函式中，可以將運算式與常數進行比較。</span><span class="sxs-lookup"><span data-stu-id="daeeb-116">In the key selector function, an expression can be compared with a constant.</span></span> <span data-ttu-id="daeeb-117">如果比較運算式與 null 常數，或比較兩個 null 常數，則會顯示 CLR null 語意。</span><span class="sxs-lookup"><span data-stu-id="daeeb-117">CLR null semantics are exhibited if an expression is compared to a null constant or if two null constants are compared.</span></span> <span data-ttu-id="daeeb-118">如果比較資料來源中兩個具有 null 值的資料行，則會顯示存放區 null 語意。</span><span class="sxs-lookup"><span data-stu-id="daeeb-118">Store null semantics are exhibited if two columns with null values in the data source are compared.</span></span> <span data-ttu-id="daeeb-119">索引鍵選擇器存在於許多群組和排序的標準查詢運算子 (如 <xref:System.Linq.Queryable.GroupBy%2A>)，而且是用來選取做為排序或群組依據的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="daeeb-119">Key selectors are found in many of the grouping and ordering standard query operators, such as <xref:System.Linq.Queryable.GroupBy%2A>, and are used to select keys by which to order or group the query results.</span></span>  
  
## <a name="null-property-on-a-null-object"></a><span data-ttu-id="daeeb-120">Null 物件上的 Null 屬性</span><span class="sxs-lookup"><span data-stu-id="daeeb-120">Null Property on a Null Object</span></span>  
 <span data-ttu-id="daeeb-121">在 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 中，null 物件的屬性是 null。</span><span class="sxs-lookup"><span data-stu-id="daeeb-121">In the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], the properties of a null object are null.</span></span> <span data-ttu-id="daeeb-122">當您嘗試參考 CLR 中 null 物件的屬性時，將會收到 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="daeeb-122">When you attempt to reference a property of a null object in the CLR, you will receive a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="daeeb-123">當 LINQ 查詢包含 null 物件的屬性時，可能會產生不一致的行為。</span><span class="sxs-lookup"><span data-stu-id="daeeb-123">When a LINQ query involves a property of a null object, this can result in inconsistent behavior.</span></span>  
  
 <span data-ttu-id="daeeb-124">舉例來說，下列查詢中 `NewProduct` 的轉型會在命令樹層完成，這可能導致 `Introduced` 屬性為 null。</span><span class="sxs-lookup"><span data-stu-id="daeeb-124">For example, in the following query, the cast to `NewProduct` is done in the command tree layer, which might result in the `Introduced` property being null.</span></span> <span data-ttu-id="daeeb-125">如果資料庫已定義 null 比較而使 <xref:System.DateTime> 的比較評估為 true，則會包含資料列。</span><span class="sxs-lookup"><span data-stu-id="daeeb-125">If the database defined null comparisons such that the <xref:System.DateTime> comparison evaluates to true, the row will be included.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a><span data-ttu-id="daeeb-126">將 Null 集合傳遞至彙總函式</span><span class="sxs-lookup"><span data-stu-id="daeeb-126">Passing Null Collections to Aggregate Functions</span></span>  
 <span data-ttu-id="daeeb-127">在  [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]，當您傳遞一組支援`IQueryable`彙總函式，在資料庫上執行彙總的作業。</span><span class="sxs-lookup"><span data-stu-id="daeeb-127">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], when you pass a collection that supports `IQueryable` to an aggregate function, aggregate operations are performed at the database.</span></span> <span data-ttu-id="daeeb-128">可能的記憶體中執行的查詢以及在資料庫中執行的查詢結果中的差異。</span><span class="sxs-lookup"><span data-stu-id="daeeb-128">There might be differences in the results of a query that was performed in-memory and a query that was performed at the database.</span></span> <span data-ttu-id="daeeb-129">使用記憶體中查詢，如果沒有相符的項目，查詢會傳回零。</span><span class="sxs-lookup"><span data-stu-id="daeeb-129">With an in-memory query, if there are no matches, the query returns zero.</span></span> <span data-ttu-id="daeeb-130">同樣的查詢在資料庫中則會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="daeeb-130">At the database, the same query returns `null`.</span></span> <span data-ttu-id="daeeb-131">如果`null`值會傳遞至 LINQ 彙總函式，將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="daeeb-131">If a `null` value is passed to a LINQ aggregate function, an exception will be thrown.</span></span> <span data-ttu-id="daeeb-132">若要接受可能`null`值，轉換的類型和類型接收查詢結果為 null 類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="daeeb-132">To accept possible `null` values, cast the types and the properties of the types that receive query results to nullable types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daeeb-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="daeeb-133">See also</span></span>

- [<span data-ttu-id="daeeb-134">LINQ to Entities 查詢中的運算式</span><span class="sxs-lookup"><span data-stu-id="daeeb-134">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
