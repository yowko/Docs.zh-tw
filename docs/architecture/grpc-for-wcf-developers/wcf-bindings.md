---
title: WCF 系結和傳輸-WCF 開發人員的 gRPC
description: 瞭解不同的 WCF 系結和傳輸與 gRPC 之間的比較。
ms.date: 09/02/2019
ms.openlocfilehash: ebe324eace8f5f418b920c59f6d72eaaa686ef02
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503355"
---
# <a name="wcf-bindings-and-transports"></a>WCF 繫結和傳輸

Windows Communication Foundation （WCF）有內建的系*結，可*指定不同的網路通訊協定、電傳格式和其他的執行詳細資料。 gRPC 實際上只有一個網路通訊協定和一個電傳格式。 （技術上來說，您*可以*自訂電傳格式，但這不在本書的討論範圍內）。在大部分情況下，您可能會發現 gRPC 提供最佳的解決方案。 

接下來是關於最相關的 WCF 系結，以及它們如何與 gRPC 中的對等專案進行比較的簡短討論。

## <a name="nettcp"></a>NetTCP

WCF 的 NetTCP 系結允許持續性連接、小型訊息和雙向訊息傳遞。 但它只能在 .NET 用戶端和伺服器之間運作。 gRPC 允許相同的功能，但在多個程式設計語言和平臺上都支援。 

gRPC 有許多 WCF NetTCP 系結的功能，但它們不一定會以相同的方式來執行。 例如，在 WCF 中，加密是透過設定來控制，並在架構中處理。 在 gRPC 中，加密是透過 TLS 的 HTTP/2 在連線層級達成。

## <a name="http"></a>HTTP

名為 BasicHttpBinding 的 WCF 系結通常是以文字為基礎，並使用 SOAP 做為電傳格式。 相較于 NetTCP 系結，它的速度比較慢。 它通常用來提供跨平臺互通性，或透過網際網路基礎結構的連線。 

GRPC 中的對等用法會使用 HTTP/2 作為訊息的二進位 Protobuf 電傳格式的基礎傳輸層。 因此，它可以提供 NetTCP 服務層級的效能，以及與所有新式程式設計語言和架構的完整跨平臺互通性。

## <a name="named-pipes"></a>具名管道

WCF 提供了*具名管道*系結，以便在相同實體電腦上的進程之間進行通訊。 ASP.NET Core gRPC 的第一版不支援具名管道。 新增具名管道（和 Unix 網域通訊端）的用戶端和伺服器支援是未來版本的目標。

## <a name="msmq"></a>MSMQ

MSMQ 是專屬的 Windows 訊息佇列。 WCF 對 MSMQ 的系結可讓您在未來可能會處理的用戶端「引發並忘記」要求。 gRPC 原本不提供任何訊息佇列功能。 

最佳的替代方法是直接使用訊息系統，例如 Azure 服務匯流排、RabbitMQ 或 Kafka。 您可以透過將訊息直接放入佇列的用戶端，或將訊息的 gRPC 用戶端串流服務來執行此程式。

## <a name="webhttpbinding"></a>WebHttpBinding

WebHttpBinding （也稱為 WCF REST），具有 `WebGet` 和 `WebInvoke` 屬性，可讓您開發 RESTful Api，以在這種情況較不常見時，一次就說出 JSON。 如果您有以 WCF REST 建立的 RESTful API，請考慮將它遷移至一般 ASP.NET Core MVC Web API 應用程式。 這項遷移會提供與 gRPC 的轉換相同的功能。

>[!div class="step-by-step"]
>[上一頁](wcf-endpoints-grpc-methods.md)
>[下一頁](rpc-types.md)
