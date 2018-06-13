---
title: KEY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: c35cac018392aa9688866e280ff64fdf6a1453f5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760553"
---
# <a name="key-entity-sql"></a><span data-ttu-id="f52b5-102">KEY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f52b5-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="f52b5-103">擷取參考的索引鍵，或實體運算式的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f52b5-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f52b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="f52b5-104">Syntax</span></span>  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="f52b5-105">備註</span><span class="sxs-lookup"><span data-stu-id="f52b5-105">Remarks</span></span>  
 <span data-ttu-id="f52b5-106">實體索引鍵會以指定之實體或實體參考的正確順序來包含索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="f52b5-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="f52b5-107">因為多個實體集可視相同類型而定，相同索引鍵可能出現於每個實體集。</span><span class="sxs-lookup"><span data-stu-id="f52b5-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="f52b5-108">若要取得唯一的參考，請使用 `REF`。</span><span class="sxs-lookup"><span data-stu-id="f52b5-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="f52b5-109">KEY 運算子的傳回類型是資料列類型，會以相同順序來為實體的每個索引鍵包含一個欄位。</span><span class="sxs-lookup"><span data-stu-id="f52b5-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="f52b5-110">在下列範例中，Key 運算子會傳遞 BadOrder 實體的參考，並傳回那個參考的索引鍵部分。</span><span class="sxs-lookup"><span data-stu-id="f52b5-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="f52b5-111">在上述情形中，單一個欄位的資料錄類型對應至 `Id` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f52b5-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="f52b5-112">範例</span><span class="sxs-lookup"><span data-stu-id="f52b5-112">Example</span></span>  
 <span data-ttu-id="f52b5-113">下列 Entity SQL 查詢會使用 KEY 運算子，擷取具有類型參考之運算式的索引鍵部分。</span><span class="sxs-lookup"><span data-stu-id="f52b5-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="f52b5-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="f52b5-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f52b5-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="f52b5-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f52b5-116">遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="f52b5-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="f52b5-117">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="f52b5-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a><span data-ttu-id="f52b5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f52b5-118">See Also</span></span>  
 [<span data-ttu-id="f52b5-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="f52b5-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="f52b5-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="f52b5-120">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="f52b5-121">REF</span><span class="sxs-lookup"><span data-stu-id="f52b5-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="f52b5-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="f52b5-122">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
