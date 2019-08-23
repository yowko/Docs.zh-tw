---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 76a63140668fb1f41cf9e6f901d9a43240a1d098
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936075"
---
# <a name="having-entity-sql"></a><span data-ttu-id="eec62-102">HAVING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="eec62-102">HAVING (Entity SQL)</span></span>
<span data-ttu-id="eec62-103">指定群組或彙總的搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="eec62-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eec62-104">語法</span><span class="sxs-lookup"><span data-stu-id="eec62-104">Syntax</span></span>  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="eec62-105">引數</span><span class="sxs-lookup"><span data-stu-id="eec62-105">Arguments</span></span>  
 `search_condition`  
 <span data-ttu-id="eec62-106">指定群組或彙總要符合的搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="eec62-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="eec62-107">搭配 GROUP BY ALL 使用 HAVING 時，HAVING 子句會覆寫 ALL。</span><span class="sxs-lookup"><span data-stu-id="eec62-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eec62-108">備註</span><span class="sxs-lookup"><span data-stu-id="eec62-108">Remarks</span></span>  
 <span data-ttu-id="eec62-109">HAVING 子句是用來在群組的結果上指定額外篩選條件。</span><span class="sxs-lookup"><span data-stu-id="eec62-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="eec62-110">如果查詢運算式中未指定 GROUP BY 子句，便會假設為一組隱含的單一群組。</span><span class="sxs-lookup"><span data-stu-id="eec62-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eec62-111">HAVING 只能搭配[SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)語句使用。</span><span class="sxs-lookup"><span data-stu-id="eec62-111">HAVING can be used only with the [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statement.</span></span> <span data-ttu-id="eec62-112">未使用[GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)時, HAVING 的行為就像是 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="eec62-112">When [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
 <span data-ttu-id="eec62-113">HAVING 子句的運作方式很類似 WHERE 字句，唯一不同的是它必須套用在 GROUP BY 運算後面。</span><span class="sxs-lookup"><span data-stu-id="eec62-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="eec62-114">這表示 HAVING 子句只能參考群組別名和彙總，如以下範例所述。</span><span class="sxs-lookup"><span data-stu-id="eec62-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example.</span></span>  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="eec62-115">前面的範例會將群組限制為包含一件產品以上的項目。</span><span class="sxs-lookup"><span data-stu-id="eec62-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eec62-116">範例</span><span class="sxs-lookup"><span data-stu-id="eec62-116">Example</span></span>  
 <span data-ttu-id="eec62-117">以下 Entity SQL 查詢使用 HAVING 和 GROUP BY 運算子指定群組或彙總的搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="eec62-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="eec62-118">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="eec62-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="eec62-119">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="eec62-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="eec62-120">[遵循 how to:執行可傳回 PrimitiveType 結果](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)的查詢。</span><span class="sxs-lookup"><span data-stu-id="eec62-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="eec62-121">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="eec62-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a><span data-ttu-id="eec62-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eec62-122">See also</span></span>

- [<span data-ttu-id="eec62-123">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="eec62-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="eec62-124">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="eec62-124">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
