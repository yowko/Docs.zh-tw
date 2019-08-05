---
title: 使用 NoSQL 資料庫作為持續性基礎結構
description: .NET 微服務：容器化 .NET 應用程式的架構 | 了解一般的 NoSql 資料庫用法和特定的 Azure Cosmos DB 用法，作為實作持續性選項。
ms.date: 10/08/2018
ms.openlocfilehash: 023904319651ec91000ff036850c773f66d1a267
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676335"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="1f725-103">使用 NoSQL 資料庫作為持續性基礎結構</span><span class="sxs-lookup"><span data-stu-id="1f725-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="1f725-104">當您將 NoSQL 資料庫用於基礎結構資料層時，通常不會使用 Entity Framework Core 這類 ORM。</span><span class="sxs-lookup"><span data-stu-id="1f725-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="1f725-105">相反地，您使用 NoSQL 引擎所提供的 API (例如 Azure Cosmos DB、MongoDB、Cassandra、RavenDB、CouchDB 或 Azure Storage Tables)。</span><span class="sxs-lookup"><span data-stu-id="1f725-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="1f725-106">不過，如果您使用 NoSQL 資料庫，特別是 Azure Cosmos DB、CouchDB 或 RavenDB 這類文件導向資料庫，則使用 DDD 彙總來設計模型的方式在識別彙總根、子實體類別和值物件類別方面有部分類似 EF Core 中的執行方式。</span><span class="sxs-lookup"><span data-stu-id="1f725-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="1f725-107">但最後資料庫選項會影響您的設計。</span><span class="sxs-lookup"><span data-stu-id="1f725-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="1f725-108">當您使用文件導向資料庫時，可以將彙總實作為以 JSON 或另一種格式序列化的單一文件。</span><span class="sxs-lookup"><span data-stu-id="1f725-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="1f725-109">不過，從領域模型程式碼觀點，資料庫的使用是透明的。</span><span class="sxs-lookup"><span data-stu-id="1f725-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="1f725-110">使用 NoSQL 資料庫時，您仍然會使用實體類別和彙總根類別，但彈性大於使用 EF Core 時，因為持續性不是關聯式。</span><span class="sxs-lookup"><span data-stu-id="1f725-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="1f725-111">差異在於如何持續保存該模型。</span><span class="sxs-lookup"><span data-stu-id="1f725-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="1f725-112">如果您實作根據 POCO 實體類別且無特定基礎結構持續性的領域模型，則可能可以移至不同的持續性基礎結構，即使是從關聯式到 NoSQL 也是一樣。</span><span class="sxs-lookup"><span data-stu-id="1f725-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="1f725-113">不過，這不應該是您的目標。</span><span class="sxs-lookup"><span data-stu-id="1f725-113">However, that should not be your goal.</span></span> <span data-ttu-id="1f725-114">不同資料庫技術中一律會有條件約束和取捨，因此關聯式或 NoSQL 資料庫不能使用同一模型。</span><span class="sxs-lookup"><span data-stu-id="1f725-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="1f725-115">變更持續性模型不簡單，因為交易和持續性作業大不相同。</span><span class="sxs-lookup"><span data-stu-id="1f725-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="1f725-116">例如，在文件導向資料庫中，彙總根可以有多個子集合屬性。</span><span class="sxs-lookup"><span data-stu-id="1f725-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="1f725-117">在關聯式資料庫中，查詢多個子集合屬性不易最佳化，因為會從 EF 會取回 UNION ALL SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1f725-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="1f725-118">關聯式資料庫或 NoSQL 資料庫有相同的領域模型並不簡單，您也不應該嘗試這麼做。</span><span class="sxs-lookup"><span data-stu-id="1f725-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="1f725-119">實際上，您必須透過了解要如何使用每個特定資料庫中的資料來設計模型。</span><span class="sxs-lookup"><span data-stu-id="1f725-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="1f725-120">使用 NoSQL 資料庫時的好處是實體更正規化，因此您未設定資料表對應。</span><span class="sxs-lookup"><span data-stu-id="1f725-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="1f725-121">領域模型可能會比使用關聯式資料庫更有彈性。</span><span class="sxs-lookup"><span data-stu-id="1f725-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="1f725-122">當您根據彙總來設計領域模型時，移至 NoSQL 和文件導向資料庫可能會比使用關聯式資料庫更為容易，因為您所設計的彙總與文件導向資料庫中的序列化文件類似。</span><span class="sxs-lookup"><span data-stu-id="1f725-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="1f725-123">然後您可以將可能需要的所有該彙總資訊都包含在這些「包」中。</span><span class="sxs-lookup"><span data-stu-id="1f725-123">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="1f725-124">例如，下列 JSON 程式碼是使用文件導向資料庫時的訂單彙總範例實作。</span><span class="sxs-lookup"><span data-stu-id="1f725-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="1f725-125">這類似我們在 eShopOnContainers 範例中實作的訂單彙總，但其下不使用 EF Core。</span><span class="sxs-lookup"><span data-stu-id="1f725-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

```json
{
    "id": "2017001",
    "orderDate": "2/25/2017",
    "buyerId": "1234567",
    "address": [
        {
        "street": "100 One Microsoft Way",
        "city": "Redmond",
        "state": "WA",
        "zip": "98052",
        "country": "U.S."
        }
    ],
    "orderItems": [
        {"id": 20170011, "productId": "123456", "productName": ".NET T-Shirt",
        "unitPrice": 25, "units": 2, "discount": 0},
        {"id": 20170012, "productId": "123457", "productName": ".NET Mug",
        "unitPrice": 15, "units": 1, "discount": 0}
    ]
}
```

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="1f725-126">Azure Cosmos DB 和原生 Cosmos DB API 簡介</span><span class="sxs-lookup"><span data-stu-id="1f725-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="1f725-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) 是 Microsoft 的關鍵任務應用程式的全域分散式資料庫服務。</span><span class="sxs-lookup"><span data-stu-id="1f725-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="1f725-128">Azure Cosmos DB 提供[現成全域散發](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)、全球[彈性調整輸送量和儲存體](https://docs.microsoft.com/azure/cosmos-db/partition-data)、第 99 個百分位數的單一位數毫秒延遲、[五個定義良好的一致性層級](https://docs.microsoft.com/azure/cosmos-db/consistency-levels)，以及保證高可用性，全部都是透過[領先業界的 SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/) 所支援。</span><span class="sxs-lookup"><span data-stu-id="1f725-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="1f725-129">Azure Cosmos DB [自動編製資料索引](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf)，而不需要處理結構描述和索引管理。</span><span class="sxs-lookup"><span data-stu-id="1f725-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="1f725-130">它是多模型，並支援文件、鍵值、圖表和單欄式資料模型。</span><span class="sxs-lookup"><span data-stu-id="1f725-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

<span data-ttu-id="1f725-131">![Azure Cosmos DB 是全域散發的保證低延遲資料庫，可以使用四個 API 通訊協定存取。</span><span class="sxs-lookup"><span data-stu-id="1f725-131">![Azure Cosmos DB is a globally distributed guaranteed low-latency database that can be accessed with four API protocols.</span></span> <span data-ttu-id="1f725-132">](./media/image19.1.png)
**圖 7-19**。</span><span class="sxs-lookup"><span data-stu-id="1f725-132">](./media/image19.1.png)
**Figure 7-19**.</span></span> <span data-ttu-id="1f725-133">Azure Cosmos DB 全域散發</span><span class="sxs-lookup"><span data-stu-id="1f725-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="1f725-134">當您使用 C\# 模型來實作要供 Azure Cosmos DB API 使用的彙總時，彙總可能類似與 EF Core 搭配使用的 C\# POCO 類別。</span><span class="sxs-lookup"><span data-stu-id="1f725-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="1f725-135">差異在於從應用程式和基礎結構層級使用它們的方式，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="1f725-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).

Order orderAggregate = new Order
{
    Id = "2017001",
    OrderDate = new DateTime(2005, 7, 1),
    BuyerId = "1234567",
    PurchaseOrderNumber = "PO18009186470"
}

Address address = new Address
{
    Street = "100 One Microsoft Way",
    City = "Redmond",
    State = "WA",
    Zip = "98052",
    Country = "U.S."
}

orderAggregate.UpdateAddress(address);

OrderItem orderItem1 = new OrderItem
{
    Id = 20170011,
    ProductId = "123456",
    ProductName = ".NET T-Shirt",
    UnitPrice = 25,
    Units = 2,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
// *** End of Domain Model Code ***

// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, orderAggregate);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

<span data-ttu-id="1f725-136">您可以看到領域模型使用方式可能類似其在基礎結構是 EF 時於領域模型中的使用方式。</span><span class="sxs-lookup"><span data-stu-id="1f725-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="1f725-137">您仍然可以使用相同的彙總根方法來確保彙總內的一致性、非變異值和驗證。</span><span class="sxs-lookup"><span data-stu-id="1f725-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="1f725-138">不過，相較於 EF Core 程式碼或任何其他與關聯式資料庫有關的程式碼，當您將模型持續保存至 NoSQL 資料庫時，程式碼和 API 會大幅變更。</span><span class="sxs-lookup"><span data-stu-id="1f725-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="1f725-139">實作以 MongoDB 和 Azure Cosmos DB 為目標的 .NET 程式碼</span><span class="sxs-lookup"><span data-stu-id="1f725-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="1f725-140">使用 .NET 容器中的 Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="1f725-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="1f725-141">您可以透過容器中所執行的 .NET 程式碼來存取 Azure Cosmos DB 資料庫，例如來自任何其他 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1f725-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="1f725-142">例如，實作 eShopOnContainers 中的 Locations.API 和 Marketing.API 微服務，讓它們可以利用 Azure Cosmos DB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1f725-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="1f725-143">不過，從 Docker 開發環境觀點，Azure Cosmos DB 有一些限制。</span><span class="sxs-lookup"><span data-stu-id="1f725-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="1f725-144">甚至有可以在本機開發電腦 (例如 PC) 中執行的內部部署 [Azure Cosmos DB 模擬器](https://docs.microsoft.com/azure/cosmos-db/local-emulator) 時，到 2017 年晚期，它只支援 Windows，而非 Linux。</span><span class="sxs-lookup"><span data-stu-id="1f725-144">Even when there’s a on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) able to run in a local development machine (like a PC), as of late 2017, it just supports Windows, not Linux.</span></span> 

<span data-ttu-id="1f725-145">也可能在 Docker 上執行此模擬器，但只能在 Windows 容器上，而非 Linux 容器上。</span><span class="sxs-lookup"><span data-stu-id="1f725-145">There is also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="1f725-146">如果您的應用程式部署為 Linux 容器，則這是開發環境的初始障礙，因為您目前無法在 Docker for Windows 上同時部署 Linux 和 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="1f725-146">That is an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you cannot deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="1f725-147">所有要部署的容器都必須適用於 Linux 或 Windows。</span><span class="sxs-lookup"><span data-stu-id="1f725-147">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="1f725-148">開發/測試解決方案的理想且更直接部署是要可以部署作為容器的資料庫系統以及自訂容器，讓您的開發/測試環境一律保持一致。</span><span class="sxs-lookup"><span data-stu-id="1f725-148">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="1f725-149">將 MongoDB API 用於本機開發/測試 Linux/Windows 容器和 Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="1f725-149">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="1f725-150">Cosmos DB 資料庫支援 MongoDB API for .NET 以及原生 MongoDB 有線通訊協定。</span><span class="sxs-lookup"><span data-stu-id="1f725-150">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="1f725-151">這表示使用現有的驅動程式，針對 MongoDB 所撰寫的應用程式現在可以與 Cosmos DB 通訊，且使用 Cosmos DB 資料庫，而不是使用 MongoDB 資料庫，如圖 7-20 所示。</span><span class="sxs-lookup"><span data-stu-id="1f725-151">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

<span data-ttu-id="1f725-152">![Cosmos DB 支援 MongoDB API for .NET 和 MongoDB 有線通訊協定，您可以輕鬆地從 MongoDb 切換至 Cosmos DB](./media/image19.2.png)
**圖 7-20**。</span><span class="sxs-lookup"><span data-stu-id="1f725-152">![Cosmos DB supports MongoDB API for .NET and MongoDB wire protocol, you can easily switch from MongoDb to Cosmos DB.](./media/image19.2.png)
**Figure 7-20**.</span></span> <span data-ttu-id="1f725-153">使用 MongoDB API 和通訊協定存取 Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="1f725-153">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="1f725-154">這是含 Linux 容器之 Docker 環境中概念證明的極方便使用方法，因為 [MongoDB Docker 映像](https://hub.docker.com/r/_/mongo/)是支援 Docker Linux 容器和 Docker Windows 容器的多架構映像。</span><span class="sxs-lookup"><span data-stu-id="1f725-154">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="1f725-155">如下圖所示，使用 MongoDB API，eShopOnContainers 可支援 MongoDB Linux 和 Windows 容器開發本機環境，但您接著只要[變更 MongoDB 連接字串以指向 Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account)，就可以移至可擴充的 PaaS 雲端解決方案作為 Azure Cosmos DB。</span><span class="sxs-lookup"><span data-stu-id="1f725-155">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="1f725-156">![eShopOnContainers 中的位置微服務使用 MongoDB 實作，但只要變更連接字串就可以切換到 Cosmos DB。](./media/image20-bis.png)
**圖 7-21**。</span><span class="sxs-lookup"><span data-stu-id="1f725-156">![The Location microservice in eShopOnContainers is implemented using MongoDB, but can be switched over to Cosmos DB by just changing the connection string.](./media/image20-bis.png)
**Figure 7-21**.</span></span> <span data-ttu-id="1f725-157">將 MongoDB 容器用於開發環境或將 Azure Cosmos DB 用於生產環境的 eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="1f725-157">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="1f725-158">生產 Azure Cosmos DB 將會以 PaaS 和可擴充服務形式執行於 Azure 的雲端。</span><span class="sxs-lookup"><span data-stu-id="1f725-158">The production Azure Cosmos DB would be running in Azure’s cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="1f725-159">自訂 .NET Core 容器可以在本機開發 Docker 主機 (其在 Windows 10 電腦中將使用 Docker for Windows) 上執行，或部署至生產環境 (例如 Azure AKS or Azure Service Fabric 中的 Kubernetes)。</span><span class="sxs-lookup"><span data-stu-id="1f725-159">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="1f725-160">在這個第二個環境中，您只會部署 .NET Core 自訂容器，而不是 MongoDB 容器，因為您會在雲端使用 Azure Cosmos DB 處理生產環境中的資料。</span><span class="sxs-lookup"><span data-stu-id="1f725-160">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you’d be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="1f725-161">使用 MongoDB API 的清楚優點在於您的解決方案可以透過資料庫引擎 (MongoDB 或 Azure Cosmos DB) 執行，因此，移轉至不同環境應該相當簡單。</span><span class="sxs-lookup"><span data-stu-id="1f725-161">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="1f725-162">不過，有時值得使用原生 API (即原生 Cosmos DB API) 來充分利用特定資料庫引擎的功能。</span><span class="sxs-lookup"><span data-stu-id="1f725-162">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="1f725-163">如需進一步比較只在雲端中使用 MongoDB 與 Cosmos DB，請參閱[在此頁面中使用 Azure Cosmos DB 的優點](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)。</span><span class="sxs-lookup"><span data-stu-id="1f725-163">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span> 

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="1f725-164">分析用於生產應用程式的方法：MongoDB API 與Cosmos DB API</span><span class="sxs-lookup"><span data-stu-id="1f725-164">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="1f725-165">在 eShopOnContainers 中，我們將使用 MongoDB API，因為我們的優先順序本質上是擁有使用也可處理 Azure Cosmos DB 之 NoSQL 資料庫的一致開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="1f725-165">In eShopOnContainers, we’re using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="1f725-166">不過，如果您打算使用 MongoDB API 存取 Azure 中的 Azure Cosmos DB 作為生產應用程式，則應該分析使用 MongoDB API 存取 Azure Cosmos DB 資料庫時與使用原生 Azure Cosmos DB API 相較之下的功能和效能差異。</span><span class="sxs-lookup"><span data-stu-id="1f725-166">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="1f725-167">如果類似，則您可以使用 MongoDB API，且獲得同時支援兩個 NoSQL 資料庫引擎的優點。</span><span class="sxs-lookup"><span data-stu-id="1f725-167">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="1f725-168">您也可以使用 MongoDB 叢集作為 Azure 雲端中的生產資料庫與 [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service)。</span><span class="sxs-lookup"><span data-stu-id="1f725-168">You could also use MongoDB clusters as the production database in Azure’s cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="1f725-169">但是，它不是 Microsoft 提供的 PaaS 服務。</span><span class="sxs-lookup"><span data-stu-id="1f725-169">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="1f725-170">在此情況下，Azure 只會託管來自 MongoDB 的那個解決方案。</span><span class="sxs-lookup"><span data-stu-id="1f725-170">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="1f725-171">基本上，這只是免責聲明，指出您不應該一律對 Azure Cosmos DB 使用 MongoDB API，就像在 eShopOnContainers 中一樣，因為它對 Linux 容器而言是方便使用的選擇。</span><span class="sxs-lookup"><span data-stu-id="1f725-171">Basically, this is just a disclaimer stating that you shouldn’t always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="1f725-172">這項決策應該根據您需要為生產應用程式所執行的特定需求和測試。</span><span class="sxs-lookup"><span data-stu-id="1f725-172">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a><span data-ttu-id="1f725-173">程式碼：在 .NET Core 應用程式中使用 MongoDB API</span><span class="sxs-lookup"><span data-stu-id="1f725-173">The code: Use MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="1f725-174">MongoDB API for .NET 是以您需要新增至專案的 NuGet 套件為基礎，如同下圖所示的 Locations.API 專案中一樣。</span><span class="sxs-lookup"><span data-stu-id="1f725-174">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![[方案總管] 檢視顯示 MongoDB NuGet 套件中的相依性。](./media/image21-bis.png)

<span data-ttu-id="1f725-176">**圖 7-22**。</span><span class="sxs-lookup"><span data-stu-id="1f725-176">**Figure 7-22**.</span></span> <span data-ttu-id="1f725-177">.NET Core 專案中的 MongoDB API NuGet 套件參考</span><span class="sxs-lookup"><span data-stu-id="1f725-177">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="1f725-178">讓我們先調查下列各節中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1f725-178">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="1f725-179">MongoDB API 所使用的模型</span><span class="sxs-lookup"><span data-stu-id="1f725-179">A Model used by MongoDB API</span></span>

<span data-ttu-id="1f725-180">首先，您必須定義模型，以保留來自您應用程式記憶體空間中資料庫的資料。</span><span class="sxs-lookup"><span data-stu-id="1f725-180">First, you need to define a model that will hold the data coming from the database in your application’s memory space.</span></span> <span data-ttu-id="1f725-181">以下範例是用於 eShopOnContainers 上 Locations 的模型。</span><span class="sxs-lookup"><span data-stu-id="1f725-181">Here’s an example of the model used for Locations at eShopOnContainers.</span></span>

```csharp
using MongoDB.Bson;
using MongoDB.Bson.Serialization.Attributes;
using MongoDB.Driver.GeoJsonObjectModel;
using System.Collections.Generic;

public class Locations
{
    [BsonId]
    [BsonRepresentation(BsonType.ObjectId)]
    public string Id { get; set; }
    public int LocationId { get; set; }
    public string Code { get; set; }
    [BsonRepresentation(BsonType.ObjectId)]
    public string Parent_Id { get; set; }
    public string Description { get; set; }
    public double Latitude { get; set; }
    public double Longitude { get; set; }
    public GeoJsonPoint<GeoJson2DGeographicCoordinates> Location 
                                                             { get; private set; }
    public GeoJsonPolygon<GeoJson2DGeographicCoordinates> Polygon 
                                                             { get; private set; }
    public void SetLocation(double lon, double lat) => SetPosition(lon, lat);
    public void SetArea(List<GeoJson2DGeographicCoordinates> coordinatesList) 
                                                    => SetPolygon(coordinatesList);

    private void SetPosition(double lon, double lat)
    {
        Latitude = lat;
        Longitude = lon;
        Location = new GeoJsonPoint<GeoJson2DGeographicCoordinates>(
            new GeoJson2DGeographicCoordinates(lon, lat));
    }

    private void SetPolygon(List<GeoJson2DGeographicCoordinates> coordinatesList)
    {
        Polygon = new GeoJsonPolygon<GeoJson2DGeographicCoordinates>(
                  new GeoJsonPolygonCoordinates<GeoJson2DGeographicCoordinates>(
                  new GeoJsonLinearRingCoordinates<GeoJson2DGeographicCoordinates>(
                                                                 coordinatesList)));
    }
}
```

<span data-ttu-id="1f725-182">您可以看到有幾個屬性和型別來自 MongoDB NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="1f725-182">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="1f725-183">NoSQL 資料庫通常非常適合用於處理非關聯式階層式資料。</span><span class="sxs-lookup"><span data-stu-id="1f725-183">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="1f725-184">在此範例中，我們會使用特別針對地理位置所建立的 MongoDB 類型，例如 `GeoJson2DGeographicCoordinates`。</span><span class="sxs-lookup"><span data-stu-id="1f725-184">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="1f725-185">擷取資料庫和集合</span><span class="sxs-lookup"><span data-stu-id="1f725-185">Retrieve the database and the collection</span></span>

<span data-ttu-id="1f725-186">在 eShopOnContainers 中，我們已經建立自訂資料庫內容，在其中，我們會實作可擷取資料庫和 MongoCollections 的程式碼，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="1f725-186">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

```csharp
public class LocationsContext
{
    private readonly IMongoDatabase _database = null;

    public LocationsContext(IOptions<LocationSettings> settings)
    {
        var client = new MongoClient(settings.Value.ConnectionString);
        if (client != null)
            _database = client.GetDatabase(settings.Value.Database);
    }

    public IMongoCollection<Locations> Locations
    {
        get
        {
            return _database.GetCollection<Locations>("Locations");
        }
    }       
}
```

#### <a name="retrieve-the-data"></a><span data-ttu-id="1f725-187">擷取資料</span><span class="sxs-lookup"><span data-stu-id="1f725-187">Retrieve the data</span></span>

<span data-ttu-id="1f725-188">透過 C# 程式碼 (例如 Web API 控制器或自訂存放庫實作)，您可以在透過 MongoDB API 查詢時撰寫與下列類似的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1f725-188">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="1f725-189">請注意，`_context` 物件是前一個 `LocationsContext` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1f725-189">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="1f725-190">在 docker-compose.override.yml 檔案中針對 MongoDB 連接字串使用 env-var</span><span class="sxs-lookup"><span data-stu-id="1f725-190">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="1f725-191">建立 MongoClient 物件時，需要有基礎參數，明確地說就是指向正確資料庫的 `ConnectionString` 參數。</span><span class="sxs-lookup"><span data-stu-id="1f725-191">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="1f725-192">如果是 eShopOnContainers，則連接字串可以指向本機 MongoDB Docker 容器或「生產」Azure Cosmos DB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1f725-192">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a “production” Azure Cosmos DB database.</span></span>  <span data-ttu-id="1f725-193">該連接字串來自 `docker-compose.override.yml` 檔案中所定義的環境變數，而此檔案是在使用 docker-compose 或 Visual Studio 部署時使用，如下列 yml 程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="1f725-193">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

```yml
# docker-compose.override.yml
version: '3.4'
services:
  # Other services
  locations.api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}

```

<span data-ttu-id="1f725-194">`ConnectionString` 環境變數以這種方式解析：如果在 `.env` 檔案中使用了 Azure Cosmos DB 連接字串來定義 `ESHOP_AZURE_COSMOSDB` 全域變數，則會用以在雲端中存取 Azure Cosmos DB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1f725-194">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="1f725-195">如果未定義，它會接受 mongodb://nosql.data 值，並使用開發 mongodb 容器。</span><span class="sxs-lookup"><span data-stu-id="1f725-195">If it’s not defined, it will take the mongodb://nosql.data value and use the development mongodb container.</span></span>

<span data-ttu-id="1f725-196">下列程式碼示範含 Azure Cosmos DB 連接字串全域環境變數的 `.env` 檔案，如 eShopOnContainers 中所實作：</span><span class="sxs-lookup"><span data-stu-id="1f725-196">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

```yml
# .env file, in eShopOnContainers root folder
# Other Docker environment variables

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost
ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=<YourDockerHostIP>

#ESHOP_AZURE_COSMOSDB=<YourAzureCosmosDBConnData>

#Other environment variables for additional Azure infrastructure assets
#ESHOP_AZURE_REDIS_BASKET_DB=<YourAzureRedisBasketInfo>
#ESHOP_AZURE_STORAGE_CATALOG_URL=<YourAzureStorage_Catalog_BLOB_URL>
#ESHOP_AZURE_SERVICE_BUS=<YourAzureServiceBusInfo>
```

<span data-ttu-id="1f725-197">您應該取消註解 ESHOP_AZURE_COSMOSDB 行，並使用取自 Azure 入口網站的 Azure Cosmos DB 連接字串進行更新，如[將 MongoDB 應用程式連接到 Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account)中所說明。</span><span class="sxs-lookup"><span data-stu-id="1f725-197">You should uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="1f725-198">如果 `ESHOP_AZURE_COSMOSDB` 全域變數是空的，表示它在 `.env` 檔案中已取消註解，則容器會使用預設的 MongoDB 連接字串，指向部署在名為 `nosql.data` 且在 Docker-Compose 檔案中定義之 eShopOnContainers 中的本機 MongoDB 容器，如下列 .yml 程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="1f725-198">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning that it is commented out in the `.env` file, then the container uses a default MongoDB connection string pointing to the local MongoDB container deployed in eShopOnContainers which is named `nosql.data` and was defined at the docker-compose file, as shown in the following .yml code.</span></span> 

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosql.data:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="1f725-199">其他資源</span><span class="sxs-lookup"><span data-stu-id="1f725-199">Additional resources</span></span>

- <span data-ttu-id="1f725-200">**將 NoSQL 資料庫的文件資料模組化** </span><span class="sxs-lookup"><span data-stu-id="1f725-200">**Modeling document data for NoSQL databases** </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- <span data-ttu-id="1f725-201">**Vaughn Vernon：理想的領域驅動設計彙總存放區？**</span><span class="sxs-lookup"><span data-stu-id="1f725-201">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="1f725-202">**Azure Cosmos DB 簡介：適用於 MongoDB 的 API**  </span><span class="sxs-lookup"><span data-stu-id="1f725-202">**Introduction to Azure Cosmos DB: API for MongoDB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- <span data-ttu-id="1f725-203">**Azure Cosmos DB：使用 .NET 與 Azure 入口網站建置 MongoDB API Web 應用程式**  </span><span class="sxs-lookup"><span data-stu-id="1f725-203">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  </span></span>\
  [https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet](https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet )

- <span data-ttu-id="1f725-204">**將 Azure Cosmos DB 模擬器用於本機開發及測試**  </span><span class="sxs-lookup"><span data-stu-id="1f725-204">**Use the Azure Cosmos DB Emulator for local development and testing**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- <span data-ttu-id="1f725-205">**將 MongoDB 應用程式連線至 Azure Cosmos DB**  </span><span class="sxs-lookup"><span data-stu-id="1f725-205">**Connect a MongoDB application to Azure Cosmos DB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- <span data-ttu-id="1f725-206">**Cosmos DB 模擬器 Docker 映像 (Windows 容器)**   </span><span class="sxs-lookup"><span data-stu-id="1f725-206">**The Cosmos DB Emulator Docker image (Windows Container)**  </span></span>\
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- <span data-ttu-id="1f725-207">**MongoDB Docker 映像 (Linux 與 Windows 容器)**   </span><span class="sxs-lookup"><span data-stu-id="1f725-207">**The MongoDB Docker image (Linux and Windows Container)**  </span></span>\
  <https://hub.docker.com/\_/mongo/>

- <span data-ttu-id="1f725-208">**搭配 Azure Cosmos DB 使用 MongoChef (Studio 3T)：適用於 MongoDB 的 API 帳戶**  </span><span class="sxs-lookup"><span data-stu-id="1f725-208">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
><span data-ttu-id="1f725-209">[上一頁](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[下一頁](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="1f725-209">[Previous](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>