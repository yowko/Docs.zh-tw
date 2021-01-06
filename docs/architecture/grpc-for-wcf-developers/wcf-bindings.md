---
title: Wcf 系結和傳輸-適用于 WCF 開發人員的 gRPC
description: 瞭解不同的 WCF 系結和傳輸與 gRPC 的比較。
ms.date: 12/15/2020
ms.openlocfilehash: 7a50e3e4468d86a6140066502a765818119642d4
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938503"
---
# <a name="wcf-bindings-and-transports"></a>WCF 繫結和傳輸

Windows Communication Foundation (WCF) 具有內建系 *結，可* 指定不同的網路通訊協定、電傳格式和其他的執行詳細資料。 gRPC 實際上只有一個網路通訊協定和一個電傳格式。  (技術上，您 *可以* 自訂電傳格式，但這已超出本書的範圍。 ) 您可能會發現 gRPC 在大部分情況下都能提供最佳解決方案。

接下來是關於最相關 WCF 系結的簡短討論，以及它們與 gRPC 中的對應專案之間的比較。

## <a name="nettcp"></a>NetTCP

WCF 的 NetTCP 系結允許持續連線、小型訊息和雙向訊息。 但它只能在 .NET 用戶端和伺服器之間運作。 gRPC 允許相同的功能，但在多個程式設計語言和平臺上都有支援。

gRPC 具有 WCF NetTCP 系結的許多功能，但不一定會以相同的方式來執行。 例如，在 WCF 中，加密是透過設定來控制，並在架構中處理。 在 gRPC 中，透過 TLS 透過 HTTP/2 在連線層級達到加密。

## <a name="http"></a>HTTP

稱為 BasicHttpBinding 的 WCF 系結通常是以文字為基礎，而且會使用 SOAP 做為電傳格式。 相較于 NetTCP 系結，它的速度很慢。 它是用來提供跨平臺的互通性，或透過網際網路基礎結構的連線。

GRPC 中的對等用法會使用 HTTP/2 作為訊息的二進位 Protobuf 電傳格式的基礎傳輸層。 因此它可以提供 NetTCP 服務層級的效能，以及所有新式程式設計語言和架構的完整跨平臺互通性。

## <a name="named-pipes"></a>具名管道

WCF 提供 *具名管道* 系結，以便在相同實體電腦上的進程之間進行通訊。 ASP.NET Core gRPC 的第一版不支援具名管道。 為具名管道 (和 Unix 網域通訊端新增用戶端和伺服器支援，) 是未來版本的目標。

## <a name="msmq"></a>MSMQ

MSMQ 是專屬的 Windows 訊息佇列。 WCF 對 MSMQ 的系結可讓用戶端在未來隨時處理的要求「引發」和「遺忘」。 gRPC 本身不會提供任何訊息佇列功能。

最佳替代方式是直接使用訊息系統，例如 Azure 服務匯流排、RabbitMQ 或 Kafka。 您可以透過將訊息直接放到佇列的用戶端，或將訊息的 gRPC 用戶端串流服務來執行此功能。

## <a name="webhttpbinding"></a>WebHttpBinding

WebHttpBinding (也稱為 WCF REST) ，其中包含 `WebGet` 和 `WebInvoke` 屬性，可讓您開發 RESTful api，以便在這種行為較不常見時，一次就能說出 JSON。 如果您有以 WCF REST 建立的 RESTful API，請考慮將它遷移至一般 ASP.NET Core MVC Web API 應用程式。 這項遷移會提供與 gRPC 轉換相同的功能。

>[!div class="step-by-step"]
>[上一個](wcf-endpoints-grpc-methods.md) 
>[下一步](rpc-types.md)
