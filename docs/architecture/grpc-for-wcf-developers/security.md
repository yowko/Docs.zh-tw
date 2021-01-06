---
title: GRPC 應用程式中的安全性-適用于 WCF 開發人員的 gRPC
description: GRPC 中的呼叫和通道驗證與授權總覽。
ms.date: 12/15/2020
ms.openlocfilehash: a5c16a4a4f7567e23bf4f9e3049fe116086daf12
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938087"
---
# <a name="security-in-grpc-applications"></a>gRPC 應用程式中的安全性

在任何真實世界的案例中，保護應用程式和服務是不可或缺的。 安全性涵蓋三個主要領域：

* 加密網路流量，以防止惡意駭客攔截它。
* 驗證用戶端和伺服器以建立身分識別與信任。
* 授權用戶端控制對系統的存取，並根據身分識別套用許可權。

> [!NOTE]
> *驗證* 與建立用戶端或伺服器的身分識別相關。 *授權* 與判斷用戶端是否有權存取資源或發出命令相關。

本章將涵蓋 gRPC 中的驗證和授權功能，以進行 ASP.NET Core。 它也會透過 TLS 加密連線來討論網路安全性。

## <a name="wcf-authentication-and-authorization"></a>WCF 驗證與授權

在 Windows Communication Foundation (WCF) ，驗證和授權是以不同的方式處理，視所使用的傳輸和系結而定。 WCF 支援各種 WS- \* 安全性標準。 它也支援在 IIS 中執行的 HTTP 服務，或在 Windows 系統之間 NetTCP 服務的 Windows 驗證。

## <a name="grpc-authentication-and-authorization"></a>gRPC 驗證和授權

gRPC authentication 和授權適用于兩個層級：

* 呼叫層級驗證/授權通常會透過在進行呼叫時套用於中繼資料的權杖來處理。
* 通道層級驗證會使用在連接層級套用的用戶端憑證。 它也可以包含要套用至通道上每次呼叫的呼叫層級驗證/授權認證。

您可以使用其中一種或兩種機制來協助保護您的服務。

GRPC 的 ASP.NET Core 執行透過大部分標準 ASP.NET Core 機制來支援驗證和授權：

- 呼叫驗證
  - Azure Active Directory
  - IdentityServer
  - JWT 持有人權杖
  - OAuth 2.0
  - OpenID Connect
  - WS-同盟
- 通道驗證
  - 用戶端憑證

呼叫驗證方法都是以 *權杖* 為基礎。 唯一的差別在於權杖的產生方式，以及用來驗證 ASP.NET Core 服務中權杖的程式庫。

如需詳細資訊，請參閱 [驗證和授權](/aspnet/core/grpc/authn-and-authz) 文章。

> [!NOTE]
> 當您透過 TLS 加密的 HTTP/2 連線使用 gRPC 時，用戶端與伺服器之間的所有流量都會加密，即使您未使用通道層級驗證也一樣。

本章將說明如何將通話認證和通道認證套用至 gRPC 服務。 它也會示範如何使用來自 .NET gRPC 用戶端的認證來向服務進行驗證。

>[!div class="step-by-step"]
>[上一個](client-libraries.md) 
>[下一步](call-credentials.md)
