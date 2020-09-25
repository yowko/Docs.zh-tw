---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 11abebeac682fed9e3a007986bb2f5c7bdb80f16
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204472"
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="dceb2-102">GROUPPARTITION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dceb2-102">GROUPPARTITION (Entity SQL)</span></span>

<span data-ttu-id="dceb2-103">傳回引數值的集合，該集合會將目前的群組分割投影至其相關的彙總。</span><span class="sxs-lookup"><span data-stu-id="dceb2-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="dceb2-104">`GroupPartition` 彙總是以群組為基礎的彙總，不具有以集合為基礎的形式。</span><span class="sxs-lookup"><span data-stu-id="dceb2-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dceb2-105">語法</span><span class="sxs-lookup"><span data-stu-id="dceb2-105">Syntax</span></span>  
  
```sql  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="dceb2-106">引數</span><span class="sxs-lookup"><span data-stu-id="dceb2-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="dceb2-107">任何 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算式。</span><span class="sxs-lookup"><span data-stu-id="dceb2-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dceb2-108">備註</span><span class="sxs-lookup"><span data-stu-id="dceb2-108">Remarks</span></span>  

 <span data-ttu-id="dceb2-109">下列查詢會產生產品清單，以及每項產品的訂單產品線數量集合：</span><span class="sxs-lookup"><span data-stu-id="dceb2-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="dceb2-110">以下兩個查詢的語意相同：</span><span class="sxs-lookup"><span data-stu-id="dceb2-110">The following two queries are semantically equal:</span></span>  
  
```sql  
SELECT p, Sum(GroupPartition(ol.Quantity)) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
SELET p, Sum(ol.Quantity) FROM LOB.OrderLines AS ol
  group by ol.Product as p  
```  
  
 <span data-ttu-id="dceb2-111">`GROUPPARTITION` 運算子可以搭配使用者定義的彙總函式使用。</span><span class="sxs-lookup"><span data-stu-id="dceb2-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
<span data-ttu-id="dceb2-112">`GROUPPARTITION` 是特殊的彙總運算子，可保留群組輸入集的參考。</span><span class="sxs-lookup"><span data-stu-id="dceb2-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="dceb2-113">若 GROUP BY 在範圍內，即可在查詢中任何位置使用此參考。</span><span class="sxs-lookup"><span data-stu-id="dceb2-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="dceb2-114">例如：</span><span class="sxs-lookup"><span data-stu-id="dceb2-114">For example:</span></span>
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="dceb2-115">一般情況 `GROUP BY` 下，會隱藏群組的結果。</span><span class="sxs-lookup"><span data-stu-id="dceb2-115">With a regular `GROUP BY`, the results of the grouping are hidden.</span></span> <span data-ttu-id="dceb2-116">您只能在彙總函式中使用結果。</span><span class="sxs-lookup"><span data-stu-id="dceb2-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="dceb2-117">若要查看群組的結果，您必須使用子查詢，讓群組和輸入集互相關聯。</span><span class="sxs-lookup"><span data-stu-id="dceb2-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="dceb2-118">下列兩個查詢的用法相同：</span><span class="sxs-lookup"><span data-stu-id="dceb2-118">The following two queries are equivalent:</span></span>  
  
```sql  
SELET p, (SELECT q FROM GroupPartition(ol.Quantity) AS q) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
SELECT p, (SELECT ol.Quantity AS q FROM LOB.OrderLines AS ol2 WHERE ol2.Product = p) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="dceb2-119">如範例所示，GROUPPARTITION 彙總運算子可讓您更容易在群組之後參考輸入集。</span><span class="sxs-lookup"><span data-stu-id="dceb2-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="dceb2-120">當您使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 參數時，GROUPPARTITION 運算子可以指定運算子輸入中的任何 `expression` 運算式。</span><span class="sxs-lookup"><span data-stu-id="dceb2-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="dceb2-121">下列針對群組分割的所有輸入運算式在執行個體中皆有效：</span><span class="sxs-lookup"><span data-stu-id="dceb2-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```sql  
SELECT groupkey, GroupPartition(b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(1) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(a + b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition({a + b}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition({42}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition(b > a) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="dceb2-122">範例</span><span class="sxs-lookup"><span data-stu-id="dceb2-122">Example</span></span>  

 <span data-ttu-id="dceb2-123">下列範例示範如何使用 GROUPPARTITION 子句搭配 GROUP BY 子句。</span><span class="sxs-lookup"><span data-stu-id="dceb2-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="dceb2-124">GROUP BY 子句會依 `SalesOrderHeader` 將 `Contact`實體進行分組。</span><span class="sxs-lookup"><span data-stu-id="dceb2-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="dceb2-125">GROUPPARTITION 子句接著會投影每個群組的 `TotalDue` 屬性，以產生十進位集合。</span><span class="sxs-lookup"><span data-stu-id="dceb2-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#Collection_GroupPartition](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#collection_grouppartition)]
