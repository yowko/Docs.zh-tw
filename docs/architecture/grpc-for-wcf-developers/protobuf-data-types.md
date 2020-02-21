---
title: Protobuf 純量資料類型-WCF 開發人員的 gRPC
description: 瞭解在 .NET Core 中 Protobuf 和 gRPC 支援的基本和已知資料類型。
ms.date: 09/09/2019
ms.openlocfilehash: f5215550a6a2d54dfe2e859c574a34f641fdb68d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543153"
---
# <a name="protobuf-scalar-data-types"></a>Protobuf 純量資料類型

通訊協定緩衝區（Protobuf）支援一系列的原生純量實數值型別。 下表列出所有其對等C#的類型：

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

1. 當您使用帶正負號的值時，`int32` 和 `int64` 的標準編碼就沒有效率。 如果您的欄位可能包含負數，請改用 `sint32` 或 `sint64`。 這些類型會分別對應C#至 `int` 和 `long` 類型。
2. 無論值為何，`fixed` 欄位一律會使用相同數目的位元組。 此行為可讓較大的值更快速地進行序列化和還原序列化。
3. Protobuf 字串是以 UTF-8 （或7位 ASCII）編碼。 編碼的長度不能大於 2<sup>32</sup>。
4. Protobuf 執行時間提供 `ByteString` 類型，可讓您輕鬆地在C# `byte[]` 陣列之間進行對應。

## <a name="other-net-primitive-types"></a>其他 .NET 基本類型

### <a name="dates-and-times"></a>日期和時間

原生純量類型不提供日期和時間值，相當於C#的 <xref:System.DateTimeOffset>、<xref:System.DateTime>和 <xref:System.TimeSpan>。 您可以使用一些 Google 的「知名類型」延伸模組來指定這些類型。 這些延伸模組可跨支援的平臺，為複雜的欄位類型提供程式碼產生和執行時間支援。 

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

C#類別中產生的屬性不是 .net 日期和時間類型。 屬性會使用 `Google.Protobuf.WellKnownTypes` 命名空間中的 `Timestamp` 和 `Duration` 類別。 這些類別提供轉換 `DateTimeOffset`、`DateTime`和 `TimeSpan`的方法。

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
> `Timestamp` 類型適用于 UTC 時間。 `DateTimeOffset` 值的位移一律為零，而且 `DateTime.Kind` 屬性一律會 `DateTimeKind.Utc`。

### <a name="systemguid"></a>System.Guid

Protobuf 不直接支援 <xref:System.Guid> 類型，在其他平臺上也稱為 `UUID`。 沒有適用于它的已知型別。 

最好的方法是使用標準 `8-4-4-4-12` 十六進位格式（例如 `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`）來處理 `Guid` 值，做為 `string` 欄位。 所有語言和平臺都可以剖析該格式。

請不要使用 `bytes` 欄位來 `Guid` 值。 當 Protobuf 與其他平臺（例如 JAVA）互動時， *endian* （[維琪百科定義](https://en.wikipedia.org/wiki/Endianness)）的問題可能會造成不穩定的行為。

### <a name="nullable-types"></a>可為 Null 的型別

產生的 Protobuf 程式C#代碼會使用原生類型，例如 `int32`的 `int`。 因此，一律會包含這些值，而且不能是 null。 

對於需要明確 null 的值，例如在程式C#代碼中使用 `int?`，Protobuf 的「知名類型」包含編譯成可為 null C#之類型的包裝函式。 若要使用它們，請將 `wrappers.proto` 匯入到您的 `.proto` 檔案，如下所示：

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf 會針對產生的訊息屬性使用簡單的 `T?` （例如 `int?`）。

下表顯示包裝函式類型的完整清單及其對等C#類型：

| C# 類型   | 知名的型別包裝函式       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

已知的型別 `Timestamp` 和 `Duration` 在 .NET 中以類別表示，因此不需要可為 null 的版本。 但是，當您轉換成 `DateTimeOffset` 或 `TimeSpan`時，請務必檢查這些類型的屬性是否為 null。

## <a name="decimals"></a>小數位數

Protobuf 原本就不支援 .NET `decimal` 型別，只 `double` 和 `float`。 Protobuf 專案中有一項持續的討論，告訴您將標準 `Decimal` 類型新增至已知類型的可能性，以及支援的語言和架構平臺支援。 尚未實行任何內容。

您可以建立訊息定義來代表可在 .NET 用戶端和伺服器之間安全序列化的 `decimal` 類型。 但是，其他平臺上的開發人員必須瞭解所使用的格式，並為其執行自己的處理方式。

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>建立 Protobuf 的自訂十進位類型

簡單的執行可能類似于某些 Google Api 所使用的非標準 `Money` 型別，而沒有 `currency` 欄位。

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

[`nanos`] 欄位代表從 `0.999_999_999` 到 `-0.999_999_999`的值。 例如，`decimal` 值 `1.5m` 會以 `{ units = 1, nanos = 500_000_000 }`表示。 這就是為什麼此範例中的 `nanos` 欄位使用 `sfixed32` 型別，比起 `int32` 較大的值更有效率。 如果 [`units`] 欄位是負數，[`nanos`] 欄位也應該是負值。

> [!NOTE]
> 有多個其他演算法可將 `decimal` 值編碼為位元組字串，但這則訊息比任何一個更容易瞭解。 在不同平臺上，值不會受到 endian 的影響。

此類型與 BCL `decimal` 類型之間的轉換可能會在中C#執行，如下所示：

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
> 每當您使用這類的自訂訊息類型時，您*必須*使用 `.proto`中的批註來記錄它們。 然後，其他開發人員可以在自己的語言或架構中，執行對等類型的轉換。

>[!div class="step-by-step"]
>[上一頁](protobuf-messages.md)
>[下一頁](protobuf-nested-types.md)
