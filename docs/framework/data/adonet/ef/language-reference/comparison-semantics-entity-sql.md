---
title: 比較語意 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 9a36fcc4476c25d64fed670e857f339fb20043d8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197829"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="b5bda-102">比較語意 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b5bda-102">Comparison Semantics (Entity SQL)</span></span>

<span data-ttu-id="b5bda-103">執行以下任何 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算子都會牽涉到型別執行個體的比較：</span><span class="sxs-lookup"><span data-stu-id="b5bda-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="b5bda-104">明確比較</span><span class="sxs-lookup"><span data-stu-id="b5bda-104">Explicit comparison</span></span>  

 <span data-ttu-id="b5bda-105">相等運算：</span><span class="sxs-lookup"><span data-stu-id="b5bda-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="b5bda-106">!=</span><span class="sxs-lookup"><span data-stu-id="b5bda-106">!=</span></span>  
  
 <span data-ttu-id="b5bda-107">排序作業：</span><span class="sxs-lookup"><span data-stu-id="b5bda-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="b5bda-108">可為 Null 的運算：</span><span class="sxs-lookup"><span data-stu-id="b5bda-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="b5bda-109">是 NULL</span><span class="sxs-lookup"><span data-stu-id="b5bda-109">IS NULL</span></span>  
  
- <span data-ttu-id="b5bda-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="b5bda-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="b5bda-111">明確區分</span><span class="sxs-lookup"><span data-stu-id="b5bda-111">Explicit distinction</span></span>  

 <span data-ttu-id="b5bda-112">相等區分：</span><span class="sxs-lookup"><span data-stu-id="b5bda-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="b5bda-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="b5bda-113">DISTINCT</span></span>  
  
- <span data-ttu-id="b5bda-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="b5bda-114">GROUP BY</span></span>  
  
 <span data-ttu-id="b5bda-115">排序區分：</span><span class="sxs-lookup"><span data-stu-id="b5bda-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="b5bda-116">排序依據</span><span class="sxs-lookup"><span data-stu-id="b5bda-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="b5bda-117">隱含區分</span><span class="sxs-lookup"><span data-stu-id="b5bda-117">Implicit distinction</span></span>  

 <span data-ttu-id="b5bda-118">Set 作業和述詞 (相等)：</span><span class="sxs-lookup"><span data-stu-id="b5bda-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="b5bda-119">UNION</span><span class="sxs-lookup"><span data-stu-id="b5bda-119">UNION</span></span>  
  
- <span data-ttu-id="b5bda-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="b5bda-120">INTERSECT</span></span>  
  
- <span data-ttu-id="b5bda-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="b5bda-121">EXCEPT</span></span>  
  
- <span data-ttu-id="b5bda-122">SET</span><span class="sxs-lookup"><span data-stu-id="b5bda-122">SET</span></span>  
  
- <span data-ttu-id="b5bda-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="b5bda-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="b5bda-124">Item 述詞 (相等)：</span><span class="sxs-lookup"><span data-stu-id="b5bda-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="b5bda-125">IN</span><span class="sxs-lookup"><span data-stu-id="b5bda-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="b5bda-126">支援的組合</span><span class="sxs-lookup"><span data-stu-id="b5bda-126">Supported Combinations</span></span>  

 <span data-ttu-id="b5bda-127">以下資料表針對每一種型別顯示比較運算子的所有支援組合：</span><span class="sxs-lookup"><span data-stu-id="b5bda-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="b5bda-128">**型別**</span><span class="sxs-lookup"><span data-stu-id="b5bda-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="b5bda-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="b5bda-129">**!=**</span></span>|<span data-ttu-id="b5bda-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="b5bda-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="b5bda-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="b5bda-131">**DISTINCT**</span></span>|<span data-ttu-id="b5bda-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="b5bda-132">**UNION**</span></span><br /><br /> <span data-ttu-id="b5bda-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="b5bda-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="b5bda-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="b5bda-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="b5bda-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="b5bda-135">**SET**</span></span><br /><br /> <span data-ttu-id="b5bda-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="b5bda-136">**OVERLAPS**</span></span>|<span data-ttu-id="b5bda-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="b5bda-137">**IN**</span></span>|<span data-ttu-id="b5bda-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="b5bda-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="b5bda-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="b5bda-139">**>   >=**</span></span>|<span data-ttu-id="b5bda-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="b5bda-140">**ORDER BY**</span></span>|<span data-ttu-id="b5bda-141">**是 NULL**</span><span class="sxs-lookup"><span data-stu-id="b5bda-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="b5bda-142">**不是 Null**</span><span class="sxs-lookup"><span data-stu-id="b5bda-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="b5bda-143">實體類型</span><span class="sxs-lookup"><span data-stu-id="b5bda-143">Entity type</span></span>|<span data-ttu-id="b5bda-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="b5bda-145">所有屬性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="b5bda-146">所有屬性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="b5bda-147">所有屬性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="b5bda-148">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-149">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="b5bda-151">複雜類型</span><span class="sxs-lookup"><span data-stu-id="b5bda-151">Complex type</span></span>|<span data-ttu-id="b5bda-152">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-153">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-154">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-155">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-156">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-157">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-158">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="b5bda-159">資料列</span><span class="sxs-lookup"><span data-stu-id="b5bda-159">Row</span></span>|<span data-ttu-id="b5bda-160">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="b5bda-161">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="b5bda-162">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="b5bda-163">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-164">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-165">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="b5bda-166">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="b5bda-167">基本型別</span><span class="sxs-lookup"><span data-stu-id="b5bda-167">Primitive type</span></span>|<span data-ttu-id="b5bda-168">提供者特定</span><span class="sxs-lookup"><span data-stu-id="b5bda-168">Provider-specific</span></span>|<span data-ttu-id="b5bda-169">提供者特定</span><span class="sxs-lookup"><span data-stu-id="b5bda-169">Provider-specific</span></span>|<span data-ttu-id="b5bda-170">提供者特定</span><span class="sxs-lookup"><span data-stu-id="b5bda-170">Provider-specific</span></span>|<span data-ttu-id="b5bda-171">提供者特定</span><span class="sxs-lookup"><span data-stu-id="b5bda-171">Provider-specific</span></span>|<span data-ttu-id="b5bda-172">提供者特定</span><span class="sxs-lookup"><span data-stu-id="b5bda-172">Provider-specific</span></span>|<span data-ttu-id="b5bda-173">提供者特定</span><span class="sxs-lookup"><span data-stu-id="b5bda-173">Provider-specific</span></span>|<span data-ttu-id="b5bda-174">提供者特定</span><span class="sxs-lookup"><span data-stu-id="b5bda-174">Provider-specific</span></span>|  
|<span data-ttu-id="b5bda-175">多重集</span><span class="sxs-lookup"><span data-stu-id="b5bda-175">Multiset</span></span>|<span data-ttu-id="b5bda-176">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-177">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-178">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-179">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-180">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-181">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-182">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="b5bda-183">參考</span><span class="sxs-lookup"><span data-stu-id="b5bda-183">Ref</span></span>|<span data-ttu-id="b5bda-184">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="b5bda-185">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="b5bda-186">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="b5bda-187">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="b5bda-188">Throw</span><span class="sxs-lookup"><span data-stu-id="b5bda-188">Throw</span></span>|<span data-ttu-id="b5bda-189">Throw</span><span class="sxs-lookup"><span data-stu-id="b5bda-189">Throw</span></span>|<span data-ttu-id="b5bda-190">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="b5bda-191">關聯</span><span class="sxs-lookup"><span data-stu-id="b5bda-191">Association</span></span><br /><br /> <span data-ttu-id="b5bda-192">類型</span><span class="sxs-lookup"><span data-stu-id="b5bda-192">type</span></span>|<span data-ttu-id="b5bda-193">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-194">Throw</span><span class="sxs-lookup"><span data-stu-id="b5bda-194">Throw</span></span>|<span data-ttu-id="b5bda-195">Throw</span><span class="sxs-lookup"><span data-stu-id="b5bda-195">Throw</span></span>|<span data-ttu-id="b5bda-196">Throw</span><span class="sxs-lookup"><span data-stu-id="b5bda-196">Throw</span></span>|<span data-ttu-id="b5bda-197">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-198">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="b5bda-199">擲回<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="b5bda-200"><sup>1</sup>指定之實體類型實例的參考會以隱含方式進行比較，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b5bda-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="b5bda-201">實體執行個體無法與明確參考相比較。</span><span class="sxs-lookup"><span data-stu-id="b5bda-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="b5bda-202">如果嘗試進行此作業，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b5bda-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="b5bda-203">例如，下列查詢將會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="b5bda-203">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="b5bda-204"><sup>2</sup>複雜型別的屬性會在傳送到存放區之前壓平合併，因此只要它們的所有屬性都是可比較的) ，它們就會變成可比較的 (。</span><span class="sxs-lookup"><span data-stu-id="b5bda-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="b5bda-205">另請參閱 <sup>4。</sup></span><span class="sxs-lookup"><span data-stu-id="b5bda-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="b5bda-206"><sup>3</sup>Entity Framework 執行時間會偵測不支援的大小寫，並擲回有意義的例外狀況，而不會吸引提供者/存放</span><span class="sxs-lookup"><span data-stu-id="b5bda-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="b5bda-207"><sup>4</sup>嘗試比較所有屬性。</span><span class="sxs-lookup"><span data-stu-id="b5bda-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="b5bda-208">如果某個屬性具有無法比較的型別 (如文字、ntext 或影像)，可能會擲回伺服器例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b5bda-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="b5bda-209"><sup>5</sup>參考的所有個別元素都會進行比較 (這包括實體集名稱和實體類型的所有索引鍵屬性) 。</span><span class="sxs-lookup"><span data-stu-id="b5bda-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5bda-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5bda-210">See also</span></span>

- [<span data-ttu-id="b5bda-211">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="b5bda-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
