---
title: WCF 系結和傳輸-WCF 開發人員的 gRPC
description: 瞭解不同的 WCF 系結和傳輸與 gRPC 之間的比較。
ms.date: 09/02/2019
ms.openlocfilehash: 233e3d030bc1f4450bd5cd6a7d7770486ca9e95a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966909"
---
# <a name="wcf-bindings-and-transports"></a><span data-ttu-id="a9222-103">WCF 繫結和傳輸</span><span class="sxs-lookup"><span data-stu-id="a9222-103">WCF bindings and transports</span></span>

<span data-ttu-id="a9222-104">WCF 有許多不同的內建系結 *，這些系*結會指定不同的網路通訊協定、電傳格式和其他的執行詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a9222-104">WCF has lots of different built-in *bindings* that specify different network protocols, wire formats, and other implementation details.</span></span> <span data-ttu-id="a9222-105">gRPC 實際上只有一個網路通訊協定和一個電傳格式（技術上來說，*可以*自訂電傳格式，但這不在本書的討論範圍內）。</span><span class="sxs-lookup"><span data-stu-id="a9222-105">gRPC effectively has just one network protocol and one wire format (technically the wire format *may* be customized, but that is beyond the scope of this book).</span></span> <span data-ttu-id="a9222-106">在大部分情況下，您可能會發現 gRPC 提供最佳的解決方案。</span><span class="sxs-lookup"><span data-stu-id="a9222-106">You are likely to discover that gRPC offers the best solution in most cases.</span></span> <span data-ttu-id="a9222-107">接下來是關於最相關的 WCF 系結，以及它們如何與 gRPC 中的對等項進行比較的簡短討論。</span><span class="sxs-lookup"><span data-stu-id="a9222-107">What follows is a short discussion about the most relevant WCF bindings and how they compare to their equivalent in gRPC.</span></span>

## <a name="nettcp"></a><span data-ttu-id="a9222-108">NetTCP</span><span class="sxs-lookup"><span data-stu-id="a9222-108">NetTCP</span></span>

<span data-ttu-id="a9222-109">WCF 的 NetTCP 系結允許持續連接、小型訊息和雙向訊息，但只能在 .NET 用戶端和伺服器之間運作。</span><span class="sxs-lookup"><span data-stu-id="a9222-109">WCF's NetTCP binding allows for persistent connections, small messages, and two-way messaging but only works between .NET clients and servers.</span></span> <span data-ttu-id="a9222-110">gRPC 允許相同的功能，但在多個程式設計語言和平臺上都支援。</span><span class="sxs-lookup"><span data-stu-id="a9222-110">gRPC allows the same functionality but is supported across multiple programming languages and platforms.</span></span> <span data-ttu-id="a9222-111">gRPC 有許多 WCF NetTCP 系結的功能，但不一定會以相同的方式來執行。</span><span class="sxs-lookup"><span data-stu-id="a9222-111">gRPC has many of the features of WCF NetTCP binding, although not always implemented in the same way.</span></span> <span data-ttu-id="a9222-112">例如，在 WCF 中，加密是透過設定來控制，並在架構中處理。</span><span class="sxs-lookup"><span data-stu-id="a9222-112">For example, in WCF, encryption is controlled through configuration and handled in the framework.</span></span> <span data-ttu-id="a9222-113">在 gRPC 中，加密是在透過 TLS 使用 HTTP/2 的連線層級達成。</span><span class="sxs-lookup"><span data-stu-id="a9222-113">In gRPC, encryption is achieved at the connection level using HTTP/2 over TLS.</span></span>

## <a name="http"></a><span data-ttu-id="a9222-114">HTTP</span><span class="sxs-lookup"><span data-stu-id="a9222-114">HTTP</span></span>

<span data-ttu-id="a9222-115">WCF 的 BasicHttpBinding 通常是以文字為基礎，使用 SOAP 做為電傳格式，而相較于 NetTCP 系結，它會變慢。</span><span class="sxs-lookup"><span data-stu-id="a9222-115">WCF's BasicHttpBinding is usually text based, using SOAP as the wire format, and is slow compared to the NetTCP binding.</span></span> <span data-ttu-id="a9222-116">它通常用來提供跨平臺互通性，或透過網際網路基礎結構的連線。</span><span class="sxs-lookup"><span data-stu-id="a9222-116">It's generally used to provide cross-platform interoperability, or connection over internet infrastructure.</span></span> <span data-ttu-id="a9222-117">GRPC 中的對等專案，因為它使用 HTTP/2 做為適用于訊息之 binary Protobuf 電傳格式的基礎傳輸層—可提供 NetTCP 服務層級效能，但具備所有新式程式設計語言的完整跨平臺互通性和集成.</span><span class="sxs-lookup"><span data-stu-id="a9222-117">The equivalent in gRPC—because it uses HTTP/2 as the underlying transport layer with the binary Protobuf wire format for messages—can offer NetTCP service level performance but with full cross-platform interoperability with all modern programming languages and frameworks.</span></span>

## <a name="named-pipes"></a><span data-ttu-id="a9222-118">具名管道</span><span class="sxs-lookup"><span data-stu-id="a9222-118">Named Pipes</span></span>

<span data-ttu-id="a9222-119">WCF 提供了具名管道系結，以便在相同實體電腦上的進程之間進行通訊。</span><span class="sxs-lookup"><span data-stu-id="a9222-119">WCF provided a Named Pipes binding for communication between processes on the same physical machine.</span></span> <span data-ttu-id="a9222-120">ASP.NET Core gRPC 的第一版不支援具名管道。</span><span class="sxs-lookup"><span data-stu-id="a9222-120">Named pipes are not supported by the first release of ASP.NET Core gRPC.</span></span> <span data-ttu-id="a9222-121">新增具名管道（和 Unix 網域通訊端）的用戶端和伺服器支援是未來版本的目標。</span><span class="sxs-lookup"><span data-stu-id="a9222-121">Adding client and server support for named pipes (and Unix domain sockets) is a goal for a future release.</span></span>

## <a name="msmq"></a><span data-ttu-id="a9222-122">MSMQ</span><span class="sxs-lookup"><span data-stu-id="a9222-122">MSMQ</span></span>

<span data-ttu-id="a9222-123">MSMQ 是專屬的 Windows 訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="a9222-123">MSMQ is a proprietary Windows message queue.</span></span> <span data-ttu-id="a9222-124">WCF 對 MSMQ 的系結可讓您從用戶端「引發並忘記」要求，未來可能會進行處理。</span><span class="sxs-lookup"><span data-stu-id="a9222-124">WCF's binding to MSMQ enables "fire and forget" requests from clients that may be processed at any time in the future.</span></span> <span data-ttu-id="a9222-125">gRPC 原本不提供任何訊息佇列功能。</span><span class="sxs-lookup"><span data-stu-id="a9222-125">gRPC doesn't natively provide any message queue functionality.</span></span> <span data-ttu-id="a9222-126">最佳的替代方法是直接使用訊息系統，例如 Azure 服務匯流排、RabbitMQ 或 Kafka。</span><span class="sxs-lookup"><span data-stu-id="a9222-126">The best alternative would be to directly use a messaging system like Azure Service Bus, RabbitMQ, or Kafka.</span></span> <span data-ttu-id="a9222-127">這可以透過用戶端直接將訊息放在佇列上，或 gRPC 用戶端串流服務來將訊息來執行。</span><span class="sxs-lookup"><span data-stu-id="a9222-127">This could be implemented with the client placing messages directly onto the queue, or a gRPC client streaming service that enqueues the messages.</span></span>

## <a name="webhttpbinding"></a><span data-ttu-id="a9222-128">WebHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a9222-128">WebHttpBinding</span></span>

<span data-ttu-id="a9222-129">WebHttpBinding （也稱為「WCF ReST」）具有 `WebGet` 和 `WebInvoke` 屬性，可讓您開發 ReSTful Api，而這在這種情況下並不常見，可能會一次就說出 JSON。</span><span class="sxs-lookup"><span data-stu-id="a9222-129">The WebHttpBinding (also known as WCF ReST), with the `WebGet` and `WebInvoke` attributes, enabled you to develop ReSTful APIs that could speak JSON at a time when this was less common than now.</span></span> <span data-ttu-id="a9222-130">因此，如果您有以 WCF REST 建立的 RESTful API，請考慮將它遷移至一般 ASP.NET Core MVC Web API 應用程式，這會提供對等的功能，而不是轉換成 gRPC。</span><span class="sxs-lookup"><span data-stu-id="a9222-130">Therefore, if you have a RESTful API built with WCF REST, consider migrating it to a regular ASP.NET Core MVC Web API application, which would provide equivalent functionality, rather than converting to gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a9222-131">[上一頁](wcf-endpoints-grpc-methods.md)
>[下一頁](rpc-types.md)</span><span class="sxs-lookup"><span data-stu-id="a9222-131">[Previous](wcf-endpoints-grpc-methods.md)
[Next](rpc-types.md)</span></span>
