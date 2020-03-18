---
title: 原型消息 - gRPC，面向 WCF 開發人員
description: 瞭解如何在 IDL 中定義 Protobuf 消息並在 C# 中生成。
ms.date: 09/09/2019
ms.openlocfilehash: 5b3d4383de39a3785ef804fec21939a740f54669
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147980"
---
# <a name="protobuf-messages"></a>Protobuf 訊息

本節介紹如何在`.proto`檔中聲明協定緩衝區（Protobuf）消息。 它解釋了欄位數和類型的基本概念，並查看`protoc`編譯器生成的 C# 代碼。

本章的其餘部分將更詳細地介紹在 Protobuf 中如何表示不同類型的資料。

## <a name="declaring-a-message"></a>聲明消息

在 Windows 通信基礎 （WCF） 中，股票市場交易應用程式的`Stock`類可以定義如下示例：

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

要在 Protobuf 中實現等效類，必須在`.proto`檔中聲明它。 然後`protoc`，編譯器將生成 .NET 類作為生成過程的一部分。

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

第一行聲明正在使用的語法版本。 該語言版本 3 于 2016 年發佈。 它是我們為 gRPC 服務推薦的版本。

該`option csharp_namespace`行指定要用於生成的 C# 類型的命名空間。 在為其他語言編譯檔時，`.proto`將忽略此選項。 Protobuf 檔通常包含多種語言的語言特定選項。

消息`Stock`定義指定四個欄位。 每個都有一個類型、一個名稱和一個欄位編號。

## <a name="field-numbers"></a>欄位編號

欄位編號是 Protobuf 的重要組成部分。 它們用於標識二進位編碼資料中的欄位，這意味著它們無法從服務的版本更改為版本。 優點是向後相容性和正向相容性是可能的。 只要處理丟失值的可能性，用戶端和服務將忽略他們不知道的欄位編號。

在二進位格式中，欄位編號與類型識別碼組合。 欄位編號從 1 到 15 可以編碼其類型為單個位元組。 從 16 到 2，047 的數位需要 2 個位元組。 如果出於任何原因需要郵件上的 2，047 個欄位，則可以走高。 欄位號 1 到 15 的單個位元組識別碼提供了更好的性能，因此應將它們用於最基本、最常用的欄位。

## <a name="types"></a>類型

型別宣告使用 Protobuf 的本機純量資料型別，[下一節](protobuf-data-types.md)將更詳細地討論這些類型。 本章的其餘部分將介紹 Protobuf 的內置類型，並展示它們與常見的 .NET 類型的關係。

> [!NOTE]
> Protobuf 不支援本機`decimal`類型，因此`double`使用。 對於需要全小數精度的應用程式，請參閱本章下一部分[中有關小數部分](protobuf-data-types.md#decimals)的部分。

## <a name="the-generated-code"></a>產生的程式碼

生成應用程式時，Protobuf 會為每個消息創建類，將其本機類型映射到 C# 類型。 生成的`Stock`類型將具有以下簽名：

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

生成的實際代碼要比這更複雜得多。 原因是每個類都包含序列化自身並將其反序列化為二進位線格式所需的所有代碼。

### <a name="property-names"></a>屬性名稱

請注意，Protobuf 編譯器應用於`PascalCase`屬性名稱，儘管它們位於`snake_case``.proto`檔中。 [Protobuf 樣式指南](https://developers.google.com/protocol-buffers/docs/style)建議`snake_case`在消息定義中使用，以便其他平臺的代碼生成生成其約定的預期情況。

>[!div class="step-by-step"]
>[上一個](protocol-buffers.md)
>[下一個](protobuf-data-types.md)
