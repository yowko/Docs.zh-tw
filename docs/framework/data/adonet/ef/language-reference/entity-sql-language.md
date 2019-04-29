---
title: Entity SQL 語言
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 09ec1a5518ec0847b54394449f32b3068c811577
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785186"
---
# <a name="entity-sql-language"></a><span data-ttu-id="10442-102">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="10442-102">Entity SQL Language</span></span>
<span data-ttu-id="10442-103">Entity SQL 是與儲存體無關的查詢語言，與 SQL 類似。</span><span class="sxs-lookup"><span data-stu-id="10442-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="10442-104">Entity SQL 可讓您查詢實體資料 (無論以物件形式或在表格式資料表中)。</span><span class="sxs-lookup"><span data-stu-id="10442-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="10442-105">在下列情況下，您可以考慮使用 Entity SQL：</span><span class="sxs-lookup"><span data-stu-id="10442-105">You should consider using Entity SQL in the following cases:</span></span>  
  
- <span data-ttu-id="10442-106">必須在執行階段動態建構查詢時。</span><span class="sxs-lookup"><span data-stu-id="10442-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="10442-107">在此情況下，您也可以考慮使用 <xref:System.Data.Objects.ObjectQuery%601> 的查詢產生器方法，而不在執行階段建構 Entity SQL 查詢字串。</span><span class="sxs-lookup"><span data-stu-id="10442-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
- <span data-ttu-id="10442-108">當您想要將查詢定義為模型定義的一部分時。</span><span class="sxs-lookup"><span data-stu-id="10442-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="10442-109">資料模型僅支援 Entity SQL。</span><span class="sxs-lookup"><span data-stu-id="10442-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="10442-110">如需詳細資訊，請參閱[QueryView 項目 (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="10442-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
- <span data-ttu-id="10442-111">使用 EntityClient 傳回唯讀實體資料，做為使用 <xref:System.Data.EntityClient.EntityDataReader> 的資料列集時。</span><span class="sxs-lookup"><span data-stu-id="10442-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="10442-112">如需詳細資訊，請參閱 < [Entity Framework 的 EntityClient 提供者](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="10442-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
- <span data-ttu-id="10442-113">如果您非常熟悉 SQL 查詢語言，對您來說，Entity SQL 可能最易於使用。</span><span class="sxs-lookup"><span data-stu-id="10442-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="10442-114">搭配 EntityClient 提供者使用 Entity SQL</span><span class="sxs-lookup"><span data-stu-id="10442-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="10442-115">如果您想要搭配 EntityClient 提供者使用 Entity SQL，請參閱下列主題取得詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="10442-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="10442-116">Entity Framework 的 EntityClient 提供者</span><span class="sxs-lookup"><span data-stu-id="10442-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="10442-117">如何：建置 Entitycollection 連接字串</span><span class="sxs-lookup"><span data-stu-id="10442-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="10442-118">如何：執行可傳回 PrimitiveType 結果的查詢</span><span class="sxs-lookup"><span data-stu-id="10442-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="10442-119">如何：執行可傳回 StructuralType 結果的查詢</span><span class="sxs-lookup"><span data-stu-id="10442-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="10442-120">如何：執行可傳回 RefType 結果的查詢</span><span class="sxs-lookup"><span data-stu-id="10442-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="10442-121">如何：執行可傳回複雜類型的查詢</span><span class="sxs-lookup"><span data-stu-id="10442-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="10442-122">如何：執行可傳回巢狀的集合的查詢</span><span class="sxs-lookup"><span data-stu-id="10442-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="10442-123">如何：使用 EntityCommand Entity SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="10442-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="10442-124">如何：執行參數化的預存程序，以使用 EntityCommand</span><span class="sxs-lookup"><span data-stu-id="10442-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="10442-125">如何：執行多型查詢</span><span class="sxs-lookup"><span data-stu-id="10442-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="10442-126">如何：使用巡覽關聯性巡覽運算子</span><span class="sxs-lookup"><span data-stu-id="10442-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="10442-127">搭配物件查詢使用 Entity SQL</span><span class="sxs-lookup"><span data-stu-id="10442-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="10442-128">如果您想要搭配物件查詢使用 Entity SQL，請參閱下列主題取得詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="10442-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 <span data-ttu-id="10442-129">[如何：執行可傳回實體類型集合的查詢](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10442-129">[How to: Execute a Query that Returns Entity Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span></span>  
  
 <span data-ttu-id="10442-130">[如何：執行參數化的查詢](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10442-130">[How to: Execute a Parameterized Query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>  
  
 <span data-ttu-id="10442-131">[如何：使用導覽屬性導覽關聯性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10442-131">[How to: Navigate Relationships Using Navigation Properties](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span></span>  
  
 <span data-ttu-id="10442-132">[如何：呼叫使用者定義函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10442-132">[How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span></span>  
  
 <span data-ttu-id="10442-133">[如何：篩選資料](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10442-133">[How to: Filter Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span></span>  
  
 <span data-ttu-id="10442-134">[如何：排序資料](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10442-134">[How to: Sort Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span></span>  
  
 <span data-ttu-id="10442-135">[如何：群組資料](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10442-135">[How to: Group Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span></span>  
  
 <span data-ttu-id="10442-136">[如何：彙總資料](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10442-136">[How to: Aggregate Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span></span>  
  
 <span data-ttu-id="10442-137">[如何：執行可傳回匿名類型集合的查詢](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10442-137">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>  
  
 <span data-ttu-id="10442-138">[如何：執行可傳回基本型別的集合的查詢](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10442-138">[How to: Execute a Query that Returns a Collection of Primitive Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span></span>  
  
 <span data-ttu-id="10442-139">[如何：EntityCollection 中查詢相關的物件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10442-139">[How to: Query Related Objects in an EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span></span>  
  
 <span data-ttu-id="10442-140">[如何：排序兩個查詢的聯集](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10442-140">[How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span></span>  
  
 <span data-ttu-id="10442-141">[如何：逐頁查看查詢結果](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10442-141">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10442-142">本節內容</span><span class="sxs-lookup"><span data-stu-id="10442-142">In This Section</span></span>  
 [<span data-ttu-id="10442-143">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="10442-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="10442-144">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="10442-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="10442-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10442-145">See also</span></span>

- [<span data-ttu-id="10442-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="10442-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
- [<span data-ttu-id="10442-147">語言參考</span><span class="sxs-lookup"><span data-stu-id="10442-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
