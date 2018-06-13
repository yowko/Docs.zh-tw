---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: b844c5a132d36a4ca9d660607bbfe0f39ceab718
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759630"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="7e83f-102">LIMIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7e83f-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="7e83f-103">在 ORDER BY 子句中使用 LIMIT 次子句可以執行實際分頁。</span><span class="sxs-lookup"><span data-stu-id="7e83f-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="7e83f-104">LIMIT 不可單獨使用於 ORDER BY 子句之外。</span><span class="sxs-lookup"><span data-stu-id="7e83f-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e83f-105">語法</span><span class="sxs-lookup"><span data-stu-id="7e83f-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7e83f-106">引數</span><span class="sxs-lookup"><span data-stu-id="7e83f-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="7e83f-107">要選取的項目的數目。</span><span class="sxs-lookup"><span data-stu-id="7e83f-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="7e83f-108">如果 ORDER BY 子句中有 LIMIT 運算式次子句，此查詢將會依據排序規格排序，而且所產生的資料列數目將會受到 LIMIT 運算式的限制。</span><span class="sxs-lookup"><span data-stu-id="7e83f-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="7e83f-109">例如，LIMIT 5 會將結果集限制為 5 個執行個體或資料列。</span><span class="sxs-lookup"><span data-stu-id="7e83f-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="7e83f-110">LIMIT 在功能上就相當於 TOP，不同之處在於 LIMIT 必須配合 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="7e83f-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="7e83f-111">SKIP 和 LIMIT 可以各自配合 ORDER BY 子句使用。</span><span class="sxs-lookup"><span data-stu-id="7e83f-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e83f-112">如果 TOP 修飾詞和 SKIP 次子句出現在同一個查詢運算式中，Entity SQL 查詢會被視為無效。</span><span class="sxs-lookup"><span data-stu-id="7e83f-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="7e83f-113">請將 TOP 運算式變更為 LIMIT 運算式來重新撰寫此查詢。</span><span class="sxs-lookup"><span data-stu-id="7e83f-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e83f-114">範例</span><span class="sxs-lookup"><span data-stu-id="7e83f-114">Example</span></span>  
 <span data-ttu-id="7e83f-115">以下 Entity SQL 查詢使用 ORDER BY 運算子配合 LIMIT 來指定 SELECT 陳述式所傳回物件使用的排序順序。</span><span class="sxs-lookup"><span data-stu-id="7e83f-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="7e83f-116">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="7e83f-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7e83f-117">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="7e83f-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7e83f-118">遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="7e83f-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="7e83f-119">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="7e83f-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="7e83f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e83f-120">See Also</span></span>  
 [<span data-ttu-id="7e83f-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="7e83f-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="7e83f-122">如何： 逐頁檢視查詢結果</span><span class="sxs-lookup"><span data-stu-id="7e83f-122">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="7e83f-123">分頁</span><span class="sxs-lookup"><span data-stu-id="7e83f-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="7e83f-124">TOP</span><span class="sxs-lookup"><span data-stu-id="7e83f-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
