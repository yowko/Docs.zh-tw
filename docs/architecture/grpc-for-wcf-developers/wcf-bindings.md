---
title: WCF 系結和傳輸-WCF 開發人員的 gRPC
description: 瞭解不同的 WCF 系結和傳輸與 gRPC 之間的比較。
ms.date: 09/02/2019
ms.openlocfilehash: 233e3d030bc1f4450bd5cd6a7d7770486ca9e95a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966909"
---
# <a name="wcf-bindings-and-transports"></a>WCF 繫結和傳輸

WCF 有許多不同的內建系結 *，這些系*結會指定不同的網路通訊協定、電傳格式和其他的執行詳細資料。 gRPC 實際上只有一個網路通訊協定和一個電傳格式（技術上來說，*可以*自訂電傳格式，但這不在本書的討論範圍內）。 在大部分情況下，您可能會發現 gRPC 提供最佳的解決方案。 接下來是關於最相關的 WCF 系結，以及它們如何與 gRPC 中的對等項進行比較的簡短討論。

## <a name="nettcp"></a>NetTCP

WCF 的 NetTCP 系結允許持續連接、小型訊息和雙向訊息，但只能在 .NET 用戶端和伺服器之間運作。 gRPC 允許相同的功能，但在多個程式設計語言和平臺上都支援。 gRPC 有許多 WCF NetTCP 系結的功能，但不一定會以相同的方式來執行。 例如，在 WCF 中，加密是透過設定來控制，並在架構中處理。 在 gRPC 中，加密是在透過 TLS 使用 HTTP/2 的連線層級達成。

## <a name="http"></a>HTTP

WCF 的 BasicHttpBinding 通常是以文字為基礎，使用 SOAP 做為電傳格式，而相較于 NetTCP 系結，它會變慢。 它通常用來提供跨平臺互通性，或透過網際網路基礎結構的連線。 GRPC 中的對等專案，因為它使用 HTTP/2 做為適用于訊息之 binary Protobuf 電傳格式的基礎傳輸層—可提供 NetTCP 服務層級效能，但具備所有新式程式設計語言的完整跨平臺互通性和集成.

## <a name="named-pipes"></a>具名管道

WCF 提供了具名管道系結，以便在相同實體電腦上的進程之間進行通訊。 ASP.NET Core gRPC 的第一版不支援具名管道。 新增具名管道（和 Unix 網域通訊端）的用戶端和伺服器支援是未來版本的目標。

## <a name="msmq"></a>MSMQ

MSMQ 是專屬的 Windows 訊息佇列。 WCF 對 MSMQ 的系結可讓您從用戶端「引發並忘記」要求，未來可能會進行處理。 gRPC 原本不提供任何訊息佇列功能。 最佳的替代方法是直接使用訊息系統，例如 Azure 服務匯流排、RabbitMQ 或 Kafka。 這可以透過用戶端直接將訊息放在佇列上，或 gRPC 用戶端串流服務來將訊息來執行。

## <a name="webhttpbinding"></a>WebHttpBinding

WebHttpBinding （也稱為「WCF ReST」）具有 `WebGet` 和 `WebInvoke` 屬性，可讓您開發 ReSTful Api，而這在這種情況下並不常見，可能會一次就說出 JSON。 因此，如果您有以 WCF REST 建立的 RESTful API，請考慮將它遷移至一般 ASP.NET Core MVC Web API 應用程式，這會提供對等的功能，而不是轉換成 gRPC。

>[!div class="step-by-step"]
>[上一頁](wcf-endpoints-grpc-methods.md)
>[下一頁](rpc-types.md)
