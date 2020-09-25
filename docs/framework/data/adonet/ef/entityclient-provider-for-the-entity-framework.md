---
title: Entity Framework 的 EntityClient 提供者
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: 9b3194e4a85eda6f405a3ab85723ac2cb9d00090
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181072"
---
# <a name="entityclient-provider-for-the-entity-framework"></a><span data-ttu-id="bffe6-102">Entity Framework 的 EntityClient 提供者</span><span class="sxs-lookup"><span data-stu-id="bffe6-102">EntityClient Provider for the Entity Framework</span></span>

<span data-ttu-id="bffe6-103">EntityClient 提供者是 Entity Framework 應用程式用來存取概念模型中所描述之資料的資料提供者。</span><span class="sxs-lookup"><span data-stu-id="bffe6-103">The EntityClient provider is a data provider used by Entity Framework applications to access data described in a conceptual model.</span></span> <span data-ttu-id="bffe6-104">如需概念模型的相關資訊，請參閱 [模型和對應](modeling-and-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="bffe6-104">For information about conceptual models, see [Modeling and Mapping](modeling-and-mapping.md).</span></span> <span data-ttu-id="bffe6-105">EntityClient 會使用其他 .NET Framework 資料提供者來存取資料來源。</span><span class="sxs-lookup"><span data-stu-id="bffe6-105">EntityClient uses other .NET Framework data providers to access the data source.</span></span> <span data-ttu-id="bffe6-106">例如，EntityClient 會在存取 SQL Server 資料庫時使用 .NET Framework Data Provider for SQL Server (SqlClient)。</span><span class="sxs-lookup"><span data-stu-id="bffe6-106">For example, EntityClient uses the .NET Framework Data Provider for SQL Server (SqlClient) when accessing a SQL Server database.</span></span> <span data-ttu-id="bffe6-107">如需 SqlClient 提供者的相關資訊，請參閱 [Entity Framework 的 SqlClient](sqlclient-for-the-entity-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="bffe6-107">For information about the SqlClient provider, see [SqlClient for the Entity Framework](sqlclient-for-the-entity-framework.md).</span></span> <span data-ttu-id="bffe6-108">EntityClient 提供者是在 <xref:System.Data.EntityClient> 命名空間 (Namespace) 中實作的。</span><span class="sxs-lookup"><span data-stu-id="bffe6-108">The EntityClient provider is implemented in the <xref:System.Data.EntityClient> namespace.</span></span>  
  
## <a name="managing-connections"></a><span data-ttu-id="bffe6-109">管理連接</span><span class="sxs-lookup"><span data-stu-id="bffe6-109">Managing Connections</span></span>  

 <span data-ttu-id="bffe6-110">Entity Framework 藉由提供 <xref:System.Data.EntityClient.EntityConnection> 給基礎資料提供者和關係資料庫，建立在儲存體專屬 ADO.NET 資料提供者之上。</span><span class="sxs-lookup"><span data-stu-id="bffe6-110">The Entity Framework builds on top of storage-specific ADO.NET data providers by providing an <xref:System.Data.EntityClient.EntityConnection> to an underlying data provider and relational database.</span></span> <span data-ttu-id="bffe6-111">若要建立 <xref:System.Data.EntityClient.EntityConnection> 物件，您必須參考一組包含必要模型和對應的中繼資料，以及儲存體專屬的資料提供者名稱和連接字串。</span><span class="sxs-lookup"><span data-stu-id="bffe6-111">To construct an <xref:System.Data.EntityClient.EntityConnection> object, you have to reference a set of metadata that contains the necessary models and mapping, and also a storage-specific data provider name and connection string.</span></span> <span data-ttu-id="bffe6-112"><xref:System.Data.EntityClient.EntityConnection>準備就緒之後，即可透過概念模型所產生的類別來存取實體。</span><span class="sxs-lookup"><span data-stu-id="bffe6-112">After the <xref:System.Data.EntityClient.EntityConnection> is in place, entities can be accessed through the classes generated from the conceptual model.</span></span>  
  
 <span data-ttu-id="bffe6-113">您可以在 app.config 檔案中指定連接字串。</span><span class="sxs-lookup"><span data-stu-id="bffe6-113">You can specify a connection string in app.config file.</span></span>  
  
 <span data-ttu-id="bffe6-114"><xref:System.Data.EntityClient> 也包含 <xref:System.Data.EntityClient.EntityConnectionStringBuilder> 類別。</span><span class="sxs-lookup"><span data-stu-id="bffe6-114">The <xref:System.Data.EntityClient> also includes the <xref:System.Data.EntityClient.EntityConnectionStringBuilder> class.</span></span> <span data-ttu-id="bffe6-115">這個類別可讓開發人員使用此類別的屬性和方法，以程式設計方式建立語法正確的連接字串，以及剖析和重建現有的連接字串。</span><span class="sxs-lookup"><span data-stu-id="bffe6-115">This class enables developers to programmatically create syntactically correct connection strings, and parse and rebuild existing connection strings, by using properties and methods of the class.</span></span> <span data-ttu-id="bffe6-116">如需詳細資訊，請參閱 [如何：建立 EntityConnection 連接字串](how-to-build-an-entityconnection-connection-string.md)。</span><span class="sxs-lookup"><span data-stu-id="bffe6-116">For more information, see [How to: Build an EntityConnection Connection String](how-to-build-an-entityconnection-connection-string.md).</span></span>  
  
## <a name="creating-queries"></a><span data-ttu-id="bffe6-117">建立查詢</span><span class="sxs-lookup"><span data-stu-id="bffe6-117">Creating Queries</span></span>  

 <span data-ttu-id="bffe6-118">此 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 語言是與儲存體無關的 SQL 方言，可直接與概念實體架構一起運作並支援實體資料模型的概念，例如繼承和關聯性。</span><span class="sxs-lookup"><span data-stu-id="bffe6-118">The [!INCLUDE[esql](../../../../../includes/esql-md.md)] language is a storage-independent dialect of SQL that works directly with conceptual entity schemas and supports Entity Data Model concepts such as inheritance and relationships.</span></span> <span data-ttu-id="bffe6-119"><xref:System.Data.EntityClient.EntityCommand>類別是用來 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 針對實體模型執行命令。</span><span class="sxs-lookup"><span data-stu-id="bffe6-119">The <xref:System.Data.EntityClient.EntityCommand> class is used to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] command against an entity model.</span></span> <span data-ttu-id="bffe6-120">建構 <xref:System.Data.EntityClient.EntityCommand> 物件時，您可以指定預存程序名稱或查詢文字。</span><span class="sxs-lookup"><span data-stu-id="bffe6-120">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or a query text.</span></span> <span data-ttu-id="bffe6-121">Entity Framework 適用于儲存體專屬的資料提供者，可將泛型轉譯為 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 儲存體專屬的查詢。</span><span class="sxs-lookup"><span data-stu-id="bffe6-121">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="bffe6-122">如需有關撰寫查詢的詳細資訊 [!INCLUDE[esql](../../../../../includes/esql-md.md)] ，請參閱 [Entity SQL 語言](./language-reference/entity-sql-language.md)。</span><span class="sxs-lookup"><span data-stu-id="bffe6-122">For more information about writing [!INCLUDE[esql](../../../../../includes/esql-md.md)] queries, see [Entity SQL Language](./language-reference/entity-sql-language.md).</span></span>  
  
 <span data-ttu-id="bffe6-123">下列範例會建立 <xref:System.Data.EntityClient.EntityCommand> 物件，並 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 將查詢文字指派給它的 <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="bffe6-123">The following example creates an <xref:System.Data.EntityClient.EntityCommand> object and assigns an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query text to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="bffe6-124">此 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢會要求從概念模型依標價排序的產品。</span><span class="sxs-lookup"><span data-stu-id="bffe6-124">This [!INCLUDE[esql](../../../../../includes/esql-md.md)] query requests products ordered by the list price from the conceptual model.</span></span> <span data-ttu-id="bffe6-125">下列程式碼完全不了解儲存模型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bffe6-125">The following code has no knowledge of the storage model at all.</span></span>  
  
 ```csharp
EntityCommand cmd = conn.CreateCommand();
cmd.CommandText = @"SELECT VALUE p
  FROM AdventureWorksEntities.Product AS p
  ORDER BY p.ListPrice";
```
  
## <a name="executing-queries"></a><span data-ttu-id="bffe6-126">執行查詢</span><span class="sxs-lookup"><span data-stu-id="bffe6-126">Executing Queries</span></span>  

 <span data-ttu-id="bffe6-127">執行查詢時，會先剖析查詢然後將它轉換成標準命令樹。</span><span class="sxs-lookup"><span data-stu-id="bffe6-127">When a query is executed, it is parsed and converted into a canonical command tree.</span></span> <span data-ttu-id="bffe6-128">所有後續的查詢處理都是在此命令樹上執行。</span><span class="sxs-lookup"><span data-stu-id="bffe6-128">All subsequent processing is performed on the command tree.</span></span> <span data-ttu-id="bffe6-129">命令樹是 <xref:System.Data.EntityClient> 和基礎 .NET Framework 資料提供者（例如）之間的通訊方式 <xref:System.Data.SqlClient> 。</span><span class="sxs-lookup"><span data-stu-id="bffe6-129">The command tree is the means of communication between the <xref:System.Data.EntityClient> and the underlying .NET Framework data provider, such as <xref:System.Data.SqlClient>.</span></span>  
  
 <span data-ttu-id="bffe6-130"><xref:System.Data.EntityClient.EntityDataReader> 會公開針對概念模型執行 <xref:System.Data.EntityClient.EntityCommand> 的結果。</span><span class="sxs-lookup"><span data-stu-id="bffe6-130">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against a conceptual model.</span></span> <span data-ttu-id="bffe6-131">若要執行可傳回 <xref:System.Data.EntityClient.EntityDataReader> 的命令，請呼叫 <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>。</span><span class="sxs-lookup"><span data-stu-id="bffe6-131">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span> <span data-ttu-id="bffe6-132"><xref:System.Data.EntityClient.EntityDataReader> 會實作 <xref:System.Data.IExtendedDataRecord> 來描述豐富的結構化結果。</span><span class="sxs-lookup"><span data-stu-id="bffe6-132">The <xref:System.Data.EntityClient.EntityDataReader> implements <xref:System.Data.IExtendedDataRecord> to describe rich structured results.</span></span>  
  
## <a name="managing-transactions"></a><span data-ttu-id="bffe6-133">管理交易</span><span class="sxs-lookup"><span data-stu-id="bffe6-133">Managing Transactions</span></span>  

 <span data-ttu-id="bffe6-134">Entity Framework 中有兩種使用異動的方式：自動與明確。</span><span class="sxs-lookup"><span data-stu-id="bffe6-134">In the Entity Framework, there are two ways to use transactions: automatic and explicit.</span></span> <span data-ttu-id="bffe6-135">自動交易會使用 <xref:System.Transactions> 命名空間，而明確交易會使用 <xref:System.Data.EntityClient.EntityTransaction> 類別。</span><span class="sxs-lookup"><span data-stu-id="bffe6-135">Automatic transactions use the <xref:System.Transactions> namespace, and explicit transactions use the <xref:System.Data.EntityClient.EntityTransaction> class.</span></span>  
  
 <span data-ttu-id="bffe6-136">若要更新透過概念模型公開的資料，請參閱 [如何：管理 Entity Framework 中的交易](/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="bffe6-136">To update data that is exposed through a conceptual model, see [How to: Manage Transactions in the Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bffe6-137">本節內容</span><span class="sxs-lookup"><span data-stu-id="bffe6-137">In This Section</span></span>  

 [<span data-ttu-id="bffe6-138">作法：建置 EntityCollection 連接字串</span><span class="sxs-lookup"><span data-stu-id="bffe6-138">How to: Build an EntityConnection Connection String</span></span>](how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="bffe6-139">作法：執行可傳回 PrimitiveType 結果的查詢</span><span class="sxs-lookup"><span data-stu-id="bffe6-139">How to: Execute a Query that Returns PrimitiveType Results</span></span>](how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="bffe6-140">作法：執行可傳回 StructuralType 結果的查詢</span><span class="sxs-lookup"><span data-stu-id="bffe6-140">How to: Execute a Query that Returns StructuralType Results</span></span>](how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="bffe6-141">作法：執行可傳回 RefType 結果的查詢</span><span class="sxs-lookup"><span data-stu-id="bffe6-141">How to: Execute a Query that Returns RefType Results</span></span>](how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="bffe6-142">作法：執行可傳回複雜類型的查詢</span><span class="sxs-lookup"><span data-stu-id="bffe6-142">How to: Execute a Query that Returns Complex Types</span></span>](how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="bffe6-143">作法：執行可傳回巢狀集合的查詢</span><span class="sxs-lookup"><span data-stu-id="bffe6-143">How to: Execute a Query that Returns Nested Collections</span></span>](how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="bffe6-144">作法：使用 EntityCommand 執行參數化 Entity SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="bffe6-144">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="bffe6-145">作法：使用 EntityCommand 執行參數化預存程序</span><span class="sxs-lookup"><span data-stu-id="bffe6-145">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="bffe6-146">作法：執行多型查詢</span><span class="sxs-lookup"><span data-stu-id="bffe6-146">How to: Execute a Polymorphic Query</span></span>](how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="bffe6-147">作法：使用 Navigate 運算子巡覽關聯性</span><span class="sxs-lookup"><span data-stu-id="bffe6-147">How to: Navigate Relationships with the Navigate Operator</span></span>](how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a><span data-ttu-id="bffe6-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bffe6-148">See also</span></span>

- <span data-ttu-id="bffe6-149">[管理連接和異動](/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bffe6-149">[Managing Connections and Transactions](/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))</span></span>
- [<span data-ttu-id="bffe6-150">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="bffe6-150">ADO.NET Entity Framework</span></span>](index.md)
- [<span data-ttu-id="bffe6-151">語言參考</span><span class="sxs-lookup"><span data-stu-id="bffe6-151">Language Reference</span></span>](./language-reference/index.md)
