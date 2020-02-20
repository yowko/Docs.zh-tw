---
title: WS-* 通訊協定-適用于 WCF 開發人員的 gRPC
description: 檢查 WCF 支援的 WS-* 通訊協定，以及 gRPC 所提供的替代專案
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: c8c06a5e23a4d7859165e1c562032055d63d76f7
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503292"
---
# <a name="ws--protocols"></a><span data-ttu-id="49971-103">WS-\* 通訊協定</span><span class="sxs-lookup"><span data-stu-id="49971-103">WS-\* protocols</span></span>

<span data-ttu-id="49971-104">使用 Windows Communication Foundation （WCF）的其中一項真正優點，就是支援許多現有的_WS\*_ 標準通訊協定。</span><span class="sxs-lookup"><span data-stu-id="49971-104">One of the real benefits of working with Windows Communication Foundation (WCF) was that it supported many of the existing _WS-\*_ standard protocols.</span></span> <span data-ttu-id="49971-105">本節將簡短說明 gRPC 如何管理相同的 WS\* 通訊協定，並討論沒有替代方案時可用的選項。</span><span class="sxs-lookup"><span data-stu-id="49971-105">This section will briefly cover how gRPC manages the same WS-\* protocols and discuss what options are available when there's no alternative.</span></span>

## <a name="metadata-exchange-ws-policy-ws-discovery-and-so-on"></a><span data-ttu-id="49971-106">中繼資料交換： WS-原則、WS-Discovery 等等</span><span class="sxs-lookup"><span data-stu-id="49971-106">Metadata exchange: WS-Policy, WS-Discovery, and so on</span></span>

<span data-ttu-id="49971-107">SOAP 服務會公開 Web 服務描述語言（WSDL）架構檔，其中包含資料格式、作業或通訊選項等資訊。</span><span class="sxs-lookup"><span data-stu-id="49971-107">SOAP services expose Web Services Description Language (WSDL) schema documents with information such as data formats, operations, or communication options.</span></span> <span data-ttu-id="49971-108">您可以使用此架構來產生用戶端程式代碼。</span><span class="sxs-lookup"><span data-stu-id="49971-108">You can use this schema to generate the client code.</span></span>

<span data-ttu-id="49971-109">從相同的 `.proto` 檔案產生伺服器和用戶端時，gRPC 的效果最佳，但是伺服器反映選用的延伸模組則提供了一種方式，可以從執行中的伺服器公開動態資訊。</span><span class="sxs-lookup"><span data-stu-id="49971-109">gRPC works best when servers and clients are generated from the same `.proto` files, but a Server Reflection optional extension does provide a way to expose dynamic information from a running server.</span></span> <span data-ttu-id="49971-110">如需詳細資訊，請參閱[Grpc](https://nuget.org/packages/Grpc.Reflection) NuGet 套件和[ C# Grpc Server 反映](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md)一文。</span><span class="sxs-lookup"><span data-stu-id="49971-110">For more information, see the [Grpc.Reflection](https://nuget.org/packages/Grpc.Reflection) NuGet package and the [gRPC C# Server Reflection](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) article.</span></span>

<span data-ttu-id="49971-111">WS-探索通訊協定可用來尋找區域網路上的服務。</span><span class="sxs-lookup"><span data-stu-id="49971-111">The WS-Discovery protocol is used to locate services on a local network.</span></span> <span data-ttu-id="49971-112">gRPC 服務通常是透過 DNS 或服務登錄（例如 Consul 或 ZooKeeper）來尋找。</span><span class="sxs-lookup"><span data-stu-id="49971-112">gRPC services are generally located through DNS or a service registry such as Consul or ZooKeeper.</span></span>

## <a name="security-ws-security-ws-federation-xml-encryption-and-so-on"></a><span data-ttu-id="49971-113">安全性： WS-安全性、WS-同盟、XML 加密等等</span><span class="sxs-lookup"><span data-stu-id="49971-113">Security: WS-Security, WS-Federation, XML Encryption, and so on</span></span>

<span data-ttu-id="49971-114">[第6章](security.md)會詳細討論安全性、驗證和授權。</span><span class="sxs-lookup"><span data-stu-id="49971-114">Security, authentication, and authorization are covered in much more detail in [chapter 6](security.md).</span></span> <span data-ttu-id="49971-115">但值得注意的是，與 WCF 不同的是，gRPC 不支援 WS-Security、WS-同盟或 XML 加密。</span><span class="sxs-lookup"><span data-stu-id="49971-115">But it's worth noting here that, unlike WCF, gRPC doesn't support WS-Security, WS-Federation, or XML Encryption.</span></span> <span data-ttu-id="49971-116">就算如此，gRPC 也提供絕佳的安全性。</span><span class="sxs-lookup"><span data-stu-id="49971-116">Even so, gRPC provides excellent security.</span></span> <span data-ttu-id="49971-117">當所有 gRPC 網路流量透過 TLS 使用 HTTP/2 時，都會自動加密。</span><span class="sxs-lookup"><span data-stu-id="49971-117">All gRPC network traffic is automatically encrypted when it's using HTTP/2 over TLS.</span></span> <span data-ttu-id="49971-118">您可以使用 X509 憑證進行相互用戶端/伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="49971-118">You can use X509 certificates for mutual client/server authentication.</span></span>

## <a name="ws-reliablemessaging"></a><span data-ttu-id="49971-119">WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="49971-119">WS-ReliableMessaging</span></span>

<span data-ttu-id="49971-120">gRPC 並未提供與 ws-reliablemessaging 相等的。</span><span class="sxs-lookup"><span data-stu-id="49971-120">gRPC does not provide an equivalent to WS-ReliableMessaging.</span></span> <span data-ttu-id="49971-121">重試語法應該在程式碼中處理，可能是[Polly](https://github.com/App-vNext/Polly)之類的程式庫。</span><span class="sxs-lookup"><span data-stu-id="49971-121">Retry semantics should be handled in code, possibly with a library like [Polly](https://github.com/App-vNext/Polly).</span></span> <span data-ttu-id="49971-122">當您在 Kubernetes 或類似的協調流程環境中執行時，[服務網格](service-mesh.md)也可以協助在服務之間提供可靠的訊息傳遞。</span><span class="sxs-lookup"><span data-stu-id="49971-122">When you're running in Kubernetes or similar orchestration environments, [service meshes](service-mesh.md) can also help to provide reliable messaging between services.</span></span>

## <a name="ws-transaction-ws-coordination"></a><span data-ttu-id="49971-123">WS-交易，WS-協調</span><span class="sxs-lookup"><span data-stu-id="49971-123">WS-Transaction, WS-Coordination</span></span>

<span data-ttu-id="49971-124">WCF 的分散式交易執行會使用 Microsoft 分散式交易協調器（MSDTC）。</span><span class="sxs-lookup"><span data-stu-id="49971-124">WCF's implementation of distributed transactions uses Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="49971-125">其適用于特別支援的資源管理員，例如 SQL Server、MSMQ 或 Windows 檔案系統。</span><span class="sxs-lookup"><span data-stu-id="49971-125">It works with resource managers that specifically support it, like SQL Server, MSMQ, or Windows file systems.</span></span> <span data-ttu-id="49971-126">在現代的微服務世界中，由於使用的技術範圍較廣，因此沒有對等的功能。</span><span class="sxs-lookup"><span data-stu-id="49971-126">There's no equivalent yet in the modern microservices world, in part due to the wider range of technologies in use.</span></span> <span data-ttu-id="49971-127">如需交易的討論，請參閱[附錄 a](appendix.md)。</span><span class="sxs-lookup"><span data-stu-id="49971-127">For a discussion of transactions, see [Appendix A](appendix.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="49971-128">[上一頁](error-handling.md)
>[下一頁](migrate-wcf-to-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="49971-128">[Previous](error-handling.md)
[Next](migrate-wcf-to-grpc.md)</span></span>
