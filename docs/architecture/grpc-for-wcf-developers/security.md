---
title: GRPC 應用程式中的安全性-WCF 開發人員適用的 gRPC
description: GRPC 中的呼叫和通道驗證和授權的總覽。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5f3d32817ccb5d9f278d256c0ee135f0e2a17cf2
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184138"
---
# <a name="security-in-grpc-applications"></a>GRPC 應用程式中的安全性

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在任何真實世界的案例中，保護應用程式和服務都是不可或缺的。 安全性涵蓋三個主要領域：加密網路流量以防止不良執行者攔截它;驗證用戶端和伺服器以建立身分識別和信任;和會授權用戶端控制系統的存取權，並根據身分識別套用許可權。

> [!NOTE]
> **驗證**會考慮建立用戶端或伺服器的身分識別。 **授權**會負責判斷用戶端是否有存取資源或發出命令的許可權。

本章將涵蓋 gRPC for ASP.NET Core 中驗證和授權的功能，並討論使用 TLS 加密連線的網路安全性。

## <a name="wcf-authentication-and-authorization"></a>WCF 驗證和授權

在 WCF 中，驗證和授權是以不同的方式處理，視使用的傳輸和系結而定。 WCF 支援各種 WS-\*安全性標準，以及 windows 驗證，適用于在 IIS 中執行的 HTTP 服務或 windows 系統之間的 NetTCP 服務。

## <a name="grpc-authentication-and-authorization"></a>gRPC 驗證與授權

gRPC 驗證和授權適用于兩個層級。 呼叫層級驗證/授權通常會使用在進行呼叫時于中繼資料中套用的權杖來處理。 通道層級驗證會使用在連線層級套用的用戶端憑證，也可以包含要自動套用至通道上每個呼叫的呼叫層級驗證/授權認證。 您可以使用其中一種或兩種機制來保護您的服務。

GRPC 的 ASP.NET Core 實作為使用大部分標準 ASP.NET Core 機制來支援驗證和授權：

- 呼叫驗證
  - Azure Active Directory
  - IdentityServer
  - JWT 持有人權杖
  - OAuth 2。0
  - OpenID Connect
  - WS-Federation
- 通道驗證
  - 用戶端憑證

呼叫驗證方法全都以*權杖*為基礎。 唯一的真正差異在於權杖的產生方式，以及用來驗證 ASP.NET Core 服務中之權杖的程式庫。

如需詳細資訊，請參閱[Microsoft Docs 上的驗證和授權檔](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0)。

> [!NOTE]
> 在 TLS 加密的 HTTP/2 連線上使用 gRPC 時，用戶端與伺服器之間的所有流量都會加密，即使您未使用通道層級驗證也一樣。

本章將示範如何將呼叫認證和通道認證套用至 gRPC 服務，以及如何使用 .NET Core gRPC 用戶端的認證來向服務進行驗證。

>[!div class="step-by-step"]
>[上一頁](client-libraries.md)
>[下一頁](call-credentials.md)
