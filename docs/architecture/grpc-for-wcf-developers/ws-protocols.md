---
title: WS-* 通訊協定-適用于 WCF 開發人員的 gRPC
description: 檢查 WCF 支援的 WS-* 通訊協定，以及 gRPC 所提供的替代專案
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: c8c06a5e23a4d7859165e1c562032055d63d76f7
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503292"
---
# <a name="ws--protocols"></a>WS-\* 通訊協定

使用 Windows Communication Foundation （WCF）的其中一項真正優點，就是支援許多現有的_WS\*_ 標準通訊協定。 本節將簡短說明 gRPC 如何管理相同的 WS\* 通訊協定，並討論沒有替代方案時可用的選項。

## <a name="metadata-exchange-ws-policy-ws-discovery-and-so-on"></a>中繼資料交換： WS-原則、WS-Discovery 等等

SOAP 服務會公開 Web 服務描述語言（WSDL）架構檔，其中包含資料格式、作業或通訊選項等資訊。 您可以使用此架構來產生用戶端程式代碼。

從相同的 `.proto` 檔案產生伺服器和用戶端時，gRPC 的效果最佳，但是伺服器反映選用的延伸模組則提供了一種方式，可以從執行中的伺服器公開動態資訊。 如需詳細資訊，請參閱[Grpc](https://nuget.org/packages/Grpc.Reflection) NuGet 套件和[ C# Grpc Server 反映](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md)一文。

WS-探索通訊協定可用來尋找區域網路上的服務。 gRPC 服務通常是透過 DNS 或服務登錄（例如 Consul 或 ZooKeeper）來尋找。

## <a name="security-ws-security-ws-federation-xml-encryption-and-so-on"></a>安全性： WS-安全性、WS-同盟、XML 加密等等

[第6章](security.md)會詳細討論安全性、驗證和授權。 但值得注意的是，與 WCF 不同的是，gRPC 不支援 WS-Security、WS-同盟或 XML 加密。 就算如此，gRPC 也提供絕佳的安全性。 當所有 gRPC 網路流量透過 TLS 使用 HTTP/2 時，都會自動加密。 您可以使用 X509 憑證進行相互用戶端/伺服器驗證。

## <a name="ws-reliablemessaging"></a>WS-ReliableMessaging

gRPC 並未提供與 ws-reliablemessaging 相等的。 重試語法應該在程式碼中處理，可能是[Polly](https://github.com/App-vNext/Polly)之類的程式庫。 當您在 Kubernetes 或類似的協調流程環境中執行時，[服務網格](service-mesh.md)也可以協助在服務之間提供可靠的訊息傳遞。

## <a name="ws-transaction-ws-coordination"></a>WS-交易，WS-協調

WCF 的分散式交易執行會使用 Microsoft 分散式交易協調器（MSDTC）。 其適用于特別支援的資源管理員，例如 SQL Server、MSMQ 或 Windows 檔案系統。 在現代的微服務世界中，由於使用的技術範圍較廣，因此沒有對等的功能。 如需交易的討論，請參閱[附錄 a](appendix.md)。

>[!div class="step-by-step"]
>[上一頁](error-handling.md)
>[下一頁](migrate-wcf-to-grpc.md)
