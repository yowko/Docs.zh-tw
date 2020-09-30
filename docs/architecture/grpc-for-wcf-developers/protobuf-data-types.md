---
title: Protobuf 純量資料類型-適用于 WCF 開發人員的 gRPC
description: 瞭解 .NET Core 中 Protobuf 和 gRPC 支援的基本和知名資料類型。
ms.date: 09/09/2019
ms.openlocfilehash: 5447067b953d257258950d020636e0b38245e20d
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91573640"
---
# <a name="protobuf-scalar-data-types"></a>Protobuf 純量資料類型

通訊協定緩衝區 (Protobuf) 支援一系列原生純量實數值型別。 下表列出它們都具有對等的 c # 型別：

| Protobuf 類型 | C# 類型      | 注意 |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | 1     |
| `int64`       | `long`       | 1     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | 1     |
| `sint64`      | `long`       | 1     |
| `fixed32`     | `uint`       | 2     |
| `fixed64`     | `ulong`      | 2     |
| `sfixed32`    | `int`        | 2     |
| `sfixed64`    | `long`       | 2     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | 3     |
| `bytes`       | `ByteString` | 4     |

注意：

1. `int32` `int64` 當您使用帶正負號的值時，的標準編碼和效率不佳。 如果您的欄位可能包含負數，請改用 `sint32` 或 `sint64` 。 這些類型會分別對應至 c # `int` 和 `long` 類型。
2. `fixed`無論值為何，欄位一律會使用相同數目的位元組。 此行為可讓較大的值更快進行序列化和還原序列化。
3. Protobuf 字串為 UTF-8 (或7位 ASCII) 編碼。 編碼的長度不能大於 2<sup>32</sup>。
4. Protobuf 執行時間提供可 `ByteString` 輕鬆地與 c # 陣列進行對應的型別 `byte[]` 。

## <a name="other-net-primitive-types"></a>其他 .NET 基本類型

### <a name="dates-and-times"></a>日期和時間

原生純量類型不提供日期和時間值，相當於 c # 的 <xref:System.DateTimeOffset> 、 <xref:System.DateTime> 和 <xref:System.TimeSpan> 。 您可以使用某些 Google 的「已知類型」延伸模組來指定這些類型。 這些擴充功能可在支援的平臺上，為複雜的欄位類型提供程式碼產生與執行時間支援。

下表顯示日期和時間類型：

| C# 類型 | Protobuf 知名型別 |
| ------- | ------------------------ |
| `DateTimeOffset` | `google.protobuf.Timestamp` |
| `DateTime` | `google.protobuf.Timestamp` |
| `TimeSpan` | `google.protobuf.Duration` |

```protobuf  
syntax = "proto3"

import "google/protobuf/duration.proto";  
import "google/protobuf/timestamp.proto";

message Meeting {

    string subject = 1;
    google.protobuf.Timestamp time = 2;
    google.protobuf.Duration duration = 3;

}  
```

C # 類別中產生的屬性不是 .NET 日期和時間類型。 屬性使用 `Timestamp` `Duration` 命名空間中的和類別 `Google.Protobuf.WellKnownTypes` 。 這些類別提供在、和之間轉換的 `DateTimeOffset` 方法 `DateTime` `TimeSpan` 。

```csharp
// Create Timestamp and Duration from .NET DateTimeOffset and TimeSpan
var meeting = new Meeting
{
    Time = Timestamp.FromDateTimeOffset(meetingTime), // also FromDateTime()
    Duration = Duration.FromTimeSpan(meetingLength)
};

// Convert Timestamp and Duration to .NET DateTimeOffset and TimeSpan
DateTimeOffset time = meeting.Time.ToDateTimeOffset();
TimeSpan? duration = meeting.Duration?.ToTimeSpan();
```

> [!NOTE]
> 此 `Timestamp` 類型適用于 UTC 時間。 `DateTimeOffset` 值的位移一律為零，而且 `DateTime.Kind` 屬性一律為 `DateTimeKind.Utc` 。

### <a name="systemguid"></a>System.Guid

Protobuf 不直接支援 <xref:System.Guid> 型別，也就是 `UUID` 在其他平臺上的型別。 沒有知名的型別。

最好的方法是 `Guid` `string` 使用標準的十六進位 (格式來處理值做為欄位， `8-4-4-4-12` 例如 `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`) 。 所有語言和平臺都可以剖析該格式。

請勿使用 `bytes` 值的欄位 `Guid` 。 當 Protobuf 與其他平臺（例如 JAVA）進行互動時，會導致不穩定的行為，而 *位元組* ([維琪百科定義](https://en.wikipedia.org/wiki/Endianness)) 的問題。

### <a name="nullable-types"></a>可為 Null 的型別

C # 的 Protobuf 程式碼產生會使用原生類型，例如 `int` for `int32` 。 因此，一律會包含這些值，而且不能是 null。

對於需要明確 null 的值，例如 `int?` 在 c # 程式碼中使用，Protobuf 的「已知型別」會包含編譯成可為 null 的 c # 型別的包裝函式。 若要使用這些檔案，請將其匯入您的檔案 `wrappers.proto` `.proto` 中，如下所示：

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf 會使用簡單 `T?` (例如， `int?`) 產生的訊息屬性。

下表顯示包裝函式類型的完整清單及其對等的 c # 類型：

| C# 類型   | 知名的型別包裝函式       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

已知型別 `Timestamp` 和 `Duration` 在 .net 中是以類別表示。 在 c # 8 和之後，您可以使用可為 null 的參考型別。 但是，當您轉換成或時，請務必檢查這些類型的屬性是否有 `DateTimeOffset` null `TimeSpan` 。

## <a name="decimals"></a>小數位數

Protobuf 本身並不支援 .NET `decimal` 型別， `double` 而是和 `float` 。 Protobuf 專案中有一項持續的討論，當中有可能會將標準 `Decimal` 類型新增至已知型別，並提供支援的語言和架構平臺支援。 尚未執行任何動作。

您可以建立訊息定義，以代表 `decimal` .net 用戶端和伺服器之間安全序列化的型別。 但是，其他平臺上的開發人員必須瞭解所使用的格式，並對其執行自己的處理。

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>建立 Protobuf 的自訂十進位類型

簡單的執行可能類似于 `Money` 某些 Google api 所使用的非標準型別，而沒有 `currency` 欄位。

```protobuf
package CustomTypes;

// Example: 12345.6789 -> { units = 12345, nanos = 678900000 }
message DecimalValue {

    // Whole units part of the amount
    int64 units = 1;

    // Nano units of the amount (10^-9)
    // Must be same sign as units
    sfixed32 nanos = 2;
}
```

`nanos`欄位表示從到的 `0.999_999_999` 值 `-0.999_999_999` 。 例如，此 `decimal` 值會 `1.5m` 表示為 `{ units = 1, nanos = 500_000_000 }` 。 這就是為什麼 `nanos` 此範例中的欄位使用 `sfixed32` 型別，其編碼方式比 `int32` 較大的值更有效率。 如果 `units` 欄位是負數，則 `nanos` 欄位也應為負數。

> [!NOTE]
> 有多個其他演算法可將 `decimal` 值編碼為位元組字串，但這則訊息比任何這些演算法更容易瞭解。 在不同平臺上，值不會受到位元組順序影響。

此類型與 BCL 類型之間的轉換 `decimal` 可能會在 c # 中執行，如下所示：

```csharp
namespace CustomTypes
{
    public partial class DecimalValue
    {
        private const decimal NanoFactor = 1_000_000_000;
        public DecimalValue(long units, int nanos)
        {
            Units = units;
            Nanos = nanos;
        }

        public long Units { get; }
        public int Nanos { get; }

        public static implicit operator decimal(CustomTypes.DecimalValue grpcDecimal)
        {
            return grpcDecimal.Units + grpcDecimal.Nanos / NanoFactor;
        }

        public static implicit operator CustomTypes.DecimalValue(decimal value)
        {
            var units = decimal.ToInt64(value);
            var nanos = decimal.ToInt32((value - units) * NanoFactor);
            return new CustomTypes.DecimalValue(units, nanos);
        }
    }
}
```

> [!IMPORTANT]
> 每當您使用像這樣的自訂訊息類型時，就 *必須* 在中記錄批註 `.proto` 。 然後，其他開發人員就可以在自己的語言或架構中，以對等的型別來執行轉換。

>[!div class="step-by-step"]
>[上一個](protobuf-messages.md) 
>[下一步](protobuf-nested-types.md)
