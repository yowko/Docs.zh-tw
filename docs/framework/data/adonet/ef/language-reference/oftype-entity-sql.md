---
title: OFTYPE (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5b01097cdeba555fdc7435acd563f201f4d2ec8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="f1572-102">OFTYPE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f1572-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="f1572-103">從屬於特定型別的查詢運算式中傳回物件的集合。</span><span class="sxs-lookup"><span data-stu-id="f1572-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1572-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1572-104">Syntax</span></span>  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="f1572-105">引數</span><span class="sxs-lookup"><span data-stu-id="f1572-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f1572-106">傳回物件集合的任何有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="f1572-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="f1572-107">據以測試 `expression` 所傳回之每個物件的型別。</span><span class="sxs-lookup"><span data-stu-id="f1572-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="f1572-108">此型別必須以命名空間 (Namespace) 限定。</span><span class="sxs-lookup"><span data-stu-id="f1572-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1572-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="f1572-109">Return Value</span></span>  
 <span data-ttu-id="f1572-110">屬於 `test_type`型別的物件集合，或是 `test_type`之基底型別 (Base Type) 或衍生型別 (Derived Type) 的物件集合。</span><span class="sxs-lookup"><span data-stu-id="f1572-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="f1572-111">如果指定了 ONLY，就只會傳回 `test_type` 的執行個體 (Instance) 或空白集合。</span><span class="sxs-lookup"><span data-stu-id="f1572-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1572-112">備註</span><span class="sxs-lookup"><span data-stu-id="f1572-112">Remarks</span></span>  
 <span data-ttu-id="f1572-113">`OFTYPE` 運算式會指定針對集合的每個項目執行型別測試所發出的型別運算式。</span><span class="sxs-lookup"><span data-stu-id="f1572-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="f1572-114">`OFTYPE` 運算式會產生指定之型別的新集合，其中僅包含相當於該型別或其子型別的項目。</span><span class="sxs-lookup"><span data-stu-id="f1572-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="f1572-115">`OFTYPE` 運算式是下列查詢運算式的縮寫：</span><span class="sxs-lookup"><span data-stu-id="f1572-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="f1572-116">假設 Manager 是 Employee 的子型別，下列運算式就會從員工集合中產生只有主管的集合：</span><span class="sxs-lookup"><span data-stu-id="f1572-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="f1572-117">您也可以使用型別篩選來向上轉型集合：</span><span class="sxs-lookup"><span data-stu-id="f1572-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="f1572-118">因為所有經理都是主管，所以產生的集合仍然會包含所有原始經理，但是此集合現在的型別會成為主管的集合。</span><span class="sxs-lookup"><span data-stu-id="f1572-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="f1572-119">下表所示為 `OFTYPE` 運算子在某些模式上的行為。</span><span class="sxs-lookup"><span data-stu-id="f1572-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="f1572-120">所有例外狀況 (Exception) 都是在叫用 (Invoke) 提供者之前從用戶端擲回：</span><span class="sxs-lookup"><span data-stu-id="f1572-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="f1572-121">模式</span><span class="sxs-lookup"><span data-stu-id="f1572-121">Pattern</span></span>|<span data-ttu-id="f1572-122">行為</span><span class="sxs-lookup"><span data-stu-id="f1572-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="f1572-123">OFTYPE(Collection(EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="f1572-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="f1572-124">Collection(EntityType)</span><span class="sxs-lookup"><span data-stu-id="f1572-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="f1572-125">OFTYPE(Collection(ComplexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="f1572-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="f1572-126">擲回</span><span class="sxs-lookup"><span data-stu-id="f1572-126">Throws</span></span>|  
|<span data-ttu-id="f1572-127">OFTYPE(Collection(RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="f1572-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="f1572-128">擲回</span><span class="sxs-lookup"><span data-stu-id="f1572-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f1572-129">範例</span><span class="sxs-lookup"><span data-stu-id="f1572-129">Example</span></span>  
 <span data-ttu-id="f1572-130">下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 OFTYPE 運算子，從 Course 物件集合傳回 OnsiteCourse 物件集合。</span><span class="sxs-lookup"><span data-stu-id="f1572-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="f1572-131">此查詢是以 [School Model](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac)為基礎。</span><span class="sxs-lookup"><span data-stu-id="f1572-131">The query is based on the [School Model](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="f1572-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="f1572-132">See Also</span></span>  
 [<span data-ttu-id="f1572-133">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="f1572-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
