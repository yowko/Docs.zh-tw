---
title: Protobuf 適用于 variant 類型的 Any 和一個欄位-WCF 開發人員的 gRPC
description: 瞭解如何使用 Any 型別和一個關鍵字來代表訊息中的 variant 物件類型。
ms.date: 09/09/2019
ms.openlocfilehash: af3ba22c238aa80a8c6119f62d5d8914770cad68
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971609"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Protobuf variant 類型的 Any 和一個欄位

在 WCF 中處理動態屬性類型（也就是類型 `object`的屬性）很複雜。 必須指定序列化程式，必須提供[KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute)屬性，依此類推。

Protobuf 提供兩個較簡單的選項，可處理可能屬於一種以上類型的值。 `Any` 類型可以代表任何已知的 Protobuf 訊息類型，而 `oneof` 關鍵字可讓您指定在任何指定的訊息中只能設定一個範圍的欄位。

## <a name="any"></a>任何

`Any` 是 Protobuf 的「知名型別」之一，這是一組有用、可重複使用的訊息型別，並以所有支援的語言執行。 若要使用 `Any` 類型，您必須匯入 `google/protobuf/any.proto` 定義。

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

在程式C#代碼中，`Any` 類別提供了設定欄位、將訊息解壓縮，以及檢查類型的方法。

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

Protobuf 的內部反映程式碼會使用每個產生之類型上的 `Descriptor` 靜態欄位，來解析 `Any` 欄位類型。 另外還有 `TryUnpack<T>` 方法，但即使失敗，也會建立未初始化的 `T` 實例，因此最好使用如上所示的 `Is` 方法。

## <a name="oneof"></a>一個

一個欄位是一種語言功能：編譯器在產生 message 類別時，會處理 `oneof` 關鍵字。 使用 `oneof` 來指定 `ChangeNotification` 訊息可能如下所示：

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

`oneof` 集內的欄位在整體訊息宣告中必須有唯一的欄位編號。

當您使用 `oneof`時，產生C#的程式碼會包含列舉，以指定已設定的欄位。 您可以測試列舉以尋找已設定的欄位。 未設定的欄位會傳回 `null` 或預設值，而不是擲回例外狀況。

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

設定屬於 `oneof` 集之一部分的任何欄位，將會自動清除該集合中的任何其他欄位。 您無法搭配 `oneof`使用 `repeated`。 相反地，您可以建立具有重複欄位或 `oneof` 設定的嵌套訊息，以解決這項限制。

>[!div class="step-by-step"]
>[上一頁](protobuf-reserved.md)
>[下一頁](protobuf-enums.md)
