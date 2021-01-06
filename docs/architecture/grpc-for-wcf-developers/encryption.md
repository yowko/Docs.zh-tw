---
title: 適用于 WCF 開發人員的加密和網路安全性-gRPC
description: GRPC 中的網路安全性和加密注意事項
ms.date: 12/15/2020
ms.openlocfilehash: 0735158ed69ce425c4f00eed6c42689b888a1885
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938620"
---
# <a name="encryption-and-network-security"></a>加密和網路安全性

Windows Communication Foundation (WCF) 的網路安全性模型是廣泛且複雜的。 它包含使用 HTTPS 或 TLS over TCP 的傳輸層級安全性，以及使用 WS-Security 規格將個別訊息加密的訊息層級安全性。

gRPC 會將安全的網路功能保留給基礎 HTTP/2 通訊協定，您可以使用 TLS 憑證來保護這些通訊協定。

Web 瀏覽器會堅持使用 HTTP/2 的 TLS 連線，但大部分的程式設計用戶端，包括在內。NET 的 `HttpClient` ，可以透過未加密的連接使用 HTTP/2。 `HttpClient` 預設需要加密，但您可以使用交換器覆寫此行為 <xref:System.AppContext> 。

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

針對公用 Api，您應該一律使用 TLS 連線，並從適當的 SSL 授權單位為您的服務提供有效的憑證。 [LetsEncrypt](https://letsencrypt.org) 提供免費的自動化 SSL 憑證，而大部分的裝載基礎結構現在都支援具有一般外掛程式或延伸模組的 LetsEncrypt 標準。

對於跨公司網路的內部服務，您仍然應該考慮使用 TLS 來保護進出您 gRPC 服務的網路流量。

如果您需要在 Kubernetes 中執行的服務之間使用明確的 TLS，請考慮使用叢集內的憑證授權單位單位和憑證管理員控制器（例如 [cert 管理員](https://docs.cert-manager.io/en/latest/)）。 然後，您可以在部署時自動將憑證指派給服務。

>[!div class="step-by-step"]
>[上一個](channel-credentials.md) 
>[下一步](grpc-in-production.md)
