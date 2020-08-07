---
title: System.Text.Json 中的 DateTime 和 DateTimeOffset 支援
description: 概述 System.Text.Js的程式庫中如何支援 DateTime 和 DateTimeOffset 類型。
ms.technology: dotnet-standard
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 1c573712f458d3e22cd59112b9e79e85391270c1
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854889"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a><span data-ttu-id="2830e-103">System.Text.Json 中的 DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="2830e-103">DateTime and DateTimeOffset support in System.Text.Json</span></span>

<span data-ttu-id="2830e-104">程式庫上的 System.Text.Js會 <xref:System.DateTime> <xref:System.DateTimeOffset> 根據 ISO 8601:-2019 擴充設定檔來剖析和寫入值。</span><span class="sxs-lookup"><span data-stu-id="2830e-104">The System.Text.Json library parses and writes <xref:System.DateTime> and <xref:System.DateTimeOffset> values according to the ISO 8601:-2019 extended profile.</span></span>
<span data-ttu-id="2830e-105">[轉換器](xref:System.Text.Json.Serialization.JsonConverter%601)提供使用進行序列化和還原序列化的自訂支援 <xref:System.Text.Json.JsonSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="2830e-105">[Converters](xref:System.Text.Json.Serialization.JsonConverter%601) provide custom support for serializing and deserializing with <xref:System.Text.Json.JsonSerializer>.</span></span>
<span data-ttu-id="2830e-106">使用和時，也可以實作為自訂支援 <xref:System.Text.Json.Utf8JsonReader> <xref:System.Text.Json.Utf8JsonWriter> 。</span><span class="sxs-lookup"><span data-stu-id="2830e-106">Custom support can also be implemented when using <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter>.</span></span>

## <a name="support-for-the-iso-8601-12019-format"></a><span data-ttu-id="2830e-107">支援 ISO 8601-1:2019 格式</span><span class="sxs-lookup"><span data-stu-id="2830e-107">Support for the ISO 8601-1:2019 format</span></span>

<span data-ttu-id="2830e-108"><xref:System.Text.Json.JsonSerializer>、 <xref:System.Text.Json.Utf8JsonReader> 、 <xref:System.Text.Json.Utf8JsonWriter> 和類型會 <xref:System.Text.Json.JsonElement> <xref:System.DateTime> <xref:System.DateTimeOffset> 根據 ISO 8601-1:2019 格式的延伸設定檔來剖析和寫入和文字標記法，例如 2019-07-26T16：59： 57-05：00。</span><span class="sxs-lookup"><span data-stu-id="2830e-108">The <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>, and <xref:System.Text.Json.JsonElement> types parse and write <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations according to the extended profile of the ISO 8601-1:2019 format; for example, 2019-07-26T16:59:57-05:00.</span></span>

<span data-ttu-id="2830e-109"><xref:System.DateTime>和 <xref:System.DateTimeOffset> 資料可以使用進行序列化 <xref:System.Text.Json.JsonSerializer> ：</span><span class="sxs-lookup"><span data-stu-id="2830e-109"><xref:System.DateTime> and <xref:System.DateTimeOffset> data can be serialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

<span data-ttu-id="2830e-110">它們也可以使用還原序列化 <xref:System.Text.Json.JsonSerializer> ：</span><span class="sxs-lookup"><span data-stu-id="2830e-110">They can also be deserialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

<span data-ttu-id="2830e-111">使用預設選項時，輸入 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 文字標記法必須符合擴充 ISO 8601-1:2019 設定檔。</span><span class="sxs-lookup"><span data-stu-id="2830e-111">With default options, input <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations must conform to the extended ISO 8601-1:2019 profile.</span></span>
<span data-ttu-id="2830e-112">嘗試還原序列化不符合設定檔的標記法會導致 <xref:System.Text.Json.JsonSerializer> 擲回 <xref:System.Text.Json.JsonException> ：</span><span class="sxs-lookup"><span data-stu-id="2830e-112">Attempting to deserialize representations that don't conform to the profile will cause <xref:System.Text.Json.JsonSerializer> to throw a <xref:System.Text.Json.JsonException>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

<span data-ttu-id="2830e-113"><xref:System.Text.Json.JsonDocument>提供 JSON 裝載內容的結構化存取，包括 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 標記法。</span><span class="sxs-lookup"><span data-stu-id="2830e-113">The <xref:System.Text.Json.JsonDocument> provides structured access to the contents of a JSON payload, including <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span> <span data-ttu-id="2830e-114">下列範例顯示如何在指定溫度的集合時，可以計算星期一的平均溫度：</span><span class="sxs-lookup"><span data-stu-id="2830e-114">The example below shows how, when given a collection of temperatures, the average temperature on Mondays can be calculated:</span></span>

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

<span data-ttu-id="2830e-115">嘗試計算出具有不符合規範之承載的平均溫度， <xref:System.DateTime> 會導致 <xref:System.Text.Json.JsonDocument> 擲回 <xref:System.FormatException> ：</span><span class="sxs-lookup"><span data-stu-id="2830e-115">Attempting to compute the average temperature given a payload with non-compliant <xref:System.DateTime> representations will cause <xref:System.Text.Json.JsonDocument> to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

<span data-ttu-id="2830e-116">較低層級的 <xref:System.Text.Json.Utf8JsonWriter> 寫入 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 資料：</span><span class="sxs-lookup"><span data-stu-id="2830e-116">The lower level <xref:System.Text.Json.Utf8JsonWriter> writes <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<span data-ttu-id="2830e-117"><xref:System.Text.Json.Utf8JsonReader>剖析 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 資料：</span><span class="sxs-lookup"><span data-stu-id="2830e-117"><xref:System.Text.Json.Utf8JsonReader> parses <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

<span data-ttu-id="2830e-118">嘗試使用讀取不相容的格式 <xref:System.Text.Json.Utf8JsonReader> 會導致它擲回 <xref:System.FormatException> ：</span><span class="sxs-lookup"><span data-stu-id="2830e-118">Attempting to read non-compliant formats with <xref:System.Text.Json.Utf8JsonReader> will cause it to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a><span data-ttu-id="2830e-119">和的自訂支援 <xref:System.DateTime><xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="2830e-119">Custom support for <xref:System.DateTime> and <xref:System.DateTimeOffset></span></span>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a><span data-ttu-id="2830e-120">使用時<xref:System.Text.Json.JsonSerializer></span><span class="sxs-lookup"><span data-stu-id="2830e-120">When using <xref:System.Text.Json.JsonSerializer></span></span>

<span data-ttu-id="2830e-121">如果您想要序列化程式執行自訂剖析或格式設定，您可以實作為[自訂轉換器](xref:System.Text.Json.Serialization.JsonConverter%601)。</span><span class="sxs-lookup"><span data-stu-id="2830e-121">If you want the serializer to perform custom parsing or formatting, you can implement [custom converters](xref:System.Text.Json.Serialization.JsonConverter%601).</span></span>
<span data-ttu-id="2830e-122">以下是一些範例：</span><span class="sxs-lookup"><span data-stu-id="2830e-122">Here are a few examples:</span></span>

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a><span data-ttu-id="2830e-123">使用 `DateTime(Offset).Parse` 和`DateTime(Offset).ToString`</span><span class="sxs-lookup"><span data-stu-id="2830e-123">Using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`</span></span>

<span data-ttu-id="2830e-124">如果您無法判斷輸入 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 文字標記法的格式，您可以 `DateTime(Offset).Parse` 在轉換子中使用方法讀取邏輯。</span><span class="sxs-lookup"><span data-stu-id="2830e-124">If you can't determine the formats of your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations, you can use the `DateTime(Offset).Parse` method in your converter read logic.</span></span> <span data-ttu-id="2830e-125">這可讓您使用。NET 對於剖析各種 <xref:System.DateTime> 和文字格式的廣泛支援 <xref:System.DateTimeOffset> ，包括非 iso 8601 字串和 ISO 8601 格式，但不符合延伸的 iso 8601-1:2019 設定檔。</span><span class="sxs-lookup"><span data-stu-id="2830e-125">This allows you to use .NET's extensive support for parsing various <xref:System.DateTime> and <xref:System.DateTimeOffset> text formats, including non-ISO 8601 strings and ISO 8601 formats that don't conform to the extended ISO 8601-1:2019 profile.</span></span> <span data-ttu-id="2830e-126">相較于使用序列化程式的原生執行，此方法的效能大幅降低。</span><span class="sxs-lookup"><span data-stu-id="2830e-126">This approach is significantly less performant than using the serializer's native implementation.</span></span>

<span data-ttu-id="2830e-127">若要進行序列化，您可以 `DateTime(Offset).ToString` 在轉換器寫入邏輯中使用方法。</span><span class="sxs-lookup"><span data-stu-id="2830e-127">For serializing, you can use the `DateTime(Offset).ToString` method in your converter write logic.</span></span> <span data-ttu-id="2830e-128">這可讓您 <xref:System.DateTime> <xref:System.DateTimeOffset> 使用任何[標準日期和時間格式](../base-types/standard-date-and-time-format-strings.md)，以及[自訂日期和時間格式](../base-types/custom-date-and-time-format-strings.md)來撰寫和值。</span><span class="sxs-lookup"><span data-stu-id="2830e-128">This allows you to write <xref:System.DateTime> and <xref:System.DateTimeOffset> values using any of the [standard date and time formats](../base-types/standard-date-and-time-format-strings.md), and the [custom date and time formats](../base-types/custom-date-and-time-format-strings.md).</span></span>
<span data-ttu-id="2830e-129">相較于使用序列化程式的原生執行，這也會大幅降低效能。</span><span class="sxs-lookup"><span data-stu-id="2830e-129">This is also significantly less performant than using the serializer's native implementation.</span></span>

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <span data-ttu-id="2830e-130">在執行時 <xref:System.Text.Json.Serialization.JsonConverter%601> ，如果 `T` 是 <xref:System.DateTime> ，則 `typeToConvert` 參數一律會是 `typeof(DateTime)` 。</span><span class="sxs-lookup"><span data-stu-id="2830e-130">When implementing <xref:System.Text.Json.Serialization.JsonConverter%601>, and `T` is <xref:System.DateTime>, the `typeToConvert` parameter will always be `typeof(DateTime)`.</span></span>
<span data-ttu-id="2830e-131">參數適用于處理多型案例，以及使用泛型以高效能的方式取得時 `typeof(T)` 。</span><span class="sxs-lookup"><span data-stu-id="2830e-131">The parameter is useful for handling polymorphic cases and when using generics to get `typeof(T)` in a performant way.</span></span>

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><span data-ttu-id="2830e-132">使用 <xref:System.Buffers.Text.Utf8Parser> 和<xref:System.Buffers.Text.Utf8Formatter></span><span class="sxs-lookup"><span data-stu-id="2830e-132">Using <xref:System.Buffers.Text.Utf8Parser> and <xref:System.Buffers.Text.Utf8Formatter></span></span>

<span data-ttu-id="2830e-133">如果您的輸入 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 文字標記法符合其中一個 "R"、"l"、"O" 或 "G"[標準日期和時間格式字串](../base-types/standard-date-and-time-format-strings.md)，或者您想要根據其中一種格式來撰寫，則您可以在轉換器邏輯中使用快速以 utf-8 為基礎的剖析和格式化方法。</span><span class="sxs-lookup"><span data-stu-id="2830e-133">You can use fast UTF-8-based parsing and formatting methods in your converter logic if your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations are compliant with one of the "R", "l", "O", or "G" [standard date and time format strings](../base-types/standard-date-and-time-format-strings.md), or you want to write according to one of these formats.</span></span> <span data-ttu-id="2830e-134">這比使用和更快 `DateTime(Offset).Parse` `DateTime(Offset).ToString` 。</span><span class="sxs-lookup"><span data-stu-id="2830e-134">This is much faster than using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`.</span></span>

<span data-ttu-id="2830e-135">這個範例會顯示 <xref:System.DateTime> 根據["R" 標準格式](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier)序列化和還原序列化值的自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="2830e-135">This example shows a custom converter that serializes and deserializes <xref:System.DateTime> values according to [the "R" standard format](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier):</span></span>

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> <span data-ttu-id="2830e-136">"R" 標準格式的長度一律為29個字元。</span><span class="sxs-lookup"><span data-stu-id="2830e-136">The "R" standard format will always be 29 characters long.</span></span>
>
> <span data-ttu-id="2830e-137">"L" (小寫 "L" ) 格式不會與其他[標準日期和時間格式字串](../base-types/standard-date-and-time-format-strings.md)一起記載，因為只有 `Utf8Parser` 和類型才支援 `Utf8Formatter` 。</span><span class="sxs-lookup"><span data-stu-id="2830e-137">The "l" (lowercase "L") format is not documented with the other [standard date and time format strings](../base-types/standard-date-and-time-format-strings.md) because it is supported only by the `Utf8Parser` and `Utf8Formatter` types.</span></span> <span data-ttu-id="2830e-138">格式為小寫 RFC 1123 (小寫版本的 "R" 格式) ，例如： "thu，25七月 2019 06:36:07 gmt"。</span><span class="sxs-lookup"><span data-stu-id="2830e-138">The format is lowercase RFC 1123 (a lowercase version of the "R" format), for example: "thu, 25 jul 2019 06:36:07 gmt".</span></span>

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a><span data-ttu-id="2830e-139">使用 `DateTime(Offset).Parse` 做為序列化程式的原生剖析</span><span class="sxs-lookup"><span data-stu-id="2830e-139">Using `DateTime(Offset).Parse` as a fallback to the serializer's native parsing</span></span>

<span data-ttu-id="2830e-140">如果您通常會預期輸入 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 資料必須符合擴充 ISO 8601-1:2019 設定檔，您可以使用序列化程式的原生剖析邏輯。</span><span class="sxs-lookup"><span data-stu-id="2830e-140">If you generally expect your input <xref:System.DateTime> or <xref:System.DateTimeOffset> data to conform to the extended ISO 8601-1:2019 profile, you can use the serializer's native parsing logic.</span></span> <span data-ttu-id="2830e-141">您也可以只在案例中執行回溯機制。</span><span class="sxs-lookup"><span data-stu-id="2830e-141">You can also implement a fallback mechanism just in case.</span></span>
<span data-ttu-id="2830e-142">這個範例顯示，在無法 <xref:System.DateTime> 使用剖析文字標記法之後， <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)> 轉換器會使用成功地剖析資料 <xref:System.DateTime.Parse(System.String)> 。</span><span class="sxs-lookup"><span data-stu-id="2830e-142">This example shows that, after failing to parse a <xref:System.DateTime> text representation using <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, the converter successfully parses the data using <xref:System.DateTime.Parse(System.String)>.</span></span>

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a><span data-ttu-id="2830e-143">寫入時<xref:System.Text.Json.Utf8JsonWriter></span><span class="sxs-lookup"><span data-stu-id="2830e-143">When writing with <xref:System.Text.Json.Utf8JsonWriter></span></span>

<span data-ttu-id="2830e-144">如果您想要使用撰寫自訂 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 文字表示 <xref:System.Text.Json.Utf8JsonWriter> ，您可以將自訂表格示格式格式化為 <xref:System.String> 、 `ReadOnlySpan<Byte>` 、 `ReadOnlySpan<Char>` 或 <xref:System.Text.Json.JsonEncodedText> ，然後將它傳遞給對應的 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> 或 <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="2830e-144">If you want to write a custom <xref:System.DateTime> or <xref:System.DateTimeOffset> text representation with <xref:System.Text.Json.Utf8JsonWriter>, you can format your custom representation to a <xref:System.String>, `ReadOnlySpan<Byte>`, `ReadOnlySpan<Char>`, or <xref:System.Text.Json.JsonEncodedText>, then pass it to the corresponding <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> or <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="2830e-145">下列範例顯示如何 <xref:System.DateTime> 使用來建立自訂格式 <xref:System.DateTime.ToString(System.String,System.IFormatProvider)> ，然後使用 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> 方法撰寫：</span><span class="sxs-lookup"><span data-stu-id="2830e-145">The following example shows how a custom <xref:System.DateTime> format can be created with <xref:System.DateTime.ToString(System.String,System.IFormatProvider)>, then written with the <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> method:</span></span>

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a><span data-ttu-id="2830e-146">讀取時<xref:System.Text.Json.Utf8JsonReader></span><span class="sxs-lookup"><span data-stu-id="2830e-146">When reading with <xref:System.Text.Json.Utf8JsonReader></span></span>

<span data-ttu-id="2830e-147">如果您想要使用讀取自訂 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 文字表示 <xref:System.Text.Json.Utf8JsonReader> ，您可以使用來取得目前 JSON token 的值 <xref:System.String> <xref:System.Text.Json.Utf8JsonReader.GetString> ，然後使用自訂邏輯來剖析該值。</span><span class="sxs-lookup"><span data-stu-id="2830e-147">If you want to read a custom <xref:System.DateTime> or <xref:System.DateTimeOffset> text representation with <xref:System.Text.Json.Utf8JsonReader>, you can get the value of the current JSON token as a <xref:System.String> using <xref:System.Text.Json.Utf8JsonReader.GetString>, then parse the value using custom logic.</span></span>

<span data-ttu-id="2830e-148">下列範例顯示如何使用來抓取自訂 <xref:System.DateTimeOffset> 文字表示 <xref:System.Text.Json.Utf8JsonReader.GetString> ，然後使用進行剖析 <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)> ：</span><span class="sxs-lookup"><span data-stu-id="2830e-148">The following example shows how a custom <xref:System.DateTimeOffset> text representation can be retrieved using <xref:System.Text.Json.Utf8JsonReader.GetString>, then parsed using <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>:</span></span>

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a><span data-ttu-id="2830e-149">System.Text.Js中的擴充 ISO 8601-1:2019 設定檔</span><span class="sxs-lookup"><span data-stu-id="2830e-149">The extended ISO 8601-1:2019 profile in System.Text.Json</span></span>

### <a name="date-and-time-components"></a><span data-ttu-id="2830e-150">日期和時間元件</span><span class="sxs-lookup"><span data-stu-id="2830e-150">Date and time components</span></span>

<span data-ttu-id="2830e-151">在中執行的延伸 ISO 8601-1:2019 設定檔會 <xref:System.Text.Json> 定義下列日期和時程表示的元件。</span><span class="sxs-lookup"><span data-stu-id="2830e-151">The extended ISO 8601-1:2019 profile implemented in <xref:System.Text.Json> defines the following components for date and time representations.</span></span> <span data-ttu-id="2830e-152">這些元件是用來定義剖析和格式化 <xref:System.DateTime> 和標記法時，所支援的各種資料細微性層級 <xref:System.DateTimeOffset> 。</span><span class="sxs-lookup"><span data-stu-id="2830e-152">These components are used to define various levels of granularity supported when parsing and formatting <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span>

| <span data-ttu-id="2830e-153">元件</span><span class="sxs-lookup"><span data-stu-id="2830e-153">Component</span></span>       | <span data-ttu-id="2830e-154">格式</span><span class="sxs-lookup"><span data-stu-id="2830e-154">Format</span></span>                      | <span data-ttu-id="2830e-155">描述</span><span class="sxs-lookup"><span data-stu-id="2830e-155">Description</span></span>                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| <span data-ttu-id="2830e-156">Year</span><span class="sxs-lookup"><span data-stu-id="2830e-156">Year</span></span>            | <span data-ttu-id="2830e-157">"yyyy"</span><span class="sxs-lookup"><span data-stu-id="2830e-157">"yyyy"</span></span>                      | <span data-ttu-id="2830e-158">0001-9999</span><span class="sxs-lookup"><span data-stu-id="2830e-158">0001-9999</span></span>                                                                       |
| <span data-ttu-id="2830e-159">Month</span><span class="sxs-lookup"><span data-stu-id="2830e-159">Month</span></span>           | <span data-ttu-id="2830e-160">"MM"</span><span class="sxs-lookup"><span data-stu-id="2830e-160">"MM"</span></span>                        | <span data-ttu-id="2830e-161">01-12</span><span class="sxs-lookup"><span data-stu-id="2830e-161">01-12</span></span>                                                                           |
| <span data-ttu-id="2830e-162">天</span><span class="sxs-lookup"><span data-stu-id="2830e-162">Day</span></span>             | <span data-ttu-id="2830e-163">"dd"</span><span class="sxs-lookup"><span data-stu-id="2830e-163">"dd"</span></span>                        | <span data-ttu-id="2830e-164">01-28、01-29、01-30、01-31 （以月/年為基礎）</span><span class="sxs-lookup"><span data-stu-id="2830e-164">01-28, 01-29, 01-30, 01-31 based on month/year</span></span>                                  |
| <span data-ttu-id="2830e-165">小時</span><span class="sxs-lookup"><span data-stu-id="2830e-165">Hour</span></span>            | <span data-ttu-id="2830e-166">"HH"</span><span class="sxs-lookup"><span data-stu-id="2830e-166">"HH"</span></span>                        | <span data-ttu-id="2830e-167">00-23</span><span class="sxs-lookup"><span data-stu-id="2830e-167">00-23</span></span>                                                                           |
| <span data-ttu-id="2830e-168">Minute</span><span class="sxs-lookup"><span data-stu-id="2830e-168">Minute</span></span>          | <span data-ttu-id="2830e-169">"mm"</span><span class="sxs-lookup"><span data-stu-id="2830e-169">"mm"</span></span>                        | <span data-ttu-id="2830e-170">00-59</span><span class="sxs-lookup"><span data-stu-id="2830e-170">00-59</span></span>                                                                           |
| <span data-ttu-id="2830e-171">Second</span><span class="sxs-lookup"><span data-stu-id="2830e-171">Second</span></span>          | <span data-ttu-id="2830e-172">"ss"</span><span class="sxs-lookup"><span data-stu-id="2830e-172">"ss"</span></span>                        | <span data-ttu-id="2830e-173">00-59</span><span class="sxs-lookup"><span data-stu-id="2830e-173">00-59</span></span>                                                                           |
| <span data-ttu-id="2830e-174">第二個分數</span><span class="sxs-lookup"><span data-stu-id="2830e-174">Second fraction</span></span> | <span data-ttu-id="2830e-175">"FFFFFFF"</span><span class="sxs-lookup"><span data-stu-id="2830e-175">"FFFFFFF"</span></span>                   | <span data-ttu-id="2830e-176">最少一個數位，最多16位數</span><span class="sxs-lookup"><span data-stu-id="2830e-176">Minimum of one digit, maximum of 16 digits</span></span>                                      |
| <span data-ttu-id="2830e-177">時間位移</span><span class="sxs-lookup"><span data-stu-id="2830e-177">Time offset</span></span>     | <span data-ttu-id="2830e-178">"K"</span><span class="sxs-lookup"><span data-stu-id="2830e-178">"K"</span></span>                         | <span data-ttu-id="2830e-179">"Z" 或 " ( ' + '/'-' ) HH '： ' mm"</span><span class="sxs-lookup"><span data-stu-id="2830e-179">Either "Z" or "('+'/'-')HH':'mm"</span></span>                                                |
| <span data-ttu-id="2830e-180">部分時間</span><span class="sxs-lookup"><span data-stu-id="2830e-180">Partial time</span></span>    | <span data-ttu-id="2830e-181">"HH '： ' mm '： ' ss [FFFFFFF]"</span><span class="sxs-lookup"><span data-stu-id="2830e-181">"HH':'mm':'ss[FFFFFFF]"</span></span>     | <span data-ttu-id="2830e-182">沒有 UTC 時差的時間資訊</span><span class="sxs-lookup"><span data-stu-id="2830e-182">Time without UTC offset information</span></span>                                             |
| <span data-ttu-id="2830e-183">完整日期</span><span class="sxs-lookup"><span data-stu-id="2830e-183">Full date</span></span>       | <span data-ttu-id="2830e-184">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-'dd"</span><span class="sxs-lookup"><span data-stu-id="2830e-184">"yyyy'-'MM'-'dd"</span></span>            | <span data-ttu-id="2830e-185">行事曆日期</span><span class="sxs-lookup"><span data-stu-id="2830e-185">Calendar date</span></span>                                                                   |
| <span data-ttu-id="2830e-186">完整時間</span><span class="sxs-lookup"><span data-stu-id="2830e-186">Full time</span></span>       | <span data-ttu-id="2830e-187">「部分 time'K」</span><span class="sxs-lookup"><span data-stu-id="2830e-187">"'Partial time'K"</span></span>           | <span data-ttu-id="2830e-188">在當地時間與 UTC 之間時間位移的日或本地時間 UTC</span><span class="sxs-lookup"><span data-stu-id="2830e-188">UTC of day or Local time of day with the time offset between local time and UTC</span></span> |
| <span data-ttu-id="2830e-189">日期時間</span><span class="sxs-lookup"><span data-stu-id="2830e-189">Date time</span></span>       | <span data-ttu-id="2830e-190">「完整日期 ' 不是 '」完整時間 '」</span><span class="sxs-lookup"><span data-stu-id="2830e-190">"'Full date''T''Full time'"</span></span> | <span data-ttu-id="2830e-191">行事曆日期和時間，例如 2019-07-26T16：59： 57-05：00</span><span class="sxs-lookup"><span data-stu-id="2830e-191">Calendar date and time of day, e.g. 2019-07-26T16:59:57-05:00</span></span>                   |

### <a name="support-for-parsing"></a><span data-ttu-id="2830e-192">支援剖析</span><span class="sxs-lookup"><span data-stu-id="2830e-192">Support for parsing</span></span>

<span data-ttu-id="2830e-193">下列資料細微性層級是針對剖析而定義：</span><span class="sxs-lookup"><span data-stu-id="2830e-193">The following levels of granularity are defined for parsing:</span></span>

1. <span data-ttu-id="2830e-194">「完整日期」</span><span class="sxs-lookup"><span data-stu-id="2830e-194">'Full date'</span></span>
    1. <span data-ttu-id="2830e-195">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-'dd"</span><span class="sxs-lookup"><span data-stu-id="2830e-195">"yyyy'-'MM'-'dd"</span></span>

2. <span data-ttu-id="2830e-196">「完整日期 ' 不是 ' ' 小時 ' '： ' ' 分鐘 '」</span><span class="sxs-lookup"><span data-stu-id="2830e-196">"'Full date''T''Hour'':''Minute'"</span></span>
    1. <span data-ttu-id="2830e-197">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM"</span><span class="sxs-lookup"><span data-stu-id="2830e-197">"yyyy'-'MM'-'dd'T'HH':'mm"</span></span>

3. <span data-ttu-id="2830e-198">「完整日期 ' 不是」 ' 部分時間 '」</span><span class="sxs-lookup"><span data-stu-id="2830e-198">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="2830e-199">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss" (可[排序的 ( "s" ) 格式規範](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier)) </span><span class="sxs-lookup"><span data-stu-id="2830e-199">"yyyy'-'MM'-'dd'T'HH':'mm':'ss" ([The Sortable ("s") Format Specifier](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))</span></span>
    2. <span data-ttu-id="2830e-200">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。 'FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="2830e-200">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

4. <span data-ttu-id="2830e-201">「完整日期 ' t ' ' 時間小時 ' '： ' ' 分鐘 ' ' 時間位移 '」</span><span class="sxs-lookup"><span data-stu-id="2830e-201">"'Full date''T''Time hour'':''Minute''Time offset'"</span></span>
    1. <span data-ttu-id="2830e-202">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' mmZ"</span><span class="sxs-lookup"><span data-stu-id="2830e-202">"yyyy'-'MM'-'dd'T'HH':'mmZ"</span></span>
    2. <span data-ttu-id="2830e-203">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' mm ( ' + '/'-' ) HH '： ' mm"</span><span class="sxs-lookup"><span data-stu-id="2830e-203">"yyyy'-'MM'-'dd'T'HH':'mm('+'/'-')HH':'mm"</span></span>

5. <span data-ttu-id="2830e-204">「日期時間」</span><span class="sxs-lookup"><span data-stu-id="2830e-204">'Date time'</span></span>
    1. <span data-ttu-id="2830e-205">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ssZ"</span><span class="sxs-lookup"><span data-stu-id="2830e-205">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>
    2. <span data-ttu-id="2830e-206">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。 'SS.FFFFFFFZ</span><span class="sxs-lookup"><span data-stu-id="2830e-206">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>
    3. <span data-ttu-id="2830e-207">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' mm '： ' ss ( ' + '/'-' ) HH '： ' MM"</span><span class="sxs-lookup"><span data-stu-id="2830e-207">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>
    4. <span data-ttu-id="2830e-208">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。 'FFFFFFF ( ' + '/'-' ) HH '： ' mm "</span><span class="sxs-lookup"><span data-stu-id="2830e-208">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

<span data-ttu-id="2830e-209">如果秒數有小數，則至少必須有一個數位。`2019-07-26T00:00:00.`不允許。</span><span class="sxs-lookup"><span data-stu-id="2830e-209">If there are decimal fractions for seconds, there must be at least one digit; `2019-07-26T00:00:00.` is not allowed.</span></span>
<span data-ttu-id="2830e-210">雖然允許最多16個小數位數，但只有前七個會經過剖析。</span><span class="sxs-lookup"><span data-stu-id="2830e-210">While up to 16 fractional digits are allowed, only the first seven are parsed.</span></span> <span data-ttu-id="2830e-211">除了之外的任何專案都會被視為零。</span><span class="sxs-lookup"><span data-stu-id="2830e-211">Anything beyond that is considered a zero.</span></span>
<span data-ttu-id="2830e-212">例如，將會剖析 `2019-07-26T00:00:00.1234567890` 為 `2019-07-26T00:00:00.1234567` 。</span><span class="sxs-lookup"><span data-stu-id="2830e-212">For example, `2019-07-26T00:00:00.1234567890` will be parsed as if it is `2019-07-26T00:00:00.1234567`.</span></span>
<span data-ttu-id="2830e-213">這是為了與實施保持相容 <xref:System.DateTime> ，這僅限於此解決方案。</span><span class="sxs-lookup"><span data-stu-id="2830e-213">This is to stay compatible with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>

<span data-ttu-id="2830e-214">不支援閏秒。</span><span class="sxs-lookup"><span data-stu-id="2830e-214">Leap seconds are not supported.</span></span>

### <a name="support-for-formatting"></a><span data-ttu-id="2830e-215">支援格式化</span><span class="sxs-lookup"><span data-stu-id="2830e-215">Support for formatting</span></span>

<span data-ttu-id="2830e-216">下列資料細微性層級是針對格式而定義的：</span><span class="sxs-lookup"><span data-stu-id="2830e-216">The following levels of granularity are defined for formatting:</span></span>

1. <span data-ttu-id="2830e-217">「完整日期 ' 不是」 ' 部分時間 '」</span><span class="sxs-lookup"><span data-stu-id="2830e-217">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="2830e-218">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss" (可[排序的 ( "s" ) 格式規範](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier)) </span><span class="sxs-lookup"><span data-stu-id="2830e-218">"yyyy'-'MM'-'dd'T'HH':'mm':'ss"  ([The Sortable ("s") Format Specifier](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))</span></span>

        <span data-ttu-id="2830e-219">用來格式化 <xref:System.DateTime> 不含小數秒的，且不含位移資訊。</span><span class="sxs-lookup"><span data-stu-id="2830e-219">Used to format a <xref:System.DateTime> without fractional seconds and without offset information.</span></span>

    2. <span data-ttu-id="2830e-220">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。 'FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="2830e-220">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

        <span data-ttu-id="2830e-221">用來格式化 <xref:System.DateTime> ，並以小數秒為單位，但不含位移資訊。</span><span class="sxs-lookup"><span data-stu-id="2830e-221">Used to format a <xref:System.DateTime> with fractional seconds but without offset information.</span></span>

2. <span data-ttu-id="2830e-222">「日期時間」</span><span class="sxs-lookup"><span data-stu-id="2830e-222">'Date time'</span></span>
    1. <span data-ttu-id="2830e-223">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ssZ"</span><span class="sxs-lookup"><span data-stu-id="2830e-223">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>

        <span data-ttu-id="2830e-224">用來格式化 <xref:System.DateTime> 不含小數秒的，但使用 UTC 時差。</span><span class="sxs-lookup"><span data-stu-id="2830e-224">Used to format a <xref:System.DateTime> without fractional seconds but with a UTC offset.</span></span>

    2. <span data-ttu-id="2830e-225">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。 'SS.FFFFFFFZ</span><span class="sxs-lookup"><span data-stu-id="2830e-225">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>

        <span data-ttu-id="2830e-226">用來以 <xref:System.DateTime> 小數秒和 UTC 位移來格式化。</span><span class="sxs-lookup"><span data-stu-id="2830e-226">Used to format a <xref:System.DateTime> with fractional seconds and with a UTC offset.</span></span>

    3. <span data-ttu-id="2830e-227">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' mm '： ' ss ( ' + '/'-' ) HH '： ' MM"</span><span class="sxs-lookup"><span data-stu-id="2830e-227">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="2830e-228">用來格式化 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 不含小數秒，但具有區域位移。</span><span class="sxs-lookup"><span data-stu-id="2830e-228">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a local offset.</span></span>

    4. <span data-ttu-id="2830e-229">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '。 'FFFFFFF ( ' + '/'-' ) HH '： ' mm "</span><span class="sxs-lookup"><span data-stu-id="2830e-229">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="2830e-230">用來格式化 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> （以小數秒為單位），並使用本機位移。</span><span class="sxs-lookup"><span data-stu-id="2830e-230">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a local offset.</span></span>

<span data-ttu-id="2830e-231">如果或實例的[來回行程格式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier)表示 <xref:System.DateTime> <xref:System.DateTimeOffset> 在其小數秒的結尾為零，則 <xref:System.Text.Json.JsonSerializer> 和 <xref:System.Text.Json.Utf8JsonWriter> 會將實例的標記法格式化，而不會有尾端零。</span><span class="sxs-lookup"><span data-stu-id="2830e-231">If the [round-trip format](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) representation of a <xref:System.DateTime> or <xref:System.DateTimeOffset> instance has trailing zeros in its fractional seconds, then <xref:System.Text.Json.JsonSerializer> and <xref:System.Text.Json.Utf8JsonWriter> will format a representation of the instance without trailing zeros.</span></span>
<span data-ttu-id="2830e-232">例如，如果 <xref:System.DateTime> 實例的[來回格式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier)表示為，則的 `2019-04-24T14:50:17.1010000Z` 格式會是 `2019-04-24T14:50:17.101Z` <xref:System.Text.Json.JsonSerializer> 和 <xref:System.Text.Json.Utf8JsonWriter> 。</span><span class="sxs-lookup"><span data-stu-id="2830e-232">For example, a <xref:System.DateTime> instance whose [round-trip format](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) representation is `2019-04-24T14:50:17.1010000Z`, will be formatted as `2019-04-24T14:50:17.101Z` by <xref:System.Text.Json.JsonSerializer> and <xref:System.Text.Json.Utf8JsonWriter>.</span></span>

<span data-ttu-id="2830e-233">如果或實例的[來回行程格式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier)表示 <xref:System.DateTime> <xref:System.DateTimeOffset> 在其小數秒中全部為零，則 <xref:System.Text.Json.JsonSerializer> 和 <xref:System.Text.Json.Utf8JsonWriter> 會將實例的標記法格式化，而不含小數秒數。</span><span class="sxs-lookup"><span data-stu-id="2830e-233">If the [round-trip format](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) representation of a <xref:System.DateTime> or <xref:System.DateTimeOffset> instance has all zeros in its fractional seconds, then <xref:System.Text.Json.JsonSerializer> and <xref:System.Text.Json.Utf8JsonWriter> will format a representation of the instance without fractional seconds.</span></span>
<span data-ttu-id="2830e-234">例如，如果 <xref:System.DateTime> 實例的[來回格式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier)表示為，則的 `2019-04-24T14:50:17.0000000+02:00` 格式會是 `2019-04-24T14:50:17+02:00` <xref:System.Text.Json.JsonSerializer> 和 <xref:System.Text.Json.Utf8JsonWriter> 。</span><span class="sxs-lookup"><span data-stu-id="2830e-234">For example, a <xref:System.DateTime> instance whose [round-trip format](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) representation is `2019-04-24T14:50:17.0000000+02:00`, will be formatted as `2019-04-24T14:50:17+02:00` by <xref:System.Text.Json.JsonSerializer> and <xref:System.Text.Json.Utf8JsonWriter>.</span></span>

<span data-ttu-id="2830e-235">以小數秒數來截斷零會允許最小的輸出，以便在要寫入的來回行程上保留資訊。</span><span class="sxs-lookup"><span data-stu-id="2830e-235">Truncating zeros in fractional-second digits allows the smallest output needed to preserve information on a round trip to be written.</span></span>

<span data-ttu-id="2830e-236">最多可寫入7個小數秒數位。</span><span class="sxs-lookup"><span data-stu-id="2830e-236">A maximum of 7 fractional-second digits are written.</span></span> <span data-ttu-id="2830e-237">這會與實作為配合 <xref:System.DateTime> ，僅限於此解析度。</span><span class="sxs-lookup"><span data-stu-id="2830e-237">This aligns with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>
