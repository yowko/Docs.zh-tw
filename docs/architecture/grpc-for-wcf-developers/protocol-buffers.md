---
title: 協定緩衝區 - 適用于 WCF 開發人員的 gRPC
description: 用於 gRPC 網路的協定緩衝區線格式簡介。
ms.date: 09/09/2019
ms.openlocfilehash: 35319d299a8bc2866a87954b3e54bfda9314ffe8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147928"
---
# <a name="protocol-buffers"></a>協定緩衝區

gRPC 服務以*協定緩衝區 （Protobuf） 消息*發送和接收資料，類似于 Windows 通信基礎 （WCF） 中的資料協定。 Protobuf 是一種用於電腦讀取和寫入的結構化資料序列化的有效方法，無需產生 XML 或 JSON 等人類可讀格式的開銷。

本章介紹 Protobuf 的工作原理，以及如何定義您自己的 Protobuf 消息。

## <a name="how-protobuf-works"></a>普羅托布夫的工作原理

大多數 .NET 物件序列化技術（包括 WCF 的資料協定）都使用反射來分析運行時的物件結構。 相比之下，大多數 Protobuf 庫要求您在`.proto`檔中使用專用語言（*協定緩衝區語言*）來預先定義結構。 然後，編譯器使用此檔為任何受支援的平臺生成代碼。 支援的平臺包括 .NET、JAVA、C/C++、JavaScript 等。

Protobuf 編譯器`protoc`（） 由 Google 維護，儘管有替代實現可用。 生成的代碼高效且優化，可快速序列化和資料反序列化。

Protobuf 線格式是二進位編碼。 它使用一些巧妙的技巧來最小化用於表示消息的位元組數。 使用 Protobuf 不需要瞭解二進位編碼格式。 但是，如果你有興趣，你可以瞭解更多關於它[的協定緩衝區網站](https://developers.google.com/protocol-buffers/docs/encoding)。

>[!div class="step-by-step"]
>[上一個](why-grpc.md)
>[下一個](protobuf-messages.md)
