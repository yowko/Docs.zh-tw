---
title: Wcf 系結和傳輸-適用于 WCF 開發人員的 gRPC
description: 瞭解不同的 WCF 系結和傳輸與 gRPC 的比較。
ms.date: 12/15/2020
ms.openlocfilehash: 7a50e3e4468d86a6140066502a765818119642d4
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938503"
---
# <a name="wcf-bindings-and-transports"></a><span data-ttu-id="b7572-103">WCF 繫結和傳輸</span><span class="sxs-lookup"><span data-stu-id="b7572-103">WCF bindings and transports</span></span>

<span data-ttu-id="b7572-104">Windows Communication Foundation (WCF) 具有內建系 *結，可* 指定不同的網路通訊協定、電傳格式和其他的執行詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b7572-104">Windows Communication Foundation (WCF) has built-in *bindings* that specify different network protocols, wire formats, and other implementation details.</span></span> <span data-ttu-id="b7572-105">gRPC 實際上只有一個網路通訊協定和一個電傳格式。</span><span class="sxs-lookup"><span data-stu-id="b7572-105">gRPC effectively has just one network protocol and one wire format.</span></span> <span data-ttu-id="b7572-106"> (技術上，您 *可以* 自訂電傳格式，但這已超出本書的範圍。 ) 您可能會發現 gRPC 在大部分情況下都能提供最佳解決方案。</span><span class="sxs-lookup"><span data-stu-id="b7572-106">(Technically you *can* customize the wire format, but that's beyond the scope of this book.) You're likely to discover that gRPC offers the best solution in most cases.</span></span>

<span data-ttu-id="b7572-107">接下來是關於最相關 WCF 系結的簡短討論，以及它們與 gRPC 中的對應專案之間的比較。</span><span class="sxs-lookup"><span data-stu-id="b7572-107">What follows is a short discussion about the most relevant WCF bindings and how they compare to their equivalents in gRPC.</span></span>

## <a name="nettcp"></a><span data-ttu-id="b7572-108">NetTCP</span><span class="sxs-lookup"><span data-stu-id="b7572-108">NetTCP</span></span>

<span data-ttu-id="b7572-109">WCF 的 NetTCP 系結允許持續連線、小型訊息和雙向訊息。</span><span class="sxs-lookup"><span data-stu-id="b7572-109">WCF's NetTCP binding allows for persistent connections, small messages, and two-way messaging.</span></span> <span data-ttu-id="b7572-110">但它只能在 .NET 用戶端和伺服器之間運作。</span><span class="sxs-lookup"><span data-stu-id="b7572-110">But it works only between .NET clients and servers.</span></span> <span data-ttu-id="b7572-111">gRPC 允許相同的功能，但在多個程式設計語言和平臺上都有支援。</span><span class="sxs-lookup"><span data-stu-id="b7572-111">gRPC allows the same functionality but is supported across multiple programming languages and platforms.</span></span>

<span data-ttu-id="b7572-112">gRPC 具有 WCF NetTCP 系結的許多功能，但不一定會以相同的方式來執行。</span><span class="sxs-lookup"><span data-stu-id="b7572-112">gRPC has many features of WCF's NetTCP binding, but they're not always implemented in the same way.</span></span> <span data-ttu-id="b7572-113">例如，在 WCF 中，加密是透過設定來控制，並在架構中處理。</span><span class="sxs-lookup"><span data-stu-id="b7572-113">For example, in WCF, encryption is controlled through configuration and handled in the framework.</span></span> <span data-ttu-id="b7572-114">在 gRPC 中，透過 TLS 透過 HTTP/2 在連線層級達到加密。</span><span class="sxs-lookup"><span data-stu-id="b7572-114">In gRPC, encryption is achieved at the connection level through HTTP/2 over TLS.</span></span>

## <a name="http"></a><span data-ttu-id="b7572-115">HTTP</span><span class="sxs-lookup"><span data-stu-id="b7572-115">HTTP</span></span>

<span data-ttu-id="b7572-116">稱為 BasicHttpBinding 的 WCF 系結通常是以文字為基礎，而且會使用 SOAP 做為電傳格式。</span><span class="sxs-lookup"><span data-stu-id="b7572-116">The WCF binding called BasicHttpBinding is usually text-based and uses SOAP as the wire format.</span></span> <span data-ttu-id="b7572-117">相較于 NetTCP 系結，它的速度很慢。</span><span class="sxs-lookup"><span data-stu-id="b7572-117">It's slow compared to the NetTCP binding.</span></span> <span data-ttu-id="b7572-118">它是用來提供跨平臺的互通性，或透過網際網路基礎結構的連線。</span><span class="sxs-lookup"><span data-stu-id="b7572-118">It's used to provide cross-platform interoperability, or connection over internet infrastructure.</span></span>

<span data-ttu-id="b7572-119">GRPC 中的對等用法會使用 HTTP/2 作為訊息的二進位 Protobuf 電傳格式的基礎傳輸層。</span><span class="sxs-lookup"><span data-stu-id="b7572-119">The equivalent in gRPC uses HTTP/2 as the underlying transport layer with the binary Protobuf wire format for messages.</span></span> <span data-ttu-id="b7572-120">因此它可以提供 NetTCP 服務層級的效能，以及所有新式程式設計語言和架構的完整跨平臺互通性。</span><span class="sxs-lookup"><span data-stu-id="b7572-120">So it can offer performance at the NetTCP service level and full cross-platform interoperability with all modern programming languages and frameworks.</span></span>

## <a name="named-pipes"></a><span data-ttu-id="b7572-121">具名管道</span><span class="sxs-lookup"><span data-stu-id="b7572-121">Named pipes</span></span>

<span data-ttu-id="b7572-122">WCF 提供 *具名管道* 系結，以便在相同實體電腦上的進程之間進行通訊。</span><span class="sxs-lookup"><span data-stu-id="b7572-122">WCF provided a *named pipes* binding for communication between processes on the same physical machine.</span></span> <span data-ttu-id="b7572-123">ASP.NET Core gRPC 的第一版不支援具名管道。</span><span class="sxs-lookup"><span data-stu-id="b7572-123">The first release of ASP.NET Core gRPC does not support named pipes.</span></span> <span data-ttu-id="b7572-124">為具名管道 (和 Unix 網域通訊端新增用戶端和伺服器支援，) 是未來版本的目標。</span><span class="sxs-lookup"><span data-stu-id="b7572-124">Adding client and server support for named pipes (and Unix domain sockets) is a goal for a future release.</span></span>

## <a name="msmq"></a><span data-ttu-id="b7572-125">MSMQ</span><span class="sxs-lookup"><span data-stu-id="b7572-125">MSMQ</span></span>

<span data-ttu-id="b7572-126">MSMQ 是專屬的 Windows 訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="b7572-126">MSMQ is a proprietary Windows message queue.</span></span> <span data-ttu-id="b7572-127">WCF 對 MSMQ 的系結可讓用戶端在未來隨時處理的要求「引發」和「遺忘」。</span><span class="sxs-lookup"><span data-stu-id="b7572-127">WCF's binding to MSMQ enables "fire and forget" requests from clients that might be processed at any time in the future.</span></span> <span data-ttu-id="b7572-128">gRPC 本身不會提供任何訊息佇列功能。</span><span class="sxs-lookup"><span data-stu-id="b7572-128">gRPC doesn't natively provide any message queue functionality.</span></span>

<span data-ttu-id="b7572-129">最佳替代方式是直接使用訊息系統，例如 Azure 服務匯流排、RabbitMQ 或 Kafka。</span><span class="sxs-lookup"><span data-stu-id="b7572-129">The best alternative is to directly use a messaging system like Azure Service Bus, RabbitMQ, or Kafka.</span></span> <span data-ttu-id="b7572-130">您可以透過將訊息直接放到佇列的用戶端，或將訊息的 gRPC 用戶端串流服務來執行此功能。</span><span class="sxs-lookup"><span data-stu-id="b7572-130">You can implement this functionality with the client placing messages directly onto the queue, or a gRPC client streaming service that enqueues the messages.</span></span>

## <a name="webhttpbinding"></a><span data-ttu-id="b7572-131">WebHttpBinding</span><span class="sxs-lookup"><span data-stu-id="b7572-131">WebHttpBinding</span></span>

<span data-ttu-id="b7572-132">WebHttpBinding (也稱為 WCF REST) ，其中包含 `WebGet` 和 `WebInvoke` 屬性，可讓您開發 RESTful api，以便在這種行為較不常見時，一次就能說出 JSON。</span><span class="sxs-lookup"><span data-stu-id="b7572-132">WebHttpBinding (also known as WCF REST), with the `WebGet` and `WebInvoke` attributes, enabled you to develop RESTful APIs that could speak JSON at a time when this behavior was less common.</span></span> <span data-ttu-id="b7572-133">如果您有以 WCF REST 建立的 RESTful API，請考慮將它遷移至一般 ASP.NET Core MVC Web API 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b7572-133">If you have a RESTful API built with WCF REST, consider migrating it to a regular ASP.NET Core MVC Web API application.</span></span> <span data-ttu-id="b7572-134">這項遷移會提供與 gRPC 轉換相同的功能。</span><span class="sxs-lookup"><span data-stu-id="b7572-134">This migration would provide the same functionality as a conversion to gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b7572-135">[上一個](wcf-endpoints-grpc-methods.md) 
>[下一步](rpc-types.md)</span><span class="sxs-lookup"><span data-stu-id="b7572-135">[Previous](wcf-endpoints-grpc-methods.md)
[Next](rpc-types.md)</span></span>
