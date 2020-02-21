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
# <a name="encryption-and-network-security"></a>加密和網路安全性

Windows Communication Foundation （WCF）的網路安全性模型是廣泛且複雜的。 它包含使用 HTTPS 或 TLS over TCP 的傳輸層級安全性，以及透過使用 WS-Security 規格來加密個別訊息的訊息層級安全性。

gRPC 會將安全的網路功能保留在基礎 HTTP/2 通訊協定中，您可以使用 TLS 憑證來保護它的安全。

Web 瀏覽器會堅持使用 HTTP/2 的 TLS 連線，但大部分的程式設計用戶端（包括）都是如此。NET 的 `HttpClient`，可以透過未加密的連接使用 HTTP/2。 `HttpClient` 預設需要加密，但是您可以使用 <xref:System.AppContext> 交換器來覆寫此項。

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

針對公用 Api，您應該一律使用 TLS 連線，並從適當的 SSL 授權單位為您的服務提供有效的憑證。 [LetsEncrypt](https://letsencrypt.org)提供免費的自動化 SSL 憑證，而大部分的裝載基礎結構目前都支援使用一般外掛程式或延伸模組的 LetsEncrypt 標準。

對於整個公司網路的內部服務，您仍應考慮使用 TLS 來保護進出 gRPC 服務的網路流量。

如果您需要在 Kubernetes 中執行的服務之間使用明確的 TLS，請考慮使用叢集內憑證授權單位單位和憑證管理員控制器（如[cert manager](https://docs.cert-manager.io/en/latest/)）。 接著，您可以在部署時，自動將憑證指派給服務。

>[!div class="step-by-step"]
>[上一頁](channel-credentials.md)
>[下一頁](grpc-in-production.md)
