---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: ad54450b8f987da9a7a502d6561a58794a24b207
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655175"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="a23fd-102">MULTISET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a23fd-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="a23fd-103">從值清單建立多重集的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a23fd-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="a23fd-104">MULTISET 建構函式 (Constructor) 中的所有值都必須是相容型別 `T`。</span><span class="sxs-lookup"><span data-stu-id="a23fd-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="a23fd-105">不允許空的多重集建構函式。</span><span class="sxs-lookup"><span data-stu-id="a23fd-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a23fd-106">語法</span><span class="sxs-lookup"><span data-stu-id="a23fd-106">Syntax</span></span>  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="a23fd-107">引數</span><span class="sxs-lookup"><span data-stu-id="a23fd-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a23fd-108">任何有效的值清單。</span><span class="sxs-lookup"><span data-stu-id="a23fd-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a23fd-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="a23fd-109">Return Value</span></span>  
 <span data-ttu-id="a23fd-110">集合的型別 MULTISET\<T >。</span><span class="sxs-lookup"><span data-stu-id="a23fd-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a23fd-111">備註</span><span class="sxs-lookup"><span data-stu-id="a23fd-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="a23fd-112">提供三種建構函式：資料列建構函式、物件建構函式和多重集 (或集合) 建構函式。</span><span class="sxs-lookup"><span data-stu-id="a23fd-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="a23fd-113">如需詳細資訊，請參閱 <<c0> [ 建構類型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="a23fd-113">For more information, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="a23fd-114">多重集建構函式會從值清單建立多重集的例項。</span><span class="sxs-lookup"><span data-stu-id="a23fd-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="a23fd-115">該建構函式中的所有值都必須是相容型別。</span><span class="sxs-lookup"><span data-stu-id="a23fd-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="a23fd-116">例如，下列運算式會建立整數的多重集。</span><span class="sxs-lookup"><span data-stu-id="a23fd-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  <span data-ttu-id="a23fd-117">包裝多重集有單一多重集項目; 時，才支援巢狀多重集常值比方說， `{{1, 2, 3}}`。</span><span class="sxs-lookup"><span data-stu-id="a23fd-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="a23fd-118">在包裝多重集有多個多重集項目 (例如 `{{1, 2}, {3, 4}}`) 的情況下，並不支援巢狀多重集常值。</span><span class="sxs-lookup"><span data-stu-id="a23fd-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a23fd-119">範例</span><span class="sxs-lookup"><span data-stu-id="a23fd-119">Example</span></span>  
 <span data-ttu-id="a23fd-120">下列 Entity SQL 查詢會使用 MULTISET 運算子，從值清單建立多重集的例項。</span><span class="sxs-lookup"><span data-stu-id="a23fd-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="a23fd-121">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="a23fd-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a23fd-122">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="a23fd-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a23fd-123">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="a23fd-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="a23fd-124">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="a23fd-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="a23fd-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a23fd-125">See also</span></span>
- [<span data-ttu-id="a23fd-126">建構類型</span><span class="sxs-lookup"><span data-stu-id="a23fd-126">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="a23fd-127">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="a23fd-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
