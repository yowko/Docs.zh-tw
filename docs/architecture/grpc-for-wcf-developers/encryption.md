---
title: WCF 開發人員的加密和網路安全性 gRPC
description: GRPC 中網路安全性和加密的一些注意事項
ms.date: 09/02/2019
ms.openlocfilehash: f8a7aeaf2a65e4ff56ac33d728e40f09a436f7a6
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542764"
---
# <a name="encryption-and-network-security"></a><span data-ttu-id="5f6d7-103">加密和網路安全性</span><span class="sxs-lookup"><span data-stu-id="5f6d7-103">Encryption and network security</span></span>

<span data-ttu-id="5f6d7-104">Windows Communication Foundation （WCF）的網路安全性模型是廣泛且複雜的。</span><span class="sxs-lookup"><span data-stu-id="5f6d7-104">The network security model for Windows Communication Foundation (WCF) is extensive and complex.</span></span> <span data-ttu-id="5f6d7-105">它包含使用 HTTPS 或 TLS over TCP 的傳輸層級安全性，以及透過使用 WS-Security 規格來加密個別訊息的訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="5f6d7-105">It includes transport-level security by using HTTPS or TLS-over-TCP, and message-level security by using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="5f6d7-106">gRPC 會將安全的網路功能保留在基礎 HTTP/2 通訊協定中，您可以使用 TLS 憑證來保護它的安全。</span><span class="sxs-lookup"><span data-stu-id="5f6d7-106">gRPC leaves secure networking to the underlying HTTP/2 protocol, which you can secure by using TLS certificates.</span></span>

<span data-ttu-id="5f6d7-107">Web 瀏覽器會堅持使用 HTTP/2 的 TLS 連線，但大部分的程式設計用戶端（包括）都是如此。NET 的 `HttpClient`，可以透過未加密的連接使用 HTTP/2。</span><span class="sxs-lookup"><span data-stu-id="5f6d7-107">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span> <span data-ttu-id="5f6d7-108">`HttpClient` 預設需要加密，但是您可以使用 <xref:System.AppContext> 交換器來覆寫此項。</span><span class="sxs-lookup"><span data-stu-id="5f6d7-108">`HttpClient` does require encryption by default, but you can override this by using an <xref:System.AppContext> switch.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="5f6d7-109">針對公用 Api，您應該一律使用 TLS 連線，並從適當的 SSL 授權單位為您的服務提供有效的憑證。</span><span class="sxs-lookup"><span data-stu-id="5f6d7-109">For public APIs, you should always use TLS connections, and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="5f6d7-110">[LetsEncrypt](https://letsencrypt.org)提供免費的自動化 SSL 憑證，而大部分的裝載基礎結構目前都支援使用一般外掛程式或延伸模組的 LetsEncrypt 標準。</span><span class="sxs-lookup"><span data-stu-id="5f6d7-110">[LetsEncrypt](https://letsencrypt.org) provides free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="5f6d7-111">對於整個公司網路的內部服務，您仍應考慮使用 TLS 來保護進出 gRPC 服務的網路流量。</span><span class="sxs-lookup"><span data-stu-id="5f6d7-111">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="5f6d7-112">如果您需要在 Kubernetes 中執行的服務之間使用明確的 TLS，請考慮使用叢集內憑證授權單位單位和憑證管理員控制器（如[cert manager](https://docs.cert-manager.io/en/latest/)）。</span><span class="sxs-lookup"><span data-stu-id="5f6d7-112">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster certificate authority and a certificate manager controller like [cert-manager](https://docs.cert-manager.io/en/latest/).</span></span> <span data-ttu-id="5f6d7-113">接著，您可以在部署時，自動將憑證指派給服務。</span><span class="sxs-lookup"><span data-stu-id="5f6d7-113">You can then automatically assign certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5f6d7-114">[上一頁](channel-credentials.md)
>[下一頁](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="5f6d7-114">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
