---
title: 適用于 WCF 開發人員的加密和網路安全性-gRPC
description: GRPC 中的網路安全性和加密注意事項
ms.date: 01/06/2021
ms.openlocfilehash: cf4d30ff862e64aadfeacf45ed3768fc14737800
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970137"
---
# <a name="encryption-and-network-security"></a><span data-ttu-id="b2f57-103">加密和網路安全性</span><span class="sxs-lookup"><span data-stu-id="b2f57-103">Encryption and network security</span></span>

<span data-ttu-id="b2f57-104">Windows Communication Foundation (WCF) 的網路安全性模型是廣泛且複雜的。</span><span class="sxs-lookup"><span data-stu-id="b2f57-104">The network security model for Windows Communication Foundation (WCF) is extensive and complex.</span></span> <span data-ttu-id="b2f57-105">它包含使用 HTTPS 或 TLS over TCP 的傳輸層級安全性，以及使用 WS-Security 規格將個別訊息加密的訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="b2f57-105">It includes transport-level security by using HTTPS or TLS-over-TCP, and message-level security by using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="b2f57-106">gRPC 會將安全的網路功能保留給基礎 HTTP/2 通訊協定，您可以使用 TLS 憑證來保護這些通訊協定。</span><span class="sxs-lookup"><span data-stu-id="b2f57-106">gRPC leaves secure networking to the underlying HTTP/2 protocol, which you can secure by using TLS certificates.</span></span>

<span data-ttu-id="b2f57-107">Web 瀏覽器會堅持使用 HTTP/2 的 TLS 連線，但大部分的程式設計用戶端，包括在內。NET 的 `HttpClient` ，可以透過未加密的連接使用 HTTP/2。</span><span class="sxs-lookup"><span data-stu-id="b2f57-107">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span>

<span data-ttu-id="b2f57-108">針對公用 Api，您應該一律使用 TLS 連線，並從適當的 SSL 授權單位為您的服務提供有效的憑證。</span><span class="sxs-lookup"><span data-stu-id="b2f57-108">For public APIs, you should always use TLS connections, and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="b2f57-109">[LetsEncrypt](https://letsencrypt.org) 提供免費的自動化 SSL 憑證，而大部分的裝載基礎結構現在都支援具有一般外掛程式或延伸模組的 LetsEncrypt 標準。</span><span class="sxs-lookup"><span data-stu-id="b2f57-109">[LetsEncrypt](https://letsencrypt.org) provides free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="b2f57-110">對於跨公司網路的內部服務，您仍然應該考慮使用 TLS 來保護進出您 gRPC 服務的網路流量。</span><span class="sxs-lookup"><span data-stu-id="b2f57-110">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="b2f57-111">如果您需要在 Kubernetes 中執行的服務之間使用明確的 TLS，請考慮使用叢集內的憑證授權單位單位和憑證管理員控制器（例如 [cert 管理員](https://docs.cert-manager.io/en/latest/)）。</span><span class="sxs-lookup"><span data-stu-id="b2f57-111">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster certificate authority and a certificate manager controller like [cert-manager](https://docs.cert-manager.io/en/latest/).</span></span> <span data-ttu-id="b2f57-112">然後，您可以在部署時自動將憑證指派給服務。</span><span class="sxs-lookup"><span data-stu-id="b2f57-112">You can then automatically assign certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b2f57-113">[上一個](channel-credentials.md) 
>[下一步](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="b2f57-113">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
