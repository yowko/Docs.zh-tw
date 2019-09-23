---
title: WCF 開發人員的加密和網路安全性 gRPC
description: GRPC 中網路安全性和加密的一些注意事項
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 8a115b59337003669b4e5436edffe239489ca79e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184460"
---
# <a name="encryption-and-network-security"></a><span data-ttu-id="ca93c-103">加密和網路安全性</span><span class="sxs-lookup"><span data-stu-id="ca93c-103">Encryption and network security</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ca93c-104">WCF 的網路安全性模型是廣泛且複雜的，包括使用 HTTPS 或 TLS over TCP 的傳輸層級安全性，以及使用 WS-Security 規格來加密個別訊息的訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="ca93c-104">WCF's network security model is extensive and complex, including transport-level security using HTTPS or TLS-over-TCP, and message-level security using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="ca93c-105">gRPC 會將安全的網路功能保留在基礎 HTTP/2 通訊協定中，這可以使用一般 TLS 憑證來加以保護。</span><span class="sxs-lookup"><span data-stu-id="ca93c-105">gRPC leaves secure networking to the underlying HTTP/2 protocol, which can be secured using regular TLS certificates.</span></span>

<span data-ttu-id="ca93c-106">Web 瀏覽器會堅持使用 HTTP/2 的 TLS 連線，但大部分的程式設計用戶端（包括）都是如此。NET 的`HttpClient`，可以透過未加密的連接使用 HTTP/2。</span><span class="sxs-lookup"><span data-stu-id="ca93c-106">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span> <span data-ttu-id="ca93c-107">`HttpClient`預設*需要加密*，但您可以使用<xref:System.AppContext>參數覆寫此項。</span><span class="sxs-lookup"><span data-stu-id="ca93c-107">`HttpClient` *does* require encryption by default, but you can override this using an <xref:System.AppContext> switch.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="ca93c-108">針對公用 Api，您應該一律使用 TLS 連線，並從適當的 SSL 授權單位為您的服務提供有效的憑證。</span><span class="sxs-lookup"><span data-stu-id="ca93c-108">For public APIs, you should always use TLS connections and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="ca93c-109">[LetsEncrypt](https://letsencrypt.org)提供免費的自動化 SSL 憑證，而大部分的裝載基礎結構目前都支援使用一般外掛程式或延伸模組的 LetsEncrypt 標準。</span><span class="sxs-lookup"><span data-stu-id="ca93c-109">[LetsEncrypt](https://letsencrypt.org) provide free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="ca93c-110">對於整個公司網路的內部服務，您仍應考慮使用 TLS 來保護進出 gRPC 服務的網路流量。</span><span class="sxs-lookup"><span data-stu-id="ca93c-110">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="ca93c-111">叢集（例如 Kubernetes 或 Docker Swarm）之間的微服務之間的通訊一般是由容器網路層自動加密，因此不需要在這類叢集內以獨佔方式執行的服務中進行 TLS。</span><span class="sxs-lookup"><span data-stu-id="ca93c-111">Communication between microservices in a cluster like Kubernetes or Docker Swarm is in general automatically encrypted by the container networking layer, so implementing TLS in services running exclusively in such a cluster isn't necessary.</span></span> <span data-ttu-id="ca93c-112">下一章的「服務網格」一節中將會有更多關於此主題的資訊。</span><span class="sxs-lookup"><span data-stu-id="ca93c-112">There will be more on this subject in the "Service Mesh" section of the next chapter.</span></span>

<span data-ttu-id="ca93c-113">如果您需要在 Kubernetes 中執行的服務之間使用明確的 TLS，請考慮使用叢集內的憑證授權單位單位和憑證管理員控制器（例如[cert 管理員](https://docs.cert-manager.io/en/latest/)），在部署期間指派自動憑證給服務。</span><span class="sxs-lookup"><span data-stu-id="ca93c-113">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster Certificate Authority and a Certificate Manager Controller like [cert-manager](https://docs.cert-manager.io/en/latest/) to assign automatically certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ca93c-114">[上一頁](channel-credentials.md)
>[下一頁](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="ca93c-114">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
