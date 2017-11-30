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
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a>使用 NoSQL 資料庫做為持續性基礎結構

當您使用的 NoSQL 資料庫用於您基礎結構的資料層時，您通常不使用 Entity Framework Core 像 ORM。 相反地，您會使用 NoSQL 引擎，例如 Azure Cosmos DB、 MongoDB、 Cassandra、 RavenDB、 CouchDB 或 Azure 儲存體資料表所提供的 API。

不過，當您使用 NoSQL 資料庫，特別是文件導向的資料庫，如 Azure Cosmos DB、 CouchDB 或 RavenDB，設計您的模型與 DDD 彙總的方式是部分類似於如何這麼做在 EF 核心中的識別彙總根，子實體類別，以及值物件類別。 但是，最後，資料庫選項會影響您的設計中。

當您使用文件導向的資料庫時，您可以實作彙總為單一文件，以 JSON 或另一種格式序列化。 不過，資料庫的使用是從網域模型的程式碼的觀點透明的。 當使用 NoSQL 資料庫，您仍然使用實體類別和彙總根類別，但有更大的彈性比使用 EF 核心因為持續性不是關聯式。

差異在於您將該模型的保存。 如果您實作網域模型 POCO 實體類別為基礎，無特定的基礎結構持續性，它可能外觀無法移至不同的持續性的基礎結構，甚至是從關聯式 NoSQL 至。 不過，，不應該是您的目標。 總是會有不同的資料庫中的條件約束會推您，因此您不能有相同的模型為關聯式或 NoSQL 資料庫。 變更持續性模型不是簡單式，因為交易和持續性作業將會是非常不同。

例如，在文件導向資料庫中，也沒關係彙總根，有多個子集合的屬性。 在關聯式資料庫中，查詢多個子集合的屬性是，因為您的聯集的所有 SQL 陳述式會傳回 EF。 有相同的網域模型，針對關聯式資料庫或 NoSQL 資料庫並不簡單，而您應該不會嘗試它。 實際上，您必須設計您的模型，了解要如何使用每個特定的資料庫中的資料。

使用 NoSQL 資料庫時的好處是實體是更正規化，因此您無法設定資料表對應。 網域模型可以比使用關聯式資料庫更有彈性。

當您設計您的網域模型根據彙總，移至 NoSQL 和文件導向資料庫可能比使用關聯式資料庫中，更容易，因為您所設計的彙總如下序列化文件導向的資料庫中的文件。 然後您可以包含這些"包 」 進行彙總，您可能需要的所有資訊。

比方說，下列 JSON 程式碼時的順序彙總的範例實作使用文件導向的資料庫。 我們實作在 eShopOnContainers 範例中，但不使用 EF 核心的順序彙總與相似。

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

當您使用 C\#來實作類似 Azure Cosmos DB SDK，彙總所使用的彙總模型很類似 C\# POCO 類別使用 EF 核心。 不同之處在於它們使用從應用程式和基礎結構層級，如下列程式碼所示的方式：

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

您可以看到您使用網域模型的方式可以是當使用這個網域模型層中的基礎結構是以 EF 的方式類似。 您仍然可以使用相同的彙總根方法以確保一致性，非變異項目和彙總內的驗證。

不過，當您將保存您的模型 NoSQL 資料庫、 程式碼和應用程式開發介面變更大幅相較於 EF 核心程式碼或任何其他關聯式資料庫與相關的程式碼。

#### <a name="additional-resources"></a>其他資源

-   **在 DocumentDB 中的資料模型化**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)

-   **Vaughn Vernon：在理想網域導向設計彙總存放區嗎？** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)

-   **持續性無從驗證適用於.NET 的事件存放區。** GitHub 儲存機制。
    [*https://github.com/NEventStore/NEventStore*](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
[上一個](infrastructure-persistence-layer-implemenation-entity-framework-core.md) [下一步] (microservice-application-layer-web-api-design.md)
