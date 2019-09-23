---
title: Protobuf 適用于 variant 類型的 Any 和一個欄位-WCF 開發人員的 gRPC
description: 瞭解如何使用 Any 型別和一個關鍵字來代表訊息中的 variant 物件類型。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 9e730e96bfdb25ef6e07ee10967921408c6f2e84
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184278"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Protobuf variant 類型的 Any 和一個欄位

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在 WCF 中處理動態屬性類型（也就是`object`類型的屬性）很複雜。 必須指定序列化程式，必須提供[KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute)屬性，依此類推。

Protobuf 提供兩個較簡單的選項，可處理可能屬於一種以上類型的值。 型別可以代表任何已知的 Protobuf 訊息型別， `oneof`而關鍵字可讓您指定在任何指定的訊息中只能設定一個欄位範圍的其中一個。 `Any`

## <a name="any"></a>Any

`Any`是 Protobuf 的「知名型別」之一，這是一組有用、可重複使用的訊息型別，並以所有支援的語言執行。 若要使用`Any`類型，您必須匯`google/protobuf/any.proto`入定義。

```protobuf
syntax "proto3"

import "google/protobuf/any.proto"

message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
    int32 id = 1;
    google.protobuf.Any instrument = 2;
}
```

在程式C#代碼中， `Any`類別會提供方法來設定欄位、將訊息解壓縮，以及檢查類型。

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    if (change.Instrument.Is(Stock.Descriptor))
    {
        FormatStock(change.Instrument.Unpack<Stock>());
    }
    else if (change.Instrument.Is(Currency.Descriptor))
    {
        FormatCurrency(change.Instrument.Unpack<Currency>());
    }
    else
    {
        throw new ArgumentException("Unknown instrument type");
    }
}
```

Protobuf `Descriptor`的內部反映程式碼會使用每個產生之類型上的靜態欄位`Any`來解析欄位類型。 另外還有`TryUnpack<T>`方法，但即使失敗，也會建立未初始化`T`的實例，因此最好使用`Is`方法，如上所示。

## <a name="oneof"></a>一個

一個欄位是一種語言功能： `oneof`編譯器會在產生 message 類別時處理關鍵字。 使用`oneof` 來`ChangeNotification`指定訊息可能如下所示：

```protobuf
message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
  int32 id = 1;
  oneof instrument {
    Stock stock = 2;
    Currency currency = 3;
  }
}
```

`oneof`集合內的欄位在整體訊息宣告中必須有唯一的欄位編號。

當您使用`oneof`時，產生C#的程式碼會包含列舉，以指定已設定的欄位。 您可以測試列舉以尋找已設定的欄位。 未設定的欄位會`null`傳回或預設值，而不會擲回例外狀況。

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    switch (change.InstrumentCase)
    {
        case ChangeNotification.InstrumentOneofCase.None:
            return;
        case ChangeNotification.InstrumentOneofCase.Stock:
            FormatStock(change.Stock);
            break;
        case ChangeNotification.InstrumentOneofCase.Currency:
            FormatCurrency(change.Currency);
            break;
        default:
            throw new ArgumentException("Unknown instrument type");
    }
}
```

設定屬於`oneof`集合之一部分的任何欄位，將會自動清除該集合中的任何其他欄位。 您無法搭配`repeated`使用`oneof`。 相反地，您可以建立具有重複欄位或`oneof`集合的嵌套訊息，以解決這項限制。

>[!div class="step-by-step"]
>[上一頁](protobuf-reserved.md)
>[下一頁](protobuf-enums.md)
