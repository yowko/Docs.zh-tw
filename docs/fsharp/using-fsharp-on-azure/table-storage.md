---
title: 開始使用 Azure 資料表儲存體使用F#
description: 使用 Azure 資料表儲存體或 Azure Cosmos DB 在雲端中儲存結構化的資料。
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 54c777acd454e4f675175b814675c185e41ad9a4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086698"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="14a38-103">開始使用 Azure 資料表儲存體和 Azure Cosmos DB 資料表 API 使用 F\#</span><span class="sxs-lookup"><span data-stu-id="14a38-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F\#</span></span>

<span data-ttu-id="14a38-104">Azure 資料表儲存體是一項服務，將結構化的 NoSQL 資料儲存在雲端中。</span><span class="sxs-lookup"><span data-stu-id="14a38-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="14a38-105">資料表儲存體是具有無結構描述設計的索引鍵/屬性存放區。</span><span class="sxs-lookup"><span data-stu-id="14a38-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="14a38-106">資料表儲存體沒有結構描述，因為很容易就能隨著應用程式發展需求改寫資料。</span><span class="sxs-lookup"><span data-stu-id="14a38-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="14a38-107">快速且符合成本效益的所有類型的應用程式資料的存取。</span><span class="sxs-lookup"><span data-stu-id="14a38-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="14a38-108">資料表儲存體通常是大幅降低成本比傳統 SQL 類似的磁碟區的資料。</span><span class="sxs-lookup"><span data-stu-id="14a38-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="14a38-109">您可以使用資料表儲存體來儲存具彈性的資料集，例如 web 應用程式、 通訊錄、 裝置的詳細資訊和任何其他類型的服務所需的中繼資料的使用者資料。</span><span class="sxs-lookup"><span data-stu-id="14a38-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="14a38-110">您可以在資料表中，儲存任意數目的實體和儲存體帳戶可能包含任意數目的資料表，最大容量限制的儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="14a38-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="14a38-111">Azure Cosmos DB 會提供資料表 API 應用程式，會寫入 Azure 表格儲存體及所需要進階功能，例如：</span><span class="sxs-lookup"><span data-stu-id="14a38-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="14a38-112">周全的全域散發。</span><span class="sxs-lookup"><span data-stu-id="14a38-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="14a38-113">全球有專用的輸送量。</span><span class="sxs-lookup"><span data-stu-id="14a38-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="14a38-114">99 百分位數的個位數毫秒延遲。</span><span class="sxs-lookup"><span data-stu-id="14a38-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="14a38-115">保證高可用性。</span><span class="sxs-lookup"><span data-stu-id="14a38-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="14a38-116">自動的次要索引。</span><span class="sxs-lookup"><span data-stu-id="14a38-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="14a38-117">針對 Azure 資料表儲存體所撰寫的應用程式可以使用資料表 API 不必變更程式碼移轉至 Azure Cosmos DB，並利用進階功能。</span><span class="sxs-lookup"><span data-stu-id="14a38-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="14a38-118">「 資料表 API 具有.NET、 Java、 Python 和 Node.js 用戶端 Sdk 提供。</span><span class="sxs-lookup"><span data-stu-id="14a38-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="14a38-119">如需詳細資訊，請參閱 < [Azure Cosmos DB 資料表 API 簡介](https://docs.microsoft.com/azure/cosmos-db/table-introduction)。</span><span class="sxs-lookup"><span data-stu-id="14a38-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="14a38-120">關於本教學課程</span><span class="sxs-lookup"><span data-stu-id="14a38-120">About this tutorial</span></span>

<span data-ttu-id="14a38-121">本教學課程示範如何撰寫F#如何使用 Azure 資料表儲存體或 Azure Cosmos DB 資料表 API，包括建立和刪除資料表並插入、 更新、 刪除和查詢資料表資料的一些常見工作的程式碼。</span><span class="sxs-lookup"><span data-stu-id="14a38-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="14a38-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="14a38-122">Prerequisites</span></span>

<span data-ttu-id="14a38-123">若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)或是[Azure Cosmos DB 帳戶](https://azure.microsoft.com/try/cosmosdb/)。</span><span class="sxs-lookup"><span data-stu-id="14a38-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="14a38-124">建立F#指令碼，然後啟動F#互動</span><span class="sxs-lookup"><span data-stu-id="14a38-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="14a38-125">這篇文章中的範例可以用於在F#應用程式或F#指令碼。</span><span class="sxs-lookup"><span data-stu-id="14a38-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="14a38-126">若要建立F#指令碼，建立的檔案`.fsx`擴充功能，例如`tables.fsx`，請在您F#開發環境。</span><span class="sxs-lookup"><span data-stu-id="14a38-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="14a38-127">接下來，使用[套件管理員](package-management.md)這類[Paket](https://fsprojects.github.io/Paket/)或是[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`封裝和參考`WindowsAzure.Storage.dll`使用指令碼中`#r`指示詞。</span><span class="sxs-lookup"><span data-stu-id="14a38-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="14a38-128">請勿重新`Microsoft.WindowsAzure.ConfigurationManager`才能取得 Microsoft.Azure 命名空間。</span><span class="sxs-lookup"><span data-stu-id="14a38-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="14a38-129">加入命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="14a38-129">Add namespace declarations</span></span>

<span data-ttu-id="14a38-130">新增下列`open`陳述式的`tables.fsx`檔案：</span><span class="sxs-lookup"><span data-stu-id="14a38-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="14a38-131">取得 Azure 儲存體連接字串</span><span class="sxs-lookup"><span data-stu-id="14a38-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="14a38-132">如果您要連線到 Azure 儲存體表格服務，您必須將連接字串在本教學課程。</span><span class="sxs-lookup"><span data-stu-id="14a38-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="14a38-133">您可以從 Azure 入口網站複製您的連接字串。</span><span class="sxs-lookup"><span data-stu-id="14a38-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="14a38-134">如需有關連接字串的詳細資訊，請參閱 <<c0> [ 設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="14a38-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="14a38-135">取得 Azure Cosmos DB 連接字串</span><span class="sxs-lookup"><span data-stu-id="14a38-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="14a38-136">如果您要連線到 Azure Cosmos DB，您必須將連接字串在本教學課程。</span><span class="sxs-lookup"><span data-stu-id="14a38-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="14a38-137">您可以從 Azure 入口網站複製您的連接字串。</span><span class="sxs-lookup"><span data-stu-id="14a38-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="14a38-138">在 Azure 入口網站中，在 Cosmos DB 帳戶中，移至**設定** > **連接字串**，然後按一下**複製**按鈕以複製主要的連線字串。</span><span class="sxs-lookup"><span data-stu-id="14a38-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="14a38-139">教學課程中，輸入您的連接字串中您的指令碼，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="14a38-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="14a38-140">不過，這是**不建議使用**實際的專案。</span><span class="sxs-lookup"><span data-stu-id="14a38-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="14a38-141">儲存體帳戶金鑰很類似儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="14a38-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="14a38-142">請務必小心保護您的儲存體帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="14a38-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="14a38-143">請避免轉發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。</span><span class="sxs-lookup"><span data-stu-id="14a38-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="14a38-144">您可以重新產生您使用 Azure 入口網站，如果您認為可能已遭盜用的金鑰。</span><span class="sxs-lookup"><span data-stu-id="14a38-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="14a38-145">實際的應用程式，來維護您的儲存體連接字串的最佳方式是在組態檔中。</span><span class="sxs-lookup"><span data-stu-id="14a38-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="14a38-146">若要從組態檔擷取連接字串，您可以這樣做：</span><span class="sxs-lookup"><span data-stu-id="14a38-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="14a38-147">使用 Azure Configuration Manager 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="14a38-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="14a38-148">您也可以使用 API，例如.NET Framework 的`ConfigurationManager`型別。</span><span class="sxs-lookup"><span data-stu-id="14a38-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="14a38-149">剖析連接字串</span><span class="sxs-lookup"><span data-stu-id="14a38-149">Parse the connection string</span></span>

<span data-ttu-id="14a38-150">若要剖析的連接字串，請使用：</span><span class="sxs-lookup"><span data-stu-id="14a38-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="14a38-151">這會傳回`CloudStorageAccount`。</span><span class="sxs-lookup"><span data-stu-id="14a38-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="14a38-152">建立表格服務用戶端</span><span class="sxs-lookup"><span data-stu-id="14a38-152">Create the Table service client</span></span>

<span data-ttu-id="14a38-153">`CloudTableClient`類別可讓您擷取資料表和資料表儲存體中的實體。</span><span class="sxs-lookup"><span data-stu-id="14a38-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="14a38-154">若要建立服務用戶端的其中一個方法如下：</span><span class="sxs-lookup"><span data-stu-id="14a38-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="14a38-155">現在您已準備好撰寫程式碼來讀取資料，並將資料寫入資料表儲存體。</span><span class="sxs-lookup"><span data-stu-id="14a38-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="14a38-156">建立資料表</span><span class="sxs-lookup"><span data-stu-id="14a38-156">Create a table</span></span>

<span data-ttu-id="14a38-157">此範例示範如何建立資料表，如果不存在：</span><span class="sxs-lookup"><span data-stu-id="14a38-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="14a38-158">將實體新增至資料表</span><span class="sxs-lookup"><span data-stu-id="14a38-158">Add an entity to a table</span></span>

<span data-ttu-id="14a38-159">實體必須具有型別繼承自`TableEntity`。</span><span class="sxs-lookup"><span data-stu-id="14a38-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="14a38-160">您可以延伸`TableEntity`各種方式，但您的型別*必須*具有無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="14a38-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="14a38-161">同時具有的屬性`get`和`set`會儲存在您的 Azure 資料表。</span><span class="sxs-lookup"><span data-stu-id="14a38-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="14a38-162">實體的資料分割和資料列索引鍵可唯一識別資料表中的實體。</span><span class="sxs-lookup"><span data-stu-id="14a38-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="14a38-163">可在速度快於不同的資料分割索引鍵，查詢具有相同的資料分割索引鍵的實體，但使用不同的資料分割索引鍵可提供更佳的延展性的平行作業。</span><span class="sxs-lookup"><span data-stu-id="14a38-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="14a38-164">以下是範例`Customer`使用`lastName`做為資料分割索引鍵和`firstName`做為資料列索引鍵。</span><span class="sxs-lookup"><span data-stu-id="14a38-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="14a38-165">現在加入`Customer`至資料表。</span><span class="sxs-lookup"><span data-stu-id="14a38-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="14a38-166">若要這樣做，請建立`TableOperation`資料表上執行。</span><span class="sxs-lookup"><span data-stu-id="14a38-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="14a38-167">在此案例中，您建立`Insert`作業。</span><span class="sxs-lookup"><span data-stu-id="14a38-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="14a38-168">插入實體批次</span><span class="sxs-lookup"><span data-stu-id="14a38-168">Insert a batch of entities</span></span>

<span data-ttu-id="14a38-169">您可以將一批實體插入資料表中使用單一寫入作業。</span><span class="sxs-lookup"><span data-stu-id="14a38-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="14a38-170">批次作業可讓您將作業結合成單一的執行，但是它們有一些限制：</span><span class="sxs-lookup"><span data-stu-id="14a38-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="14a38-171">您可以執行更新、 刪除和插入相同的批次作業中。</span><span class="sxs-lookup"><span data-stu-id="14a38-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="14a38-172">批次作業可以包含最多 100 個實體。</span><span class="sxs-lookup"><span data-stu-id="14a38-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="14a38-173">批次作業中的所有實體必須都具有相同的資料分割索引鍵。</span><span class="sxs-lookup"><span data-stu-id="14a38-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="14a38-174">雖然您可以在批次作業中執行查詢，它必須是批次中唯一的作業。</span><span class="sxs-lookup"><span data-stu-id="14a38-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="14a38-175">以下是一些結合成一個批次作業的兩個插入的程式碼：</span><span class="sxs-lookup"><span data-stu-id="14a38-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="14a38-176">擷取資料分割中的所有實體</span><span class="sxs-lookup"><span data-stu-id="14a38-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="14a38-177">若要查詢資料表的資料分割中的所有實體，請使用`TableQuery`物件。</span><span class="sxs-lookup"><span data-stu-id="14a38-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="14a38-178">在這裡，您篩選實體"Smith"所在的資料分割索引鍵。</span><span class="sxs-lookup"><span data-stu-id="14a38-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="14a38-179">您現在會列印結果：</span><span class="sxs-lookup"><span data-stu-id="14a38-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="14a38-180">擷取範圍的資料分割中的實體</span><span class="sxs-lookup"><span data-stu-id="14a38-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="14a38-181">如果您不想要查詢資料分割中的所有實體，您可以藉由結合資料分割索引鍵篩選器與資料列索引鍵篩選器來指定範圍。</span><span class="sxs-lookup"><span data-stu-id="14a38-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="14a38-182">在這裡，您使用兩個篩選器來取得"Smith"資料分割中的所有實體資料列索引鍵 （名字） 開始的位置以字母"M"字母之前。</span><span class="sxs-lookup"><span data-stu-id="14a38-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="14a38-183">您現在會列印結果：</span><span class="sxs-lookup"><span data-stu-id="14a38-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="14a38-184">擷取單一實體</span><span class="sxs-lookup"><span data-stu-id="14a38-184">Retrieve a single entity</span></span>

<span data-ttu-id="14a38-185">您可以撰寫查詢來擷取單一特定實體。</span><span class="sxs-lookup"><span data-stu-id="14a38-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="14a38-186">在這裡，您使用`TableOperation`來指定客戶"Ben Smith"。</span><span class="sxs-lookup"><span data-stu-id="14a38-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="14a38-187">而不是集合中，您會回到`Customer`。</span><span class="sxs-lookup"><span data-stu-id="14a38-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="14a38-188">在查詢中指定資料分割索引鍵和資料列索引鍵是最快的方法，從資料表服務中擷取單一實體。</span><span class="sxs-lookup"><span data-stu-id="14a38-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="14a38-189">您現在會列印結果：</span><span class="sxs-lookup"><span data-stu-id="14a38-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a><span data-ttu-id="14a38-190">取代實體</span><span class="sxs-lookup"><span data-stu-id="14a38-190">Replace an entity</span></span>

<span data-ttu-id="14a38-191">若要更新實體，從資料表服務中擷取、 修改實體物件，和接著將變更儲存回資料表服務會使用`Replace`作業。</span><span class="sxs-lookup"><span data-stu-id="14a38-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="14a38-192">除非伺服器上的實體自擷取後，在此情況下作業將會失敗，已變更，這樣會完全取代伺服器上的實體。</span><span class="sxs-lookup"><span data-stu-id="14a38-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="14a38-193">此失敗是為了防止您的應用程式不小心覆寫從其他來源的變更。</span><span class="sxs-lookup"><span data-stu-id="14a38-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="14a38-194">插入或取代實體</span><span class="sxs-lookup"><span data-stu-id="14a38-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="14a38-195">有時候，您不知道實體是否存在於資料表中。</span><span class="sxs-lookup"><span data-stu-id="14a38-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="14a38-196">如果有的話，不再需要儲存在它的目前值。</span><span class="sxs-lookup"><span data-stu-id="14a38-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="14a38-197">您可以使用`InsertOrReplace`建立實體，或取代它，若有的話，不論其狀態。</span><span class="sxs-lookup"><span data-stu-id="14a38-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="14a38-198">查詢實體屬性的子集</span><span class="sxs-lookup"><span data-stu-id="14a38-198">Query a subset of entity properties</span></span>

<span data-ttu-id="14a38-199">資料表查詢可以擷取而不是所有的這些實體的少數屬性。</span><span class="sxs-lookup"><span data-stu-id="14a38-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="14a38-200">這項技巧，稱為 「 投射 」 可改善查詢效能，尤其是對大型實體。</span><span class="sxs-lookup"><span data-stu-id="14a38-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="14a38-201">在這裡，您可以傳回只有電子郵件地址使用`DynamicTableEntity`和`EntityResolver`。</span><span class="sxs-lookup"><span data-stu-id="14a38-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="14a38-202">請注意，投射不支援在本機儲存體模擬器中，讓您在資料表服務上使用的帳戶時，才執行此程式碼。</span><span class="sxs-lookup"><span data-stu-id="14a38-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="14a38-203">以非同步方式擷取頁面中的實體</span><span class="sxs-lookup"><span data-stu-id="14a38-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="14a38-204">如果您正在閱讀大量實體，而且您想要擷取這些，而非等待它們全部傳回，您可以使用分割的查詢時進行處理。</span><span class="sxs-lookup"><span data-stu-id="14a38-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="14a38-205">在這裡，您傳回的結果頁面中所使用的非同步工作流程，如此一來，您於等待的一大組要傳回的結果時，不會封鎖執行。</span><span class="sxs-lookup"><span data-stu-id="14a38-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="14a38-206">您現在執行這項計算以同步方式：</span><span class="sxs-lookup"><span data-stu-id="14a38-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="14a38-207">刪除實體</span><span class="sxs-lookup"><span data-stu-id="14a38-207">Delete an entity</span></span>

<span data-ttu-id="14a38-208">在擷取之後，您可以刪除實體。</span><span class="sxs-lookup"><span data-stu-id="14a38-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="14a38-209">使用更新實體，這將會無法如果實體變更您在擷取之後。</span><span class="sxs-lookup"><span data-stu-id="14a38-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="14a38-210">刪除資料表</span><span class="sxs-lookup"><span data-stu-id="14a38-210">Delete a table</span></span>

<span data-ttu-id="14a38-211">您可以從儲存體帳戶刪除資料表。</span><span class="sxs-lookup"><span data-stu-id="14a38-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="14a38-212">已刪除的資料表將無法針對一段時間在刪除後加以重新建立。</span><span class="sxs-lookup"><span data-stu-id="14a38-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="14a38-213">後續步驟</span><span class="sxs-lookup"><span data-stu-id="14a38-213">Next steps</span></span>

<span data-ttu-id="14a38-214">既然您已了解資料表儲存體的基本概念，請遵循下列連結以深入了解更複雜的儲存體工作以及 Azure Cosmos DB 資料表 API。</span><span class="sxs-lookup"><span data-stu-id="14a38-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="14a38-215">Azure Cosmos DB 資料表 API 簡介</span><span class="sxs-lookup"><span data-stu-id="14a38-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="14a38-216">For.NET 參考資料的儲存體用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="14a38-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [<span data-ttu-id="14a38-217">Azure 儲存體類型提供者</span><span class="sxs-lookup"><span data-stu-id="14a38-217">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="14a38-218">Azure 儲存體團隊部落格</span><span class="sxs-lookup"><span data-stu-id="14a38-218">Azure Storage Team Blog</span></span>](https://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="14a38-219">設定連接字串</span><span class="sxs-lookup"><span data-stu-id="14a38-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="14a38-220">Getting Started with.NET 中的 Azure 資料表儲存體</span><span class="sxs-lookup"><span data-stu-id="14a38-220">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
