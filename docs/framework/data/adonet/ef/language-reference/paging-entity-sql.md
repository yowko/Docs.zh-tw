---
title: 分頁 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 42f685e0b84109f3099b501b2a75e681af1ea1bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177471"
---
# <a name="paging-entity-sql"></a><span data-ttu-id="9dfaf-102">分頁 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9dfaf-102">Paging (Entity SQL)</span></span>

<span data-ttu-id="9dfaf-103">您可以在[ORDER by](order-by-entity-sql.md)子句中使用[SKIP](skip-entity-sql.md)和[LIMIT](limit-entity-sql.md)子子句來執行實體分頁。</span><span class="sxs-lookup"><span data-stu-id="9dfaf-103">Physical paging can be performed by using the [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses in the [ORDER BY](order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="9dfaf-104">若要以決定性的方式執行實體分頁，您應該要使用 SKIP 和 LIMIT。</span><span class="sxs-lookup"><span data-stu-id="9dfaf-104">To perform physical paging deterministically, you should use SKIP and LIMIT.</span></span> <span data-ttu-id="9dfaf-105">如果您只想要以不具決定性的方式限制結果中的資料列數目，您應該使用 [TOP](top-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="9dfaf-105">If you only want to restrict the number of rows in the result in a non-deterministic way, you should use [TOP](top-entity-sql.md).</span></span> <span data-ttu-id="9dfaf-106">TOP 和 SKIP/LIMIT 互斥。</span><span class="sxs-lookup"><span data-stu-id="9dfaf-106">TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="top-overview"></a><span data-ttu-id="9dfaf-107">TOP 概觀</span><span class="sxs-lookup"><span data-stu-id="9dfaf-107">TOP Overview</span></span>  

 <span data-ttu-id="9dfaf-108">SELECT 子句在選擇性 ALL/DISTINCT 修飾詞之後可以有選擇性 TOP 子項子句。</span><span class="sxs-lookup"><span data-stu-id="9dfaf-108">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="9dfaf-109">TOP 子項子句指定只會從查詢結果傳回第一組資料列。</span><span class="sxs-lookup"><span data-stu-id="9dfaf-109">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span> <span data-ttu-id="9dfaf-110">如需詳細資訊，請參閱 [頂端](top-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="9dfaf-110">For more information, see [TOP](top-entity-sql.md).</span></span>  
  
## <a name="skip-and-limit-overview"></a><span data-ttu-id="9dfaf-111">SKIP 和 LIMIT 概觀</span><span class="sxs-lookup"><span data-stu-id="9dfaf-111">SKIP And LIMIT Overview</span></span>  

 <span data-ttu-id="9dfaf-112">SKIP 和 LIMIT 是 ORDER BY 子句的一部分。</span><span class="sxs-lookup"><span data-stu-id="9dfaf-112">SKIP and LIMIT are part of the ORDER BY clause.</span></span> <span data-ttu-id="9dfaf-113">如果 ORDER BY 子句中有 SKIP 運算式子項子句存在，將會根據排序的指定來排序結果，而且結果集將包含緊接在 SKIP 運算式之後的下一個資料列開始的資料列。</span><span class="sxs-lookup"><span data-stu-id="9dfaf-113">If a SKIP expression sub-clause is present in a ORDER BY clause, the results will be sorted according to the sort specification and the result set will include row(s) starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="9dfaf-114">例如，SKIP 5 將會略過前五個資料列，並且傳回從第六個資料列以後的資料列。</span><span class="sxs-lookup"><span data-stu-id="9dfaf-114">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span> <span data-ttu-id="9dfaf-115">如果 ORDER BY 子句中有 LIMIT 運算式次子句，此查詢將會依據排序規格排序，而且所產生的資料列數目將會受到 LIMIT 運算式的限制。</span><span class="sxs-lookup"><span data-stu-id="9dfaf-115">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="9dfaf-116">舉例來說，LIMIT 5 會將結果集限制為五個執行個體或資料列。</span><span class="sxs-lookup"><span data-stu-id="9dfaf-116">For instance, LIMIT 5 will restrict the result set to five instances or rows.</span></span> <span data-ttu-id="9dfaf-117">SKIP 和 LIMIT 不必一起使用，您可以搭配 ORDER BY 子句來單獨使用 SKIP 或 LIMIT。</span><span class="sxs-lookup"><span data-stu-id="9dfaf-117">SKIP and LIMIT do not have to be used together; you can use just SKIP or just LIMIT with ORDER BY clause.</span></span> <span data-ttu-id="9dfaf-118">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="9dfaf-118">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="9dfaf-119">跳</span><span class="sxs-lookup"><span data-stu-id="9dfaf-119">SKIP</span></span>](skip-entity-sql.md)  
  
- [<span data-ttu-id="9dfaf-120">限制</span><span class="sxs-lookup"><span data-stu-id="9dfaf-120">LIMIT</span></span>](limit-entity-sql.md)  
  
- [<span data-ttu-id="9dfaf-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="9dfaf-121">ORDER BY</span></span>](order-by-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="9dfaf-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dfaf-122">See also</span></span>

- [<span data-ttu-id="9dfaf-123">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="9dfaf-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="9dfaf-124">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="9dfaf-124">Entity SQL Overview</span></span>](entity-sql-overview.md)
- <span data-ttu-id="9dfaf-125">[如何：逐頁檢視查詢結果](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9dfaf-125">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
