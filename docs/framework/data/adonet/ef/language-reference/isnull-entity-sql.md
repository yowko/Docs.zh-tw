---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 894d3ab91623aa4246bf7735fb1b7d04e066825a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072632"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="ea3f0-102">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ea3f0-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="ea3f0-103">判斷查詢運算式是否為 null。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea3f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea3f0-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="ea3f0-105">引數</span><span class="sxs-lookup"><span data-stu-id="ea3f0-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ea3f0-106">任何有效的查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-106">Any valid query expression.</span></span> <span data-ttu-id="ea3f0-107">不可為集合、不可有集合成員，也不可為集合型別屬性的記錄型別。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="ea3f0-108">NOT</span><span class="sxs-lookup"><span data-stu-id="ea3f0-108">NOT</span></span>  
 <span data-ttu-id="ea3f0-109">否定 IS NULL 的 EDM.Boolean 結果。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea3f0-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="ea3f0-110">Return Value</span></span>  
 `true` <span data-ttu-id="ea3f0-111">如果`expression`會傳回 null; 否則即為`false`。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-111">if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea3f0-112">備註</span><span class="sxs-lookup"><span data-stu-id="ea3f0-112">Remarks</span></span>  
 <span data-ttu-id="ea3f0-113">使用 `IS NULL` 判斷外部連結的項目是否為 null：</span><span class="sxs-lookup"><span data-stu-id="ea3f0-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="ea3f0-114">使用 `IS NULL` 判斷成員是否有實際值：</span><span class="sxs-lookup"><span data-stu-id="ea3f0-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="ea3f0-115">下表所示為 `IS NULL` 在某些模式上的行為。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="ea3f0-116">所有例外狀況都是在叫用提供者之前從用戶端擲回：</span><span class="sxs-lookup"><span data-stu-id="ea3f0-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="ea3f0-117">模式</span><span class="sxs-lookup"><span data-stu-id="ea3f0-117">Pattern</span></span>|<span data-ttu-id="ea3f0-118">行為</span><span class="sxs-lookup"><span data-stu-id="ea3f0-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="ea3f0-119">null IS NULL</span><span class="sxs-lookup"><span data-stu-id="ea3f0-119">null IS NULL</span></span>|<span data-ttu-id="ea3f0-120">傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-120">Returns `true`.</span></span>|  
|<span data-ttu-id="ea3f0-121">TREAT (null AS EntityType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="ea3f0-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="ea3f0-122">傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-122">Returns `true`.</span></span>|  
|<span data-ttu-id="ea3f0-123">TREAT (null AS ComplexType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="ea3f0-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="ea3f0-124">擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-124">Throws an error.</span></span>|  
|<span data-ttu-id="ea3f0-125">TREAT (null AS RowType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="ea3f0-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="ea3f0-126">擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-126">Throws an error.</span></span>|  
|<span data-ttu-id="ea3f0-127">EntityType IS NULL</span><span class="sxs-lookup"><span data-stu-id="ea3f0-127">EntityType IS NULL</span></span>|<span data-ttu-id="ea3f0-128">傳回 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="ea3f0-129">ComplexType IS NULL</span><span class="sxs-lookup"><span data-stu-id="ea3f0-129">ComplexType IS NULL</span></span>|<span data-ttu-id="ea3f0-130">擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-130">Throws an error.</span></span>|  
|<span data-ttu-id="ea3f0-131">RowType IS NULL</span><span class="sxs-lookup"><span data-stu-id="ea3f0-131">RowType IS NULL</span></span>|<span data-ttu-id="ea3f0-132">擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ea3f0-133">範例</span><span class="sxs-lookup"><span data-stu-id="ea3f0-133">Example</span></span>  
 <span data-ttu-id="ea3f0-134">下列[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢使用 IS NOT NULL 運算子來判斷是否查詢運算式不是 null。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="ea3f0-135">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ea3f0-136">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="ea3f0-136">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ea3f0-137">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="ea3f0-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ea3f0-138">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="ea3f0-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="ea3f0-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea3f0-139">See also</span></span>

- [<span data-ttu-id="ea3f0-140">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="ea3f0-140">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
