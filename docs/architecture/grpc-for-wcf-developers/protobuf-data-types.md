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
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="c1c67-103">Protobuf 純量資料類型</span><span class="sxs-lookup"><span data-stu-id="c1c67-103">Protobuf scalar data types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="c1c67-104">Protobuf 支援某個範圍的原生純量實數值型別。</span><span class="sxs-lookup"><span data-stu-id="c1c67-104">Protobuf supports a range of native scalar value types.</span></span> <span data-ttu-id="c1c67-105">下表列出所有其對等C#的類型：</span><span class="sxs-lookup"><span data-stu-id="c1c67-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="c1c67-106">Protobuf 類型</span><span class="sxs-lookup"><span data-stu-id="c1c67-106">Protobuf type</span></span> | <span data-ttu-id="c1c67-107">C# 類型</span><span class="sxs-lookup"><span data-stu-id="c1c67-107">C# type</span></span>      | <span data-ttu-id="c1c67-108">注意</span><span class="sxs-lookup"><span data-stu-id="c1c67-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="c1c67-109">1</span><span class="sxs-lookup"><span data-stu-id="c1c67-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="c1c67-110">1</span><span class="sxs-lookup"><span data-stu-id="c1c67-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="c1c67-111">1</span><span class="sxs-lookup"><span data-stu-id="c1c67-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="c1c67-112">1</span><span class="sxs-lookup"><span data-stu-id="c1c67-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="c1c67-113">2</span><span class="sxs-lookup"><span data-stu-id="c1c67-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="c1c67-114">2</span><span class="sxs-lookup"><span data-stu-id="c1c67-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="c1c67-115">2</span><span class="sxs-lookup"><span data-stu-id="c1c67-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="c1c67-116">2</span><span class="sxs-lookup"><span data-stu-id="c1c67-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="c1c67-117">3</span><span class="sxs-lookup"><span data-stu-id="c1c67-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="c1c67-118">4</span><span class="sxs-lookup"><span data-stu-id="c1c67-118">4</span></span>     |

## <a name="notes"></a><span data-ttu-id="c1c67-119">注意</span><span class="sxs-lookup"><span data-stu-id="c1c67-119">Notes</span></span>

1. <span data-ttu-id="c1c67-120">使用帶正負號`int32`的`int64`值時，和的標準編碼效率不佳。</span><span class="sxs-lookup"><span data-stu-id="c1c67-120">The standard encoding for `int32` and `int64` is inefficient when working with signed values.</span></span> <span data-ttu-id="c1c67-121">如果您的欄位可能包含負數，請`sint32`改用或。 `sint64`</span><span class="sxs-lookup"><span data-stu-id="c1c67-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="c1c67-122">這兩種類型分別C# `int`對應`long`至和類型。</span><span class="sxs-lookup"><span data-stu-id="c1c67-122">Both types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="c1c67-123">不論值為何，欄位一律會使用相同數目的位元組。`fixed`</span><span class="sxs-lookup"><span data-stu-id="c1c67-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="c1c67-124">此行為可讓較大的值更快速地進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="c1c67-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="c1c67-125">Protobuf 字串是以 UTF-8 （或7位 ASCII）編碼，且編碼的長度不能大於 2<sup>32</sup>。</span><span class="sxs-lookup"><span data-stu-id="c1c67-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded, and the encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="c1c67-126">Protobuf 執行時間提供`ByteString`的類型，可輕鬆地與C# `byte[]`陣列進行對應。</span><span class="sxs-lookup"><span data-stu-id="c1c67-126">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="c1c67-127">其他 .NET 基本類型</span><span class="sxs-lookup"><span data-stu-id="c1c67-127">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="c1c67-128">日期和時間</span><span class="sxs-lookup"><span data-stu-id="c1c67-128">Dates and times</span></span>

<span data-ttu-id="c1c67-129">原生純量類型不提供日期和時間值，相當於C#的<xref:System.DateTimeOffset>、 <xref:System.DateTime>和<xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="c1c67-129">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="c1c67-130">您可以使用 Google 的「知名型別」延伸模組來指定這些型別，這些擴充功能可跨支援的平臺，為更複雜的欄位類型提供程式碼產生和執行時間支援。</span><span class="sxs-lookup"><span data-stu-id="c1c67-130">These types can be specified using some of Google's "Well Known Types" extensions, which provide code generation and runtime support for more complex field types across the supported platforms.</span></span> <span data-ttu-id="c1c67-131">下表顯示日期和時間類型：</span><span class="sxs-lookup"><span data-stu-id="c1c67-131">The following table shows the date and time types:</span></span>

| <span data-ttu-id="c1c67-132">C# 類型</span><span class="sxs-lookup"><span data-stu-id="c1c67-132">C# type</span></span> | <span data-ttu-id="c1c67-133">Protobuf 知名型別</span><span class="sxs-lookup"><span data-stu-id="c1c67-133">Protobuf well-known type</span></span> |
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

<span data-ttu-id="c1c67-134">C#類別中產生的屬性不是 .net 日期和時間類型。</span><span class="sxs-lookup"><span data-stu-id="c1c67-134">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="c1c67-135">屬性`Timestamp`會使用`Google.Protobuf.WellKnownTypes`命名空間`Duration`中的和類別，以提供在、 `DateTime` `TimeSpan`和之間`DateTimeOffset`來回轉換的方法。</span><span class="sxs-lookup"><span data-stu-id="c1c67-135">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace, which provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="c1c67-136">`Timestamp`類型適用于 UTC 時間;值的位移一律為零， `DateTime.Kind`而屬性則一律為`DateTimeKind.Utc`。 `DateTimeOffset`</span><span class="sxs-lookup"><span data-stu-id="c1c67-136">The `Timestamp` type works with UTC times; `DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property will always be `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="c1c67-137">System.Guid</span><span class="sxs-lookup"><span data-stu-id="c1c67-137">System.Guid</span></span>

<span data-ttu-id="c1c67-138">類型（也`UUID`就是在其他平臺上）不會直接受到 Protobuf 的支援，而且沒有已知的類型。 <xref:System.Guid></span><span class="sxs-lookup"><span data-stu-id="c1c67-138">The <xref:System.Guid> type, known as `UUID` on other platforms, isn't directly supported by Protobuf and there's no well-known type for it.</span></span> <span data-ttu-id="c1c67-139">最好的方法是使用標準`Guid` `8-4-4-4-12`的十六進位`string`格式（ `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`例如），將值當做欄位來處理，這可由所有語言和平臺進行剖析。</span><span class="sxs-lookup"><span data-stu-id="c1c67-139">The best approach is to handle `Guid` values as `string` field, using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), which can be parsed by all languages and platforms.</span></span> <span data-ttu-id="c1c67-140">請不要使用`bytes` `Guid`欄位做為值，因為當 endian 與其他平臺（例如 JAVA）互動時，可能會造成不穩定的行為。</span><span class="sxs-lookup"><span data-stu-id="c1c67-140">Don't use a `bytes` field for `Guid` values, as problems with endianness can result in erratic behavior when interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="c1c67-141">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="c1c67-141">Nullable types</span></span>

<span data-ttu-id="c1c67-142">產生的 Protobuf 程式C#代碼會使用原生類型， `int`例如適用于。 `int32`</span><span class="sxs-lookup"><span data-stu-id="c1c67-142">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="c1c67-143">這表示一定會包含這些值，而且不能是 null。</span><span class="sxs-lookup"><span data-stu-id="c1c67-143">This means that the values are always included and can't be null.</span></span> <span data-ttu-id="c1c67-144">對於需要明確 null 的值，例如在您`int?`的程式C#代碼中使用，Protobuf 的「知名類型」包含編譯成可為 null C#類型的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="c1c67-144">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="c1c67-145">若要使用它們， `wrappers.proto`請匯`.proto`入您的檔案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c1c67-145">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="c1c67-146">Protobuf 會針對產生的`T?`訊息屬性使用簡單`int?`（例如）。</span><span class="sxs-lookup"><span data-stu-id="c1c67-146">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="c1c67-147">下表顯示包裝函式類型的完整清單及其對等C#類型：</span><span class="sxs-lookup"><span data-stu-id="c1c67-147">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="c1c67-148">C# 類型</span><span class="sxs-lookup"><span data-stu-id="c1c67-148">C# type</span></span>   | <span data-ttu-id="c1c67-149">知名的型別包裝函式</span><span class="sxs-lookup"><span data-stu-id="c1c67-149">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="c1c67-150">已知`Timestamp`的型別和`Duration`在 .net 中是以類別表示，因此不需要可為 null 的版本，但在轉換為`DateTimeOffset`或`TimeSpan`時，請務必檢查這些類型的屬性是否為 null。</span><span class="sxs-lookup"><span data-stu-id="c1c67-150">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version, but it's important to check for null on properties of those types when converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="c1c67-151">小</span><span class="sxs-lookup"><span data-stu-id="c1c67-151">Decimals</span></span>

<span data-ttu-id="c1c67-152">Protobuf 原本就不支援 .net `decimal`型別， `double`只有`float`和。</span><span class="sxs-lookup"><span data-stu-id="c1c67-152">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="c1c67-153">Protobuf 專案中有一項持續性的討論，說明如何將標準`Decimal`類型新增至已知類型，並提供支援的語言和架構平臺支援，但尚未實行任何功能。</span><span class="sxs-lookup"><span data-stu-id="c1c67-153">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it, but nothing has been implemented yet.</span></span>

<span data-ttu-id="c1c67-154">您可以建立訊息定義來代表可在`decimal` .net 用戶端和伺服器之間安全序列化的類型，但是其他平臺上的開發人員必須瞭解所使用的格式並自行執行對其進行處理。</span><span class="sxs-lookup"><span data-stu-id="c1c67-154">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers, but developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="c1c67-155">建立 Protobuf 的自訂十進位類型</span><span class="sxs-lookup"><span data-stu-id="c1c67-155">Creating a custom Decimal type for Protobuf</span></span>

<span data-ttu-id="c1c67-156">非常簡單的執行可能類似于某些 Google api 所使用`Money`的非標準型別， `currency`而沒有欄位。</span><span class="sxs-lookup"><span data-stu-id="c1c67-156">A very simple implementation could be similar to the non-standard `Money` type used by some Google APIs, without the `currency` field.</span></span>

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

<span data-ttu-id="c1c67-157">欄位代表從`0.999_999_999` 到`-0.999_999_999`的值。 `nanos`</span><span class="sxs-lookup"><span data-stu-id="c1c67-157">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="c1c67-158">例如， `decimal`此值`sfixed32` `int32` `nanos`會表示為`{ units = 1, nanos = 500_000_000 }` （這就是為什麼此範例中的欄位使用型別，其編碼比較大的值更有效率）。 `1.5m`</span><span class="sxs-lookup"><span data-stu-id="c1c67-158">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }` (this is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values).</span></span> <span data-ttu-id="c1c67-159">如果欄位是負數，欄位也應該是負值。 `nanos` `units`</span><span class="sxs-lookup"><span data-stu-id="c1c67-159">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="c1c67-160">有多個其他演算法可將`decimal`值編碼為位元組字串，但此訊息比其中任何一個更容易瞭解，而且這些值不會受到不同平臺上的 *[endian](https://en.wikipedia.org/wiki/Endianness)* 值影響。</span><span class="sxs-lookup"><span data-stu-id="c1c67-160">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is much easier to understand than any of them, and the values are not affected by *[endianness](https://en.wikipedia.org/wiki/Endianness)* on different platforms.</span></span>

<span data-ttu-id="c1c67-161">此類型與 BCL `decimal`類型之間的轉換可以C#像這樣執行。</span><span class="sxs-lookup"><span data-stu-id="c1c67-161">Conversion between this type and the BCL `decimal` type could be implemented in C# like this.</span></span>

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
> <span data-ttu-id="c1c67-162">當您使用像這樣的自訂公用程式訊息類型時，您**必須**使用中`.proto`的批註來記載它們，讓其他開發人員可以在自己的語言或架構中，執行對等類型的轉換。</span><span class="sxs-lookup"><span data-stu-id="c1c67-162">Whenever you use custom utility message types like this, you **must** document them with comments in the `.proto` so that other developers can implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c1c67-163">[上一頁](protobuf-messages.md)
>[下一頁](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="c1c67-163">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
