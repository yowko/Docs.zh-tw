---
title: "分頁 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6398edb34a2389b113970444d98eec33f4833b93
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="paging-entity-sql"></a><span data-ttu-id="861f3-102">分頁 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="861f3-102">Paging (Entity SQL)</span></span>
<span data-ttu-id="861f3-103">可以透過執行實際分頁[略過](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)和[限制](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)中的子子句[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)子句。</span><span class="sxs-lookup"><span data-stu-id="861f3-103">Physical paging can be performed by using the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="861f3-104">若要以決定性的方式執行實體分頁，您應該要使用 SKIP 和 LIMIT。</span><span class="sxs-lookup"><span data-stu-id="861f3-104">To perform physical paging deterministically, you should use SKIP and LIMIT.</span></span> <span data-ttu-id="861f3-105">如果您只想要限制非決定性的方式在結果中的資料列數目，您應該使用[頂端](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="861f3-105">If you only want to restrict the number of rows in the result in a non-determinsitic way, you should use [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span></span> <span data-ttu-id="861f3-106">TOP 和 SKIP/LIMIT 互斥。</span><span class="sxs-lookup"><span data-stu-id="861f3-106">TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="top-overview"></a><span data-ttu-id="861f3-107">TOP 概觀</span><span class="sxs-lookup"><span data-stu-id="861f3-107">TOP Overview</span></span>  
 <span data-ttu-id="861f3-108">SELECT 子句在選擇性 ALL/DISTINCT 修飾詞之後可以有選擇性 TOP 子項子句。</span><span class="sxs-lookup"><span data-stu-id="861f3-108">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="861f3-109">TOP 子項子句指定只會從查詢結果傳回第一組資料列。</span><span class="sxs-lookup"><span data-stu-id="861f3-109">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span> <span data-ttu-id="861f3-110">如需詳細資訊，請參閱[頂端](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="861f3-110">For more information, see [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span></span>  
  
## <a name="skip-and-limit-overview"></a><span data-ttu-id="861f3-111">SKIP 和 LIMIT 概觀</span><span class="sxs-lookup"><span data-stu-id="861f3-111">SKIP And LIMIT Overview</span></span>  
 <span data-ttu-id="861f3-112">SKIP 和 LIMIT 是 ORDER BY 子句的一部分。</span><span class="sxs-lookup"><span data-stu-id="861f3-112">SKIP and LIMIT are part of the ORDER BY clause.</span></span> <span data-ttu-id="861f3-113">如果 ORDER BY 子句中有 SKIP 運算式子項子句存在，將會根據排序的指定來排序結果，而且結果集將包含緊接在 SKIP 運算式之後的下一個資料列開始的資料列。</span><span class="sxs-lookup"><span data-stu-id="861f3-113">If a SKIP expression sub-clause is present in a ORDER BY clause, the results will be sorted according to the sort specification and the result set will include row(s) starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="861f3-114">例如，SKIP 5 將會略過前五個資料列，並且傳回從第六個資料列以後的資料列。</span><span class="sxs-lookup"><span data-stu-id="861f3-114">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span> <span data-ttu-id="861f3-115">如果 ORDER BY 子句中有 LIMIT 運算式次子句，此查詢將會依據排序規格排序，而且所產生的資料列數目將會受到 LIMIT 運算式的限制。</span><span class="sxs-lookup"><span data-stu-id="861f3-115">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="861f3-116">舉例來說，LIMIT 5 會將結果集限制為五個執行個體或資料列。</span><span class="sxs-lookup"><span data-stu-id="861f3-116">For instance, LIMIT 5 will restrict the result set to five instances or rows.</span></span> <span data-ttu-id="861f3-117">SKIP 和 LIMIT 不必一起使用，您可以搭配 ORDER BY 子句來單獨使用 SKIP 或 LIMIT。</span><span class="sxs-lookup"><span data-stu-id="861f3-117">SKIP and LIMIT do not have to be used together; you can use just SKIP or just LIMIT with ORDER BY clause.</span></span> <span data-ttu-id="861f3-118">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="861f3-118">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="861f3-119">SKIP</span><span class="sxs-lookup"><span data-stu-id="861f3-119">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [<span data-ttu-id="861f3-120">LIMIT</span><span class="sxs-lookup"><span data-stu-id="861f3-120">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [<span data-ttu-id="861f3-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="861f3-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="861f3-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="861f3-122">See Also</span></span>  
 [<span data-ttu-id="861f3-123">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="861f3-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="861f3-124">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="861f3-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="861f3-125">如何： 逐頁檢視查詢結果</span><span class="sxs-lookup"><span data-stu-id="861f3-125">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)
