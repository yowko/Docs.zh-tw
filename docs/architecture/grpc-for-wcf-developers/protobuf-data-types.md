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
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="71074-103">Protobuf 純量資料類型</span><span class="sxs-lookup"><span data-stu-id="71074-103">Protobuf scalar data types</span></span>

<span data-ttu-id="71074-104">協定緩衝區（Protobuf）支援一系列本機標量數值型別。</span><span class="sxs-lookup"><span data-stu-id="71074-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="71074-105">下表列出了它們與等效的 C# 類型：</span><span class="sxs-lookup"><span data-stu-id="71074-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="71074-106">原型</span><span class="sxs-lookup"><span data-stu-id="71074-106">Protobuf type</span></span> | <span data-ttu-id="71074-107">C# 類型</span><span class="sxs-lookup"><span data-stu-id="71074-107">C# type</span></span>      | <span data-ttu-id="71074-108">注意</span><span class="sxs-lookup"><span data-stu-id="71074-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="71074-109">1</span><span class="sxs-lookup"><span data-stu-id="71074-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="71074-110">1</span><span class="sxs-lookup"><span data-stu-id="71074-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="71074-111">1</span><span class="sxs-lookup"><span data-stu-id="71074-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="71074-112">1</span><span class="sxs-lookup"><span data-stu-id="71074-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="71074-113">2</span><span class="sxs-lookup"><span data-stu-id="71074-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="71074-114">2</span><span class="sxs-lookup"><span data-stu-id="71074-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="71074-115">2</span><span class="sxs-lookup"><span data-stu-id="71074-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="71074-116">2</span><span class="sxs-lookup"><span data-stu-id="71074-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="71074-117">3</span><span class="sxs-lookup"><span data-stu-id="71074-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="71074-118">4</span><span class="sxs-lookup"><span data-stu-id="71074-118">4</span></span>     |

<span data-ttu-id="71074-119">注意：</span><span class="sxs-lookup"><span data-stu-id="71074-119">Notes:</span></span>

1. <span data-ttu-id="71074-120">使用已簽名值`int32`時`int64`，和 的標準編碼效率很低。</span><span class="sxs-lookup"><span data-stu-id="71074-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="71074-121">如果欄位可能包含負數，請使用`sint32`或`sint64`改為。</span><span class="sxs-lookup"><span data-stu-id="71074-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="71074-122">這些類型分別映射到 C# `int` `long`和類型。</span><span class="sxs-lookup"><span data-stu-id="71074-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="71074-123">無論`fixed`值是什麼，欄位始終使用相同的位元組數。</span><span class="sxs-lookup"><span data-stu-id="71074-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="71074-124">此行為使較大值的序列化和反序列化更快。</span><span class="sxs-lookup"><span data-stu-id="71074-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="71074-125">Protobuf 字串是 UTF-8（或 7 位 ASCII）編碼的。</span><span class="sxs-lookup"><span data-stu-id="71074-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="71074-126">編碼的長度不能大於2<sup>32</sup>。</span><span class="sxs-lookup"><span data-stu-id="71074-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="71074-127">Protobuf 運行時提供了一種`ByteString`易於映射到 C# 陣列和從`byte[]`C# 陣列的類型。</span><span class="sxs-lookup"><span data-stu-id="71074-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="71074-128">其他 .NET 基元類型</span><span class="sxs-lookup"><span data-stu-id="71074-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="71074-129">日期和時間</span><span class="sxs-lookup"><span data-stu-id="71074-129">Dates and times</span></span>

<span data-ttu-id="71074-130">本機標量類型不提供日期和時間值，等效于 C# <xref:System.DateTimeOffset> <xref:System.DateTime>和 。 <xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="71074-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="71074-131">您可以使用 Google 的一些"已知類型"擴展來指定這些類型。</span><span class="sxs-lookup"><span data-stu-id="71074-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="71074-132">這些擴展為受支援的平臺的複雜欄位類型提供代碼生成和運行時支援。</span><span class="sxs-lookup"><span data-stu-id="71074-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span>

<span data-ttu-id="71074-133">下表顯示了日期和時間類型：</span><span class="sxs-lookup"><span data-stu-id="71074-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="71074-134">C# 類型</span><span class="sxs-lookup"><span data-stu-id="71074-134">C# type</span></span> | <span data-ttu-id="71074-135">原型公司知名類型</span><span class="sxs-lookup"><span data-stu-id="71074-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="71074-136">C# 類中生成的屬性不是 .NET 日期和時間類型。</span><span class="sxs-lookup"><span data-stu-id="71074-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="71074-137">屬性在`Google.Protobuf.WellKnownTypes`命名空間`Timestamp`中使用`Duration`和 類。</span><span class="sxs-lookup"><span data-stu-id="71074-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="71074-138">這些類提供轉換 到 和`DateTimeOffset``DateTime`和 的方法。 `TimeSpan`</span><span class="sxs-lookup"><span data-stu-id="71074-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="71074-139">該`Timestamp`類型適用于 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="71074-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="71074-140">`DateTimeOffset`值的偏移量始終為零，`DateTime.Kind`屬性始終`DateTimeKind.Utc`為 。</span><span class="sxs-lookup"><span data-stu-id="71074-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="71074-141">System.Guid</span><span class="sxs-lookup"><span data-stu-id="71074-141">System.Guid</span></span>

<span data-ttu-id="71074-142">Protobuf 並不直接支援<xref:System.Guid>該類型，這`UUID`稱為其他平臺。</span><span class="sxs-lookup"><span data-stu-id="71074-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="71074-143">沒有眾所周知的類型。</span><span class="sxs-lookup"><span data-stu-id="71074-143">There's no well-known type for it.</span></span>

<span data-ttu-id="71074-144">最好的`Guid`方法是使用標準的`string``8-4-4-4-12`十六進位格式（例如， `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`） 將值作為欄位處理。</span><span class="sxs-lookup"><span data-stu-id="71074-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="71074-145">所有語言和平臺都可以解析該格式。</span><span class="sxs-lookup"><span data-stu-id="71074-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="71074-146">不要對`bytes``Guid`值使用欄位。</span><span class="sxs-lookup"><span data-stu-id="71074-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="71074-147">當Protobuf與其他平臺（如JAVA）交互時，*內皮性*問題（[維琪百科定義](https://en.wikipedia.org/wiki/Endianness)）可能會導致行為不穩定。</span><span class="sxs-lookup"><span data-stu-id="71074-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="71074-148">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="71074-148">Nullable types</span></span>

<span data-ttu-id="71074-149">C# 的 Protobuf 代碼生成使用本機類型，例如`int` `int32`。</span><span class="sxs-lookup"><span data-stu-id="71074-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="71074-150">因此，這些值始終包含，不能為空。</span><span class="sxs-lookup"><span data-stu-id="71074-150">So the values are always included and can't be null.</span></span>

<span data-ttu-id="71074-151">對於需要顯式 null 的值（如`int?`在 C# 代碼中使用），Protobuf 的"已知類型"包括編譯為空 C# 類型的包裝。</span><span class="sxs-lookup"><span data-stu-id="71074-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="71074-152">要使用它們，請導入`wrappers.proto`到檔中`.proto`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="71074-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="71074-153">Protobuf 將使用生成的消息`T?`屬性的簡單 （`int?`例如 ， ） 。</span><span class="sxs-lookup"><span data-stu-id="71074-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="71074-154">下表顯示了具有等效 C# 類型的包裝類型的完整清單：</span><span class="sxs-lookup"><span data-stu-id="71074-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="71074-155">C# 類型</span><span class="sxs-lookup"><span data-stu-id="71074-155">C# type</span></span>   | <span data-ttu-id="71074-156">眾所周知的類型包裝器</span><span class="sxs-lookup"><span data-stu-id="71074-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="71074-157">已知類型`Timestamp`，並在`Duration`.NET 中表示為類。</span><span class="sxs-lookup"><span data-stu-id="71074-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes.</span></span> <span data-ttu-id="71074-158">在 C# 8 及以後，可以使用可無參考型別。</span><span class="sxs-lookup"><span data-stu-id="71074-158">In C# 8 and beyond, you can use nullable reference types.</span></span> <span data-ttu-id="71074-159">但是，在轉換為`DateTimeOffset`或`TimeSpan`時，請務必檢查這些類型的屬性的 null。</span><span class="sxs-lookup"><span data-stu-id="71074-159">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="71074-160">小數位數</span><span class="sxs-lookup"><span data-stu-id="71074-160">Decimals</span></span>

<span data-ttu-id="71074-161">Protobuf 不本機支援 .NET`decimal`類型，只是`double`和`float`。</span><span class="sxs-lookup"><span data-stu-id="71074-161">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="71074-162">Protobuf 專案中正在進行討論，討論向已知類型添加標準`Decimal`類型的可能性，以及支援它的語言和框架的平臺支援。</span><span class="sxs-lookup"><span data-stu-id="71074-162">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="71074-163">尚未實施任何措施。</span><span class="sxs-lookup"><span data-stu-id="71074-163">Nothing has been implemented yet.</span></span>

<span data-ttu-id="71074-164">可以創建消息定義來表示適用于 .NET 用戶端`decimal`和伺服器之間安全序列化的類型。</span><span class="sxs-lookup"><span data-stu-id="71074-164">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="71074-165">但是，其他平臺上的開發人員必須瞭解所使用的格式，並實現自己的處理。</span><span class="sxs-lookup"><span data-stu-id="71074-165">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="71074-166">為 Protobuf 創建自訂十進位類型</span><span class="sxs-lookup"><span data-stu-id="71074-166">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="71074-167">簡單實現可能與某些 Google API 在沒有`Money``currency`欄位的情況下使用的非標準類型類似。</span><span class="sxs-lookup"><span data-stu-id="71074-167">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="71074-168">此欄位`nanos`表示從`0.999_999_999`到`-0.999_999_999`的值。</span><span class="sxs-lookup"><span data-stu-id="71074-168">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="71074-169">例如，`decimal`該值`1.5m`將表示為`{ units = 1, nanos = 500_000_000 }`。</span><span class="sxs-lookup"><span data-stu-id="71074-169">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="71074-170">這就是為什麼此示例中的`nanos`欄位使用`sfixed32`類型，該類型編碼的效率高於`int32`對較大值的編碼。</span><span class="sxs-lookup"><span data-stu-id="71074-170">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="71074-171">如果`units`欄位為負，則`nanos`該欄位也應為負數。</span><span class="sxs-lookup"><span data-stu-id="71074-171">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="71074-172">將值編碼`decimal`為位元組字串還有其他多個演算法，但此消息比其中任何演算法更易於理解。</span><span class="sxs-lookup"><span data-stu-id="71074-172">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="71074-173">值不受不同平臺上的內端性的影響。</span><span class="sxs-lookup"><span data-stu-id="71074-173">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="71074-174">此類型和 BCL`decimal`類型之間的轉換可能在 C# 中實現，如下所示：</span><span class="sxs-lookup"><span data-stu-id="71074-174">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="71074-175">每當使用此類自訂訊息類型時，*都必須*在 中`.proto`使用 注釋來記錄它們。</span><span class="sxs-lookup"><span data-stu-id="71074-175">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="71074-176">然後，其他開發人員可以使用他們自己的語言或框架實現從等效類型轉換。</span><span class="sxs-lookup"><span data-stu-id="71074-176">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="71074-177">[上一個](protobuf-messages.md)
>[下一個](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="71074-177">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
