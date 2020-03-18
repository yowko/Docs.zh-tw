---
title: gRPC 應用中的安全性 - 適用于 WCF 開發人員的 gRPC
description: gRPC 中的呼叫和通道身份驗證和授權的概述。
ms.date: 09/02/2019
ms.openlocfilehash: 70cbf441bbc1b299b997f7d1f02bcd2bf7fde60c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147811"
---
# <a name="security-in-grpc-applications"></a>gRPC 應用程式中的安全性

在任何實際場景中，保護應用程式和服務都至關重要。 安全涵蓋三個關鍵領域：

* 加密網路流量，防止惡意駭客攔截網路流量。
* 驗證用戶端和伺服器以建立身份和信任。
* 授權用戶端控制對系統的訪問，並根據標識應用許可權。

> [!NOTE]
> *身份驗證*與建立用戶端或伺服器的標識有關。 *授權*涉及確定用戶端是否具有訪問資源或發出命令的許可權。

本章將介紹 gRPC 中用於ASP.NET核心的身份驗證和授權功能。 它還將討論通過 TLS 加密連接的網路安全。

## <a name="wcf-authentication-and-authorization"></a>WCF 身份驗證和授權

在 Windows 通信基礎 （WCF） 中，身份驗證和授權的處理方式不同，具體取決於所使用的傳輸和綁定。 WCF 支援各種\*WS-安全標準。 它還支援對在 IIS 中運行的 HTTP 服務或 Windows 系統之間的 NetTCP 服務進行 Windows 身份驗證。

## <a name="grpc-authentication-and-authorization"></a>gRPC 身份驗證和授權

gRPC 身份驗證和授權在兩個級別上工作：

* 調用級別的身份驗證/授權通常通過在進行調用時在中繼資料中應用的權杖進行處理。
* 通道級身份驗證使用在連接級別應用的用戶端憑證。 它還可以包括呼叫級身份驗證/授權憑據，以便自動應用於通道上的每個呼叫。

您可以使用以下任一機制或兩種機制來説明保護服務。

gRPC ASP.NET核心實現通過大多數標準ASP.NET核心機制支援身份驗證和授權：

- 呼叫身份驗證
  - Azure Active Directory
  - 標識伺服器
  - JWT 持票代幣
  - OAuth 2.0
  - OpenID Connect
  - WS-同盟
- 通道身份驗證
  - 用戶端憑證

調用身份驗證方法都基於*權杖*。 唯一的真正區別是權杖的生成方式以及用於驗證 ASP.NET Core 服務中的權杖的庫。

有關詳細資訊，請參閱[身份驗證和授權](/aspnet/core/grpc/authn-and-authz)一文。

> [!NOTE]
> 當您通過 TLS 加密的 HTTP/2 連接使用 gRPC 時，用戶端和伺服器之間的所有流量都加密，即使您不使用通道級身份驗證也是如此。

本章將演示如何將呼叫憑據和通道憑據應用於 gRPC 服務。 它還將演示如何使用 .NET Core gRPC 用戶端的憑據對服務進行身份驗證。

>[!div class="step-by-step"]
>[上一個](client-libraries.md)
>[下一個](call-credentials.md)
