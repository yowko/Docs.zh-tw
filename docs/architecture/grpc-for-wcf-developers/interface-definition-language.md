---
title: 適用于 WCF 開發人員的介面定義語言-gRPC
description: 介紹通訊協定緩衝區 IDL。
ms.date: 12/15/2020
ms.openlocfilehash: 60cedd9b7c29bf54165b15f512c0b2159cb5dda9
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938074"
---
# <a name="interface-definition-language"></a>介面定義語言

使用 WCF) 的 Windows Communication Foundation (，服務可以使用 Web 服務定義語言 (WSDL) 來公開描述中繼資料。 WSDL 是在執行時間使用 .NET 反映動態產生的。 開發人員可以使用此中繼資料來產生這些服務的用戶端，如果它們是使用平臺中立的系結（例如 SOAP over HTTP），可能會使用其他語言。

gRPC 使用介面定義語言 (從通訊協定緩衝區) 的 IDL。 通訊協定緩衝區的 IDL 是具有開啟規格的自訂、平臺中立語言。 開發人員會撰寫 `.proto` 用來描述服務的檔案，以及它們的輸入和輸出。 `.proto`然後，您可以使用這些檔案來產生用戶端和伺服器的語言或平臺特定的存根，讓多個不同的平臺進行通訊。 藉由共用檔案 `.proto` ，小組可以產生程式碼來使用彼此的服務，而不需要採取程式碼相依性。

Protobuf IDL 的優點之一，就是作為自訂語言，它可讓 gRPC 完全與語言和平臺無關，而不會 favoring 任何技術。

Protobuf IDL 也設計為方便人們進行讀取和寫入，而 WSDL 則是以機器可讀取/可寫入的格式表示。 變更 WCF 服務的 WSDL 通常需要變更服務、執行服務，以及重新產生伺服器的 WSDL 檔案。 相較之下，使用檔案時 `.proto` ，變更很容易與文字編輯器一起套用，並且會自動流經產生的程式碼。 Visual Studio 2019 在 `.proto` 儲存檔案時，會在背景中建立檔案。 使用其他編輯器（例如 VS Code）時，會在建立專案時套用變更。

相較于 XML （尤其是 SOAP），使用 Protobuf 編碼的訊息有許多優點。 Protobuf 訊息通常會小於序列化為 SOAP XML 的相同資料，並透過網路進行編碼、解碼和傳輸，可能會更快。

相較于 SOAP，Protobuf 的潛在缺點是，因為人類無法讀取訊息，所以需要其他工具來將訊息內容進行調試。

> [!TIP]
> gRPC *支援* 的伺服器反映可動態存取不含預先編譯存根的服務，不過它比應用程式特定的用戶端更適合一般用途工具。 如需詳細資訊，請參閱 GitHub 上的 [GRPC 伺服器反映通訊協定](https://github.com/grpc/grpc/blob/master/doc/server-reflection.md) 。

> [!NOTE]
> 與 NetTCP 系結搭配使用的 WCF 二進位格式，在壓縮度和效能方面更接近 Protobuf。 但是，NetTCP 只能在 .NET 用戶端和伺服器之間使用，而 Protobuf 則是跨平臺的解決方案。

>[!div class="step-by-step"]
>[上一個](approach.md) 
>[下一步](network-protocols.md)
