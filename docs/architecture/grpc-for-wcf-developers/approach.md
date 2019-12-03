---
title: GRPC 如何為 WCF 開發人員提供 RPC gRPC 的方法
description: 比較 WCF 與 gRPC 的主要功能。
ms.date: 09/02/2019
ms.openlocfilehash: b924d2f20b54de2d6476a0b27626d5dd7fd0986f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711484"
---
# <a name="how-grpc-approaches-rpc"></a>gRPC 如何處理 RPC

Windows Communication Foundation （WCF）和 gRPC 都是*遠端程序呼叫*（RPC）模式的兩種執行方式。 此模式的目的是要呼叫在不同電腦上執行的服務，或在不同的進程中順暢地工作，例如用戶端應用程式中的方法呼叫。 雖然 WCF 和 gRPC 的目標都相同，但執行的詳細資料也很不同。

下表將說明 WCF 的主要功能與 gRPC 的關聯性，以及您可以在哪裡找到更詳細的解釋。

| 功能 | WCF | gRPC |
| -------- | --- | ---- |
| 目標 | 將商務程式碼與網路功能分開。 | 將商務程式碼與介面定義和網路功能執行分開。 |
| 定義服務和訊息（章節3-4）  | 服務合約、作業合約和資料合約。 | 使用 proto 檔案來宣告服務和訊息。 |
| 語言（章節3-5） | 在或 Visual Basic C#中撰寫的合約。 | 通訊協定緩衝區語言。 |
| 電傳格式（第3章） | 可設定，包括 SOAP/XML、純 XML、JSON 和 .NET 二進位檔。 | 通訊協定緩衝區二進位格式（雖然可以使用其他格式）。
| 互通性（第4章） | 使用 SOAP over HTTP 時。 | 正式支援： .NET、JAVA、Python、JavaScript、C/C++、Go、Rust、Ruby、Swift、DART、PHP。 來自社區的其他語言非官方支援。 |
| 網路功能（第4章） | 在執行時間設定。 在 NetTCP、HTTP 和 MSMQ 之間切換。 | HTTP/2，目前只有 TCP 與 ASP.NET Core gRPC。 |
| 方法（第4章） | 在基類中產生序列化、還原序列化和網路程式碼的執行時間。 | 在基類中產生序列化、還原序列化和網路程式碼的組建階段。 |
| 安全性（第6章） | 驗證、安全性、訊息加密。 | 認證、ASP.NET Core 安全性、TLS 網路功能。 |

>[!div class="step-by-step"]
>[上一頁](grpc-overview.md)
>[下一頁](interface-definition-language.md)
