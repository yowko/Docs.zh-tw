---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: fb7f8040e9e310798b003ad02614cd464e996389
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="except-entity-sql"></a><span data-ttu-id="af501-102">EXCEPT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="af501-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="af501-103">從 EXCEPT 運算元左側的查詢運算式傳回任何相異值集合，這些相異值是 EXCEPT 運算元右側的查詢運算式沒有傳回的。</span><span class="sxs-lookup"><span data-stu-id="af501-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="af501-104">所有運算式都必須具有與 `expression`相同的型別或是共同基底型別或衍生型別。</span><span class="sxs-lookup"><span data-stu-id="af501-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af501-105">語法</span><span class="sxs-lookup"><span data-stu-id="af501-105">Syntax</span></span>  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="af501-106">引數</span><span class="sxs-lookup"><span data-stu-id="af501-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="af501-107">任何有效的查詢運算式，該運算式會傳回要與另一個查詢運算式傳回之集合相比較的集合。</span><span class="sxs-lookup"><span data-stu-id="af501-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af501-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="af501-108">Return Value</span></span>  
 <span data-ttu-id="af501-109">具有與 `expression`相同的型別或是共同基底類型或衍生型別的集合。</span><span class="sxs-lookup"><span data-stu-id="af501-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af501-110">備註</span><span class="sxs-lookup"><span data-stu-id="af501-110">Remarks</span></span>  
 <span data-ttu-id="af501-111">EXCEPT 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。</span><span class="sxs-lookup"><span data-stu-id="af501-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="af501-112">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="af501-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="af501-113">下表顯示 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子的優先順序。</span><span class="sxs-lookup"><span data-stu-id="af501-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="af501-114">優先順序</span><span class="sxs-lookup"><span data-stu-id="af501-114">Precedence</span></span>|<span data-ttu-id="af501-115">運算子</span><span class="sxs-lookup"><span data-stu-id="af501-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="af501-116">最高</span><span class="sxs-lookup"><span data-stu-id="af501-116">Highest</span></span>|<span data-ttu-id="af501-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="af501-117">INTERSECT</span></span>|  
||<span data-ttu-id="af501-118">UNION</span><span class="sxs-lookup"><span data-stu-id="af501-118">UNION</span></span><br /><br /> <span data-ttu-id="af501-119">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="af501-119">UNION ALL</span></span>|  
||<span data-ttu-id="af501-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="af501-120">EXCEPT</span></span>|  
|<span data-ttu-id="af501-121">最低</span><span class="sxs-lookup"><span data-stu-id="af501-121">Lowest</span></span>|<span data-ttu-id="af501-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="af501-122">EXISTS</span></span><br /><br /> <span data-ttu-id="af501-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="af501-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="af501-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="af501-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="af501-125">SET</span><span class="sxs-lookup"><span data-stu-id="af501-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="af501-126">範例</span><span class="sxs-lookup"><span data-stu-id="af501-126">Example</span></span>  
 <span data-ttu-id="af501-127">下列 Entity SQL 查詢會使用 EXCEPT 運算子，從兩個查詢運算式傳回任何相異值的集合。</span><span class="sxs-lookup"><span data-stu-id="af501-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="af501-128">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="af501-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="af501-129">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="af501-129">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="af501-130">遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="af501-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="af501-131">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="af501-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a><span data-ttu-id="af501-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af501-132">See Also</span></span>  
 [<span data-ttu-id="af501-133">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="af501-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
