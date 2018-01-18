---
title: "彙總函式 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1ed9a7532269a149f6f522e8fe9c6161e1aae27
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="aggregate-functions-entity-sql"></a><span data-ttu-id="7ef9e-102">彙總函式 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7ef9e-102">Aggregate Functions (Entity SQL)</span></span>
<span data-ttu-id="7ef9e-103">彙總是語言建構，可將集合壓縮至純量，做為群組作業的一部份。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-103">An aggregate is a language construct that condenses a collection into a scalar as a part of a group operation.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7ef9e-104"> 彙總以兩種形式出現：</span><span class="sxs-lookup"><span data-stu-id="7ef9e-104"> aggregates come in two forms:</span></span>  
  
-   [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7ef9e-105">集合函式可能會在運算式中任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-105"> collection functions that may be used anywhere in an expression.</span></span> <span data-ttu-id="7ef9e-106">包括於投影和述詞中 (在集合上作用) 使用彙總函式。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-106">This includes using aggregate functions in projections and predicates that act on collections.</span></span> <span data-ttu-id="7ef9e-107">集合函式是在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中指定彙總的慣用模式。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-107">Collection functions are the preferred mode of specifying aggregates in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
-   <span data-ttu-id="7ef9e-108">查詢運算式中的群組彙總有 GROUP BY 子句。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-108">Group aggregates in query expressions that have a GROUP BY clause.</span></span> <span data-ttu-id="7ef9e-109">與 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 相同，群組彙總接受 DISTINCT 和 ALL 做為彙總輸入的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-109">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], group aggregates accept DISTINCT and ALL as modifiers to the aggregate input.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7ef9e-110">先嘗試將運算式解譯為集合函式，如果運算式位於 SELECT 運算式的內容中則會將它解譯為群組彙總。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-110"> first tries to interpret an expression as a collection function and if the expression is in the context of a SELECT expression it interprets it as a group aggregate.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7ef9e-111">定義特殊的彙總運算子，稱為[GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-111"> defines a special aggregate operator called [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span></span> <span data-ttu-id="7ef9e-112">這個運算子可讓您取得群組輸入集的參考。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-112">This operator enables you to get a reference to the grouped input set.</span></span> <span data-ttu-id="7ef9e-113">如此可允許更多進階的分組查詢，其中的 GROUP BY 子句結果可用於不是群組彙總或集合函式的地方。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-113">This allows more advanced grouping queries, where the results of the GROUP BY clause can be used in places other than group aggregate or collection functions.</span></span>  
  
## <a name="collection-functions"></a><span data-ttu-id="7ef9e-114">集合函式</span><span class="sxs-lookup"><span data-stu-id="7ef9e-114">Collection Functions</span></span>  
 <span data-ttu-id="7ef9e-115">集合函式會針對集合運作，並傳回一個純量值。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-115">Collection functions operate on collections and return a scalar value.</span></span> <span data-ttu-id="7ef9e-116">例如，如果 `orders` 是所有 `orders` 的集合，您就可以使用下列運算式，計算最早出貨日期：</span><span class="sxs-lookup"><span data-stu-id="7ef9e-116">For example, if `orders` is a collection of all `orders`, you can calculate the earliest ship date with the following expression:</span></span>  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a><span data-ttu-id="7ef9e-117">群組彙總</span><span class="sxs-lookup"><span data-stu-id="7ef9e-117">Group Aggregates</span></span>  
 <span data-ttu-id="7ef9e-118">群組彙總會計算 GROUP BY 子句所定義的群組結果。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-118">Group aggregates are calculated over a group result as defined by the GROUP BY clause.</span></span> <span data-ttu-id="7ef9e-119">GROUP BY 子句會將資料分割成數個群組。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-119">The GROUP BY clause partitions data  into groups.</span></span> <span data-ttu-id="7ef9e-120">系統會針對結果中的每個群組套用彙總函式，並使用每個群組中的項目做為彙總計算的輸入，計算個別彙總。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-120">For each group in the result, the aggregate function is applied and a separate aggregate is calculated by using the elements in each group as inputs to the aggregate calculation.</span></span> <span data-ttu-id="7ef9e-121">當 GROUP BY 子句用於 SELECT 運算式時，只有群組運算式名稱、彙總或常數運算式可以出現在投影、HAVING 或 ORDER BY 子句中。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-121">When a GROUP BY clause is used in a SELECT expression, only grouping expression names, aggregates, or constant expressions may be present in the projection, HAVING, or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="7ef9e-122">下列範例會計算針對每個產品訂購的平均數量。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-122">The following example calculates the average quantity ordered for each product.</span></span>  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 <span data-ttu-id="7ef9e-123">您可以在 SELECT 運算式中使用群組彙總，但不使用明確的 GROUP BY 子句。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-123">It is possible to have a group aggregate without an explicit GROUP BY clause in the SELECT expression.</span></span> <span data-ttu-id="7ef9e-124">所有項目都會被視為單一群組，這就相當於根據常數指定群組的情況。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-124">All elements will be treated as a single group, equivalent to the case of specifying a grouping based on a constant.</span></span>  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 <span data-ttu-id="7ef9e-125">GROUP BY 子句中使用的運算式會使用 WHERE 子句運算式中可見的相同名稱解析範圍，進行評估。</span><span class="sxs-lookup"><span data-stu-id="7ef9e-125">Expressions used in the GROUP BY clause are evaluated by using the same name-resolution scope that would be visible to the WHERE clause expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ef9e-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ef9e-126">See Also</span></span>  
 [<span data-ttu-id="7ef9e-127">函式</span><span class="sxs-lookup"><span data-stu-id="7ef9e-127">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
