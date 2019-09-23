---
title: 介面定義語言-適用于 WCF 開發人員的 gRPC
description: 介紹通訊協定緩衝區 IDL。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 71bdf8bf488e0a5bed177817343051bcd7847d25
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184425"
---
# <a name="interface-definition-language"></a>介面定義語言

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

使用 WCF 時，服務可以使用 Web 服務定義語言（WSDL）公開描述中繼資料，這是在執行時間使用 .NET 反映動態產生的。 開發人員可以使用此中繼資料來產生這些服務的用戶端，如果使用以平臺中立的系結（例如 SOAP over HTTP），則可能是其他語言。

gRPC 會使用來自通訊協定緩衝區的介面定義語言（IDL）。 通訊協定緩衝區 IDL 是一種自訂的平臺中立語言，具有開放式規格。 開發人員會撰寫`.proto`程式碼檔案，以描述服務及其輸入和輸出。 然後`.proto` ，這些檔案可以用來為用戶端和伺服器產生語言或平臺特定的存根，讓多個不同的平臺能夠進行通訊。 藉由`.proto`共用檔案，小組可以產生程式碼以使用彼此的服務，而不需要採取程式碼相依性。

Protobuf IDL 的其中一個優點是，身為自訂語言，其可讓 gRPC 完全不受語言和平臺限制，而不是優先列出其他技術。

Protobuf IDL 也是專為讀取和寫入而設計，而 WSDL 則是做為電腦可讀取/可寫入的格式。 變更 WCF 服務的 WSDL 通常需要對服務程式代碼本身進行變更、執行服務，以及從伺服器重新產生 WSDL 檔案。 相較之下，使用`.proto`檔案時，您可以輕鬆地使用文字編輯器來套用變更，並自動流經產生的程式碼。 Visual Studio 2019 會`.proto`在儲存檔案時于背景建立檔案; 使用其他編輯器（例如 VS Code）時，將會在建立專案時套用變更。

相較于 XML，特別是 SOAP，使用 Protobuf 編碼的訊息有許多優點。 Protobuf 訊息通常會小於序列化為 SOAP XML 的相同資料，而透過網路進行編碼、解碼和傳輸可能會更快。

相較于 SOAP，Protobuf 的可能缺點是，由於訊息不是人類可讀的，因此需要額外的工具來進行訊息內容的偵錯工具。

> [!TIP]
> gRPC*不*支援伺服器反映來動態存取服務，而不需要預先編譯的存根，雖然它比應用程式特定的用戶端更適用于一般用途的工具。 如需 gRPC 伺服器反映的詳細資訊，請參閱 GitHub 上的[gRPC/gRPC](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md)儲存機制。

> [!NOTE]
> 與 NetTCP 系結搭配使用的 WCF 二進位格式，比簡潔性和效能更接近 Protobuf，但是 NetTCP 只能在 .NET 用戶端和伺服器之間使用，而 Protobuf 則是跨平臺的解決方案。

>[!div class="step-by-step"]
>[上一頁](approach.md)
>[下一頁](network-protocols.md)
