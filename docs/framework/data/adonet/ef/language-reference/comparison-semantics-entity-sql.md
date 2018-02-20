---
title: "比較語意 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: e20d47e0ae97067d2dcafcf929f717598d4e3e80
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2018
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="d81cb-102">比較語意 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d81cb-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="d81cb-103">執行以下任何 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算子都會牽涉到型別執行個體的比較：</span><span class="sxs-lookup"><span data-stu-id="d81cb-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="d81cb-104">明確比較</span><span class="sxs-lookup"><span data-stu-id="d81cb-104">Explicit comparison</span></span>  
 <span data-ttu-id="d81cb-105">相等運算：</span><span class="sxs-lookup"><span data-stu-id="d81cb-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="d81cb-106">!=</span><span class="sxs-lookup"><span data-stu-id="d81cb-106">!=</span></span>  
  
 <span data-ttu-id="d81cb-107">排序作業：</span><span class="sxs-lookup"><span data-stu-id="d81cb-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 <span data-ttu-id="d81cb-108">可為 Null 的運算：</span><span class="sxs-lookup"><span data-stu-id="d81cb-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="d81cb-109">IS NULL</span><span class="sxs-lookup"><span data-stu-id="d81cb-109">IS NULL</span></span>  
  
-   <span data-ttu-id="d81cb-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="d81cb-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="d81cb-111">明確區分</span><span class="sxs-lookup"><span data-stu-id="d81cb-111">Explicit distinction</span></span>  
 <span data-ttu-id="d81cb-112">相等區分：</span><span class="sxs-lookup"><span data-stu-id="d81cb-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="d81cb-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="d81cb-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="d81cb-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="d81cb-114">GROUP BY</span></span>  
  
 <span data-ttu-id="d81cb-115">排序區分：</span><span class="sxs-lookup"><span data-stu-id="d81cb-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="d81cb-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="d81cb-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="d81cb-117">隱含區分</span><span class="sxs-lookup"><span data-stu-id="d81cb-117">Implicit distinction</span></span>  
 <span data-ttu-id="d81cb-118">Set 作業和述詞 (相等)：</span><span class="sxs-lookup"><span data-stu-id="d81cb-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="d81cb-119">UNION</span><span class="sxs-lookup"><span data-stu-id="d81cb-119">UNION</span></span>  
  
-   <span data-ttu-id="d81cb-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="d81cb-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="d81cb-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="d81cb-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="d81cb-122">SET</span><span class="sxs-lookup"><span data-stu-id="d81cb-122">SET</span></span>  
  
-   <span data-ttu-id="d81cb-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="d81cb-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="d81cb-124">Item 述詞 (相等)：</span><span class="sxs-lookup"><span data-stu-id="d81cb-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="d81cb-125">IN</span><span class="sxs-lookup"><span data-stu-id="d81cb-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="d81cb-126">支援的組合</span><span class="sxs-lookup"><span data-stu-id="d81cb-126">Supported Combinations</span></span>  
 <span data-ttu-id="d81cb-127">以下資料表針對每一種型別顯示比較運算子的所有支援組合：</span><span class="sxs-lookup"><span data-stu-id="d81cb-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="d81cb-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="d81cb-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="d81cb-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="d81cb-129">**!=**</span></span>|<span data-ttu-id="d81cb-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="d81cb-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="d81cb-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="d81cb-131">**DISTINCT**</span></span>|<span data-ttu-id="d81cb-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="d81cb-132">**UNION**</span></span><br /><br /> <span data-ttu-id="d81cb-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="d81cb-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="d81cb-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="d81cb-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="d81cb-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="d81cb-135">**SET**</span></span><br /><br /> <span data-ttu-id="d81cb-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="d81cb-136">**OVERLAPS**</span></span>|<span data-ttu-id="d81cb-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="d81cb-137">**IN**</span></span>|<span data-ttu-id="d81cb-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="d81cb-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="d81cb-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="d81cb-139">**>   >=**</span></span>|<span data-ttu-id="d81cb-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="d81cb-140">**ORDER BY**</span></span>|<span data-ttu-id="d81cb-141">**為 NULL**</span><span class="sxs-lookup"><span data-stu-id="d81cb-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="d81cb-142">**不是 NULL**</span><span class="sxs-lookup"><span data-stu-id="d81cb-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="d81cb-143">實體類型</span><span class="sxs-lookup"><span data-stu-id="d81cb-143">Entity type</span></span>|<span data-ttu-id="d81cb-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="d81cb-145">所有屬性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="d81cb-146">所有屬性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="d81cb-147">所有屬性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="d81cb-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="d81cb-151">複雜類型</span><span class="sxs-lookup"><span data-stu-id="d81cb-151">Complex type</span></span>|<span data-ttu-id="d81cb-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="d81cb-159">表格列</span><span class="sxs-lookup"><span data-stu-id="d81cb-159">Row</span></span>|<span data-ttu-id="d81cb-160">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="d81cb-161">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="d81cb-162">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="d81cb-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-165">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="d81cb-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="d81cb-167">基本型別</span><span class="sxs-lookup"><span data-stu-id="d81cb-167">Primitive type</span></span>|<span data-ttu-id="d81cb-168">提供者特定</span><span class="sxs-lookup"><span data-stu-id="d81cb-168">Provider-specific</span></span>|<span data-ttu-id="d81cb-169">提供者特定</span><span class="sxs-lookup"><span data-stu-id="d81cb-169">Provider-specific</span></span>|<span data-ttu-id="d81cb-170">提供者特定</span><span class="sxs-lookup"><span data-stu-id="d81cb-170">Provider-specific</span></span>|<span data-ttu-id="d81cb-171">提供者特定</span><span class="sxs-lookup"><span data-stu-id="d81cb-171">Provider-specific</span></span>|<span data-ttu-id="d81cb-172">提供者特定</span><span class="sxs-lookup"><span data-stu-id="d81cb-172">Provider-specific</span></span>|<span data-ttu-id="d81cb-173">提供者特定</span><span class="sxs-lookup"><span data-stu-id="d81cb-173">Provider-specific</span></span>|<span data-ttu-id="d81cb-174">提供者特定</span><span class="sxs-lookup"><span data-stu-id="d81cb-174">Provider-specific</span></span>|  
|<span data-ttu-id="d81cb-175">多重集</span><span class="sxs-lookup"><span data-stu-id="d81cb-175">Multiset</span></span>|<span data-ttu-id="d81cb-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="d81cb-183">參考</span><span class="sxs-lookup"><span data-stu-id="d81cb-183">Ref</span></span>|<span data-ttu-id="d81cb-184">[是]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="d81cb-185">[是]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="d81cb-186">[是]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="d81cb-187">[是]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="d81cb-188">Throw</span><span class="sxs-lookup"><span data-stu-id="d81cb-188">Throw</span></span>|<span data-ttu-id="d81cb-189">Throw</span><span class="sxs-lookup"><span data-stu-id="d81cb-189">Throw</span></span>|<span data-ttu-id="d81cb-190">[是]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="d81cb-191">關聯</span><span class="sxs-lookup"><span data-stu-id="d81cb-191">Association</span></span><br /><br /> <span data-ttu-id="d81cb-192">類型</span><span class="sxs-lookup"><span data-stu-id="d81cb-192">type</span></span>|<span data-ttu-id="d81cb-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-194">Throw</span><span class="sxs-lookup"><span data-stu-id="d81cb-194">Throw</span></span>|<span data-ttu-id="d81cb-195">Throw</span><span class="sxs-lookup"><span data-stu-id="d81cb-195">Throw</span></span>|<span data-ttu-id="d81cb-196">Throw</span><span class="sxs-lookup"><span data-stu-id="d81cb-196">Throw</span></span>|<span data-ttu-id="d81cb-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="d81cb-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="d81cb-200"><sup>1</sup>給定的實體類型執行個體的參考會以隱含方式相較之下，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d81cb-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="d81cb-201">實體執行個體無法與明確參考相比較。</span><span class="sxs-lookup"><span data-stu-id="d81cb-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="d81cb-202">如果嘗試進行此作業，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d81cb-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="d81cb-203">例如，下列查詢將會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="d81cb-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="d81cb-204"><sup>2</sup>複雜類型的屬性會先簡維傳送至存放區，以便可加以比較 （只要其所有屬性都都可比較）。</span><span class="sxs-lookup"><span data-stu-id="d81cb-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="d81cb-205">另請參閱<sup>4。</sup></span><span class="sxs-lookup"><span data-stu-id="d81cb-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="d81cb-206"><sup>3</sup>Entity Framework 執行階段會偵測到不支援的案例，並擲回有意義的例外狀況，而不會佔用提供者/存放區。</span><span class="sxs-lookup"><span data-stu-id="d81cb-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="d81cb-207"><sup>4</sup>嘗試比較所有的屬性。</span><span class="sxs-lookup"><span data-stu-id="d81cb-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="d81cb-208">如果某個屬性具有無法比較的型別 (如文字、ntext 或影像)，可能會擲回伺服器例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d81cb-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="d81cb-209"><sup>5</sup>比較所有的個別項目參考 （這包括實體集名稱和實體類型的所有索引鍵屬性）。</span><span class="sxs-lookup"><span data-stu-id="d81cb-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d81cb-210">請參閱</span><span class="sxs-lookup"><span data-stu-id="d81cb-210">See Also</span></span>  
 [<span data-ttu-id="d81cb-211">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="d81cb-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
