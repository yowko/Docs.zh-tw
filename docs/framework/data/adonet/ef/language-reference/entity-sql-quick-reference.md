---
title: Entity SQL 快速參考
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: b4e3eaf8abd82b63fa2663b47f878ecfa9584897
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207067"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="fac99-102">Entity SQL 快速參考</span><span class="sxs-lookup"><span data-stu-id="fac99-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="fac99-103">本主題提供 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢的快速參考。</span><span class="sxs-lookup"><span data-stu-id="fac99-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="fac99-104">本主題中的查詢是以 AdventureWorks Sales model 為基礎。</span><span class="sxs-lookup"><span data-stu-id="fac99-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="fac99-105">常值</span><span class="sxs-lookup"><span data-stu-id="fac99-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="fac99-106">String</span><span class="sxs-lookup"><span data-stu-id="fac99-106">String</span></span>  
 <span data-ttu-id="fac99-107">字串常值包括 Unicode 和非 Unicode 字元兩種。</span><span class="sxs-lookup"><span data-stu-id="fac99-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="fac99-108">Unicode 字串前面會加一個 n比方說， `N'hello'`。</span><span class="sxs-lookup"><span data-stu-id="fac99-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="fac99-109">以下是非 Unicode 字串常值的範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="fac99-110">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-110">Output:</span></span>  
  
|<span data-ttu-id="fac99-111">值</span><span class="sxs-lookup"><span data-stu-id="fac99-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fac99-112">hello</span><span class="sxs-lookup"><span data-stu-id="fac99-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="fac99-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="fac99-113">DateTime</span></span>  
 <span data-ttu-id="fac99-114">在 DateTime 常值中，日期和時間兩者都是必要項。</span><span class="sxs-lookup"><span data-stu-id="fac99-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="fac99-115">沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="fac99-115">There are no default values.</span></span>  
  
 <span data-ttu-id="fac99-116">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="fac99-117">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-117">Output:</span></span>  
  
|<span data-ttu-id="fac99-118">值</span><span class="sxs-lookup"><span data-stu-id="fac99-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fac99-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="fac99-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="fac99-120">整數</span><span class="sxs-lookup"><span data-stu-id="fac99-120">Integer</span></span>  
 <span data-ttu-id="fac99-121">整數常值可以屬於型別 Int32 (123)、UInt32 (123U)、Int64 (123L) 和 UInt64 (123UL)。</span><span class="sxs-lookup"><span data-stu-id="fac99-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="fac99-122">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="fac99-123">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-123">Output:</span></span>  
  
|<span data-ttu-id="fac99-124">值</span><span class="sxs-lookup"><span data-stu-id="fac99-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fac99-125">1</span><span class="sxs-lookup"><span data-stu-id="fac99-125">1</span></span>|  
|<span data-ttu-id="fac99-126">2</span><span class="sxs-lookup"><span data-stu-id="fac99-126">2</span></span>|  
|<span data-ttu-id="fac99-127">3</span><span class="sxs-lookup"><span data-stu-id="fac99-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="fac99-128">其他</span><span class="sxs-lookup"><span data-stu-id="fac99-128">Other</span></span>  
 <span data-ttu-id="fac99-129">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援的其他常值包括 Guid、二進位、浮點數/雙精度浮點數、十進位和 `null`。</span><span class="sxs-lookup"><span data-stu-id="fac99-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="fac99-130">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的 Null 常值視為與概念模型的每一種其他型別相容。</span><span class="sxs-lookup"><span data-stu-id="fac99-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="fac99-131">型別建構函式</span><span class="sxs-lookup"><span data-stu-id="fac99-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="fac99-132">ROW</span><span class="sxs-lookup"><span data-stu-id="fac99-132">ROW</span></span>  
 <span data-ttu-id="fac99-133">[資料列](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)建構匿名、 結構式型別 （記錄） 值，例如：</span><span class="sxs-lookup"><span data-stu-id="fac99-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in:</span></span> `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 <span data-ttu-id="fac99-134">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="fac99-135">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-135">Output:</span></span>  
  
|<span data-ttu-id="fac99-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="fac99-136">ProductID</span></span>|<span data-ttu-id="fac99-137">名稱</span><span class="sxs-lookup"><span data-stu-id="fac99-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="fac99-138">1</span><span class="sxs-lookup"><span data-stu-id="fac99-138">1</span></span>|<span data-ttu-id="fac99-139">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="fac99-139">Adjustable Race</span></span>|  
|<span data-ttu-id="fac99-140">879</span><span class="sxs-lookup"><span data-stu-id="fac99-140">879</span></span>|<span data-ttu-id="fac99-141">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="fac99-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="fac99-142">712</span><span class="sxs-lookup"><span data-stu-id="fac99-142">712</span></span>|<span data-ttu-id="fac99-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="fac99-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="fac99-144">...</span><span class="sxs-lookup"><span data-stu-id="fac99-144">...</span></span>|<span data-ttu-id="fac99-145">...</span><span class="sxs-lookup"><span data-stu-id="fac99-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="fac99-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="fac99-146">MULTISET</span></span>  
 <span data-ttu-id="fac99-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)建構集合，例如：</span><span class="sxs-lookup"><span data-stu-id="fac99-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 <span data-ttu-id="fac99-148">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-148">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="fac99-149">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-149">Output:</span></span>  
  
|<span data-ttu-id="fac99-150">ProductID</span><span class="sxs-lookup"><span data-stu-id="fac99-150">ProductID</span></span>|<span data-ttu-id="fac99-151">名稱</span><span class="sxs-lookup"><span data-stu-id="fac99-151">Name</span></span>|<span data-ttu-id="fac99-152">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="fac99-152">ProductNumber</span></span>|<span data-ttu-id="fac99-153">…</span><span class="sxs-lookup"><span data-stu-id="fac99-153">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="fac99-154">842</span><span class="sxs-lookup"><span data-stu-id="fac99-154">842</span></span>|<span data-ttu-id="fac99-155">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="fac99-155">Touring-Panniers, Large</span></span>|<span data-ttu-id="fac99-156">PA-T100</span><span class="sxs-lookup"><span data-stu-id="fac99-156">PA-T100</span></span>|<span data-ttu-id="fac99-157">…</span><span class="sxs-lookup"><span data-stu-id="fac99-157">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="fac99-158">Object</span><span class="sxs-lookup"><span data-stu-id="fac99-158">Object</span></span>  
 <span data-ttu-id="fac99-159">[具名類型建構函式](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)建構 （具名） 使用者定義的物件，例如`person("abc", 12)`。</span><span class="sxs-lookup"><span data-stu-id="fac99-159">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="fac99-160">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-160">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="fac99-161">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-161">Output:</span></span>  
  
|<span data-ttu-id="fac99-162">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="fac99-162">SalesOrderDetailID</span></span>|<span data-ttu-id="fac99-163">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="fac99-163">CarrierTrackingNumber</span></span>|<span data-ttu-id="fac99-164">OrderQty</span><span class="sxs-lookup"><span data-stu-id="fac99-164">OrderQty</span></span>|<span data-ttu-id="fac99-165">ProductID</span><span class="sxs-lookup"><span data-stu-id="fac99-165">ProductID</span></span>|<span data-ttu-id="fac99-166">...</span><span class="sxs-lookup"><span data-stu-id="fac99-166">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="fac99-167">1</span><span class="sxs-lookup"><span data-stu-id="fac99-167">1</span></span>|<span data-ttu-id="fac99-168">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="fac99-168">4911-403C-98</span></span>|<span data-ttu-id="fac99-169">1</span><span class="sxs-lookup"><span data-stu-id="fac99-169">1</span></span>|<span data-ttu-id="fac99-170">776</span><span class="sxs-lookup"><span data-stu-id="fac99-170">776</span></span>|<span data-ttu-id="fac99-171">...</span><span class="sxs-lookup"><span data-stu-id="fac99-171">...</span></span>|  
|<span data-ttu-id="fac99-172">2</span><span class="sxs-lookup"><span data-stu-id="fac99-172">2</span></span>|<span data-ttu-id="fac99-173">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="fac99-173">4911-403C-98</span></span>|<span data-ttu-id="fac99-174">3</span><span class="sxs-lookup"><span data-stu-id="fac99-174">3</span></span>|<span data-ttu-id="fac99-175">777</span><span class="sxs-lookup"><span data-stu-id="fac99-175">777</span></span>|<span data-ttu-id="fac99-176">...</span><span class="sxs-lookup"><span data-stu-id="fac99-176">...</span></span>|  
|<span data-ttu-id="fac99-177">...</span><span class="sxs-lookup"><span data-stu-id="fac99-177">...</span></span>|<span data-ttu-id="fac99-178">...</span><span class="sxs-lookup"><span data-stu-id="fac99-178">...</span></span>|<span data-ttu-id="fac99-179">...</span><span class="sxs-lookup"><span data-stu-id="fac99-179">...</span></span>|<span data-ttu-id="fac99-180">...</span><span class="sxs-lookup"><span data-stu-id="fac99-180">...</span></span>|<span data-ttu-id="fac99-181">...</span><span class="sxs-lookup"><span data-stu-id="fac99-181">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="fac99-182">參考</span><span class="sxs-lookup"><span data-stu-id="fac99-182">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="fac99-183">REF</span><span class="sxs-lookup"><span data-stu-id="fac99-183">REF</span></span>  
 <span data-ttu-id="fac99-184">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)建立實體類型執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="fac99-184">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="fac99-185">例如，以下查詢會傳回 Orders 實體集中每一個 Order 實體的參考：</span><span class="sxs-lookup"><span data-stu-id="fac99-185">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="fac99-186">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-186">Output:</span></span>  
  
|<span data-ttu-id="fac99-187">值</span><span class="sxs-lookup"><span data-stu-id="fac99-187">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fac99-188">1</span><span class="sxs-lookup"><span data-stu-id="fac99-188">1</span></span>|  
|<span data-ttu-id="fac99-189">2</span><span class="sxs-lookup"><span data-stu-id="fac99-189">2</span></span>|  
|<span data-ttu-id="fac99-190">3</span><span class="sxs-lookup"><span data-stu-id="fac99-190">3</span></span>|  
|<span data-ttu-id="fac99-191">...</span><span class="sxs-lookup"><span data-stu-id="fac99-191">...</span></span>|  
  
 <span data-ttu-id="fac99-192">以下範例使用屬性引出運算子 (.) 來存取實體的屬性。</span><span class="sxs-lookup"><span data-stu-id="fac99-192">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="fac99-193">使用屬性引出運算子時，參考會自動取值。</span><span class="sxs-lookup"><span data-stu-id="fac99-193">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="fac99-194">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-194">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="fac99-195">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-195">Output:</span></span>  
  
|<span data-ttu-id="fac99-196">值</span><span class="sxs-lookup"><span data-stu-id="fac99-196">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fac99-197">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="fac99-197">Adjustable Race</span></span>|  
|<span data-ttu-id="fac99-198">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="fac99-198">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="fac99-199">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="fac99-199">AWC Logo Cap</span></span>|  
|<span data-ttu-id="fac99-200">...</span><span class="sxs-lookup"><span data-stu-id="fac99-200">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="fac99-201">DEREF</span><span class="sxs-lookup"><span data-stu-id="fac99-201">DEREF</span></span>  
 <span data-ttu-id="fac99-202">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)參考會值取值並且產生該取值的結果。</span><span class="sxs-lookup"><span data-stu-id="fac99-202">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="fac99-203">例如，以下查詢會對 Orders 實體集中的每一個 Order 產生 Order 實體：`SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`。</span><span class="sxs-lookup"><span data-stu-id="fac99-203">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="fac99-204">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-204">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="fac99-205">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-205">Output:</span></span>  
  
|<span data-ttu-id="fac99-206">值</span><span class="sxs-lookup"><span data-stu-id="fac99-206">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fac99-207">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="fac99-207">Adjustable Race</span></span>|  
|<span data-ttu-id="fac99-208">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="fac99-208">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="fac99-209">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="fac99-209">AWC Logo Cap</span></span>|  
|<span data-ttu-id="fac99-210">...</span><span class="sxs-lookup"><span data-stu-id="fac99-210">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="fac99-211">CREATEREF 和 KEY</span><span class="sxs-lookup"><span data-stu-id="fac99-211">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="fac99-212">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)會建立傳遞索引鍵的參考。</span><span class="sxs-lookup"><span data-stu-id="fac99-212">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="fac99-213">[索引鍵](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)擷取具有類型參考之運算式的索引鍵部分。</span><span class="sxs-lookup"><span data-stu-id="fac99-213">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="fac99-214">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-214">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="fac99-215">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-215">Output:</span></span>  
  
|<span data-ttu-id="fac99-216">ProductID</span><span class="sxs-lookup"><span data-stu-id="fac99-216">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="fac99-217">980</span><span class="sxs-lookup"><span data-stu-id="fac99-217">980</span></span>|  
|<span data-ttu-id="fac99-218">365</span><span class="sxs-lookup"><span data-stu-id="fac99-218">365</span></span>|  
|<span data-ttu-id="fac99-219">771</span><span class="sxs-lookup"><span data-stu-id="fac99-219">771</span></span>|  
|<span data-ttu-id="fac99-220">...</span><span class="sxs-lookup"><span data-stu-id="fac99-220">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="fac99-221">函式</span><span class="sxs-lookup"><span data-stu-id="fac99-221">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="fac99-222">標準</span><span class="sxs-lookup"><span data-stu-id="fac99-222">Canonical</span></span>  
 <span data-ttu-id="fac99-223">命名空間[標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)處於 Edm 中，為`Edm.Length("string")`。</span><span class="sxs-lookup"><span data-stu-id="fac99-223">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="fac99-224">除非匯入了另一個命名空間其中包含與標準函式同名的函式，否則不需要指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="fac99-224">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="fac99-225">如果兩個命名空間有相同的函式，使用者就應當指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="fac99-225">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="fac99-226">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-226">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="fac99-227">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-227">Output:</span></span>  
  
|<span data-ttu-id="fac99-228">NameLen</span><span class="sxs-lookup"><span data-stu-id="fac99-228">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="fac99-229">6</span><span class="sxs-lookup"><span data-stu-id="fac99-229">6</span></span>|  
|<span data-ttu-id="fac99-230">6</span><span class="sxs-lookup"><span data-stu-id="fac99-230">6</span></span>|  
|<span data-ttu-id="fac99-231">5</span><span class="sxs-lookup"><span data-stu-id="fac99-231">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="fac99-232">Microsoft 提供者專用</span><span class="sxs-lookup"><span data-stu-id="fac99-232">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="fac99-233">[Microsoft 提供者特有的函式](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)位於`SqlServer`命名空間。</span><span class="sxs-lookup"><span data-stu-id="fac99-233">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="fac99-234">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-234">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="fac99-235">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-235">Output:</span></span>  
  
|<span data-ttu-id="fac99-236">EmailLen</span><span class="sxs-lookup"><span data-stu-id="fac99-236">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="fac99-237">27</span><span class="sxs-lookup"><span data-stu-id="fac99-237">27</span></span>|  
|<span data-ttu-id="fac99-238">27</span><span class="sxs-lookup"><span data-stu-id="fac99-238">27</span></span>|  
|<span data-ttu-id="fac99-239">26</span><span class="sxs-lookup"><span data-stu-id="fac99-239">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="fac99-240">命名空間</span><span class="sxs-lookup"><span data-stu-id="fac99-240">Namespaces</span></span>  
 <span data-ttu-id="fac99-241">[使用](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md)指定查詢運算式中使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="fac99-241">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="fac99-242">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-242">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="fac99-243">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-243">Output:</span></span>  
  
|<span data-ttu-id="fac99-244">值</span><span class="sxs-lookup"><span data-stu-id="fac99-244">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fac99-245">aa</span><span class="sxs-lookup"><span data-stu-id="fac99-245">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="fac99-246">分頁</span><span class="sxs-lookup"><span data-stu-id="fac99-246">Paging</span></span>  
 <span data-ttu-id="fac99-247">藉由宣告可以表示分頁[略過](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)並[限制](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)子子句，以[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)子句。</span><span class="sxs-lookup"><span data-stu-id="fac99-247">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="fac99-248">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-248">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="fac99-249">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-249">Output:</span></span>  
  
|<span data-ttu-id="fac99-250">識別碼</span><span class="sxs-lookup"><span data-stu-id="fac99-250">ID</span></span>|<span data-ttu-id="fac99-251">名稱</span><span class="sxs-lookup"><span data-stu-id="fac99-251">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="fac99-252">10</span><span class="sxs-lookup"><span data-stu-id="fac99-252">10</span></span>|<span data-ttu-id="fac99-253">Adina</span><span class="sxs-lookup"><span data-stu-id="fac99-253">Adina</span></span>|  
|<span data-ttu-id="fac99-254">11</span><span class="sxs-lookup"><span data-stu-id="fac99-254">11</span></span>|<span data-ttu-id="fac99-255">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="fac99-255">Agcaoili</span></span>|  
|<span data-ttu-id="fac99-256">12</span><span class="sxs-lookup"><span data-stu-id="fac99-256">12</span></span>|<span data-ttu-id="fac99-257">Aguilar</span><span class="sxs-lookup"><span data-stu-id="fac99-257">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="fac99-258">群組</span><span class="sxs-lookup"><span data-stu-id="fac99-258">Grouping</span></span>  
 <span data-ttu-id="fac99-259">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)指定查詢所傳回物件的群組 ([選取](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) 運算式要放置。</span><span class="sxs-lookup"><span data-stu-id="fac99-259">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="fac99-260">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-260">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="fac99-261">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-261">Output:</span></span>  
  
|<span data-ttu-id="fac99-262">名稱</span><span class="sxs-lookup"><span data-stu-id="fac99-262">name</span></span>|  
|----------|  
|<span data-ttu-id="fac99-263">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="fac99-263">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="fac99-264">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="fac99-264">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="fac99-265">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="fac99-265">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="fac99-266">...</span><span class="sxs-lookup"><span data-stu-id="fac99-266">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="fac99-267">巡覽</span><span class="sxs-lookup"><span data-stu-id="fac99-267">Navigation</span></span>  
 <span data-ttu-id="fac99-268">關聯性巡覽運算子可以讓您在關聯性上從一個實體 (開始端) 巡覽到另一個實體 (結束端)。</span><span class="sxs-lookup"><span data-stu-id="fac99-268">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="fac99-269">[瀏覽](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)接受限定為的關聯性類型\<命名空間 >。\<關聯性類型名稱 >。</span><span class="sxs-lookup"><span data-stu-id="fac99-269">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="fac99-270">瀏覽傳回 Ref\<T > 如果基數的結尾為 1。</span><span class="sxs-lookup"><span data-stu-id="fac99-270">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="fac99-271">如果基數的結尾為 n，集合 < Ref\<T >> 會傳回。</span><span class="sxs-lookup"><span data-stu-id="fac99-271">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="fac99-272">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-272">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="fac99-273">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-273">Output:</span></span>  
  
|<span data-ttu-id="fac99-274">AddressID</span><span class="sxs-lookup"><span data-stu-id="fac99-274">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="fac99-275">1</span><span class="sxs-lookup"><span data-stu-id="fac99-275">1</span></span>|  
|<span data-ttu-id="fac99-276">2</span><span class="sxs-lookup"><span data-stu-id="fac99-276">2</span></span>|  
|<span data-ttu-id="fac99-277">3</span><span class="sxs-lookup"><span data-stu-id="fac99-277">3</span></span>|  
|<span data-ttu-id="fac99-278">...</span><span class="sxs-lookup"><span data-stu-id="fac99-278">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="fac99-279">SELECT VALUE 和 SELECT</span><span class="sxs-lookup"><span data-stu-id="fac99-279">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="fac99-280">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="fac99-280">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fac99-281">提供 SELECT VALUE 子句來略過隱含資料列建構。</span><span class="sxs-lookup"><span data-stu-id="fac99-281">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="fac99-282">SELECT VALUE 子句中可指定一個項目。</span><span class="sxs-lookup"><span data-stu-id="fac99-282">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="fac99-283">當使用這類子句時，任何資料列包裝函式會建構 SELECT 子句中的項目而想要的形狀的集合可以產生，例如： `SELECT VALUE a`。</span><span class="sxs-lookup"><span data-stu-id="fac99-283">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="fac99-284">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-284">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="fac99-285">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-285">Output:</span></span>  
  
|<span data-ttu-id="fac99-286">名稱</span><span class="sxs-lookup"><span data-stu-id="fac99-286">Name</span></span>|  
|----------|  
|<span data-ttu-id="fac99-287">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="fac99-287">Adjustable Race</span></span>|  
|<span data-ttu-id="fac99-288">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="fac99-288">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="fac99-289">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="fac99-289">AWC Logo Cap</span></span>|  
|<span data-ttu-id="fac99-290">...</span><span class="sxs-lookup"><span data-stu-id="fac99-290">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="fac99-291">SELECT</span><span class="sxs-lookup"><span data-stu-id="fac99-291">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fac99-292">也會提供資料列建構函式來建構任意的資料列。</span><span class="sxs-lookup"><span data-stu-id="fac99-292">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="fac99-293">SELECT 會擷取投影中的一個或多個項目，並且產生具有欄位的資料記錄，例如：`SELECT a, b, c`。</span><span class="sxs-lookup"><span data-stu-id="fac99-293">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="fac99-294">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-294">Example:</span></span>  
  
 <span data-ttu-id="fac99-295">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="fac99-295">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="fac99-296">名稱</span><span class="sxs-lookup"><span data-stu-id="fac99-296">Name</span></span>|<span data-ttu-id="fac99-297">ProductID</span><span class="sxs-lookup"><span data-stu-id="fac99-297">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="fac99-298">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="fac99-298">Adjustable Race</span></span>|<span data-ttu-id="fac99-299">1</span><span class="sxs-lookup"><span data-stu-id="fac99-299">1</span></span>|  
|<span data-ttu-id="fac99-300">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="fac99-300">All-Purpose Bike Stand</span></span>|<span data-ttu-id="fac99-301">879</span><span class="sxs-lookup"><span data-stu-id="fac99-301">879</span></span>|  
|<span data-ttu-id="fac99-302">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="fac99-302">AWC Logo Cap</span></span>|<span data-ttu-id="fac99-303">712</span><span class="sxs-lookup"><span data-stu-id="fac99-303">712</span></span>|  
|<span data-ttu-id="fac99-304">...</span><span class="sxs-lookup"><span data-stu-id="fac99-304">...</span></span>|<span data-ttu-id="fac99-305">...</span><span class="sxs-lookup"><span data-stu-id="fac99-305">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="fac99-306">CASE 運算式</span><span class="sxs-lookup"><span data-stu-id="fac99-306">CASE EXPRESSION</span></span>  
 <span data-ttu-id="fac99-307">[Case 運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)會評估一組布林運算式來得出結果。</span><span class="sxs-lookup"><span data-stu-id="fac99-307">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="fac99-308">範例：</span><span class="sxs-lookup"><span data-stu-id="fac99-308">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="fac99-309">輸出：</span><span class="sxs-lookup"><span data-stu-id="fac99-309">Output:</span></span>  
  
|<span data-ttu-id="fac99-310">值</span><span class="sxs-lookup"><span data-stu-id="fac99-310">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fac99-311">true</span><span class="sxs-lookup"><span data-stu-id="fac99-311">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fac99-312">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fac99-312">See also</span></span>

- [<span data-ttu-id="fac99-313">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="fac99-313">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="fac99-314">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="fac99-314">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
