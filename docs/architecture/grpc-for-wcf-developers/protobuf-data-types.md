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
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="48b5c-103">Protobuf 純量資料類型</span><span class="sxs-lookup"><span data-stu-id="48b5c-103">Protobuf scalar data types</span></span>

<span data-ttu-id="48b5c-104">通訊協定緩衝區（Protobuf）支援一系列的原生純量實數值型別。</span><span class="sxs-lookup"><span data-stu-id="48b5c-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="48b5c-105">下表列出所有其對等C#的類型：</span><span class="sxs-lookup"><span data-stu-id="48b5c-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="48b5c-106">Protobuf 類型</span><span class="sxs-lookup"><span data-stu-id="48b5c-106">Protobuf type</span></span> | <span data-ttu-id="48b5c-107">C# 類型</span><span class="sxs-lookup"><span data-stu-id="48b5c-107">C# type</span></span>      | <span data-ttu-id="48b5c-108">注意</span><span class="sxs-lookup"><span data-stu-id="48b5c-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="48b5c-109">1</span><span class="sxs-lookup"><span data-stu-id="48b5c-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="48b5c-110">1</span><span class="sxs-lookup"><span data-stu-id="48b5c-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="48b5c-111">1</span><span class="sxs-lookup"><span data-stu-id="48b5c-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="48b5c-112">1</span><span class="sxs-lookup"><span data-stu-id="48b5c-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="48b5c-113">2</span><span class="sxs-lookup"><span data-stu-id="48b5c-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="48b5c-114">2</span><span class="sxs-lookup"><span data-stu-id="48b5c-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="48b5c-115">2</span><span class="sxs-lookup"><span data-stu-id="48b5c-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="48b5c-116">2</span><span class="sxs-lookup"><span data-stu-id="48b5c-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="48b5c-117">3</span><span class="sxs-lookup"><span data-stu-id="48b5c-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="48b5c-118">4</span><span class="sxs-lookup"><span data-stu-id="48b5c-118">4</span></span>     |

<span data-ttu-id="48b5c-119">注意：</span><span class="sxs-lookup"><span data-stu-id="48b5c-119">Notes:</span></span>

1. <span data-ttu-id="48b5c-120">當您使用帶正負號的值時，`int32` 和 `int64` 的標準編碼就沒有效率。</span><span class="sxs-lookup"><span data-stu-id="48b5c-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="48b5c-121">如果您的欄位可能包含負數，請改用 `sint32` 或 `sint64`。</span><span class="sxs-lookup"><span data-stu-id="48b5c-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="48b5c-122">這些類型會分別對應C#至 `int` 和 `long` 類型。</span><span class="sxs-lookup"><span data-stu-id="48b5c-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="48b5c-123">無論值為何，`fixed` 欄位一律會使用相同數目的位元組。</span><span class="sxs-lookup"><span data-stu-id="48b5c-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="48b5c-124">此行為可讓較大的值更快速地進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="48b5c-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="48b5c-125">Protobuf 字串是以 UTF-8 （或7位 ASCII）編碼。</span><span class="sxs-lookup"><span data-stu-id="48b5c-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="48b5c-126">編碼的長度不能大於 2<sup>32</sup>。</span><span class="sxs-lookup"><span data-stu-id="48b5c-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="48b5c-127">Protobuf 執行時間提供 `ByteString` 類型，可讓您輕鬆地在C# `byte[]` 陣列之間進行對應。</span><span class="sxs-lookup"><span data-stu-id="48b5c-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="48b5c-128">其他 .NET 基本類型</span><span class="sxs-lookup"><span data-stu-id="48b5c-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="48b5c-129">日期和時間</span><span class="sxs-lookup"><span data-stu-id="48b5c-129">Dates and times</span></span>

<span data-ttu-id="48b5c-130">原生純量類型不提供日期和時間值，相當於C#的 <xref:System.DateTimeOffset>、<xref:System.DateTime>和 <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="48b5c-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="48b5c-131">您可以使用一些 Google 的「知名類型」延伸模組來指定這些類型。</span><span class="sxs-lookup"><span data-stu-id="48b5c-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="48b5c-132">這些延伸模組可跨支援的平臺，為複雜的欄位類型提供程式碼產生和執行時間支援。</span><span class="sxs-lookup"><span data-stu-id="48b5c-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span> 

<span data-ttu-id="48b5c-133">下表顯示日期和時間類型：</span><span class="sxs-lookup"><span data-stu-id="48b5c-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="48b5c-134">C# 類型</span><span class="sxs-lookup"><span data-stu-id="48b5c-134">C# type</span></span> | <span data-ttu-id="48b5c-135">Protobuf 知名型別</span><span class="sxs-lookup"><span data-stu-id="48b5c-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="48b5c-136">C#類別中產生的屬性不是 .net 日期和時間類型。</span><span class="sxs-lookup"><span data-stu-id="48b5c-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="48b5c-137">屬性會使用 `Google.Protobuf.WellKnownTypes` 命名空間中的 `Timestamp` 和 `Duration` 類別。</span><span class="sxs-lookup"><span data-stu-id="48b5c-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="48b5c-138">這些類別提供轉換 `DateTimeOffset`、`DateTime`和 `TimeSpan`的方法。</span><span class="sxs-lookup"><span data-stu-id="48b5c-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="48b5c-139">`Timestamp` 類型適用于 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="48b5c-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="48b5c-140">`DateTimeOffset` 值的位移一律為零，而且 `DateTime.Kind` 屬性一律會 `DateTimeKind.Utc`。</span><span class="sxs-lookup"><span data-stu-id="48b5c-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="48b5c-141">System.Guid</span><span class="sxs-lookup"><span data-stu-id="48b5c-141">System.Guid</span></span>

<span data-ttu-id="48b5c-142">Protobuf 不直接支援 <xref:System.Guid> 類型，在其他平臺上也稱為 `UUID`。</span><span class="sxs-lookup"><span data-stu-id="48b5c-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="48b5c-143">沒有適用于它的已知型別。</span><span class="sxs-lookup"><span data-stu-id="48b5c-143">There's no well-known type for it.</span></span> 

<span data-ttu-id="48b5c-144">最好的方法是使用標準 `8-4-4-4-12` 十六進位格式（例如 `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`）來處理 `Guid` 值，做為 `string` 欄位。</span><span class="sxs-lookup"><span data-stu-id="48b5c-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="48b5c-145">所有語言和平臺都可以剖析該格式。</span><span class="sxs-lookup"><span data-stu-id="48b5c-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="48b5c-146">請不要使用 `bytes` 欄位來 `Guid` 值。</span><span class="sxs-lookup"><span data-stu-id="48b5c-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="48b5c-147">當 Protobuf 與其他平臺（例如 JAVA）互動時， *endian* （[維琪百科定義](https://en.wikipedia.org/wiki/Endianness)）的問題可能會造成不穩定的行為。</span><span class="sxs-lookup"><span data-stu-id="48b5c-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="48b5c-148">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="48b5c-148">Nullable types</span></span>

<span data-ttu-id="48b5c-149">產生的 Protobuf 程式C#代碼會使用原生類型，例如 `int32`的 `int`。</span><span class="sxs-lookup"><span data-stu-id="48b5c-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="48b5c-150">因此，一律會包含這些值，而且不能是 null。</span><span class="sxs-lookup"><span data-stu-id="48b5c-150">So the values are always included and can't be null.</span></span> 

<span data-ttu-id="48b5c-151">對於需要明確 null 的值，例如在程式C#代碼中使用 `int?`，Protobuf 的「知名類型」包含編譯成可為 null C#之類型的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="48b5c-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="48b5c-152">若要使用它們，請將 `wrappers.proto` 匯入到您的 `.proto` 檔案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="48b5c-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="48b5c-153">Protobuf 會針對產生的訊息屬性使用簡單的 `T?` （例如 `int?`）。</span><span class="sxs-lookup"><span data-stu-id="48b5c-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="48b5c-154">下表顯示包裝函式類型的完整清單及其對等C#類型：</span><span class="sxs-lookup"><span data-stu-id="48b5c-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="48b5c-155">C# 類型</span><span class="sxs-lookup"><span data-stu-id="48b5c-155">C# type</span></span>   | <span data-ttu-id="48b5c-156">知名的型別包裝函式</span><span class="sxs-lookup"><span data-stu-id="48b5c-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="48b5c-157">已知的型別 `Timestamp` 和 `Duration` 在 .NET 中以類別表示，因此不需要可為 null 的版本。</span><span class="sxs-lookup"><span data-stu-id="48b5c-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version.</span></span> <span data-ttu-id="48b5c-158">但是，當您轉換成 `DateTimeOffset` 或 `TimeSpan`時，請務必檢查這些類型的屬性是否為 null。</span><span class="sxs-lookup"><span data-stu-id="48b5c-158">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="48b5c-159">小數位數</span><span class="sxs-lookup"><span data-stu-id="48b5c-159">Decimals</span></span>

<span data-ttu-id="48b5c-160">Protobuf 原本就不支援 .NET `decimal` 型別，只 `double` 和 `float`。</span><span class="sxs-lookup"><span data-stu-id="48b5c-160">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="48b5c-161">Protobuf 專案中有一項持續的討論，告訴您將標準 `Decimal` 類型新增至已知類型的可能性，以及支援的語言和架構平臺支援。</span><span class="sxs-lookup"><span data-stu-id="48b5c-161">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="48b5c-162">尚未實行任何內容。</span><span class="sxs-lookup"><span data-stu-id="48b5c-162">Nothing has been implemented yet.</span></span>

<span data-ttu-id="48b5c-163">您可以建立訊息定義來代表可在 .NET 用戶端和伺服器之間安全序列化的 `decimal` 類型。</span><span class="sxs-lookup"><span data-stu-id="48b5c-163">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="48b5c-164">但是，其他平臺上的開發人員必須瞭解所使用的格式，並為其執行自己的處理方式。</span><span class="sxs-lookup"><span data-stu-id="48b5c-164">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="48b5c-165">建立 Protobuf 的自訂十進位類型</span><span class="sxs-lookup"><span data-stu-id="48b5c-165">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="48b5c-166">簡單的執行可能類似于某些 Google Api 所使用的非標準 `Money` 型別，而沒有 `currency` 欄位。</span><span class="sxs-lookup"><span data-stu-id="48b5c-166">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="48b5c-167">[`nanos`] 欄位代表從 `0.999_999_999` 到 `-0.999_999_999`的值。</span><span class="sxs-lookup"><span data-stu-id="48b5c-167">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="48b5c-168">例如，`decimal` 值 `1.5m` 會以 `{ units = 1, nanos = 500_000_000 }`表示。</span><span class="sxs-lookup"><span data-stu-id="48b5c-168">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="48b5c-169">這就是為什麼此範例中的 `nanos` 欄位使用 `sfixed32` 型別，比起 `int32` 較大的值更有效率。</span><span class="sxs-lookup"><span data-stu-id="48b5c-169">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="48b5c-170">如果 [`units`] 欄位是負數，[`nanos`] 欄位也應該是負值。</span><span class="sxs-lookup"><span data-stu-id="48b5c-170">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="48b5c-171">有多個其他演算法可將 `decimal` 值編碼為位元組字串，但這則訊息比任何一個更容易瞭解。</span><span class="sxs-lookup"><span data-stu-id="48b5c-171">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="48b5c-172">在不同平臺上，值不會受到 endian 的影響。</span><span class="sxs-lookup"><span data-stu-id="48b5c-172">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="48b5c-173">此類型與 BCL `decimal` 類型之間的轉換可能會在中C#執行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="48b5c-173">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="48b5c-174">每當您使用這類的自訂訊息類型時，您*必須*使用 `.proto`中的批註來記錄它們。</span><span class="sxs-lookup"><span data-stu-id="48b5c-174">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="48b5c-175">然後，其他開發人員可以在自己的語言或架構中，執行對等類型的轉換。</span><span class="sxs-lookup"><span data-stu-id="48b5c-175">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="48b5c-176">[上一頁](protobuf-messages.md)
>[下一頁](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="48b5c-176">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
