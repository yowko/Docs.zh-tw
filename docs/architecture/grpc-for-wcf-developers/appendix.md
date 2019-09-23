---
title: 附錄-適用于 WCF 開發人員的 gRPC
description: 討論分散式交易及其在現代化微服務架構中的執行方式。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 10c4e77794c5ffe1aa6d5a629ce0b6cdf92f4ada
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184614"
---
# <a name="appendix-a---transactions"></a><span data-ttu-id="013fd-103">附錄 A-交易</span><span class="sxs-lookup"><span data-stu-id="013fd-103">Appendix A - Transactions</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="013fd-104">Windows Communication Foundation （WCF）支援的分散式交易，允許跨多個服務執行不可部分完成的作業。</span><span class="sxs-lookup"><span data-stu-id="013fd-104">Windows Communication Foundation (WCF) supported distributed transactions, allowing atomic operations to be performed across multiple services.</span></span> <span data-ttu-id="013fd-105">此功能是以[Microsoft 分散式交易協調器](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85))為基礎。</span><span class="sxs-lookup"><span data-stu-id="013fd-105">This functionality was based on the [Microsoft Distributed Transaction Coordinator](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85)).</span></span>

<span data-ttu-id="013fd-106">在現代化的微服務環境中，這種類型的自動化分散式交易處理並不可行。</span><span class="sxs-lookup"><span data-stu-id="013fd-106">In the modern microservices landscape, this type of automated distributed transaction processing isn't possible.</span></span> <span data-ttu-id="013fd-107">在遊戲中有太多不同的技術，包括關係資料庫、NoSQL 資料存放區和訊息系統，而不是要提及可能在單一環境中使用的作業系統、程式設計語言和架構組合。</span><span class="sxs-lookup"><span data-stu-id="013fd-107">There are too many different technologies at play, including relational databases, NoSQL data stores, and messaging systems, not to mention the mix of operating systems, programming languages and frameworks that may be used in a single environment.</span></span>

<span data-ttu-id="013fd-108">WCF 分散式交易是所謂的[兩階段認可（2pc）](https://en.wikipedia.org/wiki/Two-phase_commit_protocol)。</span><span class="sxs-lookup"><span data-stu-id="013fd-108">The WCF distributed transaction is an implementation of what is known as a [two-phase commit (2PC)](https://en.wikipedia.org/wiki/Two-phase_commit_protocol).</span></span> <span data-ttu-id="013fd-109">藉由協調服務之間的訊息、在每個服務中建立開啟的交易，以及根據成功或失敗傳送「認可」或「回復」訊息，可以手動執行2PC 交易。</span><span class="sxs-lookup"><span data-stu-id="013fd-109">It's possible to implement 2PC transactions manually by coordinating messages across services, creating open transactions within each service and sending "commit" or "rollback" messages depending upon success or failure.</span></span> <span data-ttu-id="013fd-110">不過，管理2PC 時所牽涉到的複雜性可能會隨著系統的演進而以指數方式增加，而開啟的交易則保有可能對效能造成負面影響的資料庫鎖定，因而導致跨服務的鎖死。</span><span class="sxs-lookup"><span data-stu-id="013fd-110">However, the complexity that is involved in managing 2PC can increase exponentially as systems evolve, and open transactions hold database locks that can negatively impact performance or, worse, cause cross-service deadlocks.</span></span>

<span data-ttu-id="013fd-111">可能的話，最好完全避免分散式交易。</span><span class="sxs-lookup"><span data-stu-id="013fd-111">If possible, it's best to avoid distributed transactions altogether.</span></span> <span data-ttu-id="013fd-112">如果兩個數據的專案是因此連結成需要不可部分完成的更新，請考慮同時使用相同的服務來處理它們，並使用單一要求或訊息將那些不可部分完成的變更套用至該服務。</span><span class="sxs-lookup"><span data-stu-id="013fd-112">If two items of data are so linked as to require atomic updates, consider handling them both with the same service, and applying those atomic changes using a single request or message to that service.</span></span>

<span data-ttu-id="013fd-113">如果無法這麼做，則其中一種替代方式是使用[Saga 模式](https://microservices.io/patterns/data/saga.html)。</span><span class="sxs-lookup"><span data-stu-id="013fd-113">If that isn't possible, then one alternative is to use the [Saga pattern](https://microservices.io/patterns/data/saga.html).</span></span> <span data-ttu-id="013fd-114">在 saga 中，更新會依序進行處理;當每個更新成功時，就會觸發下一個更新。</span><span class="sxs-lookup"><span data-stu-id="013fd-114">In a saga, updates are processing sequentially; as each update succeeds the next one is triggered.</span></span> <span data-ttu-id="013fd-115">這些觸發程式可以從服務傳播到服務，或由 saga 協調器或「orchestrator」進行管理。</span><span class="sxs-lookup"><span data-stu-id="013fd-115">These triggers can be propagated from service to service, or managed by a saga coordinator or "orchestrator".</span></span> <span data-ttu-id="013fd-116">如果在程式中的任何時間點發生更新失敗，已完成其更新的服務會套用特定邏輯來將它們反轉。</span><span class="sxs-lookup"><span data-stu-id="013fd-116">If an update fails at any point during the process, the services that have already completed their updates apply specific logic to reverse them.</span></span>

<span data-ttu-id="013fd-117">另一個選項是使用網域導向設計（DDD）和命令/查詢責任隔離（CQRS），如[.Net 微服務電子書](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/)中所述。</span><span class="sxs-lookup"><span data-stu-id="013fd-117">Another option is to use Domain Driven Design (DDD) and Command/Query Responsibility Segregation (CQRS), as described in the [.NET Microservices e-book](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/).</span></span> <span data-ttu-id="013fd-118">特別是，使用領域事件或[事件來源](https://martinfowler.com/eaaDev/EventSourcing.html)有助於確保更新在不會立即&mdash; &mdash;套用的情況下仍會一致。</span><span class="sxs-lookup"><span data-stu-id="013fd-118">In particular, using domain events or [event sourcing](https://martinfowler.com/eaaDev/EventSourcing.html) can help to ensure that updates are consistently&mdash;if not immediately&mdash;applied.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="013fd-119">上一步</span><span class="sxs-lookup"><span data-stu-id="013fd-119">Previous</span></span>](application-performance-management.md)
