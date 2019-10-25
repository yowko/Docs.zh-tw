---
title: Protobuf 訊息-WCF 開發人員的 gRPC
description: 瞭解 Protobuf 訊息如何定義于 IDL 中，以及如何在C#中產生。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 9943478698acfbb54b3e1dd0e6a856d11b9266c3
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846341"
---
# <a name="protobuf-messages"></a>Protobuf 訊息

本節說明如何在 `.proto` 檔案中宣告 Protobuf 訊息、解釋欄位編號和類型的基本概念，並查看 `protoc` 編譯器所產生C#的程式碼。 本章的其餘部分將詳細說明 Protobuf 中不同類型資料的呈現方式。

## <a name="declaring-a-message"></a>宣告訊息

在 WCF 中，股票市場貿易應用程式的 `Stock` 類別，可能會如下列範例所示定義：

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

若要在 Protobuf 中執行對等的類別，它必須在 `.proto` 檔案中宣告。 然後 `protoc` 編譯器會在組建程式中產生 .NET 類別。

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

第一行會宣告所使用的語法版本。 第3版語言已于2016發行，而且是建議的 gRPC 服務版本。

`option csharp_namespace` 行指定要用於產生C#之類型的命名空間。 針對其他語言編譯 `.proto` 檔案時，將會忽略此選項。 Protobuf 檔案通常會包含數種語言的語言特定選項。

`Stock` 訊息定義會指定四個欄位，每一個都有一個類型、一個名稱和一個欄位編號。

## <a name="field-numbers"></a>欄位編號

欄位編號是 Protobuf 中很重要的一部分。 它們是用來識別二進位編碼資料中的欄位，這表示它們無法從版本變更為您的服務版本。 優點是可以進行回溯和回溯相容性。 只要處理遺漏值的可能性，用戶端和服務就會直接忽略他們不知道的欄位編號。

在二進位格式中，欄位編號會與類型識別碼結合。 從1到15的欄位可以用其類型編碼為單一位元組;從16到2047的數位需要2個位元組。 如果因任何原因而需要訊息超過2047個欄位，您就可以更高。 欄位編號1到15的單一位元組識別碼提供較佳的效能，因此您應該將它們用於最基本、常用的欄位。

## <a name="types"></a>型別

類型宣告使用 Protobuf 的原生純量資料類型，將在[下一節](protobuf-data-types.md)中更詳細地討論。 本章的其餘部分將涵蓋 Protobuf 的內建型別，並說明它們與常見 .NET 類型的關聯性。

> [!NOTE]
> Protobuf 原本就不支援 `decimal` 類型，因此會改用 double。 對於需要完整十進位數精確度的應用程式，請參閱本章下一節中的[小數章節](protobuf-data-types.md#decimals)。

## <a name="the-generated-code"></a>產生的程式碼

當您建立應用程式時，Protobuf 會為您的每個訊息建立類別，並將C#其原生類型對應至類型。 產生的 `Stock` 類型會具有下列簽章：

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

所產生的實際程式碼遠比這個更為複雜，因為每個類別都包含將本身序列化和還原序列化為二進位電傳格式所需的所有程式碼。

### <a name="property-names"></a>屬性名稱

請注意，Protobuf 編譯器 `PascalCase` 套用至屬性名稱，雖然它們 `snake_case` 在 `.proto` 檔案中。 [Protobuf 樣式指南](https://developers.google.com/protocol-buffers/docs/style)會建議在您的訊息定義中使用 `snake_case`，讓其他平臺的程式碼產生會針對其慣例產生預期的大小寫。

>[!div class="step-by-step"]
>[上一頁](protocol-buffers.md)
>[下一頁](protobuf-data-types.md)
