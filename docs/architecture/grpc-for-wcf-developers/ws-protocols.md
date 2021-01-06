---
title: WS-* 通訊協定-適用于 WCF 開發人員的 gRPC
description: 檢查 WCF 所支援的 WS-* 通訊協定，以及 gRPC 提供的替代方案
author: markrendle
ms.date: 12/15/2020
ms.openlocfilehash: d6fffdd5153c799c78ad949a3b16fa72e9612e43
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938477"
---
# <a name="ws--protocols"></a>WS- \* 通訊協定

使用 Windows Communication Foundation (WCF) 真正的優點之一，就是它支援許多現有的 _WS \*_ 標準通訊協定。 本節將簡短介紹 gRPC 如何管理相同的 WS- \* 通訊協定，並討論沒有替代方案時可使用的選項。

## <a name="metadata-exchange-ws-policy-ws-discovery-and-so-on"></a>中繼資料交換： WS-原則、WS-探索等

SOAP 服務會公開 Web 服務描述語言 (WSDL) 架構檔，其中包含資料格式、作業或通訊選項等資訊。 您可以使用此架構來產生用戶端程式代碼。

從相同的檔案產生伺服器和用戶端時，gRPC 的效果最佳 `.proto` ，但伺服器反映選用的延伸模組可提供從執行中伺服器公開動態資訊的方式。 如需詳細資訊，請參閱 [Grpc。反映](https://nuget.org/packages/Grpc.Reflection) NuGet 封裝和 [Grpc c # 伺服器反映](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) 文章。

WS-Discovery 通訊協定是用來尋找區域網路上的服務。 gRPC 服務位於 DNS 或服務登錄（例如 Consul 或 ZooKeeper）。

## <a name="security-ws-security-ws-federation-xml-encryption-and-so-on"></a>安全性： WS-Security、WS-同盟、XML 加密等

[第6章](security.md)更詳細說明安全性、驗證和授權。 但值得注意的是，與 WCF 不同的是，gRPC 不支援 WS-Security、WS-同盟或 XML 加密。 儘管如此，gRPC 還提供絕佳的安全性。 所有 gRPC 的網路流量在使用 HTTP/2 over TLS 時都會自動加密。 您可以使用 X509 憑證進行相互用戶端/伺服器驗證。

## <a name="ws-reliablemessaging"></a>WS-ReliableMessaging

gRPC 不會提供與 ws-reliablemessaging 相同的專案。 重試語義應該在程式碼中處理，可能是 [Polly](https://github.com/App-vNext/Polly)之類的程式庫。 當您在 Kubernetes 或類似的協調流程環境中執行時， [服務網格](service-mesh.md) 也可以協助在服務之間提供可靠的訊息傳遞。

## <a name="ws-transaction-ws-coordination"></a>WS 交易、WS-Coordination

WCF 的分散式交易執行會使用 Microsoft Distributed Transaction Coordinator (MSDTC) 。 它適用于特別支援的資源管理員，例如 SQL Server、MSMQ 或 Windows 檔案系統。 在新式微服務世界中，沒有任何對等專案，因為使用的技術範圍較廣。 如需交易的討論，請參閱 [附錄 a](appendix.md)。

>[!div class="step-by-step"]
>[上一個](error-handling.md) 
>[下一步](migrate-wcf-to-grpc.md)
