---
title: GRPC 應用程式中的安全性-WCF 開發人員適用的 gRPC
description: GRPC 中的呼叫和通道驗證和授權的總覽。
ms.date: 09/02/2019
ms.openlocfilehash: d5804ad5de4a834eb81b90fa1ea7a61969a0b42f
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503416"
---
# <a name="security-in-grpc-applications"></a>gRPC 應用程式中的安全性

在任何真實世界的案例中，保護應用程式和服務都是不可或缺的。 安全性涵蓋三個主要領域： 

* 將網路流量加密，以防止惡意駭客攔截它。
* 驗證用戶端和伺服器以建立身分識別和信任。
* 授權用戶端控制系統的存取權，並根據身分識別套用許可權。

> [!NOTE]
> *驗證*會考慮建立用戶端或伺服器的身分識別。 *授權*會負責判斷用戶端是否有存取資源或發出命令的許可權。

本章將涵蓋 gRPC for ASP.NET Core 的驗證和授權功能。 它也會透過 TLS 加密連接討論網路安全性。

## <a name="wcf-authentication-and-authorization"></a>WCF 驗證和授權

在 Windows Communication Foundation （WCF）中，驗證和授權是以不同的方式處理，視使用的傳輸和系結而定。 WCF 支援各種 WS-\* 安全性標準。 它也支援在 IIS 中執行的 HTTP 服務或 Windows 系統之間 NetTCP 服務的 Windows 驗證。

## <a name="grpc-authentication-and-authorization"></a>gRPC 驗證與授權

gRPC 驗證和授權適用于兩個層級：

* 呼叫層級的驗證/授權通常是透過在進行呼叫時于中繼資料中套用的權杖來處理。 
* 通道層級驗證會使用在連接層級套用的用戶端憑證。 它也可以包含呼叫層級的驗證/授權認證，以自動套用至通道上的每個呼叫。 

您可以使用其中一種或兩種機制來協助保護您的服務。

GRPC 的 ASP.NET Core 實作為透過大部分標準 ASP.NET Core 機制來支援驗證和授權：

- 呼叫驗證
  - Azure Active Directory
  - IdentityServer
  - JWT 持有人權杖
  - OAuth 2.0
  - OpenID Connect
  - WS-同盟
- 通道驗證
  - 用戶端憑證

呼叫驗證方法全都以*權杖*為基礎。 唯一的真正差異在於如何產生權杖，以及用來驗證 ASP.NET Core 服務中之權杖的程式庫。

如需詳細資訊，請參閱[驗證和授權](/aspnet/core/grpc/authn-and-authz)一文。

> [!NOTE]
> 當您在 TLS 加密的 HTTP/2 連線上使用 gRPC 時，用戶端與伺服器之間的所有流量都會加密，即使您未使用通道層級驗證也一樣。

本章將示範如何將呼叫認證和通道認證套用至 gRPC 服務。 它也會示範如何使用 .NET Core gRPC 用戶端的認證來向服務進行驗證。

>[!div class="step-by-step"]
>[上一頁](client-libraries.md)
>[下一頁](call-credentials.md)
