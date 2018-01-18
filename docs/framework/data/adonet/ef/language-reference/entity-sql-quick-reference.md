---
title: "Entity SQL 快速參考"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 81fd76d09f9cc02e89ac34d5f8fa74bd7f9d92f9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="fa05f-102">Entity SQL 快速參考</span><span class="sxs-lookup"><span data-stu-id="fa05f-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="fa05f-103">本主題提供 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢的快速參考。</span><span class="sxs-lookup"><span data-stu-id="fa05f-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="fa05f-104">本主題中的查詢根據 AdventureWorks Sales model。</span><span class="sxs-lookup"><span data-stu-id="fa05f-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="fa05f-105">常值</span><span class="sxs-lookup"><span data-stu-id="fa05f-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="fa05f-106">String</span><span class="sxs-lookup"><span data-stu-id="fa05f-106">String</span></span>  
 <span data-ttu-id="fa05f-107">字串常值包括 Unicode 和非 Unicode 字元兩種。</span><span class="sxs-lookup"><span data-stu-id="fa05f-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="fa05f-108">Unicode 字串前面會加一個 n，例如， `N'hello'`。</span><span class="sxs-lookup"><span data-stu-id="fa05f-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="fa05f-109">以下是非 Unicode 字串常值的範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="fa05f-110">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-110">Output:</span></span>  
  
|<span data-ttu-id="fa05f-111">值</span><span class="sxs-lookup"><span data-stu-id="fa05f-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fa05f-112">hello</span><span class="sxs-lookup"><span data-stu-id="fa05f-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="fa05f-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="fa05f-113">DateTime</span></span>  
 <span data-ttu-id="fa05f-114">在 DateTime 常值中，日期和時間兩者都是必要項。</span><span class="sxs-lookup"><span data-stu-id="fa05f-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="fa05f-115">沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="fa05f-115">There are no default values.</span></span>  
  
 <span data-ttu-id="fa05f-116">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="fa05f-117">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-117">Output:</span></span>  
  
|<span data-ttu-id="fa05f-118">值</span><span class="sxs-lookup"><span data-stu-id="fa05f-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fa05f-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="fa05f-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="fa05f-120">Integer</span><span class="sxs-lookup"><span data-stu-id="fa05f-120">Integer</span></span>  
 <span data-ttu-id="fa05f-121">整數常值可以屬於型別 Int32 (123)、UInt32 (123U)、Int64 (123L) 和 UInt64 (123UL)。</span><span class="sxs-lookup"><span data-stu-id="fa05f-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="fa05f-122">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="fa05f-123">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-123">Output:</span></span>  
  
|<span data-ttu-id="fa05f-124">值</span><span class="sxs-lookup"><span data-stu-id="fa05f-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fa05f-125">1</span><span class="sxs-lookup"><span data-stu-id="fa05f-125">1</span></span>|  
|<span data-ttu-id="fa05f-126">2</span><span class="sxs-lookup"><span data-stu-id="fa05f-126">2</span></span>|  
|<span data-ttu-id="fa05f-127">3</span><span class="sxs-lookup"><span data-stu-id="fa05f-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="fa05f-128">其他</span><span class="sxs-lookup"><span data-stu-id="fa05f-128">Other</span></span>  
 <span data-ttu-id="fa05f-129">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援的其他常值包括 Guid、二進位、浮點數/雙精度浮點數、十進位和 `null`。</span><span class="sxs-lookup"><span data-stu-id="fa05f-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="fa05f-130">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 中的 Null 常值視為與概念模型的每一種其他型別相容。</span><span class="sxs-lookup"><span data-stu-id="fa05f-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="fa05f-131">型別建構函式</span><span class="sxs-lookup"><span data-stu-id="fa05f-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="fa05f-132">ROW</span><span class="sxs-lookup"><span data-stu-id="fa05f-132">ROW</span></span>  
 <span data-ttu-id="fa05f-133">[資料列](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)建構匿名、 結構式型別 （記錄） 中的左值做為：`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="fa05f-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="fa05f-134">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="fa05f-135">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-135">Output:</span></span>  
  
|<span data-ttu-id="fa05f-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="fa05f-136">ProductID</span></span>|<span data-ttu-id="fa05f-137">名稱</span><span class="sxs-lookup"><span data-stu-id="fa05f-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="fa05f-138">1</span><span class="sxs-lookup"><span data-stu-id="fa05f-138">1</span></span>|<span data-ttu-id="fa05f-139">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="fa05f-139">Adjustable Race</span></span>|  
|<span data-ttu-id="fa05f-140">879</span><span class="sxs-lookup"><span data-stu-id="fa05f-140">879</span></span>|<span data-ttu-id="fa05f-141">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="fa05f-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="fa05f-142">712</span><span class="sxs-lookup"><span data-stu-id="fa05f-142">712</span></span>|<span data-ttu-id="fa05f-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="fa05f-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="fa05f-144">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-144">...</span></span>|<span data-ttu-id="fa05f-145">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="fa05f-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="fa05f-146">MULTISET</span></span>  
 <span data-ttu-id="fa05f-147">[多重集](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)建構集合，例如：</span><span class="sxs-lookup"><span data-stu-id="fa05f-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="fa05f-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="fa05f-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="fa05f-149">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="fa05f-150">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-150">Output:</span></span>  
  
|<span data-ttu-id="fa05f-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="fa05f-151">ProductID</span></span>|<span data-ttu-id="fa05f-152">名稱</span><span class="sxs-lookup"><span data-stu-id="fa05f-152">Name</span></span>|<span data-ttu-id="fa05f-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="fa05f-153">ProductNumber</span></span>|<span data-ttu-id="fa05f-154">…</span><span class="sxs-lookup"><span data-stu-id="fa05f-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="fa05f-155">842</span><span class="sxs-lookup"><span data-stu-id="fa05f-155">842</span></span>|<span data-ttu-id="fa05f-156">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="fa05f-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="fa05f-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="fa05f-157">PA-T100</span></span>|<span data-ttu-id="fa05f-158">…</span><span class="sxs-lookup"><span data-stu-id="fa05f-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="fa05f-159">Object</span><span class="sxs-lookup"><span data-stu-id="fa05f-159">Object</span></span>  
 <span data-ttu-id="fa05f-160">[具名類型建構函式](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)建構 （具名） 使用者定義的物件，例如`person("abc", 12)`。</span><span class="sxs-lookup"><span data-stu-id="fa05f-160">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="fa05f-161">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="fa05f-162">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-162">Output:</span></span>  
  
|<span data-ttu-id="fa05f-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="fa05f-163">SalesOrderDetailID</span></span>|<span data-ttu-id="fa05f-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="fa05f-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="fa05f-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="fa05f-165">OrderQty</span></span>|<span data-ttu-id="fa05f-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="fa05f-166">ProductID</span></span>|<span data-ttu-id="fa05f-167">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="fa05f-168">1</span><span class="sxs-lookup"><span data-stu-id="fa05f-168">1</span></span>|<span data-ttu-id="fa05f-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="fa05f-169">4911-403C-98</span></span>|<span data-ttu-id="fa05f-170">1</span><span class="sxs-lookup"><span data-stu-id="fa05f-170">1</span></span>|<span data-ttu-id="fa05f-171">776</span><span class="sxs-lookup"><span data-stu-id="fa05f-171">776</span></span>|<span data-ttu-id="fa05f-172">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-172">...</span></span>|  
|<span data-ttu-id="fa05f-173">2</span><span class="sxs-lookup"><span data-stu-id="fa05f-173">2</span></span>|<span data-ttu-id="fa05f-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="fa05f-174">4911-403C-98</span></span>|<span data-ttu-id="fa05f-175">3</span><span class="sxs-lookup"><span data-stu-id="fa05f-175">3</span></span>|<span data-ttu-id="fa05f-176">777</span><span class="sxs-lookup"><span data-stu-id="fa05f-176">777</span></span>|<span data-ttu-id="fa05f-177">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-177">...</span></span>|  
|<span data-ttu-id="fa05f-178">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-178">...</span></span>|<span data-ttu-id="fa05f-179">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-179">...</span></span>|<span data-ttu-id="fa05f-180">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-180">...</span></span>|<span data-ttu-id="fa05f-181">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-181">...</span></span>|<span data-ttu-id="fa05f-182">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="fa05f-183">參考</span><span class="sxs-lookup"><span data-stu-id="fa05f-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="fa05f-184">REF</span><span class="sxs-lookup"><span data-stu-id="fa05f-184">REF</span></span>  
 <span data-ttu-id="fa05f-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)會建立實體類型執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="fa05f-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="fa05f-186">例如，以下查詢會傳回 Orders 實體集中每一個 Order 實體的參考：</span><span class="sxs-lookup"><span data-stu-id="fa05f-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="fa05f-187">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-187">Output:</span></span>  
  
|<span data-ttu-id="fa05f-188">值</span><span class="sxs-lookup"><span data-stu-id="fa05f-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fa05f-189">1</span><span class="sxs-lookup"><span data-stu-id="fa05f-189">1</span></span>|  
|<span data-ttu-id="fa05f-190">2</span><span class="sxs-lookup"><span data-stu-id="fa05f-190">2</span></span>|  
|<span data-ttu-id="fa05f-191">3</span><span class="sxs-lookup"><span data-stu-id="fa05f-191">3</span></span>|  
|<span data-ttu-id="fa05f-192">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-192">...</span></span>|  
  
 <span data-ttu-id="fa05f-193">以下範例使用屬性引出運算子 (.) 來存取實體的屬性。</span><span class="sxs-lookup"><span data-stu-id="fa05f-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="fa05f-194">使用屬性引出運算子時，參考會自動取值。</span><span class="sxs-lookup"><span data-stu-id="fa05f-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="fa05f-195">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="fa05f-196">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-196">Output:</span></span>  
  
|<span data-ttu-id="fa05f-197">值</span><span class="sxs-lookup"><span data-stu-id="fa05f-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fa05f-198">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="fa05f-198">Adjustable Race</span></span>|  
|<span data-ttu-id="fa05f-199">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="fa05f-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="fa05f-200">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="fa05f-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="fa05f-201">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="fa05f-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="fa05f-202">DEREF</span></span>  
 <span data-ttu-id="fa05f-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)對參考值取值並且產生該取值的結果。</span><span class="sxs-lookup"><span data-stu-id="fa05f-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="fa05f-204">例如，以下查詢會對 Orders 實體集中的每一個 Order 產生 Order 實體：`SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`。</span><span class="sxs-lookup"><span data-stu-id="fa05f-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="fa05f-205">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="fa05f-206">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-206">Output:</span></span>  
  
|<span data-ttu-id="fa05f-207">值</span><span class="sxs-lookup"><span data-stu-id="fa05f-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fa05f-208">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="fa05f-208">Adjustable Race</span></span>|  
|<span data-ttu-id="fa05f-209">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="fa05f-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="fa05f-210">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="fa05f-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="fa05f-211">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="fa05f-212">CREATEREF 和 KEY</span><span class="sxs-lookup"><span data-stu-id="fa05f-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="fa05f-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)會建立傳遞索引鍵的參考。</span><span class="sxs-lookup"><span data-stu-id="fa05f-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="fa05f-214">[索引鍵](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)會擷取具有類型參考之運算式的索引鍵部分。</span><span class="sxs-lookup"><span data-stu-id="fa05f-214">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="fa05f-215">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="fa05f-216">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-216">Output:</span></span>  
  
|<span data-ttu-id="fa05f-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="fa05f-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="fa05f-218">980</span><span class="sxs-lookup"><span data-stu-id="fa05f-218">980</span></span>|  
|<span data-ttu-id="fa05f-219">365</span><span class="sxs-lookup"><span data-stu-id="fa05f-219">365</span></span>|  
|<span data-ttu-id="fa05f-220">771</span><span class="sxs-lookup"><span data-stu-id="fa05f-220">771</span></span>|  
|<span data-ttu-id="fa05f-221">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="fa05f-222">函式</span><span class="sxs-lookup"><span data-stu-id="fa05f-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="fa05f-223">標準</span><span class="sxs-lookup"><span data-stu-id="fa05f-223">Canonical</span></span>  
 <span data-ttu-id="fa05f-224">命名空間[標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)為 Edm，像是`Edm.Length("string")`。</span><span class="sxs-lookup"><span data-stu-id="fa05f-224">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="fa05f-225">除非匯入了另一個命名空間其中包含與標準函式同名的函式，否則不需要指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="fa05f-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="fa05f-226">如果兩個命名空間有相同的函式，使用者就應當指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="fa05f-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="fa05f-227">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="fa05f-228">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-228">Output:</span></span>  
  
|<span data-ttu-id="fa05f-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="fa05f-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="fa05f-230">6</span><span class="sxs-lookup"><span data-stu-id="fa05f-230">6</span></span>|  
|<span data-ttu-id="fa05f-231">6</span><span class="sxs-lookup"><span data-stu-id="fa05f-231">6</span></span>|  
|<span data-ttu-id="fa05f-232">5</span><span class="sxs-lookup"><span data-stu-id="fa05f-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="fa05f-233">Microsoft 提供者專用</span><span class="sxs-lookup"><span data-stu-id="fa05f-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="fa05f-234">[Microsoft 提供者專屬函式](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)中`SqlServer`命名空間。</span><span class="sxs-lookup"><span data-stu-id="fa05f-234">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="fa05f-235">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="fa05f-236">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-236">Output:</span></span>  
  
|<span data-ttu-id="fa05f-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="fa05f-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="fa05f-238">27</span><span class="sxs-lookup"><span data-stu-id="fa05f-238">27</span></span>|  
|<span data-ttu-id="fa05f-239">27</span><span class="sxs-lookup"><span data-stu-id="fa05f-239">27</span></span>|  
|<span data-ttu-id="fa05f-240">26</span><span class="sxs-lookup"><span data-stu-id="fa05f-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="fa05f-241">命名空間</span><span class="sxs-lookup"><span data-stu-id="fa05f-241">Namespaces</span></span>  
 <span data-ttu-id="fa05f-242">[使用](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md)指定查詢運算式中使用命名空間。</span><span class="sxs-lookup"><span data-stu-id="fa05f-242">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="fa05f-243">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="fa05f-244">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-244">Output:</span></span>  
  
|<span data-ttu-id="fa05f-245">值</span><span class="sxs-lookup"><span data-stu-id="fa05f-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fa05f-246">aa</span><span class="sxs-lookup"><span data-stu-id="fa05f-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="fa05f-247">分頁</span><span class="sxs-lookup"><span data-stu-id="fa05f-247">Paging</span></span>  
 <span data-ttu-id="fa05f-248">藉由宣告可以表示分頁[略過](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)和[限制](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)子子句，以[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)子句。</span><span class="sxs-lookup"><span data-stu-id="fa05f-248">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="fa05f-249">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="fa05f-250">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-250">Output:</span></span>  
  
|<span data-ttu-id="fa05f-251">ID</span><span class="sxs-lookup"><span data-stu-id="fa05f-251">ID</span></span>|<span data-ttu-id="fa05f-252">名稱</span><span class="sxs-lookup"><span data-stu-id="fa05f-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="fa05f-253">10</span><span class="sxs-lookup"><span data-stu-id="fa05f-253">10</span></span>|<span data-ttu-id="fa05f-254">Adina</span><span class="sxs-lookup"><span data-stu-id="fa05f-254">Adina</span></span>|  
|<span data-ttu-id="fa05f-255">11</span><span class="sxs-lookup"><span data-stu-id="fa05f-255">11</span></span>|<span data-ttu-id="fa05f-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="fa05f-256">Agcaoili</span></span>|  
|<span data-ttu-id="fa05f-257">12</span><span class="sxs-lookup"><span data-stu-id="fa05f-257">12</span></span>|<span data-ttu-id="fa05f-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="fa05f-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="fa05f-259">群組</span><span class="sxs-lookup"><span data-stu-id="fa05f-259">Grouping</span></span>  
 <span data-ttu-id="fa05f-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)指定查詢所傳回物件的群組 ([選取](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) 運算式是要放置。</span><span class="sxs-lookup"><span data-stu-id="fa05f-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="fa05f-261">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="fa05f-262">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-262">Output:</span></span>  
  
|<span data-ttu-id="fa05f-263">name</span><span class="sxs-lookup"><span data-stu-id="fa05f-263">name</span></span>|  
|----------|  
|<span data-ttu-id="fa05f-264">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="fa05f-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="fa05f-265">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="fa05f-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="fa05f-266">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="fa05f-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="fa05f-267">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="fa05f-268">巡覽</span><span class="sxs-lookup"><span data-stu-id="fa05f-268">Navigation</span></span>  
 <span data-ttu-id="fa05f-269">關聯性巡覽運算子可以讓您在關聯性上從一個實體 (開始端) 巡覽到另一個實體 (結束端)。</span><span class="sxs-lookup"><span data-stu-id="fa05f-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="fa05f-270">[瀏覽](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)採用關聯性類型指定為\<命名空間 >。\<關聯性類型名稱 >。</span><span class="sxs-lookup"><span data-stu-id="fa05f-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="fa05f-271">瀏覽傳回 Ref\<T > 如果基數的結尾為 1。</span><span class="sxs-lookup"><span data-stu-id="fa05f-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="fa05f-272">如果基數的結尾為 n，集合 < Ref\<T >> 會傳回。</span><span class="sxs-lookup"><span data-stu-id="fa05f-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="fa05f-273">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="fa05f-274">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-274">Output:</span></span>  
  
|<span data-ttu-id="fa05f-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="fa05f-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="fa05f-276">1</span><span class="sxs-lookup"><span data-stu-id="fa05f-276">1</span></span>|  
|<span data-ttu-id="fa05f-277">2</span><span class="sxs-lookup"><span data-stu-id="fa05f-277">2</span></span>|  
|<span data-ttu-id="fa05f-278">3</span><span class="sxs-lookup"><span data-stu-id="fa05f-278">3</span></span>|  
|<span data-ttu-id="fa05f-279">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="fa05f-280">SELECT VALUE 和 SELECT</span><span class="sxs-lookup"><span data-stu-id="fa05f-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="fa05f-281">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="fa05f-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="fa05f-282"> 提供 SELECT VALUE 子句來略過隱含資料列建構。</span><span class="sxs-lookup"><span data-stu-id="fa05f-282"> provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="fa05f-283">SELECT VALUE 子句中可指定一個項目。</span><span class="sxs-lookup"><span data-stu-id="fa05f-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="fa05f-284">這類子句使用時，任何資料列包裝函式會不建構包含 SELECT 子句中的項目所需形狀的集合可以產生，例如： `SELECT VALUE a`。</span><span class="sxs-lookup"><span data-stu-id="fa05f-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="fa05f-285">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="fa05f-286">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-286">Output:</span></span>  
  
|<span data-ttu-id="fa05f-287">名稱</span><span class="sxs-lookup"><span data-stu-id="fa05f-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="fa05f-288">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="fa05f-288">Adjustable Race</span></span>|  
|<span data-ttu-id="fa05f-289">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="fa05f-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="fa05f-290">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="fa05f-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="fa05f-291">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="fa05f-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="fa05f-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="fa05f-293"> 也提供資料列建構函式來建構任意資料列。</span><span class="sxs-lookup"><span data-stu-id="fa05f-293"> also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="fa05f-294">SELECT 會擷取投影中的一個或多個項目，並且產生具有欄位的資料記錄，例如：`SELECT a, b, c`。</span><span class="sxs-lookup"><span data-stu-id="fa05f-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="fa05f-295">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-295">Example:</span></span>  
  
 <span data-ttu-id="fa05f-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="fa05f-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="fa05f-297">名稱</span><span class="sxs-lookup"><span data-stu-id="fa05f-297">Name</span></span>|<span data-ttu-id="fa05f-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="fa05f-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="fa05f-299">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="fa05f-299">Adjustable Race</span></span>|<span data-ttu-id="fa05f-300">1</span><span class="sxs-lookup"><span data-stu-id="fa05f-300">1</span></span>|  
|<span data-ttu-id="fa05f-301">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="fa05f-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="fa05f-302">879</span><span class="sxs-lookup"><span data-stu-id="fa05f-302">879</span></span>|  
|<span data-ttu-id="fa05f-303">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="fa05f-303">AWC Logo Cap</span></span>|<span data-ttu-id="fa05f-304">712</span><span class="sxs-lookup"><span data-stu-id="fa05f-304">712</span></span>|  
|<span data-ttu-id="fa05f-305">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-305">...</span></span>|<span data-ttu-id="fa05f-306">...</span><span class="sxs-lookup"><span data-stu-id="fa05f-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="fa05f-307">CASE 運算式</span><span class="sxs-lookup"><span data-stu-id="fa05f-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="fa05f-308">[Case 運算式](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)會評估一組布林運算式來得出結果。</span><span class="sxs-lookup"><span data-stu-id="fa05f-308">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="fa05f-309">範例：</span><span class="sxs-lookup"><span data-stu-id="fa05f-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="fa05f-310">輸出：</span><span class="sxs-lookup"><span data-stu-id="fa05f-310">Output:</span></span>  
  
|<span data-ttu-id="fa05f-311">值</span><span class="sxs-lookup"><span data-stu-id="fa05f-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="fa05f-312">true</span><span class="sxs-lookup"><span data-stu-id="fa05f-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa05f-313">請參閱</span><span class="sxs-lookup"><span data-stu-id="fa05f-313">See Also</span></span>  
 [<span data-ttu-id="fa05f-314">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="fa05f-314">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="fa05f-315">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="fa05f-315">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
