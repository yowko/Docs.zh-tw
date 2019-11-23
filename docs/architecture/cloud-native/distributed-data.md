---
title: 分散式資料
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |雲端原生應用程式的分散式資料
ms.date: 06/30/2019
ms.openlocfilehash: b715ae5203264a023bc9f911aa74ee222afe3d68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087450"
---
# <a name="distributed-data-for-cloud-native-apps"></a><span data-ttu-id="bf434-103">雲端原生應用程式的分散式資料</span><span class="sxs-lookup"><span data-stu-id="bf434-103">Distributed data for cloud-native apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="bf434-104">當您在建立由許多獨立微服務所組成的雲端原生系統時，您認為資料儲存體的變更方式。</span><span class="sxs-lookup"><span data-stu-id="bf434-104">When constructing a cloud-native system that consists of many independent microservices, the way you think about data storage changes.</span></span>

<span data-ttu-id="bf434-105">傳統的整合型應用程式偏好如圖5-1 所示的集中式資料存放區。</span><span class="sxs-lookup"><span data-stu-id="bf434-105">Traditional monolithic applications favor a centralized data store shown in Figure 5-1.</span></span>

![單一整合型資料庫](./media/single-monolithic-database.png)

<span data-ttu-id="bf434-107">**圖 5-1**.</span><span class="sxs-lookup"><span data-stu-id="bf434-107">**Figure 5-1**.</span></span> <span data-ttu-id="bf434-108">單一整合型資料庫</span><span class="sxs-lookup"><span data-stu-id="bf434-108">Single monolithic database</span></span>

<span data-ttu-id="bf434-109">請注意，在上圖中，所有應用程式元件都會使用單一關係資料庫。</span><span class="sxs-lookup"><span data-stu-id="bf434-109">Note in the previous figure how all of the application components consume a single relational database.</span></span>

<span data-ttu-id="bf434-110">這種方法有許多優點。</span><span class="sxs-lookup"><span data-stu-id="bf434-110">There are many benefits to this approach.</span></span> <span data-ttu-id="bf434-111">查詢分散在多個資料表中的資料很簡單，而且可以直接執行[ACID 交易](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties)以確保資料的一致性。</span><span class="sxs-lookup"><span data-stu-id="bf434-111">It's straightforward to query data spread across  multiple tables, and it's straightforward to implement [ACID transactions](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) that ensure data consistency.</span></span> <span data-ttu-id="bf434-112">最後，您會得到*立即的一致性*：您所有的資料更新，或不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="bf434-112">You always end up with *immediate consistency*: either all your data updates or none of it does.</span></span>

<span data-ttu-id="bf434-113">雲端原生系統偏好 [圖 5-2] 中所示的資料結構，每個微服務都擁有並封裝自己的資料。</span><span class="sxs-lookup"><span data-stu-id="bf434-113">Cloud-native systems favor a data architecture shown in Figure 5-2 in which each microservice owns and encapsulates its own data.</span></span>

![跨微服務的多個資料庫](./media/data-across-microservices.png)

<span data-ttu-id="bf434-115">**圖 5-2**。</span><span class="sxs-lookup"><span data-stu-id="bf434-115">**Figure 5-2**.</span></span> <span data-ttu-id="bf434-116">跨微服務的多個資料庫</span><span class="sxs-lookup"><span data-stu-id="bf434-116">Multiple databases across microservices</span></span>

<span data-ttu-id="bf434-117">請注意，在上圖中，每個微服務會擁有並封裝它的資料存放區，而且只會從其公用 API 向外界公開資料。</span><span class="sxs-lookup"><span data-stu-id="bf434-117">Note how in the previous figure each microservice owns and encapsulates it data store and only exposes data to the outside world from its public API.</span></span>

<span data-ttu-id="bf434-118">此模型可讓每個微服務獨立發展，而不需要協調其他微服務的資料架構變更。</span><span class="sxs-lookup"><span data-stu-id="bf434-118">This model enables each microservice to evolve independently without having to coordinate data schema changes with other microservices.</span></span> <span data-ttu-id="bf434-119">每個微服務都可以自由地執行最符合其需求的資料存放區（關係資料庫、檔資料庫、索引鍵/值存放區）類型。</span><span class="sxs-lookup"><span data-stu-id="bf434-119">Each microservice is free to implement the data store (relational database, document database, key-value store) type that best matches its needs.</span></span> <span data-ttu-id="bf434-120">在執行時間，每個微服務都可以據以調整其資料。</span><span class="sxs-lookup"><span data-stu-id="bf434-120">At runtime, each microservice can scale its data accordingly.</span></span> <span data-ttu-id="bf434-121">如圖5-3 所示：</span><span class="sxs-lookup"><span data-stu-id="bf434-121">This is shown in Figure 5-3:</span></span>

![多語言資料持續性](./media/polyglot-data-persistence.png)

<span data-ttu-id="bf434-123">**圖 5-3**。</span><span class="sxs-lookup"><span data-stu-id="bf434-123">**Figure 5-3**.</span></span> <span data-ttu-id="bf434-124">多語言資料持續性</span><span class="sxs-lookup"><span data-stu-id="bf434-124">Polyglot data persistence</span></span>

<span data-ttu-id="bf434-125">請注意，在上圖中，產品目錄和清查微服務會採用關係資料庫、訂購微服務、NoSql 檔資料庫和購物車微服務，這是外部索引鍵/值存放區。</span><span class="sxs-lookup"><span data-stu-id="bf434-125">Note how in the previous figure the product catalog and inventory microservices adopt relational databases, the ordering microservice, a NoSql document database, and the shopping cart microservice, which is an external key-value store.</span></span> <span data-ttu-id="bf434-126">雖然關係資料庫與複雜資料的微服務保持相關，但 NoSQL 資料庫已獲得相當大的普及，並提供適應性、快速查閱和高可用性。</span><span class="sxs-lookup"><span data-stu-id="bf434-126">While relational databases remain relevant for microservices with complex data, NoSQL databases have gained considerable popularity, providing adaptability, fast lookup, and high availability.</span></span> <span data-ttu-id="bf434-127">其無架構的本質可讓開發人員從具類型的資料類別和 Orm 的架構中移出，這會使變更成本高昂且耗時。</span><span class="sxs-lookup"><span data-stu-id="bf434-127">Their schemaless nature allows developers to move away from an architecture of typed data classes and ORMs that make change expensive and time-consuming.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bf434-128">[上一頁](service-mesh-communication-infrastructure.md)
>[下一頁](data-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="bf434-128">[Previous](service-mesh-communication-infrastructure.md)
[Next](data-patterns.md)</span></span>
