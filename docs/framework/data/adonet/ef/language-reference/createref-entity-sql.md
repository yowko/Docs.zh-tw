---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: c2a57116f56abf4db3caabcfe3acd0d8afbcf4eb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201053"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="b6a48-102">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b6a48-102">CREATEREF (Entity SQL)</span></span>

<span data-ttu-id="b6a48-103">建立實體集中實體的參考。</span><span class="sxs-lookup"><span data-stu-id="b6a48-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6a48-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6a48-104">Syntax</span></span>  
  
```sql  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="b6a48-105">引數</span><span class="sxs-lookup"><span data-stu-id="b6a48-105">Arguments</span></span>  

 `entityset_identifier`  
 <span data-ttu-id="b6a48-106">實體集識別項，非字串常值。</span><span class="sxs-lookup"><span data-stu-id="b6a48-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="b6a48-107">對應到實體類型的索引鍵屬性的資料列型別運算式。</span><span class="sxs-lookup"><span data-stu-id="b6a48-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6a48-108">備註</span><span class="sxs-lookup"><span data-stu-id="b6a48-108">Remarks</span></span>  

 <span data-ttu-id="b6a48-109">`row_typed_expression` 在結構上必須相當於實體的索引鍵型別。</span><span class="sxs-lookup"><span data-stu-id="b6a48-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="b6a48-110">換言之，它必須擁有與實體索引鍵相同的欄位數目和型別，而且順序相同。</span><span class="sxs-lookup"><span data-stu-id="b6a48-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="b6a48-111">在下面的範例中，Orders 和 BadOrders 兩者都是 Order 型別的實體集，而 Id 則相當於 Order 的單一索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="b6a48-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="b6a48-112">此範例說明如何產生 BadOrders 中實體的產考。</span><span class="sxs-lookup"><span data-stu-id="b6a48-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="b6a48-113">請留意，此參考可能會懸空。</span><span class="sxs-lookup"><span data-stu-id="b6a48-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="b6a48-114">換言之，此參考可能無法實際識別特定的實體。</span><span class="sxs-lookup"><span data-stu-id="b6a48-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="b6a48-115">在這種情況下，對該參考的 `DEREF` 作業將會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="b6a48-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```sql  
SELECT CreateRef(LOB.BadOrders, row(o.Id))
FROM LOB.Orders AS o
```  
  
## <a name="example"></a><span data-ttu-id="b6a48-116">範例</span><span class="sxs-lookup"><span data-stu-id="b6a48-116">Example</span></span>  

 <span data-ttu-id="b6a48-117">下列 Entity SQL 查詢使用 CREATEREF 運算子來建立實體集中實體的參考。</span><span class="sxs-lookup"><span data-stu-id="b6a48-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="b6a48-118">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="b6a48-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b6a48-119">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="b6a48-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b6a48-120">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="b6a48-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b6a48-121">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="b6a48-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CREATEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="b6a48-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6a48-122">See also</span></span>

- [<span data-ttu-id="b6a48-123">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="b6a48-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="b6a48-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="b6a48-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="b6a48-125">KEY</span><span class="sxs-lookup"><span data-stu-id="b6a48-125">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="b6a48-126">裁判</span><span class="sxs-lookup"><span data-stu-id="b6a48-126">REF</span></span>](ref-entity-sql.md)
