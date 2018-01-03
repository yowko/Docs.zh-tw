---
title: "傳回或略過序列中的項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d588ad393d6077d5b6e5279a1212f69da9a7d64c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="5aa4d-102">傳回或略過序列中的項目</span><span class="sxs-lookup"><span data-stu-id="5aa4d-102">Return Or Skip Elements in a Sequence</span></span>
<span data-ttu-id="5aa4d-103">使用 <xref:System.Linq.Queryable.Take%2A> 運算子傳回序列中指定數目的項目，然後略過其餘的項目。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-103">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="5aa4d-104">使用 <xref:System.Linq.Queryable.Skip%2A> 運算子略過序列中指定數目的項目，然後傳回其餘的項目。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-104">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5aa4d-105"><xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 在用於對 SQL Server 2000 進行的查詢中時會有一些限制。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-105"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="5aa4d-106">如需詳細資訊，請參閱中的"Skip 和 Take 例外狀況在 SQL Server 2000"項目[疑難排解](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-106">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5aa4d-107">將轉譯<xref:System.Linq.Queryable.Skip%2A>藉由在子查詢中使用 SQL`NOT EXISTS`子句。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-107"> translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="5aa4d-108">這項轉譯具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="5aa4d-108">This translation has the following limitations:</span></span>  
  
-   <span data-ttu-id="5aa4d-109">引數必須為集合。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-109">The argument must be a set.</span></span> <span data-ttu-id="5aa4d-110">即使多重集 (Multiset) 已排序，仍不支援多重集。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-110">Multisets are not supported, even if ordered.</span></span>  
  
-   <span data-ttu-id="5aa4d-111">產生的查詢可能會比已套用 <xref:System.Linq.Queryable.Skip%2A> 之基底查詢所產生的查詢更為複雜。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-111">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="5aa4d-112">這種複雜性會導致效能降低甚或逾時。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-112">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aa4d-113">範例</span><span class="sxs-lookup"><span data-stu-id="5aa4d-113">Example</span></span>  
 <span data-ttu-id="5aa4d-114">下列範例會使用 `Take` 來選取前五名雇用的 `Employees`。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-114">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="5aa4d-115">請注意，此集合會先按照 `HireDate` 排序。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-115">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="5aa4d-116">範例</span><span class="sxs-lookup"><span data-stu-id="5aa4d-116">Example</span></span>  
 <span data-ttu-id="5aa4d-117">下列範例會使用 <xref:System.Linq.Queryable.Skip%2A> 來選取除了 10 項最貴 `Products` 以外的所有產品。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-117">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="5aa4d-118">範例</span><span class="sxs-lookup"><span data-stu-id="5aa4d-118">Example</span></span>  
 <span data-ttu-id="5aa4d-119">下列範例會結合 <xref:System.Linq.Queryable.Skip%2A> 和 <xref:System.Linq.Queryable.Take%2A> 方法略過前 50 筆記錄，然後傳回接下來的 10 筆記錄。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-119">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="5aa4d-120"><xref:System.Linq.Queryable.Take%2A> 和 <xref:System.Linq.Queryable.Skip%2A> 作業僅針對已排序的集合加以妥善定義。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-120"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="5aa4d-121">並未定義未排序集合或多重集 (Multiset) 的語意 (Semantics)。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-121">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="5aa4d-122">由於在 SQL 中排序的限制，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會嘗試將 <xref:System.Linq.Queryable.Take%2A> 或 <xref:System.Linq.Queryable.Skip%2A> 運算子的引數排序移至運算子的結果。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-122">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5aa4d-123">[!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] 和 [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)] 的轉譯有所不同。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-123">Translation is different for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] and [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span></span> <span data-ttu-id="5aa4d-124">如果您打算使用 <xref:System.Linq.Queryable.Skip%2A> 搭配任何複雜度的查詢，請使用 [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-124">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span></span>  
  
 <span data-ttu-id="5aa4d-125">請考量下列 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] 查詢：</span><span class="sxs-lookup"><span data-stu-id="5aa4d-125">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5aa4d-126"> 會將排序移至 SQL 程式碼的結尾，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5aa4d-126"> moves the ordering to the end in the SQL code, as follows:</span></span>  
  
```  
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 <span data-ttu-id="5aa4d-127">當 <xref:System.Linq.Queryable.Take%2A> 和 <xref:System.Linq.Queryable.Skip%2A> 鏈結在一起時，所有指定的排序都必須一致。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-127">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="5aa4d-128">否則，會有未定義的結果。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-128">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="5aa4d-129">至於以 SQL 規格為基礎的非負數、常數整數引數，<xref:System.Linq.Queryable.Take%2A> 和 <xref:System.Linq.Queryable.Skip%2A> 都已定義妥善。</span><span class="sxs-lookup"><span data-stu-id="5aa4d-129">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aa4d-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="5aa4d-130">See Also</span></span>  
 [<span data-ttu-id="5aa4d-131">查詢範例</span><span class="sxs-lookup"><span data-stu-id="5aa4d-131">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="5aa4d-132">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="5aa4d-132">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
