---
title: 比較語意 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 371999df0fb3177ecc90f9b1fa43d457a51bfd7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492490"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="460a1-102">比較語意 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="460a1-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="460a1-103">執行以下任何 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算子都會牽涉到型別執行個體的比較：</span><span class="sxs-lookup"><span data-stu-id="460a1-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="460a1-104">明確比較</span><span class="sxs-lookup"><span data-stu-id="460a1-104">Explicit comparison</span></span>  
 <span data-ttu-id="460a1-105">相等運算：</span><span class="sxs-lookup"><span data-stu-id="460a1-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="460a1-106">!=</span><span class="sxs-lookup"><span data-stu-id="460a1-106">!=</span></span>  
  
 <span data-ttu-id="460a1-107">排序作業：</span><span class="sxs-lookup"><span data-stu-id="460a1-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 <span data-ttu-id="460a1-108">可為 Null 的運算：</span><span class="sxs-lookup"><span data-stu-id="460a1-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="460a1-109">IS NULL</span><span class="sxs-lookup"><span data-stu-id="460a1-109">IS NULL</span></span>  
  
-   <span data-ttu-id="460a1-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="460a1-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="460a1-111">明確區分</span><span class="sxs-lookup"><span data-stu-id="460a1-111">Explicit distinction</span></span>  
 <span data-ttu-id="460a1-112">相等區分：</span><span class="sxs-lookup"><span data-stu-id="460a1-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="460a1-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="460a1-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="460a1-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="460a1-114">GROUP BY</span></span>  
  
 <span data-ttu-id="460a1-115">排序區分：</span><span class="sxs-lookup"><span data-stu-id="460a1-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="460a1-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="460a1-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="460a1-117">隱含區分</span><span class="sxs-lookup"><span data-stu-id="460a1-117">Implicit distinction</span></span>  
 <span data-ttu-id="460a1-118">Set 作業和述詞 (相等)：</span><span class="sxs-lookup"><span data-stu-id="460a1-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="460a1-119">UNION</span><span class="sxs-lookup"><span data-stu-id="460a1-119">UNION</span></span>  
  
-   <span data-ttu-id="460a1-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="460a1-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="460a1-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="460a1-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="460a1-122">SET</span><span class="sxs-lookup"><span data-stu-id="460a1-122">SET</span></span>  
  
-   <span data-ttu-id="460a1-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="460a1-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="460a1-124">Item 述詞 (相等)：</span><span class="sxs-lookup"><span data-stu-id="460a1-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="460a1-125">IN</span><span class="sxs-lookup"><span data-stu-id="460a1-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="460a1-126">支援的組合</span><span class="sxs-lookup"><span data-stu-id="460a1-126">Supported Combinations</span></span>  
 <span data-ttu-id="460a1-127">以下資料表針對每一種型別顯示比較運算子的所有支援組合：</span><span class="sxs-lookup"><span data-stu-id="460a1-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="460a1-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="460a1-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="460a1-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="460a1-129">**!=**</span></span>|<span data-ttu-id="460a1-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="460a1-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="460a1-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="460a1-131">**DISTINCT**</span></span>|<span data-ttu-id="460a1-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="460a1-132">**UNION**</span></span><br /><br /> <span data-ttu-id="460a1-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="460a1-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="460a1-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="460a1-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="460a1-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="460a1-135">**SET**</span></span><br /><br /> <span data-ttu-id="460a1-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="460a1-136">**OVERLAPS**</span></span>|<span data-ttu-id="460a1-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="460a1-137">**IN**</span></span>|<span data-ttu-id="460a1-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="460a1-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="460a1-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="460a1-139">**>   >=**</span></span>|<span data-ttu-id="460a1-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="460a1-140">**ORDER BY**</span></span>|<span data-ttu-id="460a1-141">**為 NULL**</span><span class="sxs-lookup"><span data-stu-id="460a1-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="460a1-142">**不是 NULL**</span><span class="sxs-lookup"><span data-stu-id="460a1-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="460a1-143">實體類型</span><span class="sxs-lookup"><span data-stu-id="460a1-143">Entity type</span></span>|<span data-ttu-id="460a1-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="460a1-145">所有屬性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="460a1-146">所有屬性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="460a1-147">所有屬性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="460a1-148">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-149">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="460a1-151">複雜類型</span><span class="sxs-lookup"><span data-stu-id="460a1-151">Complex type</span></span>|<span data-ttu-id="460a1-152">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-153">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-154">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-155">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-156">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-157">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-158">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="460a1-159">表格列</span><span class="sxs-lookup"><span data-stu-id="460a1-159">Row</span></span>|<span data-ttu-id="460a1-160">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="460a1-161">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="460a1-162">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="460a1-163">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-164">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-165">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="460a1-166">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="460a1-167">基本型別</span><span class="sxs-lookup"><span data-stu-id="460a1-167">Primitive type</span></span>|<span data-ttu-id="460a1-168">提供者特定</span><span class="sxs-lookup"><span data-stu-id="460a1-168">Provider-specific</span></span>|<span data-ttu-id="460a1-169">提供者特定</span><span class="sxs-lookup"><span data-stu-id="460a1-169">Provider-specific</span></span>|<span data-ttu-id="460a1-170">提供者特定</span><span class="sxs-lookup"><span data-stu-id="460a1-170">Provider-specific</span></span>|<span data-ttu-id="460a1-171">提供者特定</span><span class="sxs-lookup"><span data-stu-id="460a1-171">Provider-specific</span></span>|<span data-ttu-id="460a1-172">提供者特定</span><span class="sxs-lookup"><span data-stu-id="460a1-172">Provider-specific</span></span>|<span data-ttu-id="460a1-173">提供者特定</span><span class="sxs-lookup"><span data-stu-id="460a1-173">Provider-specific</span></span>|<span data-ttu-id="460a1-174">提供者特定</span><span class="sxs-lookup"><span data-stu-id="460a1-174">Provider-specific</span></span>|  
|<span data-ttu-id="460a1-175">多重集</span><span class="sxs-lookup"><span data-stu-id="460a1-175">Multiset</span></span>|<span data-ttu-id="460a1-176">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-177">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-178">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-179">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-180">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-181">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-182">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="460a1-183">參考</span><span class="sxs-lookup"><span data-stu-id="460a1-183">Ref</span></span>|<span data-ttu-id="460a1-184">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="460a1-185">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="460a1-186">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="460a1-187">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="460a1-188">Throw</span><span class="sxs-lookup"><span data-stu-id="460a1-188">Throw</span></span>|<span data-ttu-id="460a1-189">Throw</span><span class="sxs-lookup"><span data-stu-id="460a1-189">Throw</span></span>|<span data-ttu-id="460a1-190">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="460a1-191">關聯</span><span class="sxs-lookup"><span data-stu-id="460a1-191">Association</span></span><br /><br /> <span data-ttu-id="460a1-192">類型</span><span class="sxs-lookup"><span data-stu-id="460a1-192">type</span></span>|<span data-ttu-id="460a1-193">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-194">Throw</span><span class="sxs-lookup"><span data-stu-id="460a1-194">Throw</span></span>|<span data-ttu-id="460a1-195">Throw</span><span class="sxs-lookup"><span data-stu-id="460a1-195">Throw</span></span>|<span data-ttu-id="460a1-196">Throw</span><span class="sxs-lookup"><span data-stu-id="460a1-196">Throw</span></span>|<span data-ttu-id="460a1-197">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-198">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="460a1-199">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="460a1-200"><sup>1</sup>給定的實體類型執行個體的參考會以隱含方式相較之下，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="460a1-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="460a1-201">實體執行個體無法與明確參考相比較。</span><span class="sxs-lookup"><span data-stu-id="460a1-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="460a1-202">如果嘗試進行此作業，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="460a1-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="460a1-203">例如，下列查詢將會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="460a1-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="460a1-204"><sup>2</sup>複雜類型的屬性會先簡維再傳送至存放區，以便可加以比較 （只要其所有屬性都都相當）。</span><span class="sxs-lookup"><span data-stu-id="460a1-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="460a1-205">另請參閱<sup>4。</sup></span><span class="sxs-lookup"><span data-stu-id="460a1-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="460a1-206"><sup>3</sup>Entity Framework 執行階段偵測到不支援的案例，並擲回有意義的例外狀況，而不會佔用提供者/存放區。</span><span class="sxs-lookup"><span data-stu-id="460a1-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="460a1-207"><sup>4</sup>嘗試比較所有的屬性。</span><span class="sxs-lookup"><span data-stu-id="460a1-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="460a1-208">如果某個屬性具有無法比較的型別 (如文字、ntext 或影像)，可能會擲回伺服器例外狀況。</span><span class="sxs-lookup"><span data-stu-id="460a1-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="460a1-209"><sup>5</sup>比較所有的個別項目參考 （這包括實體集名稱和實體類型的所有索引鍵屬性）。</span><span class="sxs-lookup"><span data-stu-id="460a1-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="460a1-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="460a1-210">See also</span></span>
- [<span data-ttu-id="460a1-211">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="460a1-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
