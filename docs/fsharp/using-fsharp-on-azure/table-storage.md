---
title: "開始使用 Azure 資料表儲存體使用 F #"
description: "將結構化的資料儲存在雲端中使用 Azure 資料表儲存體，NoSQL 資料存放區。"
keywords: "visual f #、 f #，功能性程式設計，.NET 中，.NET Core，Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9e5d6cea-a98c-461e-a5cc-75f1d154eafd
ms.openlocfilehash: e003f537c6f0f85b3b0ba932655ae2a54c980bc5
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2018
---
# <a name="get-started-with-azure-table-storage-using-f"></a><span data-ttu-id="db87b-104">開始使用 Azure 資料表儲存體使用 F #</span><span class="sxs-lookup"><span data-stu-id="db87b-104">Get started with Azure Table storage using F#</span></span> #

<span data-ttu-id="db87b-105">Azure 資料表儲存體是結構化的 NoSQL 資料存放在雲端服務。</span><span class="sxs-lookup"><span data-stu-id="db87b-105">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="db87b-106">資料表儲存體是 schemaless 設計的索引鍵/屬性存放區。</span><span class="sxs-lookup"><span data-stu-id="db87b-106">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="db87b-107">因為資料表儲存體是 schemaless，很容易就能為您的應用程式 evolve 的需求調整您的資料。</span><span class="sxs-lookup"><span data-stu-id="db87b-107">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="db87b-108">資料的存取權非常快速且符合成本效益的所有種類的應用程式。</span><span class="sxs-lookup"><span data-stu-id="db87b-108">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="db87b-109">資料表儲存體通常是遠低於成本中類似資料磁碟區的傳統 SQL。</span><span class="sxs-lookup"><span data-stu-id="db87b-109">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="db87b-110">您可以使用資料表儲存體來儲存彈性的資料集，例如 web 應用程式、 通訊錄，裝置資訊和任何其他類型的服務所需的中繼資料的使用者資料。</span><span class="sxs-lookup"><span data-stu-id="db87b-110">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="db87b-111">您可以將任意數目的實體儲存在資料表中，而且儲存體帳戶包含任何數量的資料表，儲存體帳戶的容量上限為止。</span><span class="sxs-lookup"><span data-stu-id="db87b-111">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="db87b-112">關於本教學課程</span><span class="sxs-lookup"><span data-stu-id="db87b-112">About this tutorial</span></span>

<span data-ttu-id="db87b-113">本教學課程會示範如何撰寫 F # 程式碼來執行一些常見的工作，使用 Azure 資料表儲存體，包括建立和刪除資料表並插入、 更新、 刪除和查詢資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="db87b-113">This tutorial shows how to write F# code to do some common tasks using Azure Table storage, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

<span data-ttu-id="db87b-114">資料表儲存體概念的概觀，請參閱[資料表儲存體的.NET 指南](/azure/storage/storage-dotnet-how-to-use-tables)</span><span class="sxs-lookup"><span data-stu-id="db87b-114">For a conceptual overview of table storage, please see [the .NET guide for table storage](/azure/storage/storage-dotnet-how-to-use-tables)</span></span>

## <a name="prerequisites"></a><span data-ttu-id="db87b-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="db87b-115">Prerequisites</span></span>

<span data-ttu-id="db87b-116">若要使用本指南，您必須先[建立 Azure 儲存體帳戶](/azure/storage/storage-create-storage-account)。</span><span class="sxs-lookup"><span data-stu-id="db87b-116">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="db87b-117">您還需要此帳戶的儲存體存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="db87b-117">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="db87b-118">建立 F # 指令碼，並開始 F # Interactive</span><span class="sxs-lookup"><span data-stu-id="db87b-118">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="db87b-119">這篇文章中的範例可以用於 F # 應用程式或 F # 指令碼。</span><span class="sxs-lookup"><span data-stu-id="db87b-119">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="db87b-120">若要建立 F # 指令碼，建立檔案之`.fsx`擴充功能，例如`tables.fsx`，F # 開發環境中。</span><span class="sxs-lookup"><span data-stu-id="db87b-120">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="db87b-121">接下來，使用[封裝管理員](package-management.md)例如[Paket](https://fsprojects.github.io/Paket/)或[NuGet](https://www.nuget.org/)安裝`WindowsAzure.Storage`封裝和參考`WindowsAzure.Storage.dll`指令碼使用`#r`指示詞。</span><span class="sxs-lookup"><span data-stu-id="db87b-121">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="db87b-122">執行一次的 'Microsoft.WindowsAzure.ConfigurationManager' 以取得 Microsoft.Azure 命名空間。</span><span class="sxs-lookup"><span data-stu-id="db87b-122">Do it again for \`Microsoft.WindowsAzure.ConfigurationManager' in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="db87b-123">加入命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="db87b-123">Add namespace declarations</span></span>

<span data-ttu-id="db87b-124">加入下列`open`上方的陳述式`tables.fsx`檔案：</span><span class="sxs-lookup"><span data-stu-id="db87b-124">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="db87b-125">取得連接字串</span><span class="sxs-lookup"><span data-stu-id="db87b-125">Get your connection string</span></span>

<span data-ttu-id="db87b-126">此教學課程中，您將需要 Azure 儲存體連接字串。</span><span class="sxs-lookup"><span data-stu-id="db87b-126">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="db87b-127">如需連接字串的詳細資訊，請參閱[設定儲存體連接字串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="db87b-127">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="db87b-128">教學課程中，您會輸入您的連接字串中指令碼中，像這樣：</span><span class="sxs-lookup"><span data-stu-id="db87b-128">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="db87b-129">不過，這是**不建議**用於真實的專案。</span><span class="sxs-lookup"><span data-stu-id="db87b-129">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="db87b-130">儲存體帳戶金鑰是類似於儲存體帳戶的根密碼。</span><span class="sxs-lookup"><span data-stu-id="db87b-130">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="db87b-131">一律為保護您的儲存體帳戶金鑰，請小心。</span><span class="sxs-lookup"><span data-stu-id="db87b-131">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="db87b-132">避免將其散發給其他使用者，硬式編碼，或將它儲存在其他人可以存取純文字檔案。</span><span class="sxs-lookup"><span data-stu-id="db87b-132">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="db87b-133">您可以重新產生您使用 Azure 入口網站，如果您認為可能已受到危害的金鑰。</span><span class="sxs-lookup"><span data-stu-id="db87b-133">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="db87b-134">用於真實的應用程式，以維護您的儲存體連接字串的最佳方式是在組態檔中。</span><span class="sxs-lookup"><span data-stu-id="db87b-134">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="db87b-135">若要從組態檔擷取連接字串，您可以：</span><span class="sxs-lookup"><span data-stu-id="db87b-135">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="db87b-136">使用 Azure 組態管理員是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="db87b-136">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="db87b-137">您也可以使用例如.NET Framework API`ConfigurationManager`型別。</span><span class="sxs-lookup"><span data-stu-id="db87b-137">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="db87b-138">剖析連接字串</span><span class="sxs-lookup"><span data-stu-id="db87b-138">Parse the connection string</span></span>

<span data-ttu-id="db87b-139">若要剖析的連接字串，使用：</span><span class="sxs-lookup"><span data-stu-id="db87b-139">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="db87b-140">這會傳回`CloudStorageAccount`。</span><span class="sxs-lookup"><span data-stu-id="db87b-140">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="db87b-141">建立表格服務用戶端</span><span class="sxs-lookup"><span data-stu-id="db87b-141">Create the Table service client</span></span>

<span data-ttu-id="db87b-142">`CloudTableClient`類別可讓您擷取的資料表和資料表儲存體中儲存的實體。</span><span class="sxs-lookup"><span data-stu-id="db87b-142">The `CloudTableClient` class enables you to retrieve tables and entities stored in Table storage.</span></span> <span data-ttu-id="db87b-143">以下是如何建立服務用戶端：</span><span class="sxs-lookup"><span data-stu-id="db87b-143">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="db87b-144">現在您已準備好開始撰寫程式碼讀取資料，並將資料寫入資料表儲存體。</span><span class="sxs-lookup"><span data-stu-id="db87b-144">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

## <a name="create-a-table"></a><span data-ttu-id="db87b-145">建立資料表</span><span class="sxs-lookup"><span data-stu-id="db87b-145">Create a table</span></span>

<span data-ttu-id="db87b-146">這個範例示範如何建立資料表，如果不存在：</span><span class="sxs-lookup"><span data-stu-id="db87b-146">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

## <a name="add-an-entity-to-a-table"></a><span data-ttu-id="db87b-147">將實體加入至資料表</span><span class="sxs-lookup"><span data-stu-id="db87b-147">Add an entity to a table</span></span>

<span data-ttu-id="db87b-148">實體必須要有型別繼承自`TableEntity`。</span><span class="sxs-lookup"><span data-stu-id="db87b-148">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="db87b-149">您可以擴充`TableEntity`任何方式，但您的型別*必須*具有無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="db87b-149">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="db87b-150">只有屬性同時具有`get`和`set`會儲存在 Azure 資料表。</span><span class="sxs-lookup"><span data-stu-id="db87b-150">Only properties that have both `get` and `set` will be stored in your Azure Table.</span></span>

<span data-ttu-id="db87b-151">實體的資料分割和資料列索引鍵唯一識別資料表中的實體。</span><span class="sxs-lookup"><span data-stu-id="db87b-151">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="db87b-152">具有相同的資料分割索引鍵的實體可以進行查詢速度比的不同資料分割索引鍵，但使用不同的資料分割索引鍵可讓平行作業的更佳的延展性。</span><span class="sxs-lookup"><span data-stu-id="db87b-152">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="db87b-153">以下是範例`Customer`使用`lastName`做為資料分割索引鍵和`firstName`做為資料列索引鍵。</span><span class="sxs-lookup"><span data-stu-id="db87b-153">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="db87b-154">現在我們將新增我們`Customer`至資料表。</span><span class="sxs-lookup"><span data-stu-id="db87b-154">Now we'll add our `Customer` to the table.</span></span> <span data-ttu-id="db87b-155">若要這樣做，您建立`TableOperation`用以在資料表上執行。</span><span class="sxs-lookup"><span data-stu-id="db87b-155">To do so, you create a `TableOperation` that will execute on the table.</span></span> <span data-ttu-id="db87b-156">在此情況下，您建立`Insert`作業。</span><span class="sxs-lookup"><span data-stu-id="db87b-156">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

## <a name="insert-a-batch-of-entities"></a><span data-ttu-id="db87b-157">插入實體批次</span><span class="sxs-lookup"><span data-stu-id="db87b-157">Insert a batch of entities</span></span>

<span data-ttu-id="db87b-158">您可以將實體批次插入資料表中使用單一寫入作業。</span><span class="sxs-lookup"><span data-stu-id="db87b-158">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="db87b-159">批次作業可讓您將作業結合成單一的執行，但具有一些限制：</span><span class="sxs-lookup"><span data-stu-id="db87b-159">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="db87b-160">您可以執行更新、 刪除和插入相同的批次作業中。</span><span class="sxs-lookup"><span data-stu-id="db87b-160">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="db87b-161">批次作業可以包含多達 100 個項目。</span><span class="sxs-lookup"><span data-stu-id="db87b-161">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="db87b-162">批次作業中的所有實體必須都有相同的資料分割索引鍵。</span><span class="sxs-lookup"><span data-stu-id="db87b-162">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="db87b-163">雖然也可以在批次作業中執行查詢，但是它必須是批次中唯一的作業。</span><span class="sxs-lookup"><span data-stu-id="db87b-163">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="db87b-164">以下是一些結合成一個批次作業的兩個插入的程式碼：</span><span class="sxs-lookup"><span data-stu-id="db87b-164">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

## <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="db87b-165">擷取資料分割中的所有實體</span><span class="sxs-lookup"><span data-stu-id="db87b-165">Retrieve all entities in a partition</span></span>

<span data-ttu-id="db87b-166">若要查詢的資料表資料分割中的所有實體，請使用`TableQuery`物件。</span><span class="sxs-lookup"><span data-stu-id="db87b-166">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="db87b-167">在這裡，您篩選實體"Buster"所在的資料分割索引鍵。</span><span class="sxs-lookup"><span data-stu-id="db87b-167">Here, you filter for entities where "Buster" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L80)]

<span data-ttu-id="db87b-168">您現在會列印結果：</span><span class="sxs-lookup"><span data-stu-id="db87b-168">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


## <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="db87b-169">擷取某個範圍的資料分割中的實體</span><span class="sxs-lookup"><span data-stu-id="db87b-169">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="db87b-170">如果您不想要查詢資料分割中的所有實體，您可以指定範圍，藉由結合資料分割索引鍵篩選，資料列索引鍵的篩選。</span><span class="sxs-lookup"><span data-stu-id="db87b-170">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="db87b-171">在這裡，您使用兩個篩選條件 」 Buster 」 資料分割中取得所有實體資料列索引鍵 （第一個名稱） 開始的位置以字母"M"中字母之前。</span><span class="sxs-lookup"><span data-stu-id="db87b-171">Here, you use two filters to get all entities in the "Buster" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="db87b-172">您現在會列印結果：</span><span class="sxs-lookup"><span data-stu-id="db87b-172">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

## <a name="retrieve-a-single-entity"></a><span data-ttu-id="db87b-173">擷取單一實體</span><span class="sxs-lookup"><span data-stu-id="db87b-173">Retrieve a single entity</span></span>

<span data-ttu-id="db87b-174">您可以撰寫查詢以擷取單一的特定實體。</span><span class="sxs-lookup"><span data-stu-id="db87b-174">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="db87b-175">在此，您可以使用`TableOperation`來指定客戶"Larry Buster"。</span><span class="sxs-lookup"><span data-stu-id="db87b-175">Here, you use a `TableOperation` to specify the customer "Larry Buster".</span></span> <span data-ttu-id="db87b-176">而不是集合，您會回到`Customer`。</span><span class="sxs-lookup"><span data-stu-id="db87b-176">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="db87b-177">在查詢中指定資料分割索引鍵和資料列索引鍵是最快的方法來擷取與表格服務的單一實體。</span><span class="sxs-lookup"><span data-stu-id="db87b-177">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="db87b-178">您現在會列印結果：</span><span class="sxs-lookup"><span data-stu-id="db87b-178">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


## <a name="replace-an-entity"></a><span data-ttu-id="db87b-179">取代實體</span><span class="sxs-lookup"><span data-stu-id="db87b-179">Replace an entity</span></span>

<span data-ttu-id="db87b-180">若要更新實體，擷取與表格服務、 修改實體物件，以及將變更儲存至表格服務會使用`Replace`作業。</span><span class="sxs-lookup"><span data-stu-id="db87b-180">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="db87b-181">除非變更伺服器上的實體自擷取後，作業會失敗，在此情況下，這會導致在伺服器上，完全取代實體。</span><span class="sxs-lookup"><span data-stu-id="db87b-181">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation will fail.</span></span> <span data-ttu-id="db87b-182">此失敗是為了防止您的應用程式不小心覆寫從其他來源的變更。</span><span class="sxs-lookup"><span data-stu-id="db87b-182">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

## <a name="insert-or-replace-an-entity"></a><span data-ttu-id="db87b-183">插入或取代實體</span><span class="sxs-lookup"><span data-stu-id="db87b-183">Insert-or-replace an entity</span></span>

<span data-ttu-id="db87b-184">有時候，您不知道實體是否已存在資料表中或不。</span><span class="sxs-lookup"><span data-stu-id="db87b-184">Sometimes, you don't know if the entity exists in the table or not.</span></span> <span data-ttu-id="db87b-185">而且，若是如此，不再需要儲存在它的目前值。</span><span class="sxs-lookup"><span data-stu-id="db87b-185">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="db87b-186">您可以使用`InsertOrReplace`建立實體，或取代它，如果存在的話，不論其狀態。</span><span class="sxs-lookup"><span data-stu-id="db87b-186">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L140)]

## <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="db87b-187">查詢實體屬性的子集</span><span class="sxs-lookup"><span data-stu-id="db87b-187">Query a subset of entity properties</span></span>

<span data-ttu-id="db87b-188">資料表查詢可以擷取只需要幾個屬性，而不是所有的這些實體。</span><span class="sxs-lookup"><span data-stu-id="db87b-188">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="db87b-189">這項技巧，呼叫投影，可以改善查詢效能，特別是大型的實體。</span><span class="sxs-lookup"><span data-stu-id="db87b-189">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="db87b-190">您在這裡，傳回僅電子郵件地址使用`DynamicTableEntity`和`EntityResolver`。</span><span class="sxs-lookup"><span data-stu-id="db87b-190">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="db87b-191">請注意，投影不支援在本機儲存體模擬器，以便在表格服務上使用的帳戶時，才執行此程式碼。</span><span class="sxs-lookup"><span data-stu-id="db87b-191">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L146-L157)]

## <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="db87b-192">以非同步方式擷取頁面中的實體</span><span class="sxs-lookup"><span data-stu-id="db87b-192">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="db87b-193">如果您正在閱讀大量實體，而且您想要擷取，而非等待它們全部傳回，您可以使用分割的查詢時進行處理。</span><span class="sxs-lookup"><span data-stu-id="db87b-193">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="db87b-194">在這裡，您傳回的結果頁面中使用的非同步工作流程，因此正在等待將大量要傳回的結果時，不會封鎖執行。</span><span class="sxs-lookup"><span data-stu-id="db87b-194">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L177)]

<span data-ttu-id="db87b-195">您現在執行這項計算以同步方式：</span><span class="sxs-lookup"><span data-stu-id="db87b-195">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L179-L179)]

## <a name="delete-an-entity"></a><span data-ttu-id="db87b-196">刪除實體</span><span class="sxs-lookup"><span data-stu-id="db87b-196">Delete an entity</span></span>

<span data-ttu-id="db87b-197">您可以在擷取之後，刪除實體。</span><span class="sxs-lookup"><span data-stu-id="db87b-197">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="db87b-198">與更新實體，這將會失敗之後，如果實體已變更您擷取它。</span><span class="sxs-lookup"><span data-stu-id="db87b-198">As with updating an entity, this will fail if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L185-L186)]

## <a name="delete-a-table"></a><span data-ttu-id="db87b-199">刪除資料表</span><span class="sxs-lookup"><span data-stu-id="db87b-199">Delete a table</span></span>

<span data-ttu-id="db87b-200">您可以從儲存體帳戶刪除資料表。</span><span class="sxs-lookup"><span data-stu-id="db87b-200">You can delete a table from a storage account.</span></span> <span data-ttu-id="db87b-201">已刪除的資料表將無法在重新建立此一段時間後刪除。</span><span class="sxs-lookup"><span data-stu-id="db87b-201">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L192-L192)]

## <a name="next-steps"></a><span data-ttu-id="db87b-202">後續步驟</span><span class="sxs-lookup"><span data-stu-id="db87b-202">Next steps</span></span>

<span data-ttu-id="db87b-203">既然您已學到的資料表儲存體的基本概念，請遵循下列連結，以了解更複雜的儲存體工作：</span><span class="sxs-lookup"><span data-stu-id="db87b-203">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks:</span></span>

- [<span data-ttu-id="db87b-204">適用於.NET 的 azure 儲存體 Api</span><span class="sxs-lookup"><span data-stu-id="db87b-204">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="db87b-205">Azure 儲存體型別提供者</span><span class="sxs-lookup"><span data-stu-id="db87b-205">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="db87b-206">Azure 儲存體團隊部落格</span><span class="sxs-lookup"><span data-stu-id="db87b-206">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="db87b-207">設定 Azure 儲存體連接字串</span><span class="sxs-lookup"><span data-stu-id="db87b-207">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="db87b-208">在.NET 的 Azure 資料表儲存體使用者入門</span><span class="sxs-lookup"><span data-stu-id="db87b-208">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/documentation/samples/storage-table-dotnet-getting-started/)
