---
title: GRPC 如何為 WCF 開發人員提供 RPC gRPC 的方法
description: 比較 WCF 與 gRPC 的主要功能。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 65d61c8246569d81dfec3aeb8e3df4bea26258dc
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184600"
---
# <a name="how-grpc-approaches-rpc"></a>GRPC 如何方法 RPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Windows Communication Foundation （WCF）和 gRPC 兩者都是*遠端程序呼叫*（RPC）模式的執行，它的目的是要呼叫在不同電腦上執行的服務，或是在不同的進程中，順暢地像是用戶端應用程式中的方法呼叫。 雖然 WCF 和 gRPC 的目標都相同，但執行的詳細資料也很不同。

下表將說明 WCF 的主要功能與 gRPC 的關聯性，以及您可以在本書其餘部分找到更詳細的解釋。

| 功能 | WCF | gRPC |
| -------- | --- | ---- |
| 目標 | 將商務程式碼與網路功能執行分開 | 將商務程式碼與介面定義和網路功能執行分開 |
| 定義服務和訊息（第3-4 章）  | 服務合約、作業合約和資料合約 | 使用 proto 檔案來宣告服務和訊息 |
| 語言（第3-5 章） | 在或 Visual Basic C#中撰寫的合約 | 通訊協定緩衝區語言 |
| 電傳格式（第3章） | 可設定，包括 SOAP/XML、純 XML、JSON、.NET 二進位檔等等。 | 通訊協定緩衝區二進位格式（雖然可以使用其他格式）。
| 互通性（第4章） | 使用 SOAP over HTTP 時 | 正式支援： .NET、JAVA、Python、JavaScript、C/C++、Go、Rust、Ruby、Swift、DART、PHP。 來自社區的其他語言非官方支援。 |
| 網路功能（第4章） | 在執行時間設定。 在 TCP、HTTP、MSMQ 等之間切換。 | 一律為 HTTP/2 |
| 方法（第4章） | 在基類中產生序列化/deserialization 和網路程式碼的執行時間 | 基底類別中的組建階段產生序列化/deserialization 和網路程式碼 |
| 安全性（第6章） | 驗證，WS-安全性，訊息加密 | 認證，ASP.NET Core 安全性，TLS 網路 |

>[!div class="step-by-step"]
>[上一頁](grpc-overview.md)
>[下一頁](interface-definition-language.md)
