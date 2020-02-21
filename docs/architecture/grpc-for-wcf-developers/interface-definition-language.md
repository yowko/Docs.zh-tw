---
title: 介面定義語言-適用于 WCF 開發人員的 gRPC
description: 介紹通訊協定緩衝區 IDL。
ms.date: 09/02/2019
ms.openlocfilehash: 841f041ae350e76e648c71f9d6d113b9d39e0d3b
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543205"
---
# <a name="interface-definition-language"></a>介面定義語言

使用 Windows Communication Foundation （WCF），服務可以使用 Web 服務定義語言（WSDL）公開描述中繼資料。 WSDL 是在執行時間使用 .NET 反映動態產生的。 開發人員可以使用此中繼資料來產生這些服務的用戶端，如果它們使用的是平臺中立的系結，例如 SOAP over HTTP，則可能是其他語言。

gRPC 會使用來自通訊協定緩衝區的介面定義語言（IDL）。 通訊協定緩衝區 IDL 是一種自訂的平臺中立語言，具有開放式規格。 開發人員會撰寫 `.proto` 檔案，以描述服務及其輸入和輸出。 這些 `.proto` 的檔案可以用來為用戶端和伺服器產生語言或平臺特定的存根，讓多個不同的平臺能夠進行通訊。 藉由共用 `.proto` 檔案，小組可以產生程式碼，以使用每個其他服務，而不需要採取程式碼相依性。

Protobuf IDL 的其中一個優點是，身為自訂語言，它可讓 gRPC 完全不受語言和平臺限制，而不是優先列出其他技術。

Protobuf IDL 也是專為讀取和寫入而設計，而 WSDL 則是做為電腦可讀取/可寫入的格式。 變更 WCF 服務的 WSDL 通常需要變更服務、執行服務，以及從伺服器重新產生 WSDL 檔案。 相較之下，使用 `.proto` 檔案時，變更很容易與文字編輯器一起套用，而且會自動流經產生的程式碼。 Visual Studio 2019 會在儲存檔案時，于背景建立 `.proto` 檔案。 使用其他編輯器（例如 VS Code）時，會在建立專案時套用變更。

相較于 XML，特別是 SOAP，使用 Protobuf 編碼的訊息有許多優點。 Protobuf 訊息通常會小於序列化為 SOAP XML 的相同資料，而且透過網路進行編碼、解碼和傳輸可能會更快。

相較于 SOAP，Protobuf 的可能缺點是，因為人類無法讀取訊息，所以需要額外的工具才能進行訊息內容的偵錯工具。

> [!TIP]
> gRPC*確實*支援伺服器反映，以在沒有預先編譯的存根的情況下動態存取服務，但它比應用程式特定的用戶端更適用于一般用途的工具。 如需詳細資訊，請參閱 GitHub 上的[GRPC 伺服器反映通訊協定](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md)。

> [!NOTE]
> 與 NetTCP 系結搭配使用的 WCF 二進位格式，遠接近 Protobuf 的簡潔性和效能方面。 但是 NetTCP 只能在 .NET 用戶端和伺服器之間使用，而 Protobuf 則是跨平臺的解決方案。

>[!div class="step-by-step"]
>[上一頁](approach.md)
>[下一頁](network-protocols.md)
