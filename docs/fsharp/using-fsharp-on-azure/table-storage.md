---
title: 以 F 開始使用 Azure 資料表儲存體#
description: 使用 Azure 資料表儲存體或 Azure Cosmos DB，將結構化資料儲存在雲端中。
author: sylvanc
ms.date: 03/26/2018
ms.custom: devx-track-fsharp
ms.openlocfilehash: bc8e111636013930f7c7d4f59d1ef0720298cb9f
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899278"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="4d246-103">開始使用 Azure 資料表儲存體和使用 F 的 Azure Cosmos DB 資料表 API\#</span><span class="sxs-lookup"><span data-stu-id="4d246-103">Get started with Azure Table Storage and the Azure Cosmos DB Table API using F\#</span></span>

<span data-ttu-id="4d246-104">Azure 資料表儲存體是一項服務，可將結構化的 NoSQL 資料儲存在雲端中。</span><span class="sxs-lookup"><span data-stu-id="4d246-104">Azure Table Storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="4d246-105">表格儲存體是具有無結構描述設計的索引鍵/屬性存放區。</span><span class="sxs-lookup"><span data-stu-id="4d246-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="4d246-106">由於表格儲存體並無結構描述，因此可輕易隨著應用程式發展需求改寫資料。</span><span class="sxs-lookup"><span data-stu-id="4d246-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="4d246-107">所有類型的應用程式都可以用快速且具成本效益的方式存取資料。</span><span class="sxs-lookup"><span data-stu-id="4d246-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="4d246-108">相較於類似資料量的傳統 SQL，資料表儲存體通常可大幅降低成本。</span><span class="sxs-lookup"><span data-stu-id="4d246-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="4d246-109">您可以使用表格儲存體來儲存具彈性的資料集，例如 Web 應用程式的使用者資料、通訊錄、裝置資訊，以及服務所需的任何其他中繼資料類型。</span><span class="sxs-lookup"><span data-stu-id="4d246-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="4d246-110">您可以在資料表中儲存任意數目的實體，且儲存體帳戶可包含任意數目的資料表，最高可達儲存體帳戶的容量限制。</span><span class="sxs-lookup"><span data-stu-id="4d246-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="4d246-111">Azure Cosmos DB 提供針對 Azure 資料表儲存體所撰寫，且需要高階功能的應用程式資料表 API，例如：</span><span class="sxs-lookup"><span data-stu-id="4d246-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table Storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="4d246-112">周全的全域發佈。</span><span class="sxs-lookup"><span data-stu-id="4d246-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="4d246-113">全球專用的輸送量。</span><span class="sxs-lookup"><span data-stu-id="4d246-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="4d246-114">99 百分位數的單一數字毫秒延遲。</span><span class="sxs-lookup"><span data-stu-id="4d246-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="4d246-115">保證高可用性。</span><span class="sxs-lookup"><span data-stu-id="4d246-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="4d246-116">自動次要索引。</span><span class="sxs-lookup"><span data-stu-id="4d246-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="4d246-117">針對 Azure 資料表儲存體所撰寫的應用程式可以使用資料表 API 來遷移至 Azure Cosmos DB，而不需要變更程式碼並利用 premium 功能。</span><span class="sxs-lookup"><span data-stu-id="4d246-117">Applications written for Azure Table Storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="4d246-118">資料表 API 具有適用於 .NET、Java、Python 和 Node.js 的用戶端 SDK。</span><span class="sxs-lookup"><span data-stu-id="4d246-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="4d246-119">如需詳細資訊，請參閱 [Azure Cosmos DB 資料表 API 簡介](/azure/cosmos-db/table-introduction)。</span><span class="sxs-lookup"><span data-stu-id="4d246-119">For more information, see [Introduction to Azure Cosmos DB Table API](/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="4d246-120">關於本教學課程</span><span class="sxs-lookup"><span data-stu-id="4d246-120">About this tutorial</span></span>

<span data-ttu-id="4d246-121">本教學課程說明如何使用 Azure 資料表儲存體或 Azure Cosmos DB 資料表 API 撰寫 F # 程式碼來進行一些常見工作，包括建立和刪除資料表，以及插入、更新、刪除和查詢資料表資料。</span><span class="sxs-lookup"><span data-stu-id="4d246-121">This tutorial shows how to write F# code to do some common tasks using Azure Table Storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4d246-122">先決條件</span><span class="sxs-lookup"><span data-stu-id="4d246-122">Prerequisites</span></span>

<span data-ttu-id="4d246-123">若要使用本指南，您必須先 [建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account) 或 [Azure Cosmos DB 帳戶](https://azure.microsoft.com/try/cosmosdb/)。</span><span class="sxs-lookup"><span data-stu-id="4d246-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="4d246-124">建立 F # 腳本並開始 F# 互動</span><span class="sxs-lookup"><span data-stu-id="4d246-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="4d246-125">本文中的範例可用於 F # 應用程式或 F # 腳本。</span><span class="sxs-lookup"><span data-stu-id="4d246-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="4d246-126">若要建立 F # 腳本，請 `.fsx` `tables.fsx` 在您的 f # 開發環境中建立副檔名為的檔案，例如。</span><span class="sxs-lookup"><span data-stu-id="4d246-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="4d246-127">接下來，使用 [套件管理員](package-management.md) （例如 [Paket](https://fsprojects.github.io/Paket/) 或 [NuGet](https://www.nuget.org/) ）， `WindowsAzure.Storage` `WindowsAzure.Storage.dll` 在您的腳本中使用指示詞安裝封裝和參考 `#r` 。</span><span class="sxs-lookup"><span data-stu-id="4d246-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="4d246-128">請再次進行，以 `Microsoft.WindowsAzure.ConfigurationManager` 取得 Microsoft Azure 命名空間。</span><span class="sxs-lookup"><span data-stu-id="4d246-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="4d246-129">新增命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="4d246-129">Add namespace declarations</span></span>

<span data-ttu-id="4d246-130">在 `tables.fsx` 檔案頂端新增下列 `open` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="4d246-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="4d246-131">取得 Azure 儲存體連接字串</span><span class="sxs-lookup"><span data-stu-id="4d246-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="4d246-132">如果您要連接到 Azure 儲存體表格服務，您將需要此教學課程的連接字串。</span><span class="sxs-lookup"><span data-stu-id="4d246-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="4d246-133">您可以從 Azure 入口網站複製您的連接字串。</span><span class="sxs-lookup"><span data-stu-id="4d246-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="4d246-134">如需連接字串的詳細資訊，請參閱 [設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="4d246-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="4d246-135">取得 Azure Cosmos DB 連接字串</span><span class="sxs-lookup"><span data-stu-id="4d246-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="4d246-136">如果您要連接到 Azure Cosmos DB，您將需要此教學課程的連接字串。</span><span class="sxs-lookup"><span data-stu-id="4d246-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="4d246-137">您可以從 Azure 入口網站複製您的連接字串。</span><span class="sxs-lookup"><span data-stu-id="4d246-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="4d246-138">在 Azure 入口網站的 Cosmos DB 帳戶中，移至 [**設定**  >  **連接字串**]，然後選取 [**複製**] 按鈕以複製您的主要連接字串。</span><span class="sxs-lookup"><span data-stu-id="4d246-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and select the **Copy** button to copy your Primary Connection String.</span></span>

<span data-ttu-id="4d246-139">針對本教學課程，請在腳本中輸入您的連接字串，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4d246-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="4d246-140">不過，這不 **建議** 用於實際的專案。</span><span class="sxs-lookup"><span data-stu-id="4d246-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="4d246-141">儲存體帳戶金鑰很類似儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="4d246-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="4d246-142">請務必小心保護您的儲存體帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="4d246-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="4d246-143">請避免轉發給其他使用者、進行硬式編碼，或將它儲存在其他人可以存取的純文字檔案。</span><span class="sxs-lookup"><span data-stu-id="4d246-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="4d246-144">如果您認為金鑰可能已遭盜用，您可以使用 Azure 入口網站重新產生金鑰。</span><span class="sxs-lookup"><span data-stu-id="4d246-144">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="4d246-145">針對實際的應用程式，維護儲存體連接字串的最佳方式是在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="4d246-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="4d246-146">若要從設定檔提取連接字串，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="4d246-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="4d246-147">是否使用 Azure Configuration Manager 可由您選擇。</span><span class="sxs-lookup"><span data-stu-id="4d246-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="4d246-148">您也可以使用 API，例如 .NET Framework 的型別 `ConfigurationManager` 。</span><span class="sxs-lookup"><span data-stu-id="4d246-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="4d246-149">解析連接字串</span><span class="sxs-lookup"><span data-stu-id="4d246-149">Parse the connection string</span></span>

<span data-ttu-id="4d246-150">若要剖析連接字串，請使用：</span><span class="sxs-lookup"><span data-stu-id="4d246-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="4d246-151">這會傳回 `CloudStorageAccount` 。</span><span class="sxs-lookup"><span data-stu-id="4d246-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="4d246-152">建立表格服務用戶端</span><span class="sxs-lookup"><span data-stu-id="4d246-152">Create the Table service client</span></span>

<span data-ttu-id="4d246-153">`CloudTableClient`類別可讓您在資料表儲存體中取出資料表和實體。</span><span class="sxs-lookup"><span data-stu-id="4d246-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="4d246-154">以下是建立服務用戶端的其中一種方式：</span><span class="sxs-lookup"><span data-stu-id="4d246-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="4d246-155">您現在可以開始撰寫程式碼，以讀取表格儲存體的資料並將資料寫入其中。</span><span class="sxs-lookup"><span data-stu-id="4d246-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="4d246-156">建立資料表</span><span class="sxs-lookup"><span data-stu-id="4d246-156">Create a table</span></span>

<span data-ttu-id="4d246-157">此範例說明如何建立尚不存在的資料表：</span><span class="sxs-lookup"><span data-stu-id="4d246-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="4d246-158">將實體新增至資料表</span><span class="sxs-lookup"><span data-stu-id="4d246-158">Add an entity to a table</span></span>

<span data-ttu-id="4d246-159">實體必須具有繼承自的類型 `TableEntity` 。</span><span class="sxs-lookup"><span data-stu-id="4d246-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="4d246-160">您可以使用任何想要的方式進行擴充 `TableEntity` ，但您的類型 *必須* 具有無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="4d246-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="4d246-161">只有具有和的屬性 `get` `set` 會儲存在您的 Azure 資料表中。</span><span class="sxs-lookup"><span data-stu-id="4d246-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="4d246-162">實體的資料分割和資料列索引鍵可唯一識別資料表中的實體。</span><span class="sxs-lookup"><span data-stu-id="4d246-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="4d246-163">查詢具有相同分割區索引鍵的實體，其速度快於查詢具有不同分割區索引鍵的實體，但使用不同的資料分割索引鍵可提供更佳的延展性或平行作業。</span><span class="sxs-lookup"><span data-stu-id="4d246-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="4d246-164">以下範例 `Customer` 會使用 `lastName` 做為資料分割索引鍵，並使用 `firstName` 做為資料列索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4d246-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="4d246-165">現在新增 `Customer` 至資料表。</span><span class="sxs-lookup"><span data-stu-id="4d246-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="4d246-166">若要這樣做，請建立在 `TableOperation` 資料表上執行的。</span><span class="sxs-lookup"><span data-stu-id="4d246-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="4d246-167">在此情況下，您會建立作業 `Insert` 。</span><span class="sxs-lookup"><span data-stu-id="4d246-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="4d246-168">插入一批實體</span><span class="sxs-lookup"><span data-stu-id="4d246-168">Insert a batch of entities</span></span>

<span data-ttu-id="4d246-169">您可以使用單一寫入作業，將一批實體插入資料表中。</span><span class="sxs-lookup"><span data-stu-id="4d246-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="4d246-170">批次作業可讓您將作業合併成單一執行，但是有一些限制：</span><span class="sxs-lookup"><span data-stu-id="4d246-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="4d246-171">您可以在相同的批次作業中執行更新、刪除和插入。</span><span class="sxs-lookup"><span data-stu-id="4d246-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="4d246-172">批次作業最多可包含100個實體。</span><span class="sxs-lookup"><span data-stu-id="4d246-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="4d246-173">批次作業中的所有實體都必須有相同的分割區索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4d246-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="4d246-174">雖然您可以在批次作業中執行查詢，但它必須是批次中唯一的作業。</span><span class="sxs-lookup"><span data-stu-id="4d246-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="4d246-175">以下是將兩個插入結合到批次作業的程式碼：</span><span class="sxs-lookup"><span data-stu-id="4d246-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="4d246-176">擷取資料分割中的所有實體</span><span class="sxs-lookup"><span data-stu-id="4d246-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="4d246-177">若要向資料表查詢資料分割中的所有實體，請使用 `TableQuery` 物件。</span><span class="sxs-lookup"><span data-stu-id="4d246-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="4d246-178">在這裡，您會篩選出 "Smith" 為分割區索引鍵的實體。</span><span class="sxs-lookup"><span data-stu-id="4d246-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="4d246-179">您現在會列印結果：</span><span class="sxs-lookup"><span data-stu-id="4d246-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="4d246-180">擷取資料分割中某個範圍的實體</span><span class="sxs-lookup"><span data-stu-id="4d246-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="4d246-181">如果您不想要查詢資料分割中的所有實體，可結合資料分割索引鍵篩選器與資料列索引鍵篩選器來指定範圍。</span><span class="sxs-lookup"><span data-stu-id="4d246-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="4d246-182">在這裡，您會使用兩個篩選器來取得 "Smith" 分割區中的所有實體，其中資料列索引鍵 (名字) 開頭為字母中 "M" 之前的字母。</span><span class="sxs-lookup"><span data-stu-id="4d246-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="4d246-183">您現在會列印結果：</span><span class="sxs-lookup"><span data-stu-id="4d246-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="4d246-184">擷取單一實體</span><span class="sxs-lookup"><span data-stu-id="4d246-184">Retrieve a single entity</span></span>

<span data-ttu-id="4d246-185">您可以撰寫查詢來擷取單一特定實體。</span><span class="sxs-lookup"><span data-stu-id="4d246-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="4d246-186">在這裡，您會使用 `TableOperation` 來指定客戶 "Ben Smith"。</span><span class="sxs-lookup"><span data-stu-id="4d246-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="4d246-187">您可以取回，而不是集合 `Customer` 。</span><span class="sxs-lookup"><span data-stu-id="4d246-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="4d246-188">在查詢中同時指定資料分割索引鍵和資料列索引鍵，是從表格服務中取得單一實體最快的方式。</span><span class="sxs-lookup"><span data-stu-id="4d246-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="4d246-189">您現在會列印結果：</span><span class="sxs-lookup"><span data-stu-id="4d246-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a><span data-ttu-id="4d246-190">取代實體</span><span class="sxs-lookup"><span data-stu-id="4d246-190">Replace an entity</span></span>

<span data-ttu-id="4d246-191">若要更新實體，請從表格服務中取出它、修改實體物件，然後使用作業將變更儲存回資料表服務 `Replace` 。</span><span class="sxs-lookup"><span data-stu-id="4d246-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="4d246-192">這會導致在伺服器上完全取代實體，除非伺服器上的實體在抓取之後已經變更，在這種情況下，作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="4d246-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="4d246-193">這項失敗是為了防止您的應用程式不慎覆寫其他來源的變更。</span><span class="sxs-lookup"><span data-stu-id="4d246-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="4d246-194">插入或取代實體</span><span class="sxs-lookup"><span data-stu-id="4d246-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="4d246-195">有時候，您不知道實體是否存在於資料表中。</span><span class="sxs-lookup"><span data-stu-id="4d246-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="4d246-196">如果有的話，就不再需要儲存在其中的目前值。</span><span class="sxs-lookup"><span data-stu-id="4d246-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="4d246-197">您可以使用 `InsertOrReplace` 來建立實體，或將它取代（如果存在的話），而不論其狀態為何。</span><span class="sxs-lookup"><span data-stu-id="4d246-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="4d246-198">查詢實體屬性的子集</span><span class="sxs-lookup"><span data-stu-id="4d246-198">Query a subset of entity properties</span></span>

<span data-ttu-id="4d246-199">資料表查詢可以只從實體中取出幾個屬性，而不是所有屬性。</span><span class="sxs-lookup"><span data-stu-id="4d246-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="4d246-200">這項稱為「投射」的技術可以改善查詢效能，尤其是針對大型實體。</span><span class="sxs-lookup"><span data-stu-id="4d246-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="4d246-201">在這裡，您只會使用和傳回電子郵件地址 `DynamicTableEntity` `EntityResolver` 。</span><span class="sxs-lookup"><span data-stu-id="4d246-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="4d246-202">本機儲存體模擬器不支援投影，因此此程式碼只有在您使用表格服務上的帳戶時才會執行。</span><span class="sxs-lookup"><span data-stu-id="4d246-202">Projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="4d246-203">以非同步方式擷取頁面中的實體</span><span class="sxs-lookup"><span data-stu-id="4d246-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="4d246-204">如果您要讀取大量的實體，而且想要在抓取這些實體時進行處理，而不是等候它們全部傳回，您可以使用分段的查詢。</span><span class="sxs-lookup"><span data-stu-id="4d246-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="4d246-205">在這裡，您會使用非同步工作流程在頁面中傳回結果，如此一來，當您在等候一組大型結果傳回時，不會封鎖執行。</span><span class="sxs-lookup"><span data-stu-id="4d246-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="4d246-206">您現在會同步執行此計算：</span><span class="sxs-lookup"><span data-stu-id="4d246-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="4d246-207">刪除實體</span><span class="sxs-lookup"><span data-stu-id="4d246-207">Delete an entity</span></span>

<span data-ttu-id="4d246-208">您可以在抓取實體之後將其刪除。</span><span class="sxs-lookup"><span data-stu-id="4d246-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="4d246-209">如同更新實體，如果實體自您抓取之後已經變更，就會失敗。</span><span class="sxs-lookup"><span data-stu-id="4d246-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="4d246-210">刪除資料表</span><span class="sxs-lookup"><span data-stu-id="4d246-210">Delete a table</span></span>

<span data-ttu-id="4d246-211">您可以從儲存體帳戶中刪除資料表。</span><span class="sxs-lookup"><span data-stu-id="4d246-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="4d246-212">已刪除的資料表在刪除後一段時間內，將無法重新建立。</span><span class="sxs-lookup"><span data-stu-id="4d246-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="4d246-213">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4d246-213">Next steps</span></span>

<span data-ttu-id="4d246-214">既然您已瞭解資料表儲存體的基本概念，請遵循下列連結以瞭解更複雜的儲存體工作和 Azure Cosmos DB 資料表 API。</span><span class="sxs-lookup"><span data-stu-id="4d246-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="4d246-215">Azure Cosmos DB 資料表 API 簡介</span><span class="sxs-lookup"><span data-stu-id="4d246-215">Introduction to Azure Cosmos DB Table API</span></span>](/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="4d246-216">Storage Client Library for .NET 參考資料</span><span class="sxs-lookup"><span data-stu-id="4d246-216">Storage Client Library for .NET reference</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="4d246-217">Azure 儲存體型別提供者</span><span class="sxs-lookup"><span data-stu-id="4d246-217">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="4d246-218">Azure 儲存體團隊部落格</span><span class="sxs-lookup"><span data-stu-id="4d246-218">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="4d246-219">設定連接字串</span><span class="sxs-lookup"><span data-stu-id="4d246-219">Configuring Connection Strings</span></span>](/azure/storage/common/storage-configure-connection-string)
