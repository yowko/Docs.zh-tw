---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 05e687f951930d92797a863410181585278b067d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330658"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="f623b-102">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f623b-102">REF (Entity SQL)</span></span>
<span data-ttu-id="f623b-103">傳回實體執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="f623b-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f623b-104">語法</span><span class="sxs-lookup"><span data-stu-id="f623b-104">Syntax</span></span>  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="f623b-105">引數</span><span class="sxs-lookup"><span data-stu-id="f623b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f623b-106">可產生實體類型之執行個體的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="f623b-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f623b-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f623b-107">Return Value</span></span>  
 <span data-ttu-id="f623b-108">指定之實體執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="f623b-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f623b-109">備註</span><span class="sxs-lookup"><span data-stu-id="f623b-109">Remarks</span></span>  
 <span data-ttu-id="f623b-110">實體參考由實體索引鍵和實體集名稱所組成。</span><span class="sxs-lookup"><span data-stu-id="f623b-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="f623b-111">因為不同實體集可視相同實體類型而定，特定實體索引鍵可出現於多個實體集，</span><span class="sxs-lookup"><span data-stu-id="f623b-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="f623b-112">但實體參考一定是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f623b-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="f623b-113">如果輸入運算式表示持續性實體，會傳回這個實體的參考。</span><span class="sxs-lookup"><span data-stu-id="f623b-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="f623b-114">如果輸入運算式不是持續性實體，會傳回 null 參考。</span><span class="sxs-lookup"><span data-stu-id="f623b-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="f623b-115">如果屬性引出運算子 (.) 是用於存取實體的屬性，則會為參考自動取值 (Dereference)。</span><span class="sxs-lookup"><span data-stu-id="f623b-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f623b-116">範例</span><span class="sxs-lookup"><span data-stu-id="f623b-116">Example</span></span>  
 <span data-ttu-id="f623b-117">下列 Entity SQL 查詢會使用 REF 運算子，傳回輸入實體引數的參考。</span><span class="sxs-lookup"><span data-stu-id="f623b-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="f623b-118">相同查詢會為參考取值，因為我們使用屬性引出運算子 (.) 存取 Product 實體的屬性。</span><span class="sxs-lookup"><span data-stu-id="f623b-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="f623b-119">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="f623b-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f623b-120">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="f623b-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f623b-121">請依照下列中的程序[How to:執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="f623b-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="f623b-122">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="f623b-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="f623b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f623b-123">See also</span></span>

- [<span data-ttu-id="f623b-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="f623b-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
- [<span data-ttu-id="f623b-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="f623b-125">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [<span data-ttu-id="f623b-126">KEY</span><span class="sxs-lookup"><span data-stu-id="f623b-126">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [<span data-ttu-id="f623b-127">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="f623b-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="f623b-128">類型定義</span><span class="sxs-lookup"><span data-stu-id="f623b-128">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
