---
title: '開始使用 Azure 資料表儲存體使用 F #'
description: 將結構化的資料儲存在雲端中使用 Azure 資料表儲存體或 Azure Cosmos DB。
author: sylvanc
ms.author: phcart
ms.date: 03/26/2018
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 50721ca44bbae5c52984b08a30bc87507fbf063d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="49103-103">開始使用 Azure 資料表儲存體和 Azure Cosmos DB 資料表 API 使用 F #</span><span class="sxs-lookup"><span data-stu-id="49103-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F#</span></span> # 

<span data-ttu-id="49103-104">Azure 資料表儲存體是結構化的 NoSQL 資料存放在雲端服務。</span><span class="sxs-lookup"><span data-stu-id="49103-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="49103-105">資料表儲存體是 schemaless 設計的索引鍵/屬性存放區。</span><span class="sxs-lookup"><span data-stu-id="49103-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="49103-106">因為資料表儲存體是 schemaless，很容易就能為您的應用程式 evolve 的需求調整您的資料。</span><span class="sxs-lookup"><span data-stu-id="49103-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="49103-107">資料的存取權非常快速且符合成本效益的所有種類的應用程式。</span><span class="sxs-lookup"><span data-stu-id="49103-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="49103-108">資料表儲存體通常是遠低於成本中類似資料磁碟區的傳統 SQL。</span><span class="sxs-lookup"><span data-stu-id="49103-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="49103-109">您可以使用資料表儲存體來儲存彈性的資料集，例如 web 應用程式、 通訊錄，裝置資訊和任何其他類型的服務所需的中繼資料的使用者資料。</span><span class="sxs-lookup"><span data-stu-id="49103-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="49103-110">您可以將任意數目的實體儲存在資料表中，而且儲存體帳戶包含任何數量的資料表，儲存體帳戶的容量上限為止。</span><span class="sxs-lookup"><span data-stu-id="49103-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="49103-111">Azure Cosmos DB 會提供資料表 API 所撰寫，Azure 資料表儲存體，以及這類要求高階功能的應用程式：</span><span class="sxs-lookup"><span data-stu-id="49103-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="49103-112">周全的全域通訊。</span><span class="sxs-lookup"><span data-stu-id="49103-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="49103-113">專用的輸送量全球。</span><span class="sxs-lookup"><span data-stu-id="49103-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="49103-114">個 99th 百分位數毫秒延遲。</span><span class="sxs-lookup"><span data-stu-id="49103-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="49103-115">保證高可用性。</span><span class="sxs-lookup"><span data-stu-id="49103-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="49103-116">自動的次要索引。</span><span class="sxs-lookup"><span data-stu-id="49103-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="49103-117">Azure 資料表儲存體所撰寫的應用程式可以利用資料表 API 沒有變更程式碼移轉至 Azure Cosmos 資料庫，並利用高階功能。</span><span class="sxs-lookup"><span data-stu-id="49103-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="49103-118">資料表 API 有可用的用戶端 Sdk for.NET、 Java、 Python 和 Node.js。</span><span class="sxs-lookup"><span data-stu-id="49103-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="49103-119">如需詳細資訊，請參閱[Azure Cosmos DB 資料表 API 簡介](https://docs.microsoft.com/azure/cosmos-db/table-introduction)。</span><span class="sxs-lookup"><span data-stu-id="49103-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="49103-120">關於本教學課程</span><span class="sxs-lookup"><span data-stu-id="49103-120">About this tutorial</span></span>

<span data-ttu-id="49103-121">本教學課程會示範如何撰寫 F # 程式碼來執行一些常見的工作，使用 Azure 資料表儲存體或 Azure Cosmos DB 資料表 API，包括建立和刪除資料表並插入、 更新、 刪除和查詢資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="49103-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49103-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="49103-122">Prerequisites</span></span>

<span data-ttu-id="49103-123">若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)或[Azure Cosmos DB 帳戶](https://azure.microsoft.com/try/cosmosdb/)。</span><span class="sxs-lookup"><span data-stu-id="49103-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>


## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="49103-124">建立 F # 指令碼，並開始 F # Interactive</span><span class="sxs-lookup"><span data-stu-id="49103-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="49103-125">這篇文章中的範例可以用於 F # 應用程式或 F # 指令碼。</span><span class="sxs-lookup"><span data-stu-id="49103-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="49103-126">若要建立 F # 指令碼，建立檔案之`.fsx`擴充功能，例如`tables.fsx`，F # 開發環境中。</span><span class="sxs-lookup"><span data-stu-id="49103-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="49103-127">接下來，使用[封裝管理員](package-management.md)例如[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`封裝和參考`WindowsAzure.Storage.dll`指令碼使用`#r`指示詞。</span><span class="sxs-lookup"><span data-stu-id="49103-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="49103-128">請勿重新`Microsoft.WindowsAzure.ConfigurationManager`才能取得 Microsoft.Azure 命名空間。</span><span class="sxs-lookup"><span data-stu-id="49103-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="49103-129">加入命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="49103-129">Add namespace declarations</span></span>

<span data-ttu-id="49103-130">加入下列`open`上方的陳述式`tables.fsx`檔案：</span><span class="sxs-lookup"><span data-stu-id="49103-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="49103-131">取得您的 Azure 儲存體連接字串</span><span class="sxs-lookup"><span data-stu-id="49103-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="49103-132">如果您正在連接到 Azure 儲存體資料表服務，您必須連接字串在此教學課程。</span><span class="sxs-lookup"><span data-stu-id="49103-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="49103-133">您可以從 Azure 入口網站複製您的連接字串。</span><span class="sxs-lookup"><span data-stu-id="49103-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="49103-134">如需連接字串的詳細資訊，請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="49103-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="49103-135">取得您的 Azure Cosmos DB 連接字串</span><span class="sxs-lookup"><span data-stu-id="49103-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="49103-136">如果您正在連接到 Azure Cosmos DB，您必須連接字串在此教學課程。</span><span class="sxs-lookup"><span data-stu-id="49103-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="49103-137">您可以從 Azure 入口網站複製您的連接字串。</span><span class="sxs-lookup"><span data-stu-id="49103-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="49103-138">在 Azure 入口網站，Cosmos DB 帳戶中，移至**設定** > **連接字串**，然後按一下**複製** 按鈕複製主要的連線字串。</span><span class="sxs-lookup"><span data-stu-id="49103-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="49103-139">教學課程中，輸入您的指令碼，如下列範例中的連接字串：</span><span class="sxs-lookup"><span data-stu-id="49103-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="49103-140">不過，這是**不建議**用於真實的專案。</span><span class="sxs-lookup"><span data-stu-id="49103-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="49103-141">儲存體帳戶金鑰是類似於儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="49103-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="49103-142">一律為保護您的儲存體帳戶金鑰，請小心。</span><span class="sxs-lookup"><span data-stu-id="49103-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="49103-143">避免將其散發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。</span><span class="sxs-lookup"><span data-stu-id="49103-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="49103-144">您可以重新產生您使用 Azure 入口網站，如果您認為可能已受到危害的金鑰。</span><span class="sxs-lookup"><span data-stu-id="49103-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="49103-145">用於真實的應用程式，以維護您的儲存體連接字串的最佳方式是在組態檔中。</span><span class="sxs-lookup"><span data-stu-id="49103-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="49103-146">若要從組態檔擷取連接字串，您可以：</span><span class="sxs-lookup"><span data-stu-id="49103-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="49103-147">使用 Azure 組態管理員是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="49103-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="49103-148">您也可以使用例如.NET Framework API`ConfigurationManager`型別。</span><span class="sxs-lookup"><span data-stu-id="49103-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="49103-149">剖析連接字串</span><span class="sxs-lookup"><span data-stu-id="49103-149">Parse the connection string</span></span>

<span data-ttu-id="49103-150">若要剖析的連接字串，使用：</span><span class="sxs-lookup"><span data-stu-id="49103-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="49103-151">這會傳回`CloudStorageAccount`。</span><span class="sxs-lookup"><span data-stu-id="49103-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="49103-152">建立表格服務用戶端</span><span class="sxs-lookup"><span data-stu-id="49103-152">Create the Table service client</span></span>

<span data-ttu-id="49103-153">`CloudTableClient`類別可讓您擷取資料表和資料表儲存體中的實體。</span><span class="sxs-lookup"><span data-stu-id="49103-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="49103-154">以下是如何建立服務用戶端：</span><span class="sxs-lookup"><span data-stu-id="49103-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="49103-155">現在您已準備好開始撰寫程式碼讀取資料，並將資料寫入資料表儲存體。</span><span class="sxs-lookup"><span data-stu-id="49103-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="49103-156">建立資料表</span><span class="sxs-lookup"><span data-stu-id="49103-156">Create a table</span></span>

<span data-ttu-id="49103-157">這個範例示範如何建立資料表，如果不存在：</span><span class="sxs-lookup"><span data-stu-id="49103-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="49103-158">將實體加入至資料表</span><span class="sxs-lookup"><span data-stu-id="49103-158">Add an entity to a table</span></span>

<span data-ttu-id="49103-159">實體必須要有型別繼承自`TableEntity`。</span><span class="sxs-lookup"><span data-stu-id="49103-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="49103-160">您可以擴充`TableEntity`任何方式，但您的型別*必須*具有無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="49103-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="49103-161">只有屬性同時具有`get`和`set`會儲存在 Azure 資料表。</span><span class="sxs-lookup"><span data-stu-id="49103-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="49103-162">實體的資料分割和資料列索引鍵唯一識別資料表中的實體。</span><span class="sxs-lookup"><span data-stu-id="49103-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="49103-163">具有相同的資料分割索引鍵的實體可以進行查詢速度比的不同資料分割索引鍵，但使用不同的資料分割索引鍵可讓平行作業的更佳的延展性。</span><span class="sxs-lookup"><span data-stu-id="49103-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="49103-164">以下是範例`Customer`使用`lastName`做為資料分割索引鍵和`firstName`做為資料列索引鍵。</span><span class="sxs-lookup"><span data-stu-id="49103-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="49103-165">現在，加入`Customer`至資料表。</span><span class="sxs-lookup"><span data-stu-id="49103-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="49103-166">若要這樣做，請建立`TableOperation`資料表上執行。</span><span class="sxs-lookup"><span data-stu-id="49103-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="49103-167">在此情況下，您建立`Insert`作業。</span><span class="sxs-lookup"><span data-stu-id="49103-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="49103-168">插入實體批次</span><span class="sxs-lookup"><span data-stu-id="49103-168">Insert a batch of entities</span></span>

<span data-ttu-id="49103-169">您可以將實體批次插入資料表中使用單一寫入作業。</span><span class="sxs-lookup"><span data-stu-id="49103-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="49103-170">批次作業可讓您將作業結合成單一的執行，但具有一些限制：</span><span class="sxs-lookup"><span data-stu-id="49103-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="49103-171">您可以執行更新、 刪除和插入相同的批次作業中。</span><span class="sxs-lookup"><span data-stu-id="49103-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="49103-172">批次作業可以包含多達 100 個項目。</span><span class="sxs-lookup"><span data-stu-id="49103-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="49103-173">批次作業中的所有實體必須都有相同的資料分割索引鍵。</span><span class="sxs-lookup"><span data-stu-id="49103-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="49103-174">雖然也可以在批次作業中執行查詢，但是它必須是批次中唯一的作業。</span><span class="sxs-lookup"><span data-stu-id="49103-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="49103-175">以下是一些結合成一個批次作業的兩個插入的程式碼：</span><span class="sxs-lookup"><span data-stu-id="49103-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="49103-176">擷取資料分割中的所有實體</span><span class="sxs-lookup"><span data-stu-id="49103-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="49103-177">若要查詢的資料表資料分割中的所有實體，請使用`TableQuery`物件。</span><span class="sxs-lookup"><span data-stu-id="49103-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="49103-178">在這裡，您篩選實體"Smith"所在的資料分割索引鍵。</span><span class="sxs-lookup"><span data-stu-id="49103-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="49103-179">您現在會列印結果：</span><span class="sxs-lookup"><span data-stu-id="49103-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="49103-180">擷取某個範圍的資料分割中的實體</span><span class="sxs-lookup"><span data-stu-id="49103-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="49103-181">如果您不想要查詢資料分割中的所有實體，您可以指定範圍，藉由結合資料分割索引鍵篩選，資料列索引鍵的篩選。</span><span class="sxs-lookup"><span data-stu-id="49103-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="49103-182">在這裡，您使用兩個篩選器"Smith"的分割區中取得所有實體資料列索引鍵 （第一個名稱） 開始的位置以字母"M"中字母之前。</span><span class="sxs-lookup"><span data-stu-id="49103-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="49103-183">您現在會列印結果：</span><span class="sxs-lookup"><span data-stu-id="49103-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="49103-184">擷取單一實體</span><span class="sxs-lookup"><span data-stu-id="49103-184">Retrieve a single entity</span></span>

<span data-ttu-id="49103-185">您可以撰寫查詢以擷取單一的特定實體。</span><span class="sxs-lookup"><span data-stu-id="49103-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="49103-186">在此，您可以使用`TableOperation`來指定客戶"Ben Smith"。</span><span class="sxs-lookup"><span data-stu-id="49103-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="49103-187">而不是集合，您會回到`Customer`。</span><span class="sxs-lookup"><span data-stu-id="49103-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="49103-188">在查詢中指定資料分割索引鍵和資料列索引鍵是最快的方法來擷取與表格服務的單一實體。</span><span class="sxs-lookup"><span data-stu-id="49103-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="49103-189">您現在會列印結果：</span><span class="sxs-lookup"><span data-stu-id="49103-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a><span data-ttu-id="49103-190">取代實體</span><span class="sxs-lookup"><span data-stu-id="49103-190">Replace an entity</span></span>

<span data-ttu-id="49103-191">若要更新實體，擷取與表格服務、 修改實體物件，以及將變更儲存至表格服務會使用`Replace`作業。</span><span class="sxs-lookup"><span data-stu-id="49103-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="49103-192">除非變更伺服器上的實體自擷取後，在此情況下作業失敗，這會導致在伺服器上，完全取代實體。</span><span class="sxs-lookup"><span data-stu-id="49103-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="49103-193">此失敗是為了防止您的應用程式不小心覆寫從其他來源的變更。</span><span class="sxs-lookup"><span data-stu-id="49103-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="49103-194">插入或取代實體</span><span class="sxs-lookup"><span data-stu-id="49103-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="49103-195">有時候，您不知道實體是否存在於資料表中。</span><span class="sxs-lookup"><span data-stu-id="49103-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="49103-196">而且，若是如此，不再需要儲存在它的目前值。</span><span class="sxs-lookup"><span data-stu-id="49103-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="49103-197">您可以使用`InsertOrReplace`建立實體，或取代它，如果存在的話，不論其狀態。</span><span class="sxs-lookup"><span data-stu-id="49103-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="49103-198">查詢實體屬性的子集</span><span class="sxs-lookup"><span data-stu-id="49103-198">Query a subset of entity properties</span></span>

<span data-ttu-id="49103-199">資料表查詢可以擷取只需要幾個屬性，而不是所有的這些實體。</span><span class="sxs-lookup"><span data-stu-id="49103-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="49103-200">這項技巧，呼叫投影，可以改善查詢效能，特別是大型的實體。</span><span class="sxs-lookup"><span data-stu-id="49103-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="49103-201">您在這裡，傳回僅電子郵件地址使用`DynamicTableEntity`和`EntityResolver`。</span><span class="sxs-lookup"><span data-stu-id="49103-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="49103-202">請注意，投影不支援在本機儲存體模擬器，以便在表格服務上使用的帳戶時，才執行此程式碼。</span><span class="sxs-lookup"><span data-stu-id="49103-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="49103-203">以非同步方式擷取頁面中的實體</span><span class="sxs-lookup"><span data-stu-id="49103-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="49103-204">如果您正在閱讀大量實體，而且您想要擷取，而非等待它們全部傳回，您可以使用分割的查詢時進行處理。</span><span class="sxs-lookup"><span data-stu-id="49103-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="49103-205">在這裡，您傳回的結果頁面中使用的非同步工作流程，因此正在等待將大量要傳回的結果時，不會封鎖執行。</span><span class="sxs-lookup"><span data-stu-id="49103-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="49103-206">您現在執行這項計算以同步方式：</span><span class="sxs-lookup"><span data-stu-id="49103-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="49103-207">刪除實體</span><span class="sxs-lookup"><span data-stu-id="49103-207">Delete an entity</span></span>

<span data-ttu-id="49103-208">您可以在擷取之後，刪除實體。</span><span class="sxs-lookup"><span data-stu-id="49103-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="49103-209">與更新實體，此作業失敗之後，如果實體已變更您擷取它。</span><span class="sxs-lookup"><span data-stu-id="49103-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="49103-210">刪除資料表</span><span class="sxs-lookup"><span data-stu-id="49103-210">Delete a table</span></span>

<span data-ttu-id="49103-211">您可以從儲存體帳戶刪除資料表。</span><span class="sxs-lookup"><span data-stu-id="49103-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="49103-212">已刪除的資料表將無法在重新建立此一段時間後刪除。</span><span class="sxs-lookup"><span data-stu-id="49103-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="49103-213">後續步驟</span><span class="sxs-lookup"><span data-stu-id="49103-213">Next steps</span></span>

<span data-ttu-id="49103-214">既然您已學到的資料表儲存體的基本概念，請遵循下列連結，以深入了解更複雜的儲存體工作以及 Azure Cosmos DB 資料表 API。</span><span class="sxs-lookup"><span data-stu-id="49103-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="49103-215">Azure Cosmos DB 資料表 API 簡介</span><span class="sxs-lookup"><span data-stu-id="49103-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="49103-216">儲存體用戶端程式庫.NET 參考</span><span class="sxs-lookup"><span data-stu-id="49103-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [<span data-ttu-id="49103-217">Azure 儲存體型別提供者</span><span class="sxs-lookup"><span data-stu-id="49103-217">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="49103-218">Azure 儲存體團隊部落格</span><span class="sxs-lookup"><span data-stu-id="49103-218">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="49103-219">設定連接字串</span><span class="sxs-lookup"><span data-stu-id="49103-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="49103-220">在.NET 的 Azure 資料表儲存體使用者入門</span><span class="sxs-lookup"><span data-stu-id="49103-220">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
