---
title: 比較語意 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 57d81d4b581df76a4382ad5e1d72fe8250b10d43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150450"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="0d3e3-102">比較語意 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0d3e3-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="0d3e3-103">執行以下任何 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算子都會牽涉到型別執行個體的比較：</span><span class="sxs-lookup"><span data-stu-id="0d3e3-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="0d3e3-104">明確比較</span><span class="sxs-lookup"><span data-stu-id="0d3e3-104">Explicit comparison</span></span>  
 <span data-ttu-id="0d3e3-105">相等運算：</span><span class="sxs-lookup"><span data-stu-id="0d3e3-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="0d3e3-106">!=</span><span class="sxs-lookup"><span data-stu-id="0d3e3-106">!=</span></span>  
  
 <span data-ttu-id="0d3e3-107">排序作業：</span><span class="sxs-lookup"><span data-stu-id="0d3e3-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="0d3e3-108">可為 Null 的運算：</span><span class="sxs-lookup"><span data-stu-id="0d3e3-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="0d3e3-109">是 NULL</span><span class="sxs-lookup"><span data-stu-id="0d3e3-109">IS NULL</span></span>  
  
- <span data-ttu-id="0d3e3-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="0d3e3-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="0d3e3-111">明確區分</span><span class="sxs-lookup"><span data-stu-id="0d3e3-111">Explicit distinction</span></span>  
 <span data-ttu-id="0d3e3-112">相等區分：</span><span class="sxs-lookup"><span data-stu-id="0d3e3-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="0d3e3-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="0d3e3-113">DISTINCT</span></span>  
  
- <span data-ttu-id="0d3e3-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="0d3e3-114">GROUP BY</span></span>  
  
 <span data-ttu-id="0d3e3-115">排序區分：</span><span class="sxs-lookup"><span data-stu-id="0d3e3-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="0d3e3-116">排序依據</span><span class="sxs-lookup"><span data-stu-id="0d3e3-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="0d3e3-117">隱含區分</span><span class="sxs-lookup"><span data-stu-id="0d3e3-117">Implicit distinction</span></span>  
 <span data-ttu-id="0d3e3-118">Set 作業和述詞 (相等)：</span><span class="sxs-lookup"><span data-stu-id="0d3e3-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="0d3e3-119">UNION</span><span class="sxs-lookup"><span data-stu-id="0d3e3-119">UNION</span></span>  
  
- <span data-ttu-id="0d3e3-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="0d3e3-120">INTERSECT</span></span>  
  
- <span data-ttu-id="0d3e3-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="0d3e3-121">EXCEPT</span></span>  
  
- <span data-ttu-id="0d3e3-122">SET</span><span class="sxs-lookup"><span data-stu-id="0d3e3-122">SET</span></span>  
  
- <span data-ttu-id="0d3e3-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="0d3e3-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="0d3e3-124">Item 述詞 (相等)：</span><span class="sxs-lookup"><span data-stu-id="0d3e3-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="0d3e3-125">IN</span><span class="sxs-lookup"><span data-stu-id="0d3e3-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="0d3e3-126">支援的組合</span><span class="sxs-lookup"><span data-stu-id="0d3e3-126">Supported Combinations</span></span>  
 <span data-ttu-id="0d3e3-127">以下資料表針對每一種型別顯示比較運算子的所有支援組合：</span><span class="sxs-lookup"><span data-stu-id="0d3e3-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="0d3e3-128">**類型**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="0d3e3-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-129">**!=**</span></span>|<span data-ttu-id="0d3e3-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="0d3e3-131">**不同**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-131">**DISTINCT**</span></span>|<span data-ttu-id="0d3e3-132">**聯盟**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-132">**UNION**</span></span><br /><br /> <span data-ttu-id="0d3e3-133">**相交**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="0d3e3-134">**除了**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="0d3e3-135">**設置**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-135">**SET**</span></span><br /><br /> <span data-ttu-id="0d3e3-136">**重疊**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-136">**OVERLAPS**</span></span>|<span data-ttu-id="0d3e3-137">**在**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-137">**IN**</span></span>|<span data-ttu-id="0d3e3-138">**<<|**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="0d3e3-139">**>>|**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-139">**>   >=**</span></span>|<span data-ttu-id="0d3e3-140">**按**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-140">**ORDER BY**</span></span>|<span data-ttu-id="0d3e3-141">**為空**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="0d3e3-142">**不為空**</span><span class="sxs-lookup"><span data-stu-id="0d3e3-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="0d3e3-143">實體類型</span><span class="sxs-lookup"><span data-stu-id="0d3e3-143">Entity type</span></span>|<span data-ttu-id="0d3e3-144">參考<sup>文獻 1</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="0d3e3-145">所有屬性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="0d3e3-146">所有屬性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="0d3e3-147">所有屬性<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="0d3e3-148">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-149">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-150">參考<sup>文獻 1</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="0d3e3-151">複雜類型</span><span class="sxs-lookup"><span data-stu-id="0d3e3-151">Complex type</span></span>|<span data-ttu-id="0d3e3-152">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-153">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-154">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-155">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-156">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-157">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-158">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="0d3e3-159">資料列</span><span class="sxs-lookup"><span data-stu-id="0d3e3-159">Row</span></span>|<span data-ttu-id="0d3e3-160">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="0d3e3-161">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="0d3e3-162">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="0d3e3-163">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-164">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-165">所有屬性<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="0d3e3-166">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="0d3e3-167">基本型別</span><span class="sxs-lookup"><span data-stu-id="0d3e3-167">Primitive type</span></span>|<span data-ttu-id="0d3e3-168">提供者特定</span><span class="sxs-lookup"><span data-stu-id="0d3e3-168">Provider-specific</span></span>|<span data-ttu-id="0d3e3-169">提供者特定</span><span class="sxs-lookup"><span data-stu-id="0d3e3-169">Provider-specific</span></span>|<span data-ttu-id="0d3e3-170">提供者特定</span><span class="sxs-lookup"><span data-stu-id="0d3e3-170">Provider-specific</span></span>|<span data-ttu-id="0d3e3-171">提供者特定</span><span class="sxs-lookup"><span data-stu-id="0d3e3-171">Provider-specific</span></span>|<span data-ttu-id="0d3e3-172">提供者特定</span><span class="sxs-lookup"><span data-stu-id="0d3e3-172">Provider-specific</span></span>|<span data-ttu-id="0d3e3-173">提供者特定</span><span class="sxs-lookup"><span data-stu-id="0d3e3-173">Provider-specific</span></span>|<span data-ttu-id="0d3e3-174">提供者特定</span><span class="sxs-lookup"><span data-stu-id="0d3e3-174">Provider-specific</span></span>|  
|<span data-ttu-id="0d3e3-175">多重集</span><span class="sxs-lookup"><span data-stu-id="0d3e3-175">Multiset</span></span>|<span data-ttu-id="0d3e3-176">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-177">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-178">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-179">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-180">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-181">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-182">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="0d3e3-183">參考</span><span class="sxs-lookup"><span data-stu-id="0d3e3-183">Ref</span></span>|<span data-ttu-id="0d3e3-184">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="0d3e3-185">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="0d3e3-186">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="0d3e3-187">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="0d3e3-188">Throw</span><span class="sxs-lookup"><span data-stu-id="0d3e3-188">Throw</span></span>|<span data-ttu-id="0d3e3-189">Throw</span><span class="sxs-lookup"><span data-stu-id="0d3e3-189">Throw</span></span>|<span data-ttu-id="0d3e3-190">是<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="0d3e3-191">關聯</span><span class="sxs-lookup"><span data-stu-id="0d3e3-191">Association</span></span><br /><br /> <span data-ttu-id="0d3e3-192">type</span><span class="sxs-lookup"><span data-stu-id="0d3e3-192">type</span></span>|<span data-ttu-id="0d3e3-193">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-194">Throw</span><span class="sxs-lookup"><span data-stu-id="0d3e3-194">Throw</span></span>|<span data-ttu-id="0d3e3-195">Throw</span><span class="sxs-lookup"><span data-stu-id="0d3e3-195">Throw</span></span>|<span data-ttu-id="0d3e3-196">Throw</span><span class="sxs-lookup"><span data-stu-id="0d3e3-196">Throw</span></span>|<span data-ttu-id="0d3e3-197">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-198">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="0d3e3-199">投擲<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="0d3e3-200"><sup>1</sup>隱式比較給定實體類型實例的引用，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="0d3e3-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="0d3e3-201">實體執行個體無法與明確參考相比較。</span><span class="sxs-lookup"><span data-stu-id="0d3e3-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="0d3e3-202">如果嘗試進行此作業，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0d3e3-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="0d3e3-203">例如，下列查詢將會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="0d3e3-203">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="0d3e3-204"><sup>2</sup>複雜類型的屬性在發送到存儲之前被拼合，因此它們變得可比較（只要它們的所有屬性都是可比的）。</span><span class="sxs-lookup"><span data-stu-id="0d3e3-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="0d3e3-205">另請參閱<sup>4。</sup></span><span class="sxs-lookup"><span data-stu-id="0d3e3-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="0d3e3-206"><sup>3</sup>實體框架運行時檢測不受支援的情況，並在不雇用提供程式/存儲的情況下引發有意義的異常。</span><span class="sxs-lookup"><span data-stu-id="0d3e3-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="0d3e3-207"><sup>4</sup>嘗試比較所有屬性。</span><span class="sxs-lookup"><span data-stu-id="0d3e3-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="0d3e3-208">如果某個屬性具有無法比較的型別 (如文字、ntext 或影像)，可能會擲回伺服器例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0d3e3-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="0d3e3-209"><sup>5</sup>比較引用的所有單個元素（這包括實體集名稱和實體類型的所有鍵屬性）。</span><span class="sxs-lookup"><span data-stu-id="0d3e3-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d3e3-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d3e3-210">See also</span></span>

- [<span data-ttu-id="0d3e3-211">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="0d3e3-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
