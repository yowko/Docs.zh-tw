---
title: WCF 綁定和傳輸 - gRPC 面向 WCF 開發人員
description: 瞭解不同的 WCF 綁定和傳輸與 gRPC 的比較情況。
ms.date: 09/02/2019
ms.openlocfilehash: 3a295268b486578c70c2c98f1d05f89070daaeb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147720"
---
# <a name="wcf-bindings-and-transports"></a><span data-ttu-id="6eac9-103">WCF 繫結和傳輸</span><span class="sxs-lookup"><span data-stu-id="6eac9-103">WCF bindings and transports</span></span>

<span data-ttu-id="6eac9-104">Windows 通信基礎 （WCF） 具有內置*綁定*，用於指定不同的網路通訊協定、線格式和其他實現詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="6eac9-104">Windows Communication Foundation (WCF) has built-in *bindings* that specify different network protocols, wire formats, and other implementation details.</span></span> <span data-ttu-id="6eac9-105">gRPC 實際上只有一個網路通訊協定和一個線格式。</span><span class="sxs-lookup"><span data-stu-id="6eac9-105">gRPC effectively has just one network protocol and one wire format.</span></span> <span data-ttu-id="6eac9-106">（從技術上講，*您可以*自訂線格式，但這超出了本書的範圍。您可能會發現 gRPC 在大多數情況下提供了最佳解決方案。</span><span class="sxs-lookup"><span data-stu-id="6eac9-106">(Technically you *can* customize the wire format, but that's beyond the scope of this book.) You're likely to discover that gRPC offers the best solution in most cases.</span></span>

<span data-ttu-id="6eac9-107">以下是關於最相關的 WCF 綁定及其與 gRPC 中的等效綁定的比較的簡短討論。</span><span class="sxs-lookup"><span data-stu-id="6eac9-107">What follows is a short discussion about the most relevant WCF bindings and how they compare to their equivalents in gRPC.</span></span>

## <a name="nettcp"></a><span data-ttu-id="6eac9-108">NetTCP</span><span class="sxs-lookup"><span data-stu-id="6eac9-108">NetTCP</span></span>

<span data-ttu-id="6eac9-109">WCF 的 NetTCP 綁定允許持久連接、小消息和雙向消息傳送。</span><span class="sxs-lookup"><span data-stu-id="6eac9-109">WCF's NetTCP binding allows for persistent connections, small messages, and two-way messaging.</span></span> <span data-ttu-id="6eac9-110">但它僅在 .NET 用戶端和伺服器之間工作。</span><span class="sxs-lookup"><span data-stu-id="6eac9-110">But it works only between .NET clients and servers.</span></span> <span data-ttu-id="6eac9-111">gRPC 允許相同的功能，但支援跨多個程式設計語言和平臺。</span><span class="sxs-lookup"><span data-stu-id="6eac9-111">gRPC allows the same functionality but is supported across multiple programming languages and platforms.</span></span>

<span data-ttu-id="6eac9-112">gRPC 具有 WCF NetTCP 綁定的許多功能，但它們並不總是以相同的方式實現。</span><span class="sxs-lookup"><span data-stu-id="6eac9-112">gRPC has many features of WCF's NetTCP binding, but they're not always implemented in the same way.</span></span> <span data-ttu-id="6eac9-113">例如，在 WCF 中，加密通過配置進行控制，並在框架中處理。</span><span class="sxs-lookup"><span data-stu-id="6eac9-113">For example, in WCF, encryption is controlled through configuration and handled in the framework.</span></span> <span data-ttu-id="6eac9-114">在 gRPC 中，通過 TLS 的 HTTP/2 在連接級別實現加密。</span><span class="sxs-lookup"><span data-stu-id="6eac9-114">In gRPC, encryption is achieved at the connection level through HTTP/2 over TLS.</span></span>

## <a name="http"></a><span data-ttu-id="6eac9-115">HTTP</span><span class="sxs-lookup"><span data-stu-id="6eac9-115">HTTP</span></span>

<span data-ttu-id="6eac9-116">稱為 BasicHttpBinding 的 WCF 綁定通常基於文本，並使用 SOAP 作為線格式。</span><span class="sxs-lookup"><span data-stu-id="6eac9-116">The WCF binding called BasicHttpBinding is usually text based and uses SOAP as the wire format.</span></span> <span data-ttu-id="6eac9-117">與 NetTCP 綁定相比，它的速度很慢。</span><span class="sxs-lookup"><span data-stu-id="6eac9-117">It's slow compared to the NetTCP binding.</span></span> <span data-ttu-id="6eac9-118">它通常用於提供跨平臺互通性或通過 Internet 基礎結構進行連接。</span><span class="sxs-lookup"><span data-stu-id="6eac9-118">It's generally used to provide cross-platform interoperability, or connection over internet infrastructure.</span></span>

<span data-ttu-id="6eac9-119">gRPC 中的等效項使用 HTTP/2 作為具有二進位 Protobuf 線格式的消息的基礎傳輸層。</span><span class="sxs-lookup"><span data-stu-id="6eac9-119">The equivalent in gRPC uses HTTP/2 as the underlying transport layer with the binary Protobuf wire format for messages.</span></span> <span data-ttu-id="6eac9-120">因此，它可以提供 NetTCP 服務等級的性能，並與所有現代程式設計語言和框架實現全跨平臺互通性。</span><span class="sxs-lookup"><span data-stu-id="6eac9-120">So it can offer performance at the NetTCP service level and full cross-platform interoperability with all modern programming languages and frameworks.</span></span>

## <a name="named-pipes"></a><span data-ttu-id="6eac9-121">具名管道</span><span class="sxs-lookup"><span data-stu-id="6eac9-121">Named pipes</span></span>

<span data-ttu-id="6eac9-122">WCF 提供了一*個具名管道*綁定，用於在同一物理電腦上的進程之間的通信。</span><span class="sxs-lookup"><span data-stu-id="6eac9-122">WCF provided a *named pipes* binding for communication between processes on the same physical machine.</span></span> <span data-ttu-id="6eac9-123">ASP.NET核心 gRPC 的第一個版本不支援具名管道。</span><span class="sxs-lookup"><span data-stu-id="6eac9-123">The first release of ASP.NET Core gRPC does not support named pipes.</span></span> <span data-ttu-id="6eac9-124">添加具名管道（和 Unix 域通訊端）的用戶端和伺服器支援是未來版本的目標。</span><span class="sxs-lookup"><span data-stu-id="6eac9-124">Adding client and server support for named pipes (and Unix domain sockets) is a goal for a future release.</span></span>

## <a name="msmq"></a><span data-ttu-id="6eac9-125">MSMQ</span><span class="sxs-lookup"><span data-stu-id="6eac9-125">MSMQ</span></span>

<span data-ttu-id="6eac9-126">MSMQ 是一個專有的 Windows 訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="6eac9-126">MSMQ is a proprietary Windows message queue.</span></span> <span data-ttu-id="6eac9-127">WCF 與 MSMQ 的綁定允許來自用戶端的"觸發和忘記"請求，這些請求將來可能隨時處理。</span><span class="sxs-lookup"><span data-stu-id="6eac9-127">WCF's binding to MSMQ enables "fire and forget" requests from clients that might be processed at any time in the future.</span></span> <span data-ttu-id="6eac9-128">gRPC 不本機提供任何訊息佇列功能。</span><span class="sxs-lookup"><span data-stu-id="6eac9-128">gRPC doesn't natively provide any message queue functionality.</span></span>

<span data-ttu-id="6eac9-129">最好的選擇是直接使用消息傳遞系統，如 Azure 服務匯流排、兔子MQ或 Kafka。</span><span class="sxs-lookup"><span data-stu-id="6eac9-129">The best alternative is to directly use a messaging system like Azure Service Bus, RabbitMQ, or Kafka.</span></span> <span data-ttu-id="6eac9-130">可以通過將消息直接放在佇列上的用戶端或對消息進行排隊的 gRPC 用戶端流服務來實現此項。</span><span class="sxs-lookup"><span data-stu-id="6eac9-130">You can implement this with the client placing messages directly onto the queue, or a gRPC client streaming service that enqueues the messages.</span></span>

## <a name="webhttpbinding"></a><span data-ttu-id="6eac9-131">WebHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6eac9-131">WebHttpBinding</span></span>

<span data-ttu-id="6eac9-132">WebHttpBinding（也稱為 WCF REST），具有`WebGet`和`WebInvoke`屬性，使您能夠開發 RESTful API，在不太常見時可以講 JSON。</span><span class="sxs-lookup"><span data-stu-id="6eac9-132">WebHttpBinding (also known as WCF REST), with the `WebGet` and `WebInvoke` attributes, enabled you to develop RESTful APIs that could speak JSON at a time when this was less common.</span></span> <span data-ttu-id="6eac9-133">如果使用 WCF REST 構建了 RESTful API，請考慮將其遷移到常規ASP.NET核心 MVC Web API 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6eac9-133">If you have a RESTful API built with WCF REST, consider migrating it to a regular ASP.NET Core MVC Web API application.</span></span> <span data-ttu-id="6eac9-134">此遷移將提供與轉換為 gRPC 相同的功能。</span><span class="sxs-lookup"><span data-stu-id="6eac9-134">This migration would provide the same functionality as a conversion to gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6eac9-135">[上一個](wcf-endpoints-grpc-methods.md)
>[下一個](rpc-types.md)</span><span class="sxs-lookup"><span data-stu-id="6eac9-135">[Previous](wcf-endpoints-grpc-methods.md)
[Next](rpc-types.md)</span></span>
