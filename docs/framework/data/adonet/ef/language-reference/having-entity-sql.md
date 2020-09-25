---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: a117f377b3f03b6a1a12e39426a24f3141aa40ff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204459"
---
# <a name="having-entity-sql"></a><span data-ttu-id="9a561-102">HAVING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9a561-102">HAVING (Entity SQL)</span></span>

<span data-ttu-id="9a561-103">指定群組或彙總的搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="9a561-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a561-104">語法</span><span class="sxs-lookup"><span data-stu-id="9a561-104">Syntax</span></span>  
  
```sql  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a561-105">引數</span><span class="sxs-lookup"><span data-stu-id="9a561-105">Arguments</span></span>  

 `search_condition`  
 <span data-ttu-id="9a561-106">指定群組或彙總要符合的搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="9a561-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="9a561-107">搭配 GROUP BY ALL 使用 HAVING 時，HAVING 子句會覆寫 ALL。</span><span class="sxs-lookup"><span data-stu-id="9a561-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a561-108">備註</span><span class="sxs-lookup"><span data-stu-id="9a561-108">Remarks</span></span>  

 <span data-ttu-id="9a561-109">HAVING 子句是用來在群組的結果上指定額外篩選條件。</span><span class="sxs-lookup"><span data-stu-id="9a561-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="9a561-110">如果查詢運算式中未指定 GROUP BY 子句，便會假設為一組隱含的單一群組。</span><span class="sxs-lookup"><span data-stu-id="9a561-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a561-111">HAVING 只能搭配 [SELECT](select-entity-sql.md) 語句使用。</span><span class="sxs-lookup"><span data-stu-id="9a561-111">HAVING can be used only with the [SELECT](select-entity-sql.md) statement.</span></span> <span data-ttu-id="9a561-112">未使用 [GROUP BY](group-by-entity-sql.md) 時，其行為就像 WHERE 子句一樣。</span><span class="sxs-lookup"><span data-stu-id="9a561-112">When [GROUP BY](group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
<span data-ttu-id="9a561-113">HAVING 子句的運作方式很類似 WHERE 字句，唯一不同的是它必須套用在 GROUP BY 運算後面。</span><span class="sxs-lookup"><span data-stu-id="9a561-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="9a561-114">這表示 HAVING 子句只能進行對群組別名和匯總的參考，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9a561-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example:</span></span>
  
```sql  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="9a561-115">前面的範例會將群組限制為包含一件產品以上的項目。</span><span class="sxs-lookup"><span data-stu-id="9a561-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a561-116">範例</span><span class="sxs-lookup"><span data-stu-id="9a561-116">Example</span></span>  

 <span data-ttu-id="9a561-117">以下 Entity SQL 查詢使用 HAVING 和 GROUP BY 運算子指定群組或彙總的搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="9a561-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="9a561-118">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="9a561-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9a561-119">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="9a561-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9a561-120">依照 how [to：執行傳回 PrimitiveType 結果的查詢](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的程式操作。</span><span class="sxs-lookup"><span data-stu-id="9a561-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="9a561-121">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="9a561-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#HAVING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#having)]  
  
## <a name="see-also"></a><span data-ttu-id="9a561-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a561-122">See also</span></span>

- [<span data-ttu-id="9a561-123">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="9a561-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="9a561-124">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="9a561-124">Query Expressions</span></span>](query-expressions-entity-sql.md)
