---
title: 適用於 Entity Framework 的 SqlClient 已知問題
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: 5c0b7c32e00a0cc90367a559a41f5a7ab59a33a4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251386"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a><span data-ttu-id="fc6d9-102">適用於 Entity Framework 的 SqlClient 已知問題</span><span class="sxs-lookup"><span data-stu-id="fc6d9-102">Known Issues in SqlClient for Entity Framework</span></span>
<span data-ttu-id="fc6d9-103">本節說明與 .NET Framework Data Provider for SQL Server (SqlClient) 相關的已知問題。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-103">This section describes known issues related to the .NET Framework Data Provider for SQL Server (SqlClient).</span></span>  
  
## <a name="trailing-spaces-in-string-functions"></a><span data-ttu-id="fc6d9-104">字串函式中的尾端空白</span><span class="sxs-lookup"><span data-stu-id="fc6d9-104">Trailing Spaces in String Functions</span></span>  
 <span data-ttu-id="fc6d9-105">SQL Server 會忽略字串值中的尾端空格。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-105">SQL Server ignores trailing spaces in string values.</span></span> <span data-ttu-id="fc6d9-106">因此，在字串中傳遞尾端空白會導致無法預期的結果，甚至產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-106">Therefore, passing trailing spaces in the string can lead to unpredictable results, even failures.</span></span>  
  
 <span data-ttu-id="fc6d9-107">如果您的字串中必須有尾端空格, 您應該考慮在結尾附加空白字元, 讓 SQL Server 不會修剪字串。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-107">If you have to have trailing spaces in your string, you should consider appending a white space character at the end, so that SQL Server does not trim the string.</span></span> <span data-ttu-id="fc6d9-108">如果尾端空白是不必要的，則應該在查詢管線中傳遞前先行修剪掉。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-108">If the trailing spaces are not required, they should be trimmed before they are passed down the query pipeline.</span></span>  
  
## <a name="right-function"></a><span data-ttu-id="fc6d9-109">RIGHT 函式</span><span class="sxs-lookup"><span data-stu-id="fc6d9-109">RIGHT Function</span></span>  
 <span data-ttu-id="fc6d9-110">如果將非 `null` 值傳遞做為第一個引數並將 0 傳遞做為第二個引數，成為 `RIGHT(nvarchar(max)`, 0`)` 或 `RIGHT(varchar(max)`, 0`)`，則會傳回 `NULL` 值，而非 `empty` 字串。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-110">If a non-`null` value is passed as a first argument and 0 is passed as a second argument to `RIGHT(nvarchar(max)`, 0`)` or `RIGHT(varchar(max)`, 0`)`, a `NULL` value will be returned instead of an `empty` string.</span></span>  
  
## <a name="cross-and-outer-apply-operators"></a><span data-ttu-id="fc6d9-111">CROSS 和 OUTER APPLY 運算子</span><span class="sxs-lookup"><span data-stu-id="fc6d9-111">CROSS and OUTER APPLY Operators</span></span>  
 <span data-ttu-id="fc6d9-112">CROSS 和 OUTER APPLY 運算子是在 SQL Server 2005 中引進。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-112">CROSS and OUTER APPLY operators were introduced in SQL Server 2005.</span></span> <span data-ttu-id="fc6d9-113">在某些案例中，查詢管線可能產生含有 CROSS APPLY 和 (或) OUTER APPLY 運算子的 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-113">In some cases the query pipeline might produce a Transact-SQL statement that contains CROSS APPLY and/or OUTER APPLY operators.</span></span> <span data-ttu-id="fc6d9-114">因為有些後端提供者 (包括早于 SQL Server 2005 的 SQL Server 版本) 不支援這些運算子, 所以無法在這些後端提供者上執行這類查詢。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-114">Because some backend providers, including versions of SQL Server earlier than SQL Server 2005, do not support these operators, such queries cannot be executed on these backend providers.</span></span>  
  
 <span data-ttu-id="fc6d9-115">下列是可能會導致輸出查詢中出現 CROSS APPLY 和 (或) OUTER APPLY 運算子的部分典型案例：</span><span class="sxs-lookup"><span data-stu-id="fc6d9-115">The following are some typical scenarios that might lead to the presence of CROSS APPLY and/or OUTER APPLY operators in the output query:</span></span>  
  
- <span data-ttu-id="fc6d9-116">具有分頁的相互關聯子查詢。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-116">A correlated subquery with paging.</span></span>  
  
- <span data-ttu-id="fc6d9-117">相互關聯子查詢或巡覽產生的集合上的 `AnyElement`。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-117">An `AnyElement` over a correlated sub-query, or over a collection produced by navigation.</span></span>  
  
- <span data-ttu-id="fc6d9-118">使用接受元素選擇器的群組方法的 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-118">LINQ queries that use grouping methods that accept an element selector.</span></span>  
  
- <span data-ttu-id="fc6d9-119">當中有明確指定 CROSS APPLY 或 OUTER APPLY 的查詢。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-119">A query in which a CROSS APPLY or an OUTER APPLY is explicitly specified</span></span>  
  
- <span data-ttu-id="fc6d9-120">具有 DEREF 建構對 REF 建構的查詢。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-120">A query that has a DEREF construct over a REF construct.</span></span>  
  
## <a name="skip-operator"></a><span data-ttu-id="fc6d9-121">SKIP 運算子</span><span class="sxs-lookup"><span data-stu-id="fc6d9-121">SKIP Operator</span></span>  
 <span data-ttu-id="fc6d9-122">如果您使用 SQL Server 2000, 則在非索引鍵資料行上使用 SKIP 搭配 ORDER BY 可能會傳回不正確的結果。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-122">If you are using SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="fc6d9-123">如果非索引鍵資料行中有重複的資料，可能會略過超過所指定數目的資料行。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-123">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="fc6d9-124">這是因為 SQL Server 2000 的略過轉譯方式所致。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-124">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="fc6d9-125">例如, 在下列查詢中, 如果有重複的值, 則`E.NonKeyColumn`可能會略過超過五個數據列:</span><span class="sxs-lookup"><span data-stu-id="fc6d9-125">For example, in the following query, more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a><span data-ttu-id="fc6d9-126">以正確的 SQL Server 版本為目標</span><span class="sxs-lookup"><span data-stu-id="fc6d9-126">Targeting the Correct SQL Server Version</span></span>  
 <span data-ttu-id="fc6d9-127">會根據儲存模型 (ssdl) 檔案中 Schema 元素的`ProviderManifestToken`屬性所指定的 SQL Server 版本, 以 transact-SQL 查詢為目標。[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc6d9-127">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] targets the Transact-SQL query based on the SQL Server version that is specified in the `ProviderManifestToken` attribute of the Schema element in the storage model (.ssdl) file.</span></span> <span data-ttu-id="fc6d9-128">這個版本可能會因您所連接的 SQL Server 實際版本而有所不同。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-128">This version might differ from the version of the actual SQL Server you are connected to.</span></span> <span data-ttu-id="fc6d9-129">例如, 如果您使用 SQL Server 2005, 但您`ProviderManifestToken`的屬性設定為 2008, 則產生的 transact-SQL 查詢可能無法在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-129">For example, if you are using SQL Server 2005, but your `ProviderManifestToken` attribute is set to 2008, the generated Transact-SQL query might not execute on the server.</span></span> <span data-ttu-id="fc6d9-130">例如, 使用在 SQL Server 2008 中引進之新日期時間類型的查詢, 將不會在舊版的 SQL Server 上執行。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-130">For example, a query that uses the new date time types that were introduced in SQL Server 2008 will not execute on earlier versions of the SQL Server.</span></span> <span data-ttu-id="fc6d9-131">如果您使用 SQL Server 2005, 但您`ProviderManifestToken`的屬性設定為 2000, 則產生的 transact-SQL 查詢可能較不優化, 或者您可能會收到例外狀況, 指出不支援該查詢。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-131">If you are using SQL Server 2005, but your `ProviderManifestToken` attribute is set to 2000, the generated Transact-SQL query might be less optimized, or you might get an exception that says that the query is not supported.</span></span> <span data-ttu-id="fc6d9-132">如需詳細資訊，請參閱本主題前面的「CROSS 和 OUTER APPLY 運算子」一節。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-132">For more information, see the CROSS and OUTER APPLY Operators section, earlier in this topic.</span></span>  
  
 <span data-ttu-id="fc6d9-133">某些資料庫行為取決於資料庫上設定的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-133">Certain database behaviors depend on the compatibility level set to the database.</span></span> <span data-ttu-id="fc6d9-134">如果您`ProviderManifestToken`的屬性設定為 2005, 而您的 SQL Server 版本是 2005, 但資料庫的相容性層級設定為 "80" (SQL Server 2000), 則產生的 transact-sql 將以 SQL Server 的2005為目標, 但可能不會如預期般執行, 因為相容性層級設定。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-134">If your `ProviderManifestToken` attribute is set to 2005 and your SQL Server version is 2005, but the compatibility level of a database is set to "80" (SQL Server 2000), the generated Transact-SQL will be targeting SQL Server 2005, but might not execute as expected due to the compatibility level setting.</span></span> <span data-ttu-id="fc6d9-135">例如，當 ORDER BY 清單中資料行名稱與選擇器中資料行名稱相符合時，則可能會遺失排序資訊。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-135">For example, you might lose ordering information if a column name in the ORDER BY list matches a column name in the selector.</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="fc6d9-136">投影中的巢狀查詢</span><span class="sxs-lookup"><span data-stu-id="fc6d9-136">Nested Queries in Projection</span></span>  
 <span data-ttu-id="fc6d9-137">投影子句中的巢狀查詢可能會在伺服器上轉譯成笛卡兒乘積 (Cartesian Product) 查詢。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-137">Nested queries in a projection clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="fc6d9-138">在某些後端伺服器 (包括 SLQ 伺服器) 上, 這可能會導致 TempDB 資料表變得相當大。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-138">On some back-end servers, including SLQ Server, this can cause the TempDB table to get quite large.</span></span> <span data-ttu-id="fc6d9-139">這樣會降低伺服器的效能。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-139">This can decrease server performance.</span></span>  
  
 <span data-ttu-id="fc6d9-140">下列是投影子句中巢狀查詢的範例：</span><span class="sxs-lookup"><span data-stu-id="fc6d9-140">The following is an example of  a nested query in a projection clause:</span></span>  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a><span data-ttu-id="fc6d9-141">伺服器產生的 GUID 識別值</span><span class="sxs-lookup"><span data-stu-id="fc6d9-141">Server Generated GUID Identity Values</span></span>  
 <span data-ttu-id="fc6d9-142">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 支援伺服器產生的 GUID 識別值，但是提供者必須支援在資插入資料列之後，傳回伺服器產生的識別值。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-142">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] supports server-generated GUID type identity values, but the provider must support returning the server-generated identity value after a row was inserted.</span></span> <span data-ttu-id="fc6d9-143">從 SQL Server 2005 開始, 您可以透過[OUTPUT 子句](https://go.microsoft.com/fwlink/?LinkId=169400), 在 SQL Server 資料庫中傳回伺服器產生的 GUID 型別。</span><span class="sxs-lookup"><span data-stu-id="fc6d9-143">Starting with SQL Server 2005, you can return the server-generated GUID type in a SQL Server database through the [OUTPUT clause](https://go.microsoft.com/fwlink/?LinkId=169400) .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc6d9-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc6d9-144">See also</span></span>

- [<span data-ttu-id="fc6d9-145">適用於 Entity Framework 的 SqlClient</span><span class="sxs-lookup"><span data-stu-id="fc6d9-145">SqlClient for the Entity Framework</span></span>](sqlclient-for-the-entity-framework.md)
- [<span data-ttu-id="fc6d9-146">LINQ to Entities 中的已知問題和考量</span><span class="sxs-lookup"><span data-stu-id="fc6d9-146">Known Issues and Considerations in LINQ to Entities</span></span>](./language-reference/known-issues-and-considerations-in-linq-to-entities.md)
