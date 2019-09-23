---
title: 通訊協定緩衝區-WCF 開發人員的 gRPC
description: 適用于 gRPC 網路的通訊協定緩衝區線路格式簡介。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 4f9031c86731ea7ded4a812be9967237e52c4b39
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184166"
---
# <a name="protocol-buffers"></a>通訊協定緩衝區

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

gRPC services 會以*通訊協定緩衝區（Protobuf）訊息*的方式傳送和接收資料，類似于 WCF 的資料合約。 Protobuf 是一種有效率的方式，可將結構化資料序列化以進行讀取和寫入，而不會造成 XML 或 JSON 之類的人類看得懂的格式產生額外的負擔。

本章涵蓋 Protobuf 的運作方式，以及如何定義您自己的 Protobuf 訊息。

## <a name="how-protobuf-works"></a>Protobuf 的運作方式

大部分的 .NET 物件序列化技術（包括 WCF 的資料合約）都是在執行時間使用反映來分析物件結構而運作。 相較`.proto`之下，大部分的 Protobuf 程式庫都需要您在檔案中使用專用語言（*通訊協定緩衝區語言*）來預先定義結構。 然後編譯器會使用這個檔案，為任何支援的平臺（包括 .NET、JAVA、C/C++、JavaScript 等等）產生程式碼。 Protobuf 編譯器（ `protoc`）是由 Google 維護，但有替代的執行方式可供使用。 產生的程式碼會有效率，並針對資料的快速序列化和還原序列化進行優化。

Protobuf 電傳格式本身是二進位編碼，其使用一些聰明的技巧，將用來表示訊息的位元組數目降至最低。 使用 Protobuf 並不需要瞭解二進位編碼格式，但如果您有興趣，可以在[通訊協定緩衝區網站](https://developers.google.com/protocol-buffers/docs/encoding)上深入瞭解。

>[!div class="step-by-step"]
>[上一頁](why-grpc.md)
>[下一頁](protobuf-messages.md)
