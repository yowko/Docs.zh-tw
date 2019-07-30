---
title: 使用 F# 開始使用 Azure 資料表儲存體
description: 使用 Azure 資料表儲存體或 Azure Cosmos DB, 將結構化資料儲存在雲端。
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: c8ab2d61048523ac52f305c7bd035c73ca0d3f60
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630476"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="c809c-103">開始使用 Azure 資料表儲存體和使用 F 的 Azure Cosmos DB 資料表 API\#</span><span class="sxs-lookup"><span data-stu-id="c809c-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F\#</span></span>

<span data-ttu-id="c809c-104">Azure 表格儲存體是在雲端儲存結構化 NoSQL 資料的服務。</span><span class="sxs-lookup"><span data-stu-id="c809c-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="c809c-105">資料表儲存體是具有無架構設計的索引鍵/屬性存放區。</span><span class="sxs-lookup"><span data-stu-id="c809c-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="c809c-106">因為資料表儲存體是無架構的, 所以很容易就能隨著應用程式發展的需求來調整您的資料。</span><span class="sxs-lookup"><span data-stu-id="c809c-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="c809c-107">對所有類型的應用程式而言, 資料的存取速度既快速又符合成本效益。</span><span class="sxs-lookup"><span data-stu-id="c809c-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="c809c-108">相較于類似資料量的傳統 SQL, 資料表儲存體的成本通常會大幅降低。</span><span class="sxs-lookup"><span data-stu-id="c809c-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="c809c-109">您可以使用表格儲存體來儲存具彈性的資料集, 例如 web 應用程式的使用者資料、通訊錄、裝置資訊, 以及服務所需的任何其他元資料類型。</span><span class="sxs-lookup"><span data-stu-id="c809c-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="c809c-110">您可以在資料表中儲存任意數目的實體, 且儲存體帳戶可包含任意數目的資料表, 最高可達儲存體帳戶的容量限制。</span><span class="sxs-lookup"><span data-stu-id="c809c-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="c809c-111">Azure Cosmos DB 提供針對 Azure 資料表儲存體所撰寫, 而且需要高階功能的應用程式資料表 API, 例如:</span><span class="sxs-lookup"><span data-stu-id="c809c-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="c809c-112">全包式全域散發。</span><span class="sxs-lookup"><span data-stu-id="c809c-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="c809c-113">全球專用的輸送量。</span><span class="sxs-lookup"><span data-stu-id="c809c-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="c809c-114">第99個百分位數的一位數毫秒延遲。</span><span class="sxs-lookup"><span data-stu-id="c809c-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="c809c-115">保證高可用性。</span><span class="sxs-lookup"><span data-stu-id="c809c-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="c809c-116">自動次要索引。</span><span class="sxs-lookup"><span data-stu-id="c809c-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="c809c-117">針對 Azure 資料表儲存體所撰寫的應用程式可以使用資料表 API 來遷移至 Azure Cosmos DB, 而不需要進行任何程式碼變更, 並利用 premium 功能。</span><span class="sxs-lookup"><span data-stu-id="c809c-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="c809c-118">資料表 API 具有適用于 .NET、JAVA、Python 和 node.js 的用戶端 Sdk。</span><span class="sxs-lookup"><span data-stu-id="c809c-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="c809c-119">如需詳細資訊, 請參閱[Azure Cosmos DB 資料表 API 簡介](https://docs.microsoft.com/azure/cosmos-db/table-introduction)。</span><span class="sxs-lookup"><span data-stu-id="c809c-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="c809c-120">關於本教學課程</span><span class="sxs-lookup"><span data-stu-id="c809c-120">About this tutorial</span></span>

<span data-ttu-id="c809c-121">本教學課程說明如何使用F# Azure 資料表儲存體或 Azure Cosmos DB 資料表 API 來撰寫程式碼來執行一些常見的工作, 包括建立和刪除資料表, 以及插入、更新、刪除和查詢資料表資料。</span><span class="sxs-lookup"><span data-stu-id="c809c-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c809c-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="c809c-122">Prerequisites</span></span>

<span data-ttu-id="c809c-123">若要使用本指南, 您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)或[Azure Cosmos DB 帳戶](https://azure.microsoft.com/try/cosmosdb/)。</span><span class="sxs-lookup"><span data-stu-id="c809c-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="c809c-124">建立F#腳本並啟動F#互動式</span><span class="sxs-lookup"><span data-stu-id="c809c-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="c809c-125">本文中的範例可用於F#應用程式或F#腳本中。</span><span class="sxs-lookup"><span data-stu-id="c809c-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="c809c-126">若要建立F#腳本, 請在`.fsx` F#開發環境中建立`tables.fsx`副檔名為的檔案, 例如。</span><span class="sxs-lookup"><span data-stu-id="c809c-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="c809c-127">接下來, 使用[Paket](https://fsprojects.github.io/Paket/)或`WindowsAzure.Storage` [NuGet](https://www.nuget.org/)之類的[套件管理員](package-management.md), 在您的腳本中`WindowsAzure.Storage.dll`使用`#r`指示詞安裝封裝和參考。</span><span class="sxs-lookup"><span data-stu-id="c809c-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="c809c-128">再次`Microsoft.WindowsAzure.ConfigurationManager`執行, 以取得 Microsoft Azure 命名空間。</span><span class="sxs-lookup"><span data-stu-id="c809c-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="c809c-129">新增命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="c809c-129">Add namespace declarations</span></span>

<span data-ttu-id="c809c-130">將下列`open`語句新增至檔案頂端`tables.fsx` :</span><span class="sxs-lookup"><span data-stu-id="c809c-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="c809c-131">取得您的 Azure 儲存體連接字串</span><span class="sxs-lookup"><span data-stu-id="c809c-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="c809c-132">如果您要連接到 Azure 儲存體表格服務, 您將需要此教學課程的連接字串。</span><span class="sxs-lookup"><span data-stu-id="c809c-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="c809c-133">您可以從 Azure 入口網站複製連接字串。</span><span class="sxs-lookup"><span data-stu-id="c809c-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="c809c-134">如需連接字串的詳細資訊, 請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="c809c-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="c809c-135">取得您的 Azure Cosmos DB 連接字串</span><span class="sxs-lookup"><span data-stu-id="c809c-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="c809c-136">如果您要連接到 Azure Cosmos DB, 在本教學課程中需要連接字串。</span><span class="sxs-lookup"><span data-stu-id="c809c-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="c809c-137">您可以從 Azure 入口網站複製連接字串。</span><span class="sxs-lookup"><span data-stu-id="c809c-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="c809c-138">在 Azure 入口網站的 Cosmos DB 帳戶中, 移至 [**設定** > ] [**連接字串**], 然後按一下 [**複製**] 按鈕以複製您的主要連接字串。</span><span class="sxs-lookup"><span data-stu-id="c809c-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="c809c-139">在本教學課程中, 請在腳本中輸入您的連接字串, 如下列範例所示:</span><span class="sxs-lookup"><span data-stu-id="c809c-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="c809c-140">不過, 這**不建議**用於實際的專案。</span><span class="sxs-lookup"><span data-stu-id="c809c-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="c809c-141">您的儲存體帳戶金鑰類似于儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="c809c-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="c809c-142">請務必小心保護您的儲存體帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="c809c-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="c809c-143">請避免將它散發給其他使用者、進行硬式編碼, 或將它儲存在其他人可以存取的純文字檔案中。</span><span class="sxs-lookup"><span data-stu-id="c809c-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="c809c-144">如果您認為金鑰可能遭到入侵, 您可以使用 Azure 入口網站重新產生金鑰。</span><span class="sxs-lookup"><span data-stu-id="c809c-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="c809c-145">對於實際的應用程式而言, 維護儲存體連接字串的最佳方式是在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="c809c-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="c809c-146">若要從設定檔提取連接字串, 您可以執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="c809c-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="c809c-147">使用 Azure Configuration Manager 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="c809c-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="c809c-148">您也可以使用 API (例如 .NET Framework 的`ConfigurationManager`類型)。</span><span class="sxs-lookup"><span data-stu-id="c809c-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="c809c-149">剖析連接字串</span><span class="sxs-lookup"><span data-stu-id="c809c-149">Parse the connection string</span></span>

<span data-ttu-id="c809c-150">若要剖析連接字串, 請使用:</span><span class="sxs-lookup"><span data-stu-id="c809c-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="c809c-151">這會傳回`CloudStorageAccount`。</span><span class="sxs-lookup"><span data-stu-id="c809c-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="c809c-152">建立表格服務用戶端</span><span class="sxs-lookup"><span data-stu-id="c809c-152">Create the Table service client</span></span>

<span data-ttu-id="c809c-153">`CloudTableClient`類別可讓您取得資料表儲存體中的資料表和實體。</span><span class="sxs-lookup"><span data-stu-id="c809c-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="c809c-154">以下是建立服務用戶端的其中一種方式:</span><span class="sxs-lookup"><span data-stu-id="c809c-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="c809c-155">現在您已準備好撰寫程式碼, 以讀取資料並將資料寫入資料表儲存體。</span><span class="sxs-lookup"><span data-stu-id="c809c-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="c809c-156">建立資料表</span><span class="sxs-lookup"><span data-stu-id="c809c-156">Create a table</span></span>

<span data-ttu-id="c809c-157">這個範例示範如何建立資料表 (如果尚未存在):</span><span class="sxs-lookup"><span data-stu-id="c809c-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="c809c-158">將實體新增至資料表</span><span class="sxs-lookup"><span data-stu-id="c809c-158">Add an entity to a table</span></span>

<span data-ttu-id="c809c-159">實體必須具有繼承自`TableEntity`的類型。</span><span class="sxs-lookup"><span data-stu-id="c809c-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="c809c-160">您可以使用`TableEntity`任何想要的方式來擴充, 但您的型別*必須*有不限參數的函式。</span><span class="sxs-lookup"><span data-stu-id="c809c-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="c809c-161">只有具有`get`和`set`的屬性會儲存在您的 Azure 資料表中。</span><span class="sxs-lookup"><span data-stu-id="c809c-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="c809c-162">實體的資料分割和資料列索引鍵可唯一識別資料表中的實體。</span><span class="sxs-lookup"><span data-stu-id="c809c-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="c809c-163">具有相同資料分割索引鍵的實體查詢速度可以比具有不同分割區索引鍵的實體更快, 但使用不同的分割區索引鍵可提供平行作業的更高擴充性。</span><span class="sxs-lookup"><span data-stu-id="c809c-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="c809c-164">以下是`Customer` `lastName`使用做為資料分割索引鍵和`firstName`作為資料列索引鍵的範例。</span><span class="sxs-lookup"><span data-stu-id="c809c-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="c809c-165">現在, `Customer`將加入至資料表。</span><span class="sxs-lookup"><span data-stu-id="c809c-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="c809c-166">若要這麼做, 請`TableOperation`建立在資料表上執行的。</span><span class="sxs-lookup"><span data-stu-id="c809c-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="c809c-167">在此情況下, 您會`Insert`建立作業。</span><span class="sxs-lookup"><span data-stu-id="c809c-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="c809c-168">插入實體批次</span><span class="sxs-lookup"><span data-stu-id="c809c-168">Insert a batch of entities</span></span>

<span data-ttu-id="c809c-169">您可以使用單一寫入作業, 將一批實體插入資料表。</span><span class="sxs-lookup"><span data-stu-id="c809c-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="c809c-170">批次作業可讓您將作業結合成單一執行, 但有一些限制:</span><span class="sxs-lookup"><span data-stu-id="c809c-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="c809c-171">您可以在相同的批次作業中執行更新、刪除和插入。</span><span class="sxs-lookup"><span data-stu-id="c809c-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="c809c-172">批次作業最多可包含100個實體。</span><span class="sxs-lookup"><span data-stu-id="c809c-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="c809c-173">批次作業中的所有實體都必須具有相同的分割區索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c809c-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="c809c-174">雖然您可以在批次作業中執行查詢, 但它必須是批次中唯一的作業。</span><span class="sxs-lookup"><span data-stu-id="c809c-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="c809c-175">以下的一些程式碼會將兩個插入組合成一個批次作業:</span><span class="sxs-lookup"><span data-stu-id="c809c-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="c809c-176">取出資料分割中的所有實體</span><span class="sxs-lookup"><span data-stu-id="c809c-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="c809c-177">若要查詢資料表以取得資料分割中的所有實體, `TableQuery`請使用物件。</span><span class="sxs-lookup"><span data-stu-id="c809c-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="c809c-178">在這裡, 您會篩選 "Smith" 為分割區索引鍵的實體。</span><span class="sxs-lookup"><span data-stu-id="c809c-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="c809c-179">您現在會列印結果:</span><span class="sxs-lookup"><span data-stu-id="c809c-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="c809c-180">取出分割區中的實體範圍</span><span class="sxs-lookup"><span data-stu-id="c809c-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="c809c-181">如果您不想要查詢資料分割中的所有實體, 您可以結合資料分割索引鍵篩選與資料列索引鍵篩選來指定範圍。</span><span class="sxs-lookup"><span data-stu-id="c809c-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="c809c-182">在這裡, 您會使用兩個篩選器來取得 "Smith" 資料分割中的所有實體, 其中的資料列索引鍵 (名字) 是以字母前面的 "M" 開頭。</span><span class="sxs-lookup"><span data-stu-id="c809c-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="c809c-183">您現在會列印結果:</span><span class="sxs-lookup"><span data-stu-id="c809c-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="c809c-184">取得單一實體</span><span class="sxs-lookup"><span data-stu-id="c809c-184">Retrieve a single entity</span></span>

<span data-ttu-id="c809c-185">您可以撰寫查詢來取出單一的特定實體。</span><span class="sxs-lookup"><span data-stu-id="c809c-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="c809c-186">在這裡, 您會`TableOperation`使用來指定客戶 "Ben Smith"。</span><span class="sxs-lookup"><span data-stu-id="c809c-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="c809c-187">而不是集合, 您會取回`Customer`。</span><span class="sxs-lookup"><span data-stu-id="c809c-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="c809c-188">在查詢中同時指定資料分割索引鍵和資料列索引鍵, 是從表格服務取得單一實體的最快方式。</span><span class="sxs-lookup"><span data-stu-id="c809c-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="c809c-189">您現在會列印結果:</span><span class="sxs-lookup"><span data-stu-id="c809c-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a><span data-ttu-id="c809c-190">取代實體</span><span class="sxs-lookup"><span data-stu-id="c809c-190">Replace an entity</span></span>

<span data-ttu-id="c809c-191">若要更新實體, 請從表格服務取出它、修改實體物件, 然後使用`Replace`作業將變更儲存回表格服務。</span><span class="sxs-lookup"><span data-stu-id="c809c-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="c809c-192">這會導致在伺服器上完全取代實體, 除非伺服器上的實體自抓取以來已變更, 在這種情況下, 作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="c809c-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="c809c-193">此失敗是為了防止您的應用程式不小心覆寫其他來源的變更。</span><span class="sxs-lookup"><span data-stu-id="c809c-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="c809c-194">插入或取代實體</span><span class="sxs-lookup"><span data-stu-id="c809c-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="c809c-195">有時候, 您不知道實體是否存在於資料表中。</span><span class="sxs-lookup"><span data-stu-id="c809c-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="c809c-196">如果有的話, 就不再需要儲存在其中的目前值。</span><span class="sxs-lookup"><span data-stu-id="c809c-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="c809c-197">您可以使用`InsertOrReplace`來建立實體, 或將它取代 (如果存在的話), 不論其狀態為何。</span><span class="sxs-lookup"><span data-stu-id="c809c-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="c809c-198">查詢實體屬性的子集</span><span class="sxs-lookup"><span data-stu-id="c809c-198">Query a subset of entity properties</span></span>

<span data-ttu-id="c809c-199">資料表查詢可以只從實體中抓取幾個屬性, 而不是所有的屬性。</span><span class="sxs-lookup"><span data-stu-id="c809c-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="c809c-200">這項稱為「投射」的技術可以改善查詢效能, 特別是針對大型實體。</span><span class="sxs-lookup"><span data-stu-id="c809c-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="c809c-201">在這裡, 您只會使用`DynamicTableEntity`和`EntityResolver`傳回電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="c809c-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="c809c-202">請注意, 在本機儲存體模擬器上不支援投影, 因此只有當您在表格服務上使用帳戶時, 此程式碼才會執行。</span><span class="sxs-lookup"><span data-stu-id="c809c-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="c809c-203">以非同步方式取出頁面中的實體</span><span class="sxs-lookup"><span data-stu-id="c809c-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="c809c-204">如果您要讀取大量實體, 而您想要在抓取時處理它們, 而不是等待它們全部傳回, 您可以使用分段的查詢。</span><span class="sxs-lookup"><span data-stu-id="c809c-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="c809c-205">在這裡, 您會使用非同步工作流程, 在頁面中傳回結果, 如此當您等候一組大型結果傳回時, 執行就不會遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="c809c-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="c809c-206">您現在會同步執行此計算:</span><span class="sxs-lookup"><span data-stu-id="c809c-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="c809c-207">刪除實體</span><span class="sxs-lookup"><span data-stu-id="c809c-207">Delete an entity</span></span>

<span data-ttu-id="c809c-208">您可以在抓取實體之後將其刪除。</span><span class="sxs-lookup"><span data-stu-id="c809c-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="c809c-209">就像更新實體一樣, 如果實體在您抓取之後已經變更, 這就會失敗。</span><span class="sxs-lookup"><span data-stu-id="c809c-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="c809c-210">刪除資料表</span><span class="sxs-lookup"><span data-stu-id="c809c-210">Delete a table</span></span>

<span data-ttu-id="c809c-211">您可以從儲存體帳戶刪除資料表。</span><span class="sxs-lookup"><span data-stu-id="c809c-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="c809c-212">刪除之後的一段時間, 將無法重新建立已刪除的資料表。</span><span class="sxs-lookup"><span data-stu-id="c809c-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="c809c-213">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c809c-213">Next steps</span></span>

<span data-ttu-id="c809c-214">既然您已瞭解資料表儲存體的基本概念, 請遵循下列連結以瞭解更複雜的儲存工作和 Azure Cosmos DB 的資料表 API。</span><span class="sxs-lookup"><span data-stu-id="c809c-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="c809c-215">Azure Cosmos DB 資料表 API 簡介</span><span class="sxs-lookup"><span data-stu-id="c809c-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="c809c-216">適用于 .NET 的儲存體用戶端程式庫參考</span><span class="sxs-lookup"><span data-stu-id="c809c-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [<span data-ttu-id="c809c-217">Azure 儲存體型別提供者</span><span class="sxs-lookup"><span data-stu-id="c809c-217">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="c809c-218">Azure 儲存體小組的 Blog</span><span class="sxs-lookup"><span data-stu-id="c809c-218">Azure Storage Team Blog</span></span>](https://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="c809c-219">設定連接字串</span><span class="sxs-lookup"><span data-stu-id="c809c-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="c809c-220">在 .NET 中使用 Azure 表格儲存體的消費者入門</span><span class="sxs-lookup"><span data-stu-id="c809c-220">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
