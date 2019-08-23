---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: eb676feeb168e1fb184f3869a18e138bff34211b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929348"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="bc1a9-102">MULTISET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bc1a9-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="bc1a9-103">從值清單建立多重集的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="bc1a9-104">MULTISET 建構函式 (Constructor) 中的所有值都必須是相容型別 `T`。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="bc1a9-105">不允許空的多重集建構函式。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc1a9-106">語法</span><span class="sxs-lookup"><span data-stu-id="bc1a9-106">Syntax</span></span>  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="bc1a9-107">引數</span><span class="sxs-lookup"><span data-stu-id="bc1a9-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="bc1a9-108">任何有效的值清單。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc1a9-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="bc1a9-109">Return Value</span></span>  
 <span data-ttu-id="bc1a9-110">型別多重\<集 T > 的集合。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc1a9-111">備註</span><span class="sxs-lookup"><span data-stu-id="bc1a9-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="bc1a9-112">提供三種建構函式：資料列建構函式、物件建構函式和多重集 (或集合) 建構函式。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="bc1a9-113">如需詳細資訊, 請參閱[建立類型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-113">For more information, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="bc1a9-114">多重集建構函式會從值清單建立多重集的例項。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="bc1a9-115">該建構函式中的所有值都必須是相容型別。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="bc1a9-116">例如，下列運算式會建立整數的多重集。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> <span data-ttu-id="bc1a9-117">只有在包裝多重集具有單一多重集元素時, 才支援嵌套的多重集常值。例如, `{{1, 2, 3}}`。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="bc1a9-118">在包裝多重集有多個多重集項目 (例如 `{{1, 2}, {3, 4}}`) 的情況下，並不支援巢狀多重集常值。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc1a9-119">範例</span><span class="sxs-lookup"><span data-stu-id="bc1a9-119">Example</span></span>  
 <span data-ttu-id="bc1a9-120">下列 Entity SQL 查詢會使用 MULTISET 運算子，從值清單建立多重集的例項。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="bc1a9-121">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bc1a9-122">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="bc1a9-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bc1a9-123">[遵循 how to:執行可傳回 StructuralType 結果](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bc1a9-124">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="bc1a9-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="bc1a9-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc1a9-125">See also</span></span>

- [<span data-ttu-id="bc1a9-126">建構類型</span><span class="sxs-lookup"><span data-stu-id="bc1a9-126">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="bc1a9-127">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="bc1a9-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
