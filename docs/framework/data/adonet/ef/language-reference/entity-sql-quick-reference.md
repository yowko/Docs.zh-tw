---
title: Entity SQL 快速參考
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 7ec3b6fc184b4f169d6f6489bda0ec8fa4abb4f5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148136"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="58b26-102">Entity SQL 快速參考</span><span class="sxs-lookup"><span data-stu-id="58b26-102">Entity SQL Quick Reference</span></span>

<span data-ttu-id="58b26-103">本主題提供 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢的快速參考。</span><span class="sxs-lookup"><span data-stu-id="58b26-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="58b26-104">本主題的範例是以 AdventureWorks Sales Model 為基礎。</span><span class="sxs-lookup"><span data-stu-id="58b26-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="58b26-105">常值</span><span class="sxs-lookup"><span data-stu-id="58b26-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="58b26-106">String</span><span class="sxs-lookup"><span data-stu-id="58b26-106">String</span></span>  

 <span data-ttu-id="58b26-107">字串常值包括 Unicode 和非 Unicode 字元兩種。</span><span class="sxs-lookup"><span data-stu-id="58b26-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="58b26-108">Unicode 字串前面會加上 N。例如， `N'hello'` 。</span><span class="sxs-lookup"><span data-stu-id="58b26-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="58b26-109">以下是非 Unicode 字串常值的範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="58b26-110">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-110">Output:</span></span>  
  
|<span data-ttu-id="58b26-111">值</span><span class="sxs-lookup"><span data-stu-id="58b26-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="58b26-112">hello</span><span class="sxs-lookup"><span data-stu-id="58b26-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="58b26-113">Datetime</span><span class="sxs-lookup"><span data-stu-id="58b26-113">DateTime</span></span>  

 <span data-ttu-id="58b26-114">在 DateTime 常值中，日期和時間兩者都是必要項。</span><span class="sxs-lookup"><span data-stu-id="58b26-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="58b26-115">沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="58b26-115">There are no default values.</span></span>  
  
 <span data-ttu-id="58b26-116">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-116">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="58b26-117">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-117">Output:</span></span>  
  
|<span data-ttu-id="58b26-118">值</span><span class="sxs-lookup"><span data-stu-id="58b26-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="58b26-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="58b26-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="58b26-120">整數</span><span class="sxs-lookup"><span data-stu-id="58b26-120">Integer</span></span>  

 <span data-ttu-id="58b26-121">整數常值可以屬於型別 Int32 (123)、UInt32 (123U)、Int64 (123L) 和 UInt64 (123UL)。</span><span class="sxs-lookup"><span data-stu-id="58b26-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="58b26-122">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-122">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="58b26-123">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-123">Output:</span></span>  
  
|<span data-ttu-id="58b26-124">值</span><span class="sxs-lookup"><span data-stu-id="58b26-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="58b26-125">1</span><span class="sxs-lookup"><span data-stu-id="58b26-125">1</span></span>|  
|<span data-ttu-id="58b26-126">2</span><span class="sxs-lookup"><span data-stu-id="58b26-126">2</span></span>|  
|<span data-ttu-id="58b26-127">3</span><span class="sxs-lookup"><span data-stu-id="58b26-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="58b26-128">其他</span><span class="sxs-lookup"><span data-stu-id="58b26-128">Other</span></span>  

 <span data-ttu-id="58b26-129">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援的其他常值包括 Guid、二進位、浮點數/雙精度浮點數、十進位和 `null`。</span><span class="sxs-lookup"><span data-stu-id="58b26-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="58b26-130">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的 Null 常值視為與概念模型的每一種其他型別相容。</span><span class="sxs-lookup"><span data-stu-id="58b26-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="58b26-131">型別建構函式</span><span class="sxs-lookup"><span data-stu-id="58b26-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="58b26-132">ROW</span><span class="sxs-lookup"><span data-stu-id="58b26-132">ROW</span></span>  

 <span data-ttu-id="58b26-133">資料[列](row-entity-sql.md)會將匿名的結構化型別 (記錄) 值視為：`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="58b26-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="58b26-134">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-134">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="58b26-135">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-135">Output:</span></span>  
  
|<span data-ttu-id="58b26-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="58b26-136">ProductID</span></span>|<span data-ttu-id="58b26-137">名稱</span><span class="sxs-lookup"><span data-stu-id="58b26-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="58b26-138">1</span><span class="sxs-lookup"><span data-stu-id="58b26-138">1</span></span>|<span data-ttu-id="58b26-139">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="58b26-139">Adjustable Race</span></span>|  
|<span data-ttu-id="58b26-140">879</span><span class="sxs-lookup"><span data-stu-id="58b26-140">879</span></span>|<span data-ttu-id="58b26-141">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="58b26-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="58b26-142">712</span><span class="sxs-lookup"><span data-stu-id="58b26-142">712</span></span>|<span data-ttu-id="58b26-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="58b26-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="58b26-144">...</span><span class="sxs-lookup"><span data-stu-id="58b26-144">...</span></span>|<span data-ttu-id="58b26-145">...</span><span class="sxs-lookup"><span data-stu-id="58b26-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="58b26-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="58b26-146">MULTISET</span></span>  

 <span data-ttu-id="58b26-147">[多重集](multiset-entity-sql.md) 會結構集合，例如：</span><span class="sxs-lookup"><span data-stu-id="58b26-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="58b26-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="58b26-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="58b26-149">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-149">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="58b26-150">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-150">Output:</span></span>  
  
|<span data-ttu-id="58b26-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="58b26-151">ProductID</span></span>|<span data-ttu-id="58b26-152">名稱</span><span class="sxs-lookup"><span data-stu-id="58b26-152">Name</span></span>|<span data-ttu-id="58b26-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="58b26-153">ProductNumber</span></span>|<span data-ttu-id="58b26-154">…</span><span class="sxs-lookup"><span data-stu-id="58b26-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="58b26-155">842</span><span class="sxs-lookup"><span data-stu-id="58b26-155">842</span></span>|<span data-ttu-id="58b26-156">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="58b26-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="58b26-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="58b26-157">PA-T100</span></span>|<span data-ttu-id="58b26-158">…</span><span class="sxs-lookup"><span data-stu-id="58b26-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="58b26-159">Object</span><span class="sxs-lookup"><span data-stu-id="58b26-159">Object</span></span>  

 <span data-ttu-id="58b26-160">[命名的型](named-type-constructor-entity-sql.md) 別函式會建立名為) 使用者定義物件的 (，例如 `person("abc", 12)` 。</span><span class="sxs-lookup"><span data-stu-id="58b26-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="58b26-161">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-161">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 <span data-ttu-id="58b26-162">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-162">Output:</span></span>  
  
|<span data-ttu-id="58b26-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="58b26-163">SalesOrderDetailID</span></span>|<span data-ttu-id="58b26-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="58b26-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="58b26-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="58b26-165">OrderQty</span></span>|<span data-ttu-id="58b26-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="58b26-166">ProductID</span></span>|<span data-ttu-id="58b26-167">...</span><span class="sxs-lookup"><span data-stu-id="58b26-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="58b26-168">1</span><span class="sxs-lookup"><span data-stu-id="58b26-168">1</span></span>|<span data-ttu-id="58b26-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="58b26-169">4911-403C-98</span></span>|<span data-ttu-id="58b26-170">1</span><span class="sxs-lookup"><span data-stu-id="58b26-170">1</span></span>|<span data-ttu-id="58b26-171">776</span><span class="sxs-lookup"><span data-stu-id="58b26-171">776</span></span>|<span data-ttu-id="58b26-172">...</span><span class="sxs-lookup"><span data-stu-id="58b26-172">...</span></span>|  
|<span data-ttu-id="58b26-173">2</span><span class="sxs-lookup"><span data-stu-id="58b26-173">2</span></span>|<span data-ttu-id="58b26-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="58b26-174">4911-403C-98</span></span>|<span data-ttu-id="58b26-175">3</span><span class="sxs-lookup"><span data-stu-id="58b26-175">3</span></span>|<span data-ttu-id="58b26-176">777</span><span class="sxs-lookup"><span data-stu-id="58b26-176">777</span></span>|<span data-ttu-id="58b26-177">...</span><span class="sxs-lookup"><span data-stu-id="58b26-177">...</span></span>|  
|<span data-ttu-id="58b26-178">...</span><span class="sxs-lookup"><span data-stu-id="58b26-178">...</span></span>|<span data-ttu-id="58b26-179">...</span><span class="sxs-lookup"><span data-stu-id="58b26-179">...</span></span>|<span data-ttu-id="58b26-180">...</span><span class="sxs-lookup"><span data-stu-id="58b26-180">...</span></span>|<span data-ttu-id="58b26-181">...</span><span class="sxs-lookup"><span data-stu-id="58b26-181">...</span></span>|<span data-ttu-id="58b26-182">...</span><span class="sxs-lookup"><span data-stu-id="58b26-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="58b26-183">參考資料</span><span class="sxs-lookup"><span data-stu-id="58b26-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="58b26-184">REF</span><span class="sxs-lookup"><span data-stu-id="58b26-184">REF</span></span>  

 <span data-ttu-id="58b26-185">[REF](ref-entity-sql.md) 會建立實體類型實例的參考。</span><span class="sxs-lookup"><span data-stu-id="58b26-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="58b26-186">例如，以下查詢會傳回 Orders 實體集中每一個 Order 實體的參考：</span><span class="sxs-lookup"><span data-stu-id="58b26-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="58b26-187">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-187">Output:</span></span>  
  
|<span data-ttu-id="58b26-188">值</span><span class="sxs-lookup"><span data-stu-id="58b26-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="58b26-189">1</span><span class="sxs-lookup"><span data-stu-id="58b26-189">1</span></span>|  
|<span data-ttu-id="58b26-190">2</span><span class="sxs-lookup"><span data-stu-id="58b26-190">2</span></span>|  
|<span data-ttu-id="58b26-191">3</span><span class="sxs-lookup"><span data-stu-id="58b26-191">3</span></span>|  
|<span data-ttu-id="58b26-192">...</span><span class="sxs-lookup"><span data-stu-id="58b26-192">...</span></span>|  
  
 <span data-ttu-id="58b26-193">以下範例使用屬性引出運算子 (.) 來存取實體的屬性。</span><span class="sxs-lookup"><span data-stu-id="58b26-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="58b26-194">使用屬性引出運算子時，參考會自動取值。</span><span class="sxs-lookup"><span data-stu-id="58b26-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="58b26-195">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-195">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="58b26-196">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-196">Output:</span></span>  
  
|<span data-ttu-id="58b26-197">值</span><span class="sxs-lookup"><span data-stu-id="58b26-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="58b26-198">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="58b26-198">Adjustable Race</span></span>|  
|<span data-ttu-id="58b26-199">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="58b26-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="58b26-200">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="58b26-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="58b26-201">...</span><span class="sxs-lookup"><span data-stu-id="58b26-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="58b26-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="58b26-202">DEREF</span></span>  

 <span data-ttu-id="58b26-203">[DEREF](deref-entity-sql.md) 取值參考值，並產生該取值的結果。</span><span class="sxs-lookup"><span data-stu-id="58b26-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="58b26-204">例如，以下查詢會對 Orders 實體集中的每一個 Order 產生 Order 實體：`SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`。</span><span class="sxs-lookup"><span data-stu-id="58b26-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="58b26-205">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-205">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="58b26-206">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-206">Output:</span></span>  
  
|<span data-ttu-id="58b26-207">值</span><span class="sxs-lookup"><span data-stu-id="58b26-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="58b26-208">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="58b26-208">Adjustable Race</span></span>|  
|<span data-ttu-id="58b26-209">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="58b26-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="58b26-210">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="58b26-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="58b26-211">...</span><span class="sxs-lookup"><span data-stu-id="58b26-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="58b26-212">CREATEREF 和 KEY</span><span class="sxs-lookup"><span data-stu-id="58b26-212">CREATEREF AND KEY</span></span>  

 <span data-ttu-id="58b26-213">[CREATEREF](createref-entity-sql.md) 會建立傳遞索引鍵的參考。</span><span class="sxs-lookup"><span data-stu-id="58b26-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="58b26-214">索引[鍵](key-entity-sql.md)會使用類型參考來解壓縮運算式的索引鍵部分。</span><span class="sxs-lookup"><span data-stu-id="58b26-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="58b26-215">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-215">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="58b26-216">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-216">Output:</span></span>  
  
|<span data-ttu-id="58b26-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="58b26-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="58b26-218">980</span><span class="sxs-lookup"><span data-stu-id="58b26-218">980</span></span>|  
|<span data-ttu-id="58b26-219">365</span><span class="sxs-lookup"><span data-stu-id="58b26-219">365</span></span>|  
|<span data-ttu-id="58b26-220">771</span><span class="sxs-lookup"><span data-stu-id="58b26-220">771</span></span>|  
|<span data-ttu-id="58b26-221">...</span><span class="sxs-lookup"><span data-stu-id="58b26-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="58b26-222">函式</span><span class="sxs-lookup"><span data-stu-id="58b26-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="58b26-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="58b26-223">Canonical</span></span>  

 <span data-ttu-id="58b26-224">[標準](canonical-functions.md)函式的命名空間為 Edm，如下所示 `Edm.Length("string")` 。</span><span class="sxs-lookup"><span data-stu-id="58b26-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="58b26-225">除非匯入了另一個命名空間其中包含與標準函式同名的函式，否則不需要指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="58b26-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="58b26-226">如果兩個命名空間有相同的函式，使用者就應當指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="58b26-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="58b26-227">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-227">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="58b26-228">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-228">Output:</span></span>  
  
|<span data-ttu-id="58b26-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="58b26-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="58b26-230">6</span><span class="sxs-lookup"><span data-stu-id="58b26-230">6</span></span>|  
|<span data-ttu-id="58b26-231">6</span><span class="sxs-lookup"><span data-stu-id="58b26-231">6</span></span>|  
|<span data-ttu-id="58b26-232">5</span><span class="sxs-lookup"><span data-stu-id="58b26-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="58b26-233">Microsoft 提供者專用</span><span class="sxs-lookup"><span data-stu-id="58b26-233">Microsoft Provider-Specific</span></span>  

 <span data-ttu-id="58b26-234">[Microsoft 提供者特有](../sqlclient-for-ef-functions.md) 的函式位於 `SqlServer` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="58b26-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="58b26-235">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-235">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="58b26-236">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-236">Output:</span></span>  
  
|<span data-ttu-id="58b26-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="58b26-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="58b26-238">27</span><span class="sxs-lookup"><span data-stu-id="58b26-238">27</span></span>|  
|<span data-ttu-id="58b26-239">27</span><span class="sxs-lookup"><span data-stu-id="58b26-239">27</span></span>|  
|<span data-ttu-id="58b26-240">26</span><span class="sxs-lookup"><span data-stu-id="58b26-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="58b26-241">命名空間</span><span class="sxs-lookup"><span data-stu-id="58b26-241">Namespaces</span></span>  

 <span data-ttu-id="58b26-242">[使用](using-entity-sql.md) 會指定查詢運算式中使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="58b26-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="58b26-243">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-243">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="58b26-244">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-244">Output:</span></span>  
  
|<span data-ttu-id="58b26-245">值</span><span class="sxs-lookup"><span data-stu-id="58b26-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="58b26-246">aa</span><span class="sxs-lookup"><span data-stu-id="58b26-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="58b26-247">Paging</span><span class="sxs-lookup"><span data-stu-id="58b26-247">Paging</span></span>  

 <span data-ttu-id="58b26-248">您可以將 [SKIP](skip-entity-sql.md) 和 [LIMIT](limit-entity-sql.md) 子子句宣告為 [ORDER by](order-by-entity-sql.md) 子句來表示分頁。</span><span class="sxs-lookup"><span data-stu-id="58b26-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="58b26-249">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-249">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="58b26-250">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-250">Output:</span></span>  
  
|<span data-ttu-id="58b26-251">ID</span><span class="sxs-lookup"><span data-stu-id="58b26-251">ID</span></span>|<span data-ttu-id="58b26-252">名稱</span><span class="sxs-lookup"><span data-stu-id="58b26-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="58b26-253">10</span><span class="sxs-lookup"><span data-stu-id="58b26-253">10</span></span>|<span data-ttu-id="58b26-254">Adina</span><span class="sxs-lookup"><span data-stu-id="58b26-254">Adina</span></span>|  
|<span data-ttu-id="58b26-255">11</span><span class="sxs-lookup"><span data-stu-id="58b26-255">11</span></span>|<span data-ttu-id="58b26-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="58b26-256">Agcaoili</span></span>|  
|<span data-ttu-id="58b26-257">12</span><span class="sxs-lookup"><span data-stu-id="58b26-257">12</span></span>|<span data-ttu-id="58b26-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="58b26-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="58b26-259">群組</span><span class="sxs-lookup"><span data-stu-id="58b26-259">Grouping</span></span>  

 <span data-ttu-id="58b26-260">[分組方式：](group-by-entity-sql.md) 指定要在其中放置查詢所傳回物件 ([選取](select-entity-sql.md)) 運算式的群組。</span><span class="sxs-lookup"><span data-stu-id="58b26-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="58b26-261">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-261">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="58b26-262">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-262">Output:</span></span>  
  
|<span data-ttu-id="58b26-263">NAME</span><span class="sxs-lookup"><span data-stu-id="58b26-263">name</span></span>|  
|----------|  
|<span data-ttu-id="58b26-264">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="58b26-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="58b26-265">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="58b26-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="58b26-266">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="58b26-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="58b26-267">...</span><span class="sxs-lookup"><span data-stu-id="58b26-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="58b26-268">巡覽</span><span class="sxs-lookup"><span data-stu-id="58b26-268">Navigation</span></span>  

 <span data-ttu-id="58b26-269">關聯性巡覽運算子可以讓您在關聯性上從一個實體 (開始端) 巡覽到另一個實體 (結束端)。</span><span class="sxs-lookup"><span data-stu-id="58b26-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="58b26-270">[導覽](navigate-entity-sql.md) 會採用限定為的關聯性類型 \<namespace> \<relationship type name> 。</span><span class="sxs-lookup"><span data-stu-id="58b26-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="58b26-271">\<T>如果結束端的基數為1，則流覽會傳回 Ref。</span><span class="sxs-lookup"><span data-stu-id="58b26-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="58b26-272">如果結束端的基數為 n，則會傳回<Ref> 的集合 \<T> 。</span><span class="sxs-lookup"><span data-stu-id="58b26-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="58b26-273">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-273">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="58b26-274">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-274">Output:</span></span>  
  
|<span data-ttu-id="58b26-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="58b26-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="58b26-276">1</span><span class="sxs-lookup"><span data-stu-id="58b26-276">1</span></span>|  
|<span data-ttu-id="58b26-277">2</span><span class="sxs-lookup"><span data-stu-id="58b26-277">2</span></span>|  
|<span data-ttu-id="58b26-278">3</span><span class="sxs-lookup"><span data-stu-id="58b26-278">3</span></span>|  
|<span data-ttu-id="58b26-279">...</span><span class="sxs-lookup"><span data-stu-id="58b26-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="58b26-280">SELECT VALUE 和 SELECT</span><span class="sxs-lookup"><span data-stu-id="58b26-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="58b26-281">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="58b26-281">SELECT VALUE</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="58b26-282">提供 SELECT VALUE 子句來略過隱含資料列建構。</span><span class="sxs-lookup"><span data-stu-id="58b26-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="58b26-283">SELECT VALUE 子句中可指定一個項目。</span><span class="sxs-lookup"><span data-stu-id="58b26-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="58b26-284">使用這類子句時，將不會根據 SELECT 子句中的專案來建立資料列包裝函式，而且可以產生所需圖形的集合，例如： `SELECT VALUE a` 。</span><span class="sxs-lookup"><span data-stu-id="58b26-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="58b26-285">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-285">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="58b26-286">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-286">Output:</span></span>  
  
|<span data-ttu-id="58b26-287">Name</span><span class="sxs-lookup"><span data-stu-id="58b26-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="58b26-288">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="58b26-288">Adjustable Race</span></span>|  
|<span data-ttu-id="58b26-289">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="58b26-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="58b26-290">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="58b26-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="58b26-291">...</span><span class="sxs-lookup"><span data-stu-id="58b26-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="58b26-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="58b26-292">SELECT</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="58b26-293">也提供資料列建構函式來建構任意資料列。</span><span class="sxs-lookup"><span data-stu-id="58b26-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="58b26-294">SELECT 會擷取投影中的一個或多個項目，並且產生具有欄位的資料記錄，例如：`SELECT a, b, c`。</span><span class="sxs-lookup"><span data-stu-id="58b26-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="58b26-295">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-295">Example:</span></span>  
  
 <span data-ttu-id="58b26-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="58b26-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="58b26-297">Name</span><span class="sxs-lookup"><span data-stu-id="58b26-297">Name</span></span>|<span data-ttu-id="58b26-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="58b26-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="58b26-299">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="58b26-299">Adjustable Race</span></span>|<span data-ttu-id="58b26-300">1</span><span class="sxs-lookup"><span data-stu-id="58b26-300">1</span></span>|  
|<span data-ttu-id="58b26-301">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="58b26-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="58b26-302">879</span><span class="sxs-lookup"><span data-stu-id="58b26-302">879</span></span>|  
|<span data-ttu-id="58b26-303">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="58b26-303">AWC Logo Cap</span></span>|<span data-ttu-id="58b26-304">712</span><span class="sxs-lookup"><span data-stu-id="58b26-304">712</span></span>|  
|<span data-ttu-id="58b26-305">...</span><span class="sxs-lookup"><span data-stu-id="58b26-305">...</span></span>|<span data-ttu-id="58b26-306">...</span><span class="sxs-lookup"><span data-stu-id="58b26-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="58b26-307">CASE 運算式</span><span class="sxs-lookup"><span data-stu-id="58b26-307">CASE EXPRESSION</span></span>  

 <span data-ttu-id="58b26-308">[Case 運算式](case-entity-sql.md)會評估一組布林運算式來判斷結果。</span><span class="sxs-lookup"><span data-stu-id="58b26-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="58b26-309">範例：</span><span class="sxs-lookup"><span data-stu-id="58b26-309">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="58b26-310">輸出：</span><span class="sxs-lookup"><span data-stu-id="58b26-310">Output:</span></span>  
  
|<span data-ttu-id="58b26-311">值</span><span class="sxs-lookup"><span data-stu-id="58b26-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="58b26-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="58b26-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58b26-313">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58b26-313">See also</span></span>

- [<span data-ttu-id="58b26-314">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="58b26-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="58b26-315">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="58b26-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
