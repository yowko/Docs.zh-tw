---
title: Protobuf 訊息-WCF 開發人員的 gRPC
description: '瞭解如何在 IDL 中定義 Protobuf 訊息，以及如何在 c # 中產生。'
ms.date: 12/15/2020
ms.openlocfilehash: c1f2a3071d45dcbe4b98d747f19fed508bad102f
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938100"
---
# <a name="protobuf-messages"></a>Protobuf 訊息

本節說明如何在檔案中 (Protobuf) 訊息來宣告通訊協定緩衝區 `.proto` 。 它會說明欄位編號和類型的基本概念，並查看編譯器產生的 c # 程式碼 `protoc` 。

本章的其餘部分將詳細說明不同類型的資料在 Protobuf 中的呈現方式。

## <a name="declaring-a-message"></a>宣告訊息

在 Windows Communication Foundation (WCF) 中， `Stock` 可定義股票市場交易應用程式的類別，如下列範例所示：

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

若要在 Protobuf 中執行對等的類別，您必須在檔案中宣告它 `.proto` 。 `protoc`編譯器接著會產生 .net 類別做為組建程式的一部分。

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

第一行宣告所使用的語法版本。 第3版的語言已于2016發行。 這是我們建議用來 gRPC 服務的版本。

這 `option csharp_namespace` 一行指定要用於產生之 c # 類型的命名空間。 針對其他語言編譯檔案時，將會忽略此選項 `.proto` 。 Protobuf 檔案通常包含數種語言的特定語言選項。

`Stock`訊息定義會指定四個欄位。 每個都有類型、名稱和欄位編號。

## <a name="field-numbers"></a>欄位編號

欄位號碼是 Protobuf 很重要的一部分。 它們是用來識別二進位編碼資料中的欄位，這表示它們無法從版本變更為您的服務版本。 優點是可以回溯相容性和向前相容性。 用戶端和服務會忽略他們不知道的欄位編號，只要處理遺漏值的可能性即可。

在二進位格式中，欄位編號會與類型識別碼合併。 從1到15的欄位編號可以用其類型作為單一位元組進行編碼。 從16到2047的數位需要2個位元組。 如果您基於任何原因需要在訊息上超過2047個欄位，您可以更高的版本。 欄位編號1到15的單一位元組識別碼可提供較佳的效能，因此您應該將它們用於最基本、常用的欄位。

## <a name="types"></a>類型

型別宣告使用 Protobuf 的原生純量資料類型，在 [下一節](protobuf-data-types.md)中會更詳細地討論。 本章的其餘部分將涵蓋 Protobuf 的內建類型，並顯示它們與常見 .NET 類型的關聯性。

> [!NOTE]
> Protobuf 原本不支援 `decimal` 型別，因此 `double` 改用。 對於需要完整十進位精確度的應用程式，請參閱本章節下一節中的 [小數區段](protobuf-data-types.md#decimals) 。

## <a name="the-generated-code"></a>產生的程式碼

當您建立應用程式時，Protobuf 會為每個訊息建立類別，並將其原生類型對應至 c # 類型。 產生的 `Stock` 類型會有下列簽章：

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

產生的實際程式碼遠比這個更複雜許多。 原因是每個類別都包含序列化和還原序列化為二進位電傳格式所需的所有程式碼。

### <a name="property-names"></a>屬性名稱

請注意，Protobuf 編譯器會套用 `PascalCase` 至屬性名稱，但它們是 `snake_case` 在檔案中 `.proto` 。 [Protobuf 樣式指南](https://developers.google.com/protocol-buffers/docs/style)建議 `snake_case` 在您的訊息定義中使用，讓其他平臺的程式碼產生產生其慣例的預期大小寫。

>[!div class="step-by-step"]
>[上一個](protocol-buffers.md) 
>[下一步](protobuf-data-types.md)
