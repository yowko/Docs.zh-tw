---
title: Entity SQL 快速參考
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 0617ce96acaf5a6eafb2658cfe218cc8f4135f6e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765850"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="9d1dc-102">Entity SQL 快速參考</span><span class="sxs-lookup"><span data-stu-id="9d1dc-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="9d1dc-103">本主題提供 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢的快速參考。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="9d1dc-104">本主題中的查詢根據 AdventureWorks Sales model。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="9d1dc-105">常值</span><span class="sxs-lookup"><span data-stu-id="9d1dc-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="9d1dc-106">String</span><span class="sxs-lookup"><span data-stu-id="9d1dc-106">String</span></span>  
 <span data-ttu-id="9d1dc-107">字串常值包括 Unicode 和非 Unicode 字元兩種。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="9d1dc-108">Unicode 字串前面會加一個 n，例如， `N'hello'`。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="9d1dc-109">以下是非 Unicode 字串常值的範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="9d1dc-110">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-110">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-111">值</span><span class="sxs-lookup"><span data-stu-id="9d1dc-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="9d1dc-112">hello</span><span class="sxs-lookup"><span data-stu-id="9d1dc-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="9d1dc-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="9d1dc-113">DateTime</span></span>  
 <span data-ttu-id="9d1dc-114">在 DateTime 常值中，日期和時間兩者都是必要項。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="9d1dc-115">沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-115">There are no default values.</span></span>  
  
 <span data-ttu-id="9d1dc-116">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="9d1dc-117">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-117">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-118">值</span><span class="sxs-lookup"><span data-stu-id="9d1dc-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="9d1dc-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="9d1dc-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="9d1dc-120">Integer</span><span class="sxs-lookup"><span data-stu-id="9d1dc-120">Integer</span></span>  
 <span data-ttu-id="9d1dc-121">整數常值可以屬於型別 Int32 (123)、UInt32 (123U)、Int64 (123L) 和 UInt64 (123UL)。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="9d1dc-122">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="9d1dc-123">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-123">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-124">值</span><span class="sxs-lookup"><span data-stu-id="9d1dc-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="9d1dc-125">1</span><span class="sxs-lookup"><span data-stu-id="9d1dc-125">1</span></span>|  
|<span data-ttu-id="9d1dc-126">2</span><span class="sxs-lookup"><span data-stu-id="9d1dc-126">2</span></span>|  
|<span data-ttu-id="9d1dc-127">3</span><span class="sxs-lookup"><span data-stu-id="9d1dc-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="9d1dc-128">其他</span><span class="sxs-lookup"><span data-stu-id="9d1dc-128">Other</span></span>  
 <span data-ttu-id="9d1dc-129">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援的其他常值包括 Guid、二進位、浮點數/雙精度浮點數、十進位和 `null`。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="9d1dc-130">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的 Null 常值視為與概念模型的每一種其他型別相容。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="9d1dc-131">型別建構函式</span><span class="sxs-lookup"><span data-stu-id="9d1dc-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="9d1dc-132">ROW</span><span class="sxs-lookup"><span data-stu-id="9d1dc-132">ROW</span></span>  
 <span data-ttu-id="9d1dc-133">[資料列](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)建構匿名、 結構式型別 （記錄） 中的左值做為： `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="9d1dc-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="9d1dc-134">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="9d1dc-135">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-135">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="9d1dc-136">ProductID</span></span>|<span data-ttu-id="9d1dc-137">名稱</span><span class="sxs-lookup"><span data-stu-id="9d1dc-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="9d1dc-138">1</span><span class="sxs-lookup"><span data-stu-id="9d1dc-138">1</span></span>|<span data-ttu-id="9d1dc-139">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="9d1dc-139">Adjustable Race</span></span>|  
|<span data-ttu-id="9d1dc-140">879</span><span class="sxs-lookup"><span data-stu-id="9d1dc-140">879</span></span>|<span data-ttu-id="9d1dc-141">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="9d1dc-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="9d1dc-142">712</span><span class="sxs-lookup"><span data-stu-id="9d1dc-142">712</span></span>|<span data-ttu-id="9d1dc-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="9d1dc-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="9d1dc-144">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-144">...</span></span>|<span data-ttu-id="9d1dc-145">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="9d1dc-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="9d1dc-146">MULTISET</span></span>  
 <span data-ttu-id="9d1dc-147">[多重集](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)建構集合，例如：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="9d1dc-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="9d1dc-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="9d1dc-149">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="9d1dc-150">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-150">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="9d1dc-151">ProductID</span></span>|<span data-ttu-id="9d1dc-152">名稱</span><span class="sxs-lookup"><span data-stu-id="9d1dc-152">Name</span></span>|<span data-ttu-id="9d1dc-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="9d1dc-153">ProductNumber</span></span>|<span data-ttu-id="9d1dc-154">…</span><span class="sxs-lookup"><span data-stu-id="9d1dc-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="9d1dc-155">842</span><span class="sxs-lookup"><span data-stu-id="9d1dc-155">842</span></span>|<span data-ttu-id="9d1dc-156">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="9d1dc-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="9d1dc-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="9d1dc-157">PA-T100</span></span>|<span data-ttu-id="9d1dc-158">…</span><span class="sxs-lookup"><span data-stu-id="9d1dc-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="9d1dc-159">Object</span><span class="sxs-lookup"><span data-stu-id="9d1dc-159">Object</span></span>  
 <span data-ttu-id="9d1dc-160">[具名類型建構函式](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)建構 （具名） 使用者定義的物件，例如`person("abc", 12)`。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-160">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="9d1dc-161">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="9d1dc-162">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-162">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="9d1dc-163">SalesOrderDetailID</span></span>|<span data-ttu-id="9d1dc-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="9d1dc-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="9d1dc-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="9d1dc-165">OrderQty</span></span>|<span data-ttu-id="9d1dc-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="9d1dc-166">ProductID</span></span>|<span data-ttu-id="9d1dc-167">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="9d1dc-168">1</span><span class="sxs-lookup"><span data-stu-id="9d1dc-168">1</span></span>|<span data-ttu-id="9d1dc-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="9d1dc-169">4911-403C-98</span></span>|<span data-ttu-id="9d1dc-170">1</span><span class="sxs-lookup"><span data-stu-id="9d1dc-170">1</span></span>|<span data-ttu-id="9d1dc-171">776</span><span class="sxs-lookup"><span data-stu-id="9d1dc-171">776</span></span>|<span data-ttu-id="9d1dc-172">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-172">...</span></span>|  
|<span data-ttu-id="9d1dc-173">2</span><span class="sxs-lookup"><span data-stu-id="9d1dc-173">2</span></span>|<span data-ttu-id="9d1dc-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="9d1dc-174">4911-403C-98</span></span>|<span data-ttu-id="9d1dc-175">3</span><span class="sxs-lookup"><span data-stu-id="9d1dc-175">3</span></span>|<span data-ttu-id="9d1dc-176">777</span><span class="sxs-lookup"><span data-stu-id="9d1dc-176">777</span></span>|<span data-ttu-id="9d1dc-177">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-177">...</span></span>|  
|<span data-ttu-id="9d1dc-178">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-178">...</span></span>|<span data-ttu-id="9d1dc-179">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-179">...</span></span>|<span data-ttu-id="9d1dc-180">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-180">...</span></span>|<span data-ttu-id="9d1dc-181">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-181">...</span></span>|<span data-ttu-id="9d1dc-182">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="9d1dc-183">參考</span><span class="sxs-lookup"><span data-stu-id="9d1dc-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="9d1dc-184">REF</span><span class="sxs-lookup"><span data-stu-id="9d1dc-184">REF</span></span>  
 <span data-ttu-id="9d1dc-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)會建立實體類型執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="9d1dc-186">例如，以下查詢會傳回 Orders 實體集中每一個 Order 實體的參考：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="9d1dc-187">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-187">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-188">值</span><span class="sxs-lookup"><span data-stu-id="9d1dc-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="9d1dc-189">1</span><span class="sxs-lookup"><span data-stu-id="9d1dc-189">1</span></span>|  
|<span data-ttu-id="9d1dc-190">2</span><span class="sxs-lookup"><span data-stu-id="9d1dc-190">2</span></span>|  
|<span data-ttu-id="9d1dc-191">3</span><span class="sxs-lookup"><span data-stu-id="9d1dc-191">3</span></span>|  
|<span data-ttu-id="9d1dc-192">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-192">...</span></span>|  
  
 <span data-ttu-id="9d1dc-193">以下範例使用屬性引出運算子 (.) 來存取實體的屬性。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="9d1dc-194">使用屬性引出運算子時，參考會自動取值。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="9d1dc-195">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="9d1dc-196">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-196">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-197">值</span><span class="sxs-lookup"><span data-stu-id="9d1dc-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="9d1dc-198">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="9d1dc-198">Adjustable Race</span></span>|  
|<span data-ttu-id="9d1dc-199">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="9d1dc-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="9d1dc-200">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="9d1dc-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="9d1dc-201">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="9d1dc-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="9d1dc-202">DEREF</span></span>  
 <span data-ttu-id="9d1dc-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)對參考值取值並且產生該取值的結果。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="9d1dc-204">例如，以下查詢會對 Orders 實體集中的每一個 Order 產生 Order 實體：`SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="9d1dc-205">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="9d1dc-206">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-206">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-207">值</span><span class="sxs-lookup"><span data-stu-id="9d1dc-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="9d1dc-208">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="9d1dc-208">Adjustable Race</span></span>|  
|<span data-ttu-id="9d1dc-209">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="9d1dc-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="9d1dc-210">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="9d1dc-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="9d1dc-211">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="9d1dc-212">CREATEREF 和 KEY</span><span class="sxs-lookup"><span data-stu-id="9d1dc-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="9d1dc-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)會建立傳遞索引鍵的參考。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="9d1dc-214">[索引鍵](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)會擷取具有類型參考之運算式的索引鍵部分。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-214">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="9d1dc-215">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="9d1dc-216">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-216">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="9d1dc-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="9d1dc-218">980</span><span class="sxs-lookup"><span data-stu-id="9d1dc-218">980</span></span>|  
|<span data-ttu-id="9d1dc-219">365</span><span class="sxs-lookup"><span data-stu-id="9d1dc-219">365</span></span>|  
|<span data-ttu-id="9d1dc-220">771</span><span class="sxs-lookup"><span data-stu-id="9d1dc-220">771</span></span>|  
|<span data-ttu-id="9d1dc-221">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="9d1dc-222">函式</span><span class="sxs-lookup"><span data-stu-id="9d1dc-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="9d1dc-223">標準</span><span class="sxs-lookup"><span data-stu-id="9d1dc-223">Canonical</span></span>  
 <span data-ttu-id="9d1dc-224">命名空間[標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)為 Edm，像是`Edm.Length("string")`。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-224">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="9d1dc-225">除非匯入了另一個命名空間其中包含與標準函式同名的函式，否則不需要指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="9d1dc-226">如果兩個命名空間有相同的函式，使用者就應當指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="9d1dc-227">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="9d1dc-228">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-228">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="9d1dc-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="9d1dc-230">6</span><span class="sxs-lookup"><span data-stu-id="9d1dc-230">6</span></span>|  
|<span data-ttu-id="9d1dc-231">6</span><span class="sxs-lookup"><span data-stu-id="9d1dc-231">6</span></span>|  
|<span data-ttu-id="9d1dc-232">5</span><span class="sxs-lookup"><span data-stu-id="9d1dc-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="9d1dc-233">Microsoft 提供者專用</span><span class="sxs-lookup"><span data-stu-id="9d1dc-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="9d1dc-234">[Microsoft 提供者專屬函式](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)中`SqlServer`命名空間。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-234">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="9d1dc-235">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="9d1dc-236">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-236">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="9d1dc-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="9d1dc-238">27</span><span class="sxs-lookup"><span data-stu-id="9d1dc-238">27</span></span>|  
|<span data-ttu-id="9d1dc-239">27</span><span class="sxs-lookup"><span data-stu-id="9d1dc-239">27</span></span>|  
|<span data-ttu-id="9d1dc-240">26</span><span class="sxs-lookup"><span data-stu-id="9d1dc-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="9d1dc-241">命名空間</span><span class="sxs-lookup"><span data-stu-id="9d1dc-241">Namespaces</span></span>  
 <span data-ttu-id="9d1dc-242">[使用](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md)指定查詢運算式中使用命名空間。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-242">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="9d1dc-243">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="9d1dc-244">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-244">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-245">值</span><span class="sxs-lookup"><span data-stu-id="9d1dc-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="9d1dc-246">aa</span><span class="sxs-lookup"><span data-stu-id="9d1dc-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="9d1dc-247">分頁</span><span class="sxs-lookup"><span data-stu-id="9d1dc-247">Paging</span></span>  
 <span data-ttu-id="9d1dc-248">藉由宣告可以表示分頁[略過](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)和[限制](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)子子句，以[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)子句。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-248">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="9d1dc-249">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="9d1dc-250">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-250">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-251">ID</span><span class="sxs-lookup"><span data-stu-id="9d1dc-251">ID</span></span>|<span data-ttu-id="9d1dc-252">名稱</span><span class="sxs-lookup"><span data-stu-id="9d1dc-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="9d1dc-253">10</span><span class="sxs-lookup"><span data-stu-id="9d1dc-253">10</span></span>|<span data-ttu-id="9d1dc-254">Adina</span><span class="sxs-lookup"><span data-stu-id="9d1dc-254">Adina</span></span>|  
|<span data-ttu-id="9d1dc-255">11</span><span class="sxs-lookup"><span data-stu-id="9d1dc-255">11</span></span>|<span data-ttu-id="9d1dc-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="9d1dc-256">Agcaoili</span></span>|  
|<span data-ttu-id="9d1dc-257">12</span><span class="sxs-lookup"><span data-stu-id="9d1dc-257">12</span></span>|<span data-ttu-id="9d1dc-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="9d1dc-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="9d1dc-259">群組</span><span class="sxs-lookup"><span data-stu-id="9d1dc-259">Grouping</span></span>  
 <span data-ttu-id="9d1dc-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)指定查詢所傳回物件的群組 ([選取](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) 運算式是要放置。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="9d1dc-261">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="9d1dc-262">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-262">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-263">name</span><span class="sxs-lookup"><span data-stu-id="9d1dc-263">name</span></span>|  
|----------|  
|<span data-ttu-id="9d1dc-264">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="9d1dc-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="9d1dc-265">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="9d1dc-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="9d1dc-266">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="9d1dc-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="9d1dc-267">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="9d1dc-268">巡覽</span><span class="sxs-lookup"><span data-stu-id="9d1dc-268">Navigation</span></span>  
 <span data-ttu-id="9d1dc-269">關聯性巡覽運算子可以讓您在關聯性上從一個實體 (開始端) 巡覽到另一個實體 (結束端)。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="9d1dc-270">[瀏覽](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)採用關聯性類型指定為\<命名空間 >。\<關聯性類型名稱 >。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="9d1dc-271">瀏覽傳回 Ref\<T > 如果基數的結尾為 1。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="9d1dc-272">如果基數的結尾為 n，集合 < Ref\<T >> 會傳回。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="9d1dc-273">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="9d1dc-274">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-274">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="9d1dc-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="9d1dc-276">1</span><span class="sxs-lookup"><span data-stu-id="9d1dc-276">1</span></span>|  
|<span data-ttu-id="9d1dc-277">2</span><span class="sxs-lookup"><span data-stu-id="9d1dc-277">2</span></span>|  
|<span data-ttu-id="9d1dc-278">3</span><span class="sxs-lookup"><span data-stu-id="9d1dc-278">3</span></span>|  
|<span data-ttu-id="9d1dc-279">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="9d1dc-280">SELECT VALUE 和 SELECT</span><span class="sxs-lookup"><span data-stu-id="9d1dc-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="9d1dc-281">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="9d1dc-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="9d1dc-282"> 提供 SELECT VALUE 子句來略過隱含資料列建構。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-282"> provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="9d1dc-283">SELECT VALUE 子句中可指定一個項目。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="9d1dc-284">這類子句使用時，任何資料列包裝函式會不建構包含 SELECT 子句中的項目所需形狀的集合可以產生，例如： `SELECT VALUE a`。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="9d1dc-285">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="9d1dc-286">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-286">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-287">名稱</span><span class="sxs-lookup"><span data-stu-id="9d1dc-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="9d1dc-288">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="9d1dc-288">Adjustable Race</span></span>|  
|<span data-ttu-id="9d1dc-289">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="9d1dc-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="9d1dc-290">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="9d1dc-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="9d1dc-291">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="9d1dc-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="9d1dc-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="9d1dc-293"> 也提供資料列建構函式來建構任意資料列。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-293"> also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="9d1dc-294">SELECT 會擷取投影中的一個或多個項目，並且產生具有欄位的資料記錄，例如：`SELECT a, b, c`。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="9d1dc-295">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-295">Example:</span></span>  
  
 <span data-ttu-id="9d1dc-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="9d1dc-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="9d1dc-297">名稱</span><span class="sxs-lookup"><span data-stu-id="9d1dc-297">Name</span></span>|<span data-ttu-id="9d1dc-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="9d1dc-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="9d1dc-299">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="9d1dc-299">Adjustable Race</span></span>|<span data-ttu-id="9d1dc-300">1</span><span class="sxs-lookup"><span data-stu-id="9d1dc-300">1</span></span>|  
|<span data-ttu-id="9d1dc-301">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="9d1dc-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="9d1dc-302">879</span><span class="sxs-lookup"><span data-stu-id="9d1dc-302">879</span></span>|  
|<span data-ttu-id="9d1dc-303">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="9d1dc-303">AWC Logo Cap</span></span>|<span data-ttu-id="9d1dc-304">712</span><span class="sxs-lookup"><span data-stu-id="9d1dc-304">712</span></span>|  
|<span data-ttu-id="9d1dc-305">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-305">...</span></span>|<span data-ttu-id="9d1dc-306">...</span><span class="sxs-lookup"><span data-stu-id="9d1dc-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="9d1dc-307">CASE 運算式</span><span class="sxs-lookup"><span data-stu-id="9d1dc-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="9d1dc-308">[Case 運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)會評估一組布林運算式來得出結果。</span><span class="sxs-lookup"><span data-stu-id="9d1dc-308">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="9d1dc-309">範例：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="9d1dc-310">輸出：</span><span class="sxs-lookup"><span data-stu-id="9d1dc-310">Output:</span></span>  
  
|<span data-ttu-id="9d1dc-311">值</span><span class="sxs-lookup"><span data-stu-id="9d1dc-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="9d1dc-312">true</span><span class="sxs-lookup"><span data-stu-id="9d1dc-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d1dc-313">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d1dc-313">See Also</span></span>  
 [<span data-ttu-id="9d1dc-314">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="9d1dc-314">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="9d1dc-315">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="9d1dc-315">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
