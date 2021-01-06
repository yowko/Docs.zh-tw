---
title: WS-* 通訊協定-適用于 WCF 開發人員的 gRPC
description: 檢查 WCF 所支援的 WS-* 通訊協定，以及 gRPC 提供的替代方案
author: markrendle
ms.date: 12/15/2020
ms.openlocfilehash: d6fffdd5153c799c78ad949a3b16fa72e9612e43
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938477"
---
# <a name="ws--protocols"></a><span data-ttu-id="efeb9-103">WS- \* 通訊協定</span><span class="sxs-lookup"><span data-stu-id="efeb9-103">WS-\* protocols</span></span>

<span data-ttu-id="efeb9-104">使用 Windows Communication Foundation (WCF) 真正的優點之一，就是它支援許多現有的 _WS \*_ 標準通訊協定。</span><span class="sxs-lookup"><span data-stu-id="efeb9-104">One of the real benefits of working with Windows Communication Foundation (WCF) was that it supported many of the existing _WS-\*_ standard protocols.</span></span> <span data-ttu-id="efeb9-105">本節將簡短介紹 gRPC 如何管理相同的 WS- \* 通訊協定，並討論沒有替代方案時可使用的選項。</span><span class="sxs-lookup"><span data-stu-id="efeb9-105">This section will briefly cover how gRPC manages the same WS-\* protocols and discuss what options are available when there's no alternative.</span></span>

## <a name="metadata-exchange-ws-policy-ws-discovery-and-so-on"></a><span data-ttu-id="efeb9-106">中繼資料交換： WS-原則、WS-探索等</span><span class="sxs-lookup"><span data-stu-id="efeb9-106">Metadata exchange: WS-Policy, WS-Discovery, and so on</span></span>

<span data-ttu-id="efeb9-107">SOAP 服務會公開 Web 服務描述語言 (WSDL) 架構檔，其中包含資料格式、作業或通訊選項等資訊。</span><span class="sxs-lookup"><span data-stu-id="efeb9-107">SOAP services expose Web Services Description Language (WSDL) schema documents with information such as data formats, operations, or communication options.</span></span> <span data-ttu-id="efeb9-108">您可以使用此架構來產生用戶端程式代碼。</span><span class="sxs-lookup"><span data-stu-id="efeb9-108">You can use this schema to generate the client code.</span></span>

<span data-ttu-id="efeb9-109">從相同的檔案產生伺服器和用戶端時，gRPC 的效果最佳 `.proto` ，但伺服器反映選用的延伸模組可提供從執行中伺服器公開動態資訊的方式。</span><span class="sxs-lookup"><span data-stu-id="efeb9-109">gRPC works best when servers and clients are generated from the same `.proto` files, but a Server Reflection optional extension does provide a way to expose dynamic information from a running server.</span></span> <span data-ttu-id="efeb9-110">如需詳細資訊，請參閱 [Grpc。反映](https://nuget.org/packages/Grpc.Reflection) NuGet 封裝和 [Grpc c # 伺服器反映](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="efeb9-110">For more information, see the [Grpc.Reflection](https://nuget.org/packages/Grpc.Reflection) NuGet package and the [gRPC C# Server Reflection](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) article.</span></span>

<span data-ttu-id="efeb9-111">WS-Discovery 通訊協定是用來尋找區域網路上的服務。</span><span class="sxs-lookup"><span data-stu-id="efeb9-111">The WS-Discovery protocol is used to locate services on a local network.</span></span> <span data-ttu-id="efeb9-112">gRPC 服務位於 DNS 或服務登錄（例如 Consul 或 ZooKeeper）。</span><span class="sxs-lookup"><span data-stu-id="efeb9-112">gRPC services are located through DNS or a service registry such as Consul or ZooKeeper.</span></span>

## <a name="security-ws-security-ws-federation-xml-encryption-and-so-on"></a><span data-ttu-id="efeb9-113">安全性： WS-Security、WS-同盟、XML 加密等</span><span class="sxs-lookup"><span data-stu-id="efeb9-113">Security: WS-Security, WS-Federation, XML Encryption, and so on</span></span>

<span data-ttu-id="efeb9-114">[第6章](security.md)更詳細說明安全性、驗證和授權。</span><span class="sxs-lookup"><span data-stu-id="efeb9-114">Security, authentication, and authorization are covered in much more detail in [chapter 6](security.md).</span></span> <span data-ttu-id="efeb9-115">但值得注意的是，與 WCF 不同的是，gRPC 不支援 WS-Security、WS-同盟或 XML 加密。</span><span class="sxs-lookup"><span data-stu-id="efeb9-115">But it's worth noting here that, unlike WCF, gRPC doesn't support WS-Security, WS-Federation, or XML Encryption.</span></span> <span data-ttu-id="efeb9-116">儘管如此，gRPC 還提供絕佳的安全性。</span><span class="sxs-lookup"><span data-stu-id="efeb9-116">Even so, gRPC provides excellent security.</span></span> <span data-ttu-id="efeb9-117">所有 gRPC 的網路流量在使用 HTTP/2 over TLS 時都會自動加密。</span><span class="sxs-lookup"><span data-stu-id="efeb9-117">All gRPC network traffic is automatically encrypted when it's using HTTP/2 over TLS.</span></span> <span data-ttu-id="efeb9-118">您可以使用 X509 憑證進行相互用戶端/伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="efeb9-118">You can use X509 certificates for mutual client/server authentication.</span></span>

## <a name="ws-reliablemessaging"></a><span data-ttu-id="efeb9-119">WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="efeb9-119">WS-ReliableMessaging</span></span>

<span data-ttu-id="efeb9-120">gRPC 不會提供與 ws-reliablemessaging 相同的專案。</span><span class="sxs-lookup"><span data-stu-id="efeb9-120">gRPC does not provide an equivalent to WS-ReliableMessaging.</span></span> <span data-ttu-id="efeb9-121">重試語義應該在程式碼中處理，可能是 [Polly](https://github.com/App-vNext/Polly)之類的程式庫。</span><span class="sxs-lookup"><span data-stu-id="efeb9-121">Retry semantics should be handled in code, possibly with a library like [Polly](https://github.com/App-vNext/Polly).</span></span> <span data-ttu-id="efeb9-122">當您在 Kubernetes 或類似的協調流程環境中執行時， [服務網格](service-mesh.md) 也可以協助在服務之間提供可靠的訊息傳遞。</span><span class="sxs-lookup"><span data-stu-id="efeb9-122">When you're running in Kubernetes or similar orchestration environments, [service meshes](service-mesh.md) can also help to provide reliable messaging between services.</span></span>

## <a name="ws-transaction-ws-coordination"></a><span data-ttu-id="efeb9-123">WS 交易、WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="efeb9-123">WS-Transaction, WS-Coordination</span></span>

<span data-ttu-id="efeb9-124">WCF 的分散式交易執行會使用 Microsoft Distributed Transaction Coordinator (MSDTC) 。</span><span class="sxs-lookup"><span data-stu-id="efeb9-124">WCF's implementation of distributed transactions uses Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="efeb9-125">它適用于特別支援的資源管理員，例如 SQL Server、MSMQ 或 Windows 檔案系統。</span><span class="sxs-lookup"><span data-stu-id="efeb9-125">It works with resource managers that specifically support it, like SQL Server, MSMQ, or Windows file systems.</span></span> <span data-ttu-id="efeb9-126">在新式微服務世界中，沒有任何對等專案，因為使用的技術範圍較廣。</span><span class="sxs-lookup"><span data-stu-id="efeb9-126">There's no equivalent yet in the modern microservices world, in part due to the wider range of technologies in use.</span></span> <span data-ttu-id="efeb9-127">如需交易的討論，請參閱 [附錄 a](appendix.md)。</span><span class="sxs-lookup"><span data-stu-id="efeb9-127">For a discussion of transactions, see [Appendix A](appendix.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="efeb9-128">[上一個](error-handling.md) 
>[下一步](migrate-wcf-to-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="efeb9-128">[Previous](error-handling.md)
[Next](migrate-wcf-to-grpc.md)</span></span>
