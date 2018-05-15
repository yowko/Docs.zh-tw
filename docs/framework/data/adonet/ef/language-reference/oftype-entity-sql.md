---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: e33d613f290338d63a232bf78e7ebd0826c19897
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="46499-102">OFTYPE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="46499-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="46499-103">從屬於特定型別的查詢運算式中傳回物件的集合。</span><span class="sxs-lookup"><span data-stu-id="46499-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46499-104">語法</span><span class="sxs-lookup"><span data-stu-id="46499-104">Syntax</span></span>  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="46499-105">引數</span><span class="sxs-lookup"><span data-stu-id="46499-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="46499-106">傳回物件集合的任何有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="46499-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="46499-107">據以測試 `expression` 所傳回之每個物件的型別。</span><span class="sxs-lookup"><span data-stu-id="46499-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="46499-108">此型別必須以命名空間 (Namespace) 限定。</span><span class="sxs-lookup"><span data-stu-id="46499-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46499-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="46499-109">Return Value</span></span>  
 <span data-ttu-id="46499-110">屬於 `test_type`型別的物件集合，或是 `test_type`之基底型別 (Base Type) 或衍生型別 (Derived Type) 的物件集合。</span><span class="sxs-lookup"><span data-stu-id="46499-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="46499-111">如果指定了 ONLY，就只會傳回 `test_type` 的執行個體 (Instance) 或空白集合。</span><span class="sxs-lookup"><span data-stu-id="46499-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46499-112">備註</span><span class="sxs-lookup"><span data-stu-id="46499-112">Remarks</span></span>  
 <span data-ttu-id="46499-113">`OFTYPE` 運算式會指定針對集合的每個項目執行型別測試所發出的型別運算式。</span><span class="sxs-lookup"><span data-stu-id="46499-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="46499-114">`OFTYPE` 運算式會產生指定之型別的新集合，其中僅包含相當於該型別或其子型別的項目。</span><span class="sxs-lookup"><span data-stu-id="46499-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="46499-115">`OFTYPE` 運算式是下列查詢運算式的縮寫：</span><span class="sxs-lookup"><span data-stu-id="46499-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="46499-116">假設 Manager 是 Employee 的子型別，下列運算式就會從員工集合中產生只有主管的集合：</span><span class="sxs-lookup"><span data-stu-id="46499-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="46499-117">您也可以使用型別篩選來向上轉型集合：</span><span class="sxs-lookup"><span data-stu-id="46499-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="46499-118">因為所有經理都是主管，所以產生的集合仍然會包含所有原始經理，但是此集合現在的型別會成為主管的集合。</span><span class="sxs-lookup"><span data-stu-id="46499-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="46499-119">下表所示為 `OFTYPE` 運算子在某些模式上的行為。</span><span class="sxs-lookup"><span data-stu-id="46499-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="46499-120">所有例外狀況 (Exception) 都是在叫用 (Invoke) 提供者之前從用戶端擲回：</span><span class="sxs-lookup"><span data-stu-id="46499-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="46499-121">模式</span><span class="sxs-lookup"><span data-stu-id="46499-121">Pattern</span></span>|<span data-ttu-id="46499-122">行為</span><span class="sxs-lookup"><span data-stu-id="46499-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="46499-123">OFTYPE(Collection(EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="46499-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="46499-124">Collection(EntityType)</span><span class="sxs-lookup"><span data-stu-id="46499-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="46499-125">OFTYPE(Collection(ComplexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="46499-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="46499-126">擲回</span><span class="sxs-lookup"><span data-stu-id="46499-126">Throws</span></span>|  
|<span data-ttu-id="46499-127">OFTYPE(Collection(RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="46499-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="46499-128">擲回</span><span class="sxs-lookup"><span data-stu-id="46499-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="46499-129">範例</span><span class="sxs-lookup"><span data-stu-id="46499-129">Example</span></span>  
 <span data-ttu-id="46499-130">下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 OFTYPE 運算子，從 Course 物件集合傳回 OnsiteCourse 物件集合。</span><span class="sxs-lookup"><span data-stu-id="46499-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="46499-131">此查詢根據[School 模型](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac)。</span><span class="sxs-lookup"><span data-stu-id="46499-131">The query is based on the [School Model](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="46499-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46499-132">See Also</span></span>  
 [<span data-ttu-id="46499-133">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="46499-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
