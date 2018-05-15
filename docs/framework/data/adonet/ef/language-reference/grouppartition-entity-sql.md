---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 9f0f917380e6422da753282216529580f87f1a1a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="33192-102">GROUPPARTITION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="33192-102">GROUPPARTITION (Entity SQL)</span></span>
<span data-ttu-id="33192-103">傳回引數值的集合，該集合會將目前的群組分割投影至其相關的彙總。</span><span class="sxs-lookup"><span data-stu-id="33192-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="33192-104">`GroupPartition` 彙總是以群組為基礎的彙總，不具有以集合為基礎的形式。</span><span class="sxs-lookup"><span data-stu-id="33192-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33192-105">語法</span><span class="sxs-lookup"><span data-stu-id="33192-105">Syntax</span></span>  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="33192-106">引數</span><span class="sxs-lookup"><span data-stu-id="33192-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="33192-107">任何 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算式。</span><span class="sxs-lookup"><span data-stu-id="33192-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33192-108">備註</span><span class="sxs-lookup"><span data-stu-id="33192-108">Remarks</span></span>  
 <span data-ttu-id="33192-109">下列查詢會產生產品清單，以及每項產品的訂單產品線數量集合：</span><span class="sxs-lookup"><span data-stu-id="33192-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="33192-110">以下兩個查詢的語意相同：</span><span class="sxs-lookup"><span data-stu-id="33192-110">The following two queries are semantically equal:</span></span>  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="33192-111">`GROUPPARTITION` 運算子可以搭配使用者定義的彙總函式使用。</span><span class="sxs-lookup"><span data-stu-id="33192-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
 <span data-ttu-id="33192-112">`GROUPPARTITION` 是特殊的彙總運算子，可保留群組輸入集的參考。</span><span class="sxs-lookup"><span data-stu-id="33192-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="33192-113">若 GROUP BY 在範圍內，即可在查詢中任何位置使用此參考。</span><span class="sxs-lookup"><span data-stu-id="33192-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="33192-114">例如：</span><span class="sxs-lookup"><span data-stu-id="33192-114">For example,</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="33192-115">搭配標準 GROUP BY，會隱藏群組的結果。</span><span class="sxs-lookup"><span data-stu-id="33192-115">With a regular GROUP BY, the results of the grouping are hidden.</span></span> <span data-ttu-id="33192-116">您只能在彙總函式中使用結果。</span><span class="sxs-lookup"><span data-stu-id="33192-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="33192-117">若要查看群組的結果，您必須使用子查詢，讓群組和輸入集互相關聯。</span><span class="sxs-lookup"><span data-stu-id="33192-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="33192-118">下列兩個查詢的用法相同：</span><span class="sxs-lookup"><span data-stu-id="33192-118">The following two queries are equivalent:</span></span>  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="33192-119">如範例所示，GROUPPARTITION 彙總運算子可讓您更容易在群組之後參考輸入集。</span><span class="sxs-lookup"><span data-stu-id="33192-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="33192-120">當您使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 參數時，GROUPPARTITION 運算子可以指定運算子輸入中的任何 `expression` 運算式。</span><span class="sxs-lookup"><span data-stu-id="33192-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="33192-121">下列針對群組分割的所有輸入運算式在執行個體中皆有效：</span><span class="sxs-lookup"><span data-stu-id="33192-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="33192-122">範例</span><span class="sxs-lookup"><span data-stu-id="33192-122">Example</span></span>  
 <span data-ttu-id="33192-123">下列範例示範如何使用 GROUPPARTITION 子句搭配 GROUP BY 子句。</span><span class="sxs-lookup"><span data-stu-id="33192-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="33192-124">GROUP BY 子句會依 `SalesOrderHeader` 將 `Contact`實體進行分組。</span><span class="sxs-lookup"><span data-stu-id="33192-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="33192-125">GROUPPARTITION 子句接著會投影每個群組的 `TotalDue` 屬性，以產生十進位集合。</span><span class="sxs-lookup"><span data-stu-id="33192-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
