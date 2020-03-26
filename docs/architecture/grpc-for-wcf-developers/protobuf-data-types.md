---
title: 原型純量資料型別 - gRPC，適用于 WCF 開發人員
description: 瞭解 Protobuf 和 gRPC 在 .NET Core 中支援的基本和眾所周知的資料類型。
ms.date: 09/09/2019
ms.openlocfilehash: ea3b53426ecf6f50f3bae22a537e227b07248508
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249431"
---
# <a name="protobuf-scalar-data-types"></a>Protobuf 純量資料類型

協定緩衝區（Protobuf）支援一系列本機標量數值型別。 下表列出了它們與等效的 C# 類型：

| 原型 | C# 類型      | 注意 |
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

1. 使用已簽名值`int32`時`int64`，和 的標準編碼效率很低。 如果欄位可能包含負數，請使用`sint32`或`sint64`改為。 這些類型分別映射到 C# `int` `long`和類型。
2. 無論`fixed`值是什麼，欄位始終使用相同的位元組數。 此行為使較大值的序列化和反序列化更快。
3. Protobuf 字串是 UTF-8（或 7 位 ASCII）編碼的。 編碼的長度不能大於2<sup>32</sup>。
4. Protobuf 運行時提供了一種`ByteString`易於映射到 C# 陣列和從`byte[]`C# 陣列的類型。

## <a name="other-net-primitive-types"></a>其他 .NET 基元類型

### <a name="dates-and-times"></a>日期和時間

本機標量類型不提供日期和時間值，等效于 C# <xref:System.DateTimeOffset> <xref:System.DateTime>和 。 <xref:System.TimeSpan> 您可以使用 Google 的一些"已知類型"擴展來指定這些類型。 這些擴展為受支援的平臺的複雜欄位類型提供代碼生成和運行時支援。

下表顯示了日期和時間類型：

| C# 類型 | 原型公司知名類型 |
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

C# 類中生成的屬性不是 .NET 日期和時間類型。 屬性在`Google.Protobuf.WellKnownTypes`命名空間`Timestamp`中使用`Duration`和 類。 這些類提供轉換 到 和`DateTimeOffset``DateTime`和 的方法。 `TimeSpan`

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
> 該`Timestamp`類型適用于 UTC 時間。 `DateTimeOffset`值的偏移量始終為零，`DateTime.Kind`屬性始終`DateTimeKind.Utc`為 。

### <a name="systemguid"></a>System.Guid

Protobuf 並不直接支援<xref:System.Guid>該類型，這`UUID`稱為其他平臺。 沒有眾所周知的類型。

最好的`Guid`方法是使用標準的`string``8-4-4-4-12`十六進位格式（例如， `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`） 將值作為欄位處理。 所有語言和平臺都可以解析該格式。

不要對`bytes``Guid`值使用欄位。 當Protobuf與其他平臺（如JAVA）交互時，*內皮性*問題（[維琪百科定義](https://en.wikipedia.org/wiki/Endianness)）可能會導致行為不穩定。

### <a name="nullable-types"></a>可為 Null 的型別

C# 的 Protobuf 代碼生成使用本機類型，例如`int` `int32`。 因此，這些值始終包含，不能為空。

對於需要顯式 null 的值（如`int?`在 C# 代碼中使用），Protobuf 的"已知類型"包括編譯為空 C# 類型的包裝。 要使用它們，請導入`wrappers.proto`到檔中`.proto`，如下所示：

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf 將使用生成的消息`T?`屬性的簡單 （`int?`例如 ， ） 。

下表顯示了具有等效 C# 類型的包裝類型的完整清單：

| C# 類型   | 眾所周知的類型包裝器       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

已知類型`Timestamp`，並在`Duration`.NET 中表示為類。 在 C# 8 及以後，可以使用可無參考型別。 但是，在轉換為`DateTimeOffset`或`TimeSpan`時，請務必檢查這些類型的屬性的 null。

## <a name="decimals"></a>小數位數

Protobuf 不本機支援 .NET`decimal`類型，只是`double`和`float`。 Protobuf 專案中正在進行討論，討論向已知類型添加標準`Decimal`類型的可能性，以及支援它的語言和框架的平臺支援。 尚未實施任何措施。

可以創建消息定義來表示適用于 .NET 用戶端`decimal`和伺服器之間安全序列化的類型。 但是，其他平臺上的開發人員必須瞭解所使用的格式，並實現自己的處理。

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>為 Protobuf 創建自訂十進位類型

簡單實現可能與某些 Google API 在沒有`Money``currency`欄位的情況下使用的非標準類型類似。

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

此欄位`nanos`表示從`0.999_999_999`到`-0.999_999_999`的值。 例如，`decimal`該值`1.5m`將表示為`{ units = 1, nanos = 500_000_000 }`。 這就是為什麼此示例中的`nanos`欄位使用`sfixed32`類型，該類型編碼的效率高於`int32`對較大值的編碼。 如果`units`欄位為負，則`nanos`該欄位也應為負數。

> [!NOTE]
> 將值編碼`decimal`為位元組字串還有其他多個演算法，但此消息比其中任何演算法更易於理解。 值不受不同平臺上的內端性的影響。

此類型和 BCL`decimal`類型之間的轉換可能在 C# 中實現，如下所示：

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
> 每當使用此類自訂訊息類型時，*都必須*在 中`.proto`使用 注釋來記錄它們。 然後，其他開發人員可以使用他們自己的語言或框架實現從等效類型轉換。

>[!div class="step-by-step"]
>[上一個](protobuf-messages.md)
>[下一個](protobuf-nested-types.md)
