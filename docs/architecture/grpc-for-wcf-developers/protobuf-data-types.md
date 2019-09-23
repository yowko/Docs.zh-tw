---
title: Protobuf 純量資料類型-WCF 開發人員的 gRPC
description: 瞭解 .NET Core 中 Protobuf 和 gRPC 所支援的基本和已知資料類型。
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 8c8db795e927a44e9f75ec828336630ec9978eb6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184264"
---
# <a name="protobuf-scalar-data-types"></a>Protobuf 純量資料類型

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Protobuf 支援某個範圍的原生純量實數值型別。 下表列出所有其對等C#的類型：

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

## <a name="notes"></a>注意

1. 使用帶正負號`int32`的`int64`值時，和的標準編碼效率不佳。 如果您的欄位可能包含負數，請`sint32`改用或。 `sint64` 這兩種類型分別C# `int`對應`long`至和類型。
2. 不論值為何，欄位一律會使用相同數目的位元組。`fixed` 此行為可讓較大的值更快速地進行序列化和還原序列化。
3. Protobuf 字串是以 UTF-8 （或7位 ASCII）編碼，且編碼的長度不能大於 2<sup>32</sup>。
4. Protobuf 執行時間提供`ByteString`的類型，可輕鬆地與C# `byte[]`陣列進行對應。

## <a name="other-net-primitive-types"></a>其他 .NET 基本類型

### <a name="dates-and-times"></a>日期和時間

原生純量類型不提供日期和時間值，相當於C#的<xref:System.DateTimeOffset>、 <xref:System.DateTime>和<xref:System.TimeSpan>。 您可以使用 Google 的「知名型別」延伸模組來指定這些型別，這些擴充功能可跨支援的平臺，為更複雜的欄位類型提供程式碼產生和執行時間支援。 下表顯示日期和時間類型：

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

C#類別中產生的屬性不是 .net 日期和時間類型。 屬性`Timestamp`會使用`Google.Protobuf.WellKnownTypes`命名空間`Duration`中的和類別，以提供在、 `DateTime` `TimeSpan`和之間`DateTimeOffset`來回轉換的方法。

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
> `Timestamp`類型適用于 UTC 時間;值的位移一律為零， `DateTime.Kind`而屬性則一律為`DateTimeKind.Utc`。 `DateTimeOffset`

### <a name="systemguid"></a>System.Guid

類型（也`UUID`就是在其他平臺上）不會直接受到 Protobuf 的支援，而且沒有已知的類型。 <xref:System.Guid> 最好的方法是使用標準`Guid` `8-4-4-4-12`的十六進位`string`格式（ `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`例如），將值當做欄位來處理，這可由所有語言和平臺進行剖析。 請不要使用`bytes` `Guid`欄位做為值，因為當 endian 與其他平臺（例如 JAVA）互動時，可能會造成不穩定的行為。

### <a name="nullable-types"></a>可為 Null 的型別

產生的 Protobuf 程式C#代碼會使用原生類型， `int`例如適用于。 `int32` 這表示一定會包含這些值，而且不能是 null。 對於需要明確 null 的值，例如在您`int?`的程式C#代碼中使用，Protobuf 的「知名類型」包含編譯成可為 null C#類型的包裝函式。 若要使用它們， `wrappers.proto`請匯`.proto`入您的檔案，如下所示：

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf 會針對產生的`T?`訊息屬性使用簡單`int?`（例如）。

下表顯示包裝函式類型的完整清單及其對等C#類型：

| C# 類型   | 知名的型別包裝函式       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

已知`Timestamp`的型別和`Duration`在 .net 中是以類別表示，因此不需要可為 null 的版本，但在轉換為`DateTimeOffset`或`TimeSpan`時，請務必檢查這些類型的屬性是否為 null。

## <a name="decimals"></a>小

Protobuf 原本就不支援 .net `decimal`型別， `double`只有`float`和。 Protobuf 專案中有一項持續性的討論，說明如何將標準`Decimal`類型新增至已知類型，並提供支援的語言和架構平臺支援，但尚未實行任何功能。

您可以建立訊息定義來代表可在`decimal` .net 用戶端和伺服器之間安全序列化的類型，但是其他平臺上的開發人員必須瞭解所使用的格式並自行執行對其進行處理。

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>建立 Protobuf 的自訂十進位類型

非常簡單的執行可能類似于某些 Google api 所使用`Money`的非標準型別， `currency`而沒有欄位。

```protobuf
package CustomTypes;

// Example: 12345.6789 -> { units = 12345, nanos = 678900000 }
message Decimal {

    // Whole units part of the amount
    int64 units = 1;

    // Nano units of the amount (10^-9)
    // Must be same sign as units
    sfixed32 nanos = 2;
}
```

欄位代表從`0.999_999_999` 到`-0.999_999_999`的值。 `nanos` 例如， `decimal`此值`sfixed32` `int32` `nanos`會表示為`{ units = 1, nanos = 500_000_000 }` （這就是為什麼此範例中的欄位使用型別，其編碼比較大的值更有效率）。 `1.5m` 如果欄位是負數，欄位也應該是負值。 `nanos` `units`

> [!NOTE]
> 有多個其他演算法可將`decimal`值編碼為位元組字串，但此訊息比其中任何一個更容易瞭解，而且這些值不會受到不同平臺上的 *[endian](https://en.wikipedia.org/wiki/Endianness)* 值影響。

此類型與 BCL `decimal`類型之間的轉換可以C#像這樣執行。

```csharp
namespace CustomTypes
{
    public partial class GrpcDecimal
    {
        private const decimal NanoFactor = 1_000_000_000;
        public GrpcDecimal(long units, int nanos)
        {
            Units = units;
            Nanos = nanos;
        }

        public long Units { get; }
        public int Nanos { get; }

        public static implicit operator decimal(CustomTypes.Decimal grpcDecimal)
        {
            return grpcDecimal.Units + grpcDecimal.Nanos / NanoFactor;
        }

        public static implicit operator CustomTypes.Decimal(decimal value)
        {
            var units = decimal.ToInt64(value);
            var nanos = decimal.ToInt32((value - units) * NanoFactor);
            return new CustomTypes.Decimal(units, nanos);
        }
    }
}
```

> [!IMPORTANT]
> 當您使用像這樣的自訂公用程式訊息類型時，您**必須**使用中`.proto`的批註來記載它們，讓其他開發人員可以在自己的語言或架構中，執行對等類型的轉換。

>[!div class="step-by-step"]
>[上一頁](protobuf-messages.md)
>[下一頁](protobuf-nested-types.md)
