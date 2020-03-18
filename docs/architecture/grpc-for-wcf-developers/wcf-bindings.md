---
title: WCF 綁定和傳輸 - gRPC 面向 WCF 開發人員
description: 瞭解不同的 WCF 綁定和傳輸與 gRPC 的比較情況。
ms.date: 09/02/2019
ms.openlocfilehash: 3a295268b486578c70c2c98f1d05f89070daaeb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147720"
---
# <a name="wcf-bindings-and-transports"></a>WCF 繫結和傳輸

Windows 通信基礎 （WCF） 具有內置*綁定*，用於指定不同的網路通訊協定、線格式和其他實現詳細資訊。 gRPC 實際上只有一個網路通訊協定和一個線格式。 （從技術上講，*您可以*自訂線格式，但這超出了本書的範圍。您可能會發現 gRPC 在大多數情況下提供了最佳解決方案。

以下是關於最相關的 WCF 綁定及其與 gRPC 中的等效綁定的比較的簡短討論。

## <a name="nettcp"></a>NetTCP

WCF 的 NetTCP 綁定允許持久連接、小消息和雙向消息傳送。 但它僅在 .NET 用戶端和伺服器之間工作。 gRPC 允許相同的功能，但支援跨多個程式設計語言和平臺。

gRPC 具有 WCF NetTCP 綁定的許多功能，但它們並不總是以相同的方式實現。 例如，在 WCF 中，加密通過配置進行控制，並在框架中處理。 在 gRPC 中，通過 TLS 的 HTTP/2 在連接級別實現加密。

## <a name="http"></a>HTTP

稱為 BasicHttpBinding 的 WCF 綁定通常基於文本，並使用 SOAP 作為線格式。 與 NetTCP 綁定相比，它的速度很慢。 它通常用於提供跨平臺互通性或通過 Internet 基礎結構進行連接。

gRPC 中的等效項使用 HTTP/2 作為具有二進位 Protobuf 線格式的消息的基礎傳輸層。 因此，它可以提供 NetTCP 服務等級的性能，並與所有現代程式設計語言和框架實現全跨平臺互通性。

## <a name="named-pipes"></a>具名管道

WCF 提供了一*個具名管道*綁定，用於在同一物理電腦上的進程之間的通信。 ASP.NET核心 gRPC 的第一個版本不支援具名管道。 添加具名管道（和 Unix 域通訊端）的用戶端和伺服器支援是未來版本的目標。

## <a name="msmq"></a>MSMQ

MSMQ 是一個專有的 Windows 訊息佇列。 WCF 與 MSMQ 的綁定允許來自用戶端的"觸發和忘記"請求，這些請求將來可能隨時處理。 gRPC 不本機提供任何訊息佇列功能。

最好的選擇是直接使用消息傳遞系統，如 Azure 服務匯流排、兔子MQ或 Kafka。 可以通過將消息直接放在佇列上的用戶端或對消息進行排隊的 gRPC 用戶端流服務來實現此項。

## <a name="webhttpbinding"></a>WebHttpBinding

WebHttpBinding（也稱為 WCF REST），具有`WebGet`和`WebInvoke`屬性，使您能夠開發 RESTful API，在不太常見時可以講 JSON。 如果使用 WCF REST 構建了 RESTful API，請考慮將其遷移到常規ASP.NET核心 MVC Web API 應用程式。 此遷移將提供與轉換為 gRPC 相同的功能。

>[!div class="step-by-step"]
>[上一個](wcf-endpoints-grpc-methods.md)
>[下一個](rpc-types.md)
