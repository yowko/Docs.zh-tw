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
# <a name="encryption-and-network-security"></a>加密和網路安全性

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

WCF 的網路安全性模型是廣泛且複雜的，包括使用 HTTPS 或 TLS over TCP 的傳輸層級安全性，以及使用 WS-Security 規格來加密個別訊息的訊息層級安全性。

gRPC 會將安全的網路功能保留在基礎 HTTP/2 通訊協定中，這可以使用一般 TLS 憑證來加以保護。

Web 瀏覽器會堅持使用 HTTP/2 的 TLS 連線，但大部分的程式設計用戶端（包括）都是如此。NET 的`HttpClient`，可以透過未加密的連接使用 HTTP/2。 `HttpClient`預設*需要加密*，但您可以使用<xref:System.AppContext>參數覆寫此項。

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

針對公用 Api，您應該一律使用 TLS 連線，並從適當的 SSL 授權單位為您的服務提供有效的憑證。 [LetsEncrypt](https://letsencrypt.org)提供免費的自動化 SSL 憑證，而大部分的裝載基礎結構目前都支援使用一般外掛程式或延伸模組的 LetsEncrypt 標準。

對於整個公司網路的內部服務，您仍應考慮使用 TLS 來保護進出 gRPC 服務的網路流量。

叢集（例如 Kubernetes 或 Docker Swarm）之間的微服務之間的通訊一般是由容器網路層自動加密，因此不需要在這類叢集內以獨佔方式執行的服務中進行 TLS。 下一章的「服務網格」一節中將會有更多關於此主題的資訊。

如果您需要在 Kubernetes 中執行的服務之間使用明確的 TLS，請考慮使用叢集內的憑證授權單位單位和憑證管理員控制器（例如[cert 管理員](https://docs.cert-manager.io/en/latest/)），在部署期間指派自動憑證給服務。

>[!div class="step-by-step"]
>[上一頁](channel-credentials.md)
>[下一頁](grpc-in-production.md)
