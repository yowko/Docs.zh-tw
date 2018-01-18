---
title: "Entity SQL 語言"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1618ff37ffd2b25140196a42d49d5a01f7e9da90
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="entity-sql-language"></a><span data-ttu-id="0c485-102">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="0c485-102">Entity SQL Language</span></span>
<span data-ttu-id="0c485-103">Entity SQL 是與儲存體無關的查詢語言，與 SQL 類似。</span><span class="sxs-lookup"><span data-stu-id="0c485-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="0c485-104">Entity SQL 可讓您查詢實體資料 (無論以物件形式或在表格式資料表中)。</span><span class="sxs-lookup"><span data-stu-id="0c485-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="0c485-105">在下列情況下，您可以考慮使用 Entity SQL：</span><span class="sxs-lookup"><span data-stu-id="0c485-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="0c485-106">必須在執行階段動態建構查詢時。</span><span class="sxs-lookup"><span data-stu-id="0c485-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="0c485-107">在此情況下，您也可以考慮使用 <xref:System.Data.Objects.ObjectQuery%601> 的查詢產生器方法，而不在執行階段建構 Entity SQL 查詢字串。</span><span class="sxs-lookup"><span data-stu-id="0c485-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="0c485-108">當您想要將查詢定義為模型定義的一部分時。</span><span class="sxs-lookup"><span data-stu-id="0c485-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="0c485-109">資料模型僅支援 Entity SQL。</span><span class="sxs-lookup"><span data-stu-id="0c485-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="0c485-110">如需詳細資訊，請參閱[QueryView 元素 (MSL)](http://msdn.microsoft.com/en-us/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span><span class="sxs-lookup"><span data-stu-id="0c485-110">For more information, see [QueryView Element (MSL)](http://msdn.microsoft.com/en-us/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span></span>  
  
-   <span data-ttu-id="0c485-111">使用 EntityClient 傳回唯讀實體資料，做為使用 <xref:System.Data.EntityClient.EntityDataReader> 的資料列集時。</span><span class="sxs-lookup"><span data-stu-id="0c485-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="0c485-112">如需詳細資訊，請參閱[Entity Framework 的 EntityClient 提供者](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="0c485-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="0c485-113">如果您非常熟悉 SQL 查詢語言，對您來說，Entity SQL 可能最易於使用。</span><span class="sxs-lookup"><span data-stu-id="0c485-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="0c485-114">搭配 EntityClient 提供者使用 Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0c485-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="0c485-115">如果您想要搭配 EntityClient 提供者使用 Entity SQL，請參閱下列主題取得詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="0c485-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="0c485-116">Entity Framework 的 EntityClient 提供者</span><span class="sxs-lookup"><span data-stu-id="0c485-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="0c485-117">如何：建置 EntityCollection 連接字串</span><span class="sxs-lookup"><span data-stu-id="0c485-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="0c485-118">如何：執行可傳回 PrimitiveType 結果的查詢</span><span class="sxs-lookup"><span data-stu-id="0c485-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="0c485-119">如何：執行可傳回 StructuralType 結果的查詢</span><span class="sxs-lookup"><span data-stu-id="0c485-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="0c485-120">如何：執行可傳回 RefType 結果的查詢</span><span class="sxs-lookup"><span data-stu-id="0c485-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="0c485-121">如何：執行可傳回複雜類型的查詢</span><span class="sxs-lookup"><span data-stu-id="0c485-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="0c485-122">如何：執行可傳回巢狀集合的查詢</span><span class="sxs-lookup"><span data-stu-id="0c485-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="0c485-123">如何：使用 EntityCommand 執行參數化 Entity SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="0c485-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="0c485-124">如何：使用 EntityCommand 執行參數化預存程序</span><span class="sxs-lookup"><span data-stu-id="0c485-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="0c485-125">如何：執行多型查詢</span><span class="sxs-lookup"><span data-stu-id="0c485-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="0c485-126">如何：使用 Navigate 運算子導覽關聯性 </span><span class="sxs-lookup"><span data-stu-id="0c485-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="0c485-127">搭配物件查詢使用 Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0c485-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="0c485-128">如果您想要搭配物件查詢使用 Entity SQL，請參閱下列主題取得詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="0c485-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="0c485-129">如何： 執行可傳回實體類型物件的查詢</span><span class="sxs-lookup"><span data-stu-id="0c485-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](http://msdn.microsoft.com/en-us/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [<span data-ttu-id="0c485-130">如何： 執行參數化的查詢</span><span class="sxs-lookup"><span data-stu-id="0c485-130">How to: Execute a Parameterized Query</span></span>](http://msdn.microsoft.com/en-us/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [<span data-ttu-id="0c485-131">如何： 巡覽關聯性使用導覽屬性</span><span class="sxs-lookup"><span data-stu-id="0c485-131">How to: Navigate Relationships Using Navigation Properties</span></span>](http://msdn.microsoft.com/en-us/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [<span data-ttu-id="0c485-132">如何： 呼叫使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="0c485-132">How to: Call a User-Defined Function</span></span>](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [<span data-ttu-id="0c485-133">如何： 篩選資料</span><span class="sxs-lookup"><span data-stu-id="0c485-133">How to: Filter Data</span></span>](http://msdn.microsoft.com/en-us/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [<span data-ttu-id="0c485-134">如何： 排序資料</span><span class="sxs-lookup"><span data-stu-id="0c485-134">How to: Sort Data</span></span>](http://msdn.microsoft.com/en-us/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [<span data-ttu-id="0c485-135">如何： 分組資料</span><span class="sxs-lookup"><span data-stu-id="0c485-135">How to: Group Data</span></span>](http://msdn.microsoft.com/en-us/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [<span data-ttu-id="0c485-136">如何： 彙總資料</span><span class="sxs-lookup"><span data-stu-id="0c485-136">How to: Aggregate Data</span></span>](http://msdn.microsoft.com/en-us/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [<span data-ttu-id="0c485-137">如何： 執行可傳回匿名型別物件的查詢</span><span class="sxs-lookup"><span data-stu-id="0c485-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](http://msdn.microsoft.com/en-us/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [<span data-ttu-id="0c485-138">如何： 執行可傳回基本型別的集合的查詢</span><span class="sxs-lookup"><span data-stu-id="0c485-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](http://msdn.microsoft.com/en-us/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [<span data-ttu-id="0c485-139">如何： 查詢相關的物件的 EntityCollection</span><span class="sxs-lookup"><span data-stu-id="0c485-139">How to: Query Related Objects in an EntityCollection</span></span>](http://msdn.microsoft.com/en-us/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [<span data-ttu-id="0c485-140">如何： 排序兩個查詢的 Union</span><span class="sxs-lookup"><span data-stu-id="0c485-140">How to: Order the Union of Two Queries</span></span>](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313)  
  
 [<span data-ttu-id="0c485-141">如何： 逐頁檢視查詢結果</span><span class="sxs-lookup"><span data-stu-id="0c485-141">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a><span data-ttu-id="0c485-142">本節內容</span><span class="sxs-lookup"><span data-stu-id="0c485-142">In This Section</span></span>  
 [<span data-ttu-id="0c485-143">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="0c485-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="0c485-144">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="0c485-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="0c485-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="0c485-145">See Also</span></span>  
 [<span data-ttu-id="0c485-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="0c485-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [<span data-ttu-id="0c485-147">語言參考</span><span class="sxs-lookup"><span data-stu-id="0c485-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
