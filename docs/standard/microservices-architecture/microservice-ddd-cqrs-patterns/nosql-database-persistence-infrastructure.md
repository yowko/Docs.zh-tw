---
title: "使用 NoSQL 資料庫做為持續性基礎結構"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |使用 NoSQL 資料庫做為持續性基礎結構"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e4b63511069b89cc5761ce7ed64f09e9035a56a3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="7a160-104">使用 NoSQL 資料庫做為持續性基礎結構</span><span class="sxs-lookup"><span data-stu-id="7a160-104">Using NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="7a160-105">當您使用的 NoSQL 資料庫用於您基礎結構的資料層時，您通常不使用 Entity Framework Core 像 ORM。</span><span class="sxs-lookup"><span data-stu-id="7a160-105">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="7a160-106">相反地，您會使用 NoSQL 引擎，例如 Azure Cosmos DB、 MongoDB、 Cassandra、 RavenDB、 CouchDB 或 Azure 儲存體資料表所提供的 API。</span><span class="sxs-lookup"><span data-stu-id="7a160-106">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="7a160-107">不過，當您使用 NoSQL 資料庫，特別是文件導向的資料庫，如 Azure Cosmos DB、 CouchDB 或 RavenDB，設計您的模型與 DDD 彙總的方式是部分類似於如何這麼做在 EF 核心中的識別彙總根，子實體類別，以及值物件類別。</span><span class="sxs-lookup"><span data-stu-id="7a160-107">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="7a160-108">但是，最後，資料庫選項會影響您的設計中。</span><span class="sxs-lookup"><span data-stu-id="7a160-108">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="7a160-109">當您使用文件導向的資料庫時，您可以實作彙總為單一文件，以 JSON 或另一種格式序列化。</span><span class="sxs-lookup"><span data-stu-id="7a160-109">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="7a160-110">不過，資料庫的使用是從網域模型的程式碼的觀點透明的。</span><span class="sxs-lookup"><span data-stu-id="7a160-110">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="7a160-111">當使用 NoSQL 資料庫，您仍然使用實體類別和彙總根類別，但有更大的彈性比使用 EF 核心因為持續性不是關聯式。</span><span class="sxs-lookup"><span data-stu-id="7a160-111">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="7a160-112">差異在於您將該模型的保存。</span><span class="sxs-lookup"><span data-stu-id="7a160-112">The difference is in how you persist that model.</span></span> <span data-ttu-id="7a160-113">如果您實作網域模型 POCO 實體類別為基礎，無特定的基礎結構持續性，它可能外觀無法移至不同的持續性的基礎結構，甚至是從關聯式 NoSQL 至。</span><span class="sxs-lookup"><span data-stu-id="7a160-113">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="7a160-114">不過，，不應該是您的目標。</span><span class="sxs-lookup"><span data-stu-id="7a160-114">However, that should not be your goal.</span></span> <span data-ttu-id="7a160-115">總是會有不同的資料庫中的條件約束會推您，因此您不能有相同的模型為關聯式或 NoSQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7a160-115">There are always constraints in the different databases will push you back, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="7a160-116">變更持續性模型不是簡單式，因為交易和持續性作業將會是非常不同。</span><span class="sxs-lookup"><span data-stu-id="7a160-116">Changing persistence models would not be trivial, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="7a160-117">例如，在文件導向資料庫中，也沒關係彙總根，有多個子集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="7a160-117">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="7a160-118">在關聯式資料庫中，查詢多個子集合的屬性是，因為您的聯集的所有 SQL 陳述式會傳回 EF。</span><span class="sxs-lookup"><span data-stu-id="7a160-118">In a relational database, querying multiple child collection properties is awful, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="7a160-119">有相同的網域模型，針對關聯式資料庫或 NoSQL 資料庫並不簡單，而您應該不會嘗試它。</span><span class="sxs-lookup"><span data-stu-id="7a160-119">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try it.</span></span> <span data-ttu-id="7a160-120">實際上，您必須設計您的模型，了解要如何使用每個特定的資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="7a160-120">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="7a160-121">使用 NoSQL 資料庫時的好處是實體是更正規化，因此您無法設定資料表對應。</span><span class="sxs-lookup"><span data-stu-id="7a160-121">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="7a160-122">網域模型可以比使用關聯式資料庫更有彈性。</span><span class="sxs-lookup"><span data-stu-id="7a160-122">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="7a160-123">當您設計您的網域模型根據彙總，移至 NoSQL 和文件導向資料庫可能比使用關聯式資料庫中，更容易，因為您所設計的彙總如下序列化文件導向的資料庫中的文件。</span><span class="sxs-lookup"><span data-stu-id="7a160-123">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="7a160-124">然後您可以包含這些"包 」 進行彙總，您可能需要的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="7a160-124">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="7a160-125">比方說，下列 JSON 程式碼時的順序彙總的範例實作使用文件導向的資料庫。</span><span class="sxs-lookup"><span data-stu-id="7a160-125">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="7a160-126">我們實作在 eShopOnContainers 範例中，但不使用 EF 核心的順序彙總與相似。</span><span class="sxs-lookup"><span data-stu-id="7a160-126">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

<span data-ttu-id="7a160-127">當您使用 C\#來實作類似 Azure Cosmos DB SDK，彙總所使用的彙總模型很類似 C\# POCO 類別使用 EF 核心。</span><span class="sxs-lookup"><span data-stu-id="7a160-127">When you use a C\# model to implement the aggregate to be used by something like the Azure Cosmos DB SDK, the aggregate is similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="7a160-128">不同之處在於它們使用從應用程式和基礎結構層級，如下列程式碼所示的方式：</span><span class="sxs-lookup"><span data-stu-id="7a160-128">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH DOCUMENTDB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).
// This can be saved as JSON as is without converting into rows/columns.
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

OrderItem orderItem2 = new OrderItem
{
    Id = 20170012,
    ProductId = "123457",
    ProductName = ".NET Mug",
    UnitPrice = 15,
    Units = 1,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
orderAggregate.AddOrderItem(orderItem2);

// *** End of Domain Model Code ***
//...
// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, order);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

<span data-ttu-id="7a160-129">您可以看到您使用網域模型的方式可以是當使用這個網域模型層中的基礎結構是以 EF 的方式類似。</span><span class="sxs-lookup"><span data-stu-id="7a160-129">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="7a160-130">您仍然可以使用相同的彙總根方法以確保一致性，非變異項目和彙總內的驗證。</span><span class="sxs-lookup"><span data-stu-id="7a160-130">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="7a160-131">不過，當您將保存您的模型 NoSQL 資料庫、 程式碼和應用程式開發介面變更大幅相較於 EF 核心程式碼或任何其他關聯式資料庫與相關的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7a160-131">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="7a160-132">其他資源</span><span class="sxs-lookup"><span data-stu-id="7a160-132">Additional resources</span></span>

-   <span data-ttu-id="7a160-133">**在 DocumentDB 中的資料模型化**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span><span class="sxs-lookup"><span data-stu-id="7a160-133">**Modeling data in DocumentDB**
[*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span></span>

-   <span data-ttu-id="7a160-134">**Vaughn Vernon：在理想網域導向設計彙總存放區嗎？** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span><span class="sxs-lookup"><span data-stu-id="7a160-134">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**
[*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span></span>

-   <span data-ttu-id="7a160-135">**持續性無從驗證適用於.NET 的事件存放區。**</span><span class="sxs-lookup"><span data-stu-id="7a160-135">**A persistence agnostic Event Store for .NET.**</span></span> <span data-ttu-id="7a160-136">GitHub 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="7a160-136">GitHub repo.</span></span>
    [<span data-ttu-id="7a160-137">*https://github.com/NEventStore/NEventStore*</span><span class="sxs-lookup"><span data-stu-id="7a160-137">*https://github.com/NEventStore/NEventStore*</span></span>](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
<span data-ttu-id="7a160-138">[上一個](infrastructure-persistence-layer-implemenation-entity-framework-core.md) [下一步] (microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="7a160-138">[Previous] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Next] (microservice-application-layer-web-api-design.md)</span></span>
