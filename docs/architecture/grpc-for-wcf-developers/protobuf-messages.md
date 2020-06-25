---
title: Protobuf 訊息-WCF 開發人員的 gRPC
description: '瞭解如何在 IDL 中定義 Protobuf 訊息，並在 c # 中產生。'
ms.date: 09/09/2019
ms.openlocfilehash: 6fc7b9c34810abaa8d674af56d1517a5cf87521b
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325035"
---
# <a name="protobuf-messages"></a>Protobuf 訊息

本節涵蓋如何在檔案中宣告通訊協定緩衝區（Protobuf）訊息 `.proto` 。 它會說明欄位編號和類型的基本概念，並查看編譯器所產生的 c # 程式碼 `protoc` 。

本章的其餘部分將詳細說明 Protobuf 中不同類型資料的呈現方式。

## <a name="declaring-a-message"></a>宣告訊息

在 Windows Communication Foundation （WCF）中， `Stock` 股票市場交易應用程式的類別可能會如下列範例所定義：

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

若要在 Protobuf 中執行對等的類別，您必須在檔案中宣告它 `.proto` 。 `protoc`然後編譯器會在組建程式中產生 .net 類別。

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

第一行會宣告所使用的語法版本。 語言的第3版已于2016發行。 這是我們建議的 gRPC 服務版本。

這 `option csharp_namespace` 一行指定產生的 c # 型別所要使用的命名空間。 針對其他語言編譯檔案時，將會忽略此選項 `.proto` 。 Protobuf 檔案通常包含數種語言的語言特定選項。

`Stock`訊息定義會指定四個欄位。 每個都有類型、名稱和欄位編號。

## <a name="field-numbers"></a>欄位編號

欄位編號是 Protobuf 中很重要的一部分。 它們是用來識別二進位編碼資料中的欄位，這表示它們無法從版本變更為您的服務版本。 優點是可以回溯相容性和向前相容性。 用戶端和服務只會略過不知道的欄位編號，只要處理遺漏值的可能性即可。

在二進位格式中，欄位編號會與類型識別碼結合。 從1到15的欄位可以用其類型編碼為單一位元組。 從16到2047的數位需要2個位元組。 如果因任何原因而需要訊息超過2047個欄位，您就可以更高。 欄位編號1到15的單一位元組識別碼提供較佳的效能，因此您應該將它們用於最基本、常用的欄位。

## <a name="types"></a>類型

類型宣告使用 Protobuf 的原生純量資料類型，將在[下一節](protobuf-data-types.md)中更詳細地討論。 本章的其餘部分將涵蓋 Protobuf 的內建型別，並說明它們與常見 .NET 類型的關聯性。

> [!NOTE]
> Protobuf 原本就不支援 `decimal` 型別，因此 `double` 會改用。 對於需要完整十進位數精確度的應用程式，請參閱本章下一節中的[小數章節](protobuf-data-types.md#decimals)。

## <a name="the-generated-code"></a>產生的程式碼

當您建立應用程式時，Protobuf 會為您的每個訊息建立類別，並將其原生類型對應至 c # 類型。 產生的 `Stock` 類型會具有下列簽章：

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

產生的實際程式碼遠比這個複雜。 原因是每個類別都包含將本身序列化和還原序列化為二進位電傳格式所需的所有程式碼。

### <a name="property-names"></a>屬性名稱

請注意，Protobuf 編譯器會套用 `PascalCase` 至屬性名稱，但它們是 `snake_case` 在檔案中 `.proto` 。 [Protobuf 樣式指南](https://developers.google.com/protocol-buffers/docs/style)建議 `snake_case` 在您的訊息定義中使用，讓其他平臺的程式碼產生會針對其慣例產生預期的大小寫。

>[!div class="step-by-step"]
>[上一個](protocol-buffers.md) 
>[下一步](protobuf-data-types.md)
