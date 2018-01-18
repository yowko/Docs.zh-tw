---
title: CREATEREF (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8de4266277be31fd51411d4b994f1b5de45f13df
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="createref-entity-sql"></a><span data-ttu-id="3d04c-102">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3d04c-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="3d04c-103">建立實體集中實體的參考。</span><span class="sxs-lookup"><span data-stu-id="3d04c-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d04c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3d04c-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="3d04c-105">引數</span><span class="sxs-lookup"><span data-stu-id="3d04c-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="3d04c-106">實體集識別項，非字串常值。</span><span class="sxs-lookup"><span data-stu-id="3d04c-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="3d04c-107">對應到實體類型的索引鍵屬性的資料列型別運算式。</span><span class="sxs-lookup"><span data-stu-id="3d04c-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d04c-108">備註</span><span class="sxs-lookup"><span data-stu-id="3d04c-108">Remarks</span></span>  
 <span data-ttu-id="3d04c-109">`row_typed_expression` 在結構上必須相當於實體的索引鍵型別。</span><span class="sxs-lookup"><span data-stu-id="3d04c-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="3d04c-110">換言之，它必須擁有與實體索引鍵相同的欄位數目和型別，而且順序相同。</span><span class="sxs-lookup"><span data-stu-id="3d04c-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="3d04c-111">在下面的範例中，Orders 和 BadOrders 兩者都是 Order 型別的實體集，而 Id 則相當於 Order 的單一索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="3d04c-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="3d04c-112">此範例說明如何產生 BadOrders 中實體的產考。</span><span class="sxs-lookup"><span data-stu-id="3d04c-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="3d04c-113">請留意，此參考可能會懸空。</span><span class="sxs-lookup"><span data-stu-id="3d04c-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="3d04c-114">換言之，此參考可能無法實際識別特定的實體。</span><span class="sxs-lookup"><span data-stu-id="3d04c-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="3d04c-115">在這種情況下，對該參考的 `DEREF` 作業將會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="3d04c-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="3d04c-116">範例</span><span class="sxs-lookup"><span data-stu-id="3d04c-116">Example</span></span>  
 <span data-ttu-id="3d04c-117">下列 Entity SQL 查詢使用 CREATEREF 運算子來建立實體集中實體的參考。</span><span class="sxs-lookup"><span data-stu-id="3d04c-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="3d04c-118">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="3d04c-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3d04c-119">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="3d04c-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3d04c-120">遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="3d04c-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="3d04c-121">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="3d04c-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="3d04c-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="3d04c-122">See Also</span></span>  
 [<span data-ttu-id="3d04c-123">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="3d04c-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="3d04c-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="3d04c-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="3d04c-125">KEY</span><span class="sxs-lookup"><span data-stu-id="3d04c-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="3d04c-126">REF</span><span class="sxs-lookup"><span data-stu-id="3d04c-126">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
