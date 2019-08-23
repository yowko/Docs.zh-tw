---
title: System.web 中的 DateTime 和 DateTimeOffset 支援
description: 概述 system.string 程式庫中的 DateTime 和 DateTimeOffset 類型的支援方式。
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
ms.openlocfilehash: 182694a3d2df02d5e2c709e33a02bd9fa7d20383
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69973212"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a><span data-ttu-id="a5a7e-103">System.web 中的 DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="a5a7e-103">DateTime and DateTimeOffset support in System.Text.Json</span></span>

<span data-ttu-id="a5a7e-104">根據 ISO 8601:-2019 擴充設定檔, system.object 程式庫<xref:System.DateTime>會<xref:System.DateTimeOffset>剖析和寫入值。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-104">The System.Text.Json library parses and writes <xref:System.DateTime> and <xref:System.DateTimeOffset> values according to the ISO 8601:-2019 extended profile.</span></span>
<span data-ttu-id="a5a7e-105">[轉換器](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0)提供使用<xref:System.Text.Json.JsonSerializer>進行序列化和還原序列化的自訂支援。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-105">[Converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) provide custom support for serializing and deserializing with <xref:System.Text.Json.JsonSerializer>.</span></span>

## <a name="support-for-the-iso-8601-12019-format"></a><span data-ttu-id="a5a7e-106">支援 ISO 8601-1:2019 格式</span><span class="sxs-lookup"><span data-stu-id="a5a7e-106">Support for the ISO 8601-1:2019 format</span></span>

<span data-ttu-id="a5a7e-107"><xref:System.Text.Json.JsonSerializer> <xref:System.DateTimeOffset> 、 <xref:System.DateTime> 、和類型<xref:System.Text.Json.JsonElement>會根據 ISO 8601-1:2019 格式的延伸設定檔來剖析和寫入和文字標記法, 例如 2019-07-26T16 <xref:System.Text.Json.Utf8JsonWriter> <xref:System.Text.Json.Utf8JsonReader>: 59:57-05:00。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-107">The <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>, and <xref:System.Text.Json.JsonElement> types parse and write <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations according to the extended profile of the ISO 8601-1:2019 format; for example, 2019-07-26T16:59:57-05:00.</span></span>

<span data-ttu-id="a5a7e-108"><xref:System.DateTime>和<xref:System.DateTimeOffset>資料可以使用<xref:System.Text.Json.JsonSerializer>進行序列化:</span><span class="sxs-lookup"><span data-stu-id="a5a7e-108"><xref:System.DateTime> and <xref:System.DateTimeOffset> data can be serialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/serializing-with-jsonserializer.cs)]

<span data-ttu-id="a5a7e-109">它們也可以使用<xref:System.Text.Json.JsonSerializer>還原序列化:</span><span class="sxs-lookup"><span data-stu-id="a5a7e-109">They can also be deserialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-valid.cs)]

<span data-ttu-id="a5a7e-110">使用預設選項時, <xref:System.DateTime>輸入<xref:System.DateTimeOffset>和文字標記法必須符合擴充 ISO 8601-1:2019 設定檔。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-110">With default options, input <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations must conform to the extended ISO 8601-1:2019 profile.</span></span>
<span data-ttu-id="a5a7e-111">嘗試還原序列化不符合設定檔的標記法會導致<xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonException>擲回:</span><span class="sxs-lookup"><span data-stu-id="a5a7e-111">Attempting to deserialize representations that don't conform to the profile will cause <xref:System.Text.Json.JsonSerializer> to throw a <xref:System.Text.Json.JsonException>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-error.cs)]

<span data-ttu-id="a5a7e-112">提供 JSON 裝載內容的結構化存取, 包括<xref:System.DateTime>和<xref:System.DateTimeOffset>標記法。 <xref:System.Text.Json.JsonDocument></span><span class="sxs-lookup"><span data-stu-id="a5a7e-112">The <xref:System.Text.Json.JsonDocument> provides structured access to the contents of a JSON payload, including <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span> <span data-ttu-id="a5a7e-113">下列範例顯示如何在指定溫度的集合時, 可以計算星期一的平均溫度:</span><span class="sxs-lookup"><span data-stu-id="a5a7e-113">The example below shows how, when given a collection of temperatures, the average temperature on Mondays can be calculated:</span></span>

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-valid.cs)]

<span data-ttu-id="a5a7e-114">嘗試計算出具有不符合規範<xref:System.DateTime>之承載的平均溫度, 會導致<xref:System.Text.Json.JsonDocument>擲<xref:System.FormatException>回:</span><span class="sxs-lookup"><span data-stu-id="a5a7e-114">Attempting to compute the average temperature given a payload with non-compliant <xref:System.DateTime> representations will cause <xref:System.Text.Json.JsonDocument> to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-error.cs)]

<span data-ttu-id="a5a7e-115">較低層<xref:System.Text.Json.Utf8JsonWriter>級<xref:System.DateTime>的<xref:System.DateTimeOffset>寫入和資料:</span><span class="sxs-lookup"><span data-stu-id="a5a7e-115">The lower level <xref:System.Text.Json.Utf8JsonWriter> writes <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/writing-with-utf8jsonwriter.cs)]

<span data-ttu-id="a5a7e-116"><xref:System.Text.Json.Utf8JsonReader>剖析<xref:System.DateTime> 和<xref:System.DateTimeOffset>資料:</span><span class="sxs-lookup"><span data-stu-id="a5a7e-116"><xref:System.Text.Json.Utf8JsonReader> parses <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-valid.cs)]

<span data-ttu-id="a5a7e-117">嘗試使用<xref:System.Text.Json.Utf8JsonReader>讀取不相容的格式會導致它<xref:System.FormatException>擲回:</span><span class="sxs-lookup"><span data-stu-id="a5a7e-117">Attempting to read non-compliant formats with <xref:System.Text.Json.Utf8JsonReader> will cause it to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-error.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset-in-xrefsystemtextjsonjsonserializer"></a><span data-ttu-id="a5a7e-118"><xref:System.DateTime> 和<xref:System.DateTimeOffset>中的自訂支援<xref:System.Text.Json.JsonSerializer></span><span class="sxs-lookup"><span data-stu-id="a5a7e-118">Custom support for <xref:System.DateTime> and <xref:System.DateTimeOffset> in <xref:System.Text.Json.JsonSerializer></span></span>

<span data-ttu-id="a5a7e-119">如果您想要序列化程式執行自訂剖析或格式設定, 您可以實作為[自訂轉換器](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0)。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-119">If you want the serializer to perform custom parsing or formatting, you can implement [custom converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).</span></span>
<span data-ttu-id="a5a7e-120">以下是一些範例：</span><span class="sxs-lookup"><span data-stu-id="a5a7e-120">Here are a few examples:</span></span>

### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a><span data-ttu-id="a5a7e-121">使用`DateTime(Offset).Parse`和`DateTime(Offset).ToString`</span><span class="sxs-lookup"><span data-stu-id="a5a7e-121">Using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`</span></span>

<span data-ttu-id="a5a7e-122">如果您無法判斷輸入<xref:System.DateTime>或<xref:System.DateTimeOffset>文字標記法的格式`DateTime(Offset).Parse` , 您可以在轉換子中使用方法讀取邏輯。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-122">If you can't determine the formats of your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations, you can use the `DateTime(Offset).Parse` method in your converter read logic.</span></span> <span data-ttu-id="a5a7e-123">這可讓您使用。NET 對於剖析各種<xref:System.DateTime>和<xref:System.DateTimeOffset>文字格式的廣泛支援, 包括非 iso 8601 字串和 ISO 8601 格式, 但不符合延伸的 iso 8601-1:2019 設定檔。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-123">This allows you to use .NET's extensive support for parsing various <xref:System.DateTime> and <xref:System.DateTimeOffset> text formats, including non-ISO 8601 strings and ISO 8601 formats that don't conform to the extended ISO 8601-1:2019 profile.</span></span> <span data-ttu-id="a5a7e-124">相較于使用序列化程式的原生執行, 此方法的效能大幅降低。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-124">This approach is significantly less performant than using the serializer's native implementation.</span></span>

<span data-ttu-id="a5a7e-125">若要進行序列化, 您可以`DateTime(Offset).ToString`在轉換器寫入邏輯中使用方法。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-125">For serializing, you can use the `DateTime(Offset).ToString` method in your converter write logic.</span></span> <span data-ttu-id="a5a7e-126">這可讓您使用<xref:System.DateTime>任何<xref:System.DateTimeOffset> [標準日期和時間格式](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), 以及[自訂日期和時間格式](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)來撰寫和值。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-126">This allows you to write <xref:System.DateTime> and <xref:System.DateTimeOffset> values using any of the [standard date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), and the [custom date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span></span>
<span data-ttu-id="a5a7e-127">相較于使用序列化程式的原生執行, 這也會大幅降低效能。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-127">This is also significantly less performant than using the serializer's native implementation.</span></span>

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <span data-ttu-id="a5a7e-128">在執行<xref:System.Text.Json.Serialization.JsonConverter%601> `T`時, 如果<xref:System.DateTime>是, `typeToConvert`則參數一律會`typeof(DateTime)`是。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-128">When implementing <xref:System.Text.Json.Serialization.JsonConverter%601>, and `T` is <xref:System.DateTime>, the `typeToConvert` parameter will always be `typeof(DateTime)`.</span></span>
<span data-ttu-id="a5a7e-129">參數適用于處理多型案例, 以及使用泛型以高效能`typeof(T)`的方式取得時。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-129">The parameter is useful for handling polymorphic cases and when using generics to get `typeof(T)` in a performant way.</span></span>

### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><span data-ttu-id="a5a7e-130">使用<xref:System.Buffers.Text.Utf8Parser>和<xref:System.Buffers.Text.Utf8Formatter></span><span class="sxs-lookup"><span data-stu-id="a5a7e-130">Using <xref:System.Buffers.Text.Utf8Parser> and <xref:System.Buffers.Text.Utf8Formatter></span></span>

<span data-ttu-id="a5a7e-131">如果您的輸入<xref:System.DateTime>或<xref:System.DateTimeOffset>文字標記法符合其中一個 "R"、"l"、"O" 或 "G"[標準日期和時間格式字串](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), 或者您想要, 您可以在轉換子邏輯中使用快速以 utf-8 為基礎的剖析和格式化方法。根據這些格式的其中一種來撰寫。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-131">You can use fast UTF-8-based parsing and formatting methods in your converter logic if your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations are compliant with one of the "R", "l", "O", or "G" [standard date and time format Strings](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), or you want to write according to one of these formats.</span></span> <span data-ttu-id="a5a7e-132">這比使用`DateTime(Offset).Parse`和`DateTime(Offset).ToString`更快。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-132">This is much faster than using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`.</span></span>

<span data-ttu-id="a5a7e-133">這個範例會顯示根據<xref:System.DateTime> ["R" 標準格式](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier)序列化和還原序列化值的自訂轉換器:</span><span class="sxs-lookup"><span data-stu-id="a5a7e-133">This example shows a custom converter that serializes and deserializes <xref:System.DateTime> values according to [the "R" standard format](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span></span>

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> <span data-ttu-id="a5a7e-134">"R" 標準格式的長度一律為29個字元。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-134">The "R" standard format will always be 29 characters long.</span></span>

### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a><span data-ttu-id="a5a7e-135">使用`DateTime(Offset).Parse`做為序列化程式的原生剖析</span><span class="sxs-lookup"><span data-stu-id="a5a7e-135">Using `DateTime(Offset).Parse` as a fallback to the serializer's native parsing</span></span>

<span data-ttu-id="a5a7e-136">如果您通常會預期輸入<xref:System.DateTime>或<xref:System.DateTimeOffset>資料必須符合擴充 ISO 8601-1:2019 設定檔, 您可以使用序列化程式的原生剖析邏輯。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-136">If you generally expect your input <xref:System.DateTime> or <xref:System.DateTimeOffset> data to conform to the extended ISO 8601-1:2019 profile, you can use the serializer's native parsing logic.</span></span> <span data-ttu-id="a5a7e-137">您也可以只在案例中執行回溯機制。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-137">You can also implement a fallback mechanism just in case.</span></span>
<span data-ttu-id="a5a7e-138">這個範例顯示, 在無法使用<xref:System.DateTime> <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>剖析文字標記法之後, 轉換器會使用<xref:System.DateTime.Parse(System.String)>成功地剖析資料。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-138">This example shows that, after failing to parse a <xref:System.DateTime> text representation using <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, the converter successfully parses the data using <xref:System.DateTime.Parse(System.String)>.</span></span>

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example3/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a><span data-ttu-id="a5a7e-139">在 system.string 中的延伸 ISO 8601-1:2019 設定檔</span><span class="sxs-lookup"><span data-stu-id="a5a7e-139">The extended ISO 8601-1:2019 profile in System.Text.Json</span></span>

### <a name="date-and-time-components"></a><span data-ttu-id="a5a7e-140">日期和時間元件</span><span class="sxs-lookup"><span data-stu-id="a5a7e-140">Date and time components</span></span>

<span data-ttu-id="a5a7e-141">在中<xref:System.Text.Json>執行的延伸 ISO 8601-1:2019 設定檔會定義下列日期和時程表示的元件。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-141">The extended ISO 8601-1:2019 profile implemented in <xref:System.Text.Json> defines the following components for date and time representations.</span></span> <span data-ttu-id="a5a7e-142">這些元件是用來定義剖析和格式化<xref:System.DateTime>和<xref:System.DateTimeOffset>標記法時, 所支援的各種資料細微性層級。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-142">These components are used to define various levels of granularity supported when parsing and formatting <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span>

| <span data-ttu-id="a5a7e-143">元件</span><span class="sxs-lookup"><span data-stu-id="a5a7e-143">Component</span></span>       | <span data-ttu-id="a5a7e-144">格式</span><span class="sxs-lookup"><span data-stu-id="a5a7e-144">Format</span></span>                      | <span data-ttu-id="a5a7e-145">說明</span><span class="sxs-lookup"><span data-stu-id="a5a7e-145">Description</span></span>                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| <span data-ttu-id="a5a7e-146">Year</span><span class="sxs-lookup"><span data-stu-id="a5a7e-146">Year</span></span>            | <span data-ttu-id="a5a7e-147">"yyyy"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-147">"yyyy"</span></span>                      | <span data-ttu-id="a5a7e-148">0001-9999</span><span class="sxs-lookup"><span data-stu-id="a5a7e-148">0001-9999</span></span>                                                                       |
| <span data-ttu-id="a5a7e-149">Month</span><span class="sxs-lookup"><span data-stu-id="a5a7e-149">Month</span></span>           | <span data-ttu-id="a5a7e-150">"MM"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-150">"MM"</span></span>                        | <span data-ttu-id="a5a7e-151">01-12</span><span class="sxs-lookup"><span data-stu-id="a5a7e-151">01-12</span></span>                                                                           |
| <span data-ttu-id="a5a7e-152">Day</span><span class="sxs-lookup"><span data-stu-id="a5a7e-152">Day</span></span>             | <span data-ttu-id="a5a7e-153">"dd"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-153">"dd"</span></span>                        | <span data-ttu-id="a5a7e-154">01-28、01-29、01-30、01-31 (以月/年為基礎)</span><span class="sxs-lookup"><span data-stu-id="a5a7e-154">01-28, 01-29, 01-30, 01-31 based on month/year</span></span>                                  |
| <span data-ttu-id="a5a7e-155">Hour</span><span class="sxs-lookup"><span data-stu-id="a5a7e-155">Hour</span></span>            | <span data-ttu-id="a5a7e-156">"HH"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-156">"HH"</span></span>                        | <span data-ttu-id="a5a7e-157">00-23</span><span class="sxs-lookup"><span data-stu-id="a5a7e-157">00-23</span></span>                                                                           |
| <span data-ttu-id="a5a7e-158">Minute</span><span class="sxs-lookup"><span data-stu-id="a5a7e-158">Minute</span></span>          | <span data-ttu-id="a5a7e-159">"mm"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-159">"mm"</span></span>                        | <span data-ttu-id="a5a7e-160">00-59</span><span class="sxs-lookup"><span data-stu-id="a5a7e-160">00-59</span></span>                                                                           |
| <span data-ttu-id="a5a7e-161">第二個</span><span class="sxs-lookup"><span data-stu-id="a5a7e-161">Second</span></span>          | <span data-ttu-id="a5a7e-162">"ss"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-162">"ss"</span></span>                        | <span data-ttu-id="a5a7e-163">00-59</span><span class="sxs-lookup"><span data-stu-id="a5a7e-163">00-59</span></span>                                                                           |
| <span data-ttu-id="a5a7e-164">第二個分數</span><span class="sxs-lookup"><span data-stu-id="a5a7e-164">Second fraction</span></span> | <span data-ttu-id="a5a7e-165">"FFFFFFF"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-165">"FFFFFFF"</span></span>                   | <span data-ttu-id="a5a7e-166">最少一個數位, 最多16位數</span><span class="sxs-lookup"><span data-stu-id="a5a7e-166">Minimum of one digit, maximum of 16 digits</span></span>                                      |
| <span data-ttu-id="a5a7e-167">時間位移</span><span class="sxs-lookup"><span data-stu-id="a5a7e-167">Time offset</span></span>     | <span data-ttu-id="a5a7e-168">"K"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-168">"K"</span></span>                         | <span data-ttu-id="a5a7e-169">"Z" 或 "(' + '/'-') HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-169">Either "Z" or "('+'/'-')HH':'mm"</span></span>                                                |
| <span data-ttu-id="a5a7e-170">部分時間</span><span class="sxs-lookup"><span data-stu-id="a5a7e-170">Partial time</span></span>    | <span data-ttu-id="a5a7e-171">"HH ': ' mm ': ' ss [FFFFFFF]"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-171">"HH':'mm':'ss[FFFFFFF]"</span></span>     | <span data-ttu-id="a5a7e-172">沒有 UTC 時差的時間資訊</span><span class="sxs-lookup"><span data-stu-id="a5a7e-172">Time without UTC offset information</span></span>                                             |
| <span data-ttu-id="a5a7e-173">完整日期</span><span class="sxs-lookup"><span data-stu-id="a5a7e-173">Full date</span></span>       | <span data-ttu-id="a5a7e-174">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-'dd"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-174">"yyyy'-'MM'-'dd"</span></span>            | <span data-ttu-id="a5a7e-175">行事曆日期</span><span class="sxs-lookup"><span data-stu-id="a5a7e-175">Calendar date</span></span>                                                                   |
| <span data-ttu-id="a5a7e-176">完整時間</span><span class="sxs-lookup"><span data-stu-id="a5a7e-176">Full time</span></span>       | <span data-ttu-id="a5a7e-177">「部分 time'K」</span><span class="sxs-lookup"><span data-stu-id="a5a7e-177">"'Partial time'K"</span></span>           | <span data-ttu-id="a5a7e-178">在當地時間與 UTC 之間時間位移的日或本地時間 UTC</span><span class="sxs-lookup"><span data-stu-id="a5a7e-178">UTC of day or Local time of day with the time offset between local time and UTC</span></span> |
| <span data-ttu-id="a5a7e-179">日期時間</span><span class="sxs-lookup"><span data-stu-id="a5a7e-179">Date time</span></span>       | <span data-ttu-id="a5a7e-180">「完整日期 ' 不是 '」完整時間 '」</span><span class="sxs-lookup"><span data-stu-id="a5a7e-180">"'Full date''T''Full time'"</span></span> | <span data-ttu-id="a5a7e-181">行事曆日期和時間, 例如 2019-07-26T16:59:57-05:00</span><span class="sxs-lookup"><span data-stu-id="a5a7e-181">Calendar date and time of day, e.g. 2019-07-26T16:59:57-05:00</span></span>                   |

### <a name="support-for-parsing"></a><span data-ttu-id="a5a7e-182">支援剖析</span><span class="sxs-lookup"><span data-stu-id="a5a7e-182">Support for parsing</span></span>

<span data-ttu-id="a5a7e-183">下列資料細微性層級是針對剖析而定義:</span><span class="sxs-lookup"><span data-stu-id="a5a7e-183">The following levels of granularity are defined for parsing:</span></span>

1. <span data-ttu-id="a5a7e-184">「完整日期」</span><span class="sxs-lookup"><span data-stu-id="a5a7e-184">'Full date'</span></span>
    1. <span data-ttu-id="a5a7e-185">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-'dd"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-185">"yyyy'-'MM'-'dd"</span></span>

2. <span data-ttu-id="a5a7e-186">「完整日期 ' 不是 ' ' 小時 ' ': ' ' 分鐘 '」</span><span class="sxs-lookup"><span data-stu-id="a5a7e-186">"'Full date''T''Hour'':''Minute'"</span></span>
    1. <span data-ttu-id="a5a7e-187">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' MM"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-187">"yyyy'-'MM'-'dd'T'HH':'mm"</span></span>

3. <span data-ttu-id="a5a7e-188">「完整日期 ' 不是」 ' 部分時間 '」</span><span class="sxs-lookup"><span data-stu-id="a5a7e-188">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="a5a7e-189">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' MM ': ' ss" (可[排序 ("s") 格式規範](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="a5a7e-189">"yyyy'-'MM'-'dd'T'HH':'mm':'ss" ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>
    2. <span data-ttu-id="a5a7e-190">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' MM ': ' ss '。 'FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="a5a7e-190">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

4. <span data-ttu-id="a5a7e-191">「完整日期 ' t ' ' 時間小時 ' ': ' ' 分鐘 ' ' 時間位移 '」</span><span class="sxs-lookup"><span data-stu-id="a5a7e-191">"'Full date''T''Time hour'':''Minute''Time offset'"</span></span>
    1. <span data-ttu-id="a5a7e-192">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' mmZ"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-192">"yyyy'-'MM'-'dd'T'HH':'mmZ"</span></span>
    2. <span data-ttu-id="a5a7e-193">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' mm (' + '/'-') HH ': ' mm"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-193">"yyyy'-'MM'-'dd'T'HH':'mm('+'/'-')HH':'mm"</span></span>

5. <span data-ttu-id="a5a7e-194">「日期時間」</span><span class="sxs-lookup"><span data-stu-id="a5a7e-194">'Date time'</span></span>
    1. <span data-ttu-id="a5a7e-195">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' MM ': ' ssZ"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-195">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>
    2. <span data-ttu-id="a5a7e-196">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' MM ': ' ss '。 'SS.FFFFFFFZ</span><span class="sxs-lookup"><span data-stu-id="a5a7e-196">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>
    3. <span data-ttu-id="a5a7e-197">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' MM ': ' ss (' + '/'-') HH ': ' MM"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-197">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>
    4. <span data-ttu-id="a5a7e-198">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' MM ': ' ss '。 'FFFFFFF (' + '/'-') HH ': ' mm "</span><span class="sxs-lookup"><span data-stu-id="a5a7e-198">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

<span data-ttu-id="a5a7e-199">如果秒數有小數, 則至少必須有一個數位。`2019-07-26T00:00:00.`不允許。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-199">If there are decimal fractions for seconds, there must be at least one digit; `2019-07-26T00:00:00.` is not allowed.</span></span>
<span data-ttu-id="a5a7e-200">雖然允許最多16個小數位數, 但只有前七個會經過剖析。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-200">While up to 16 fractional digits are allowed, only the first seven are parsed.</span></span> <span data-ttu-id="a5a7e-201">除了之外的任何專案都會被視為零。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-201">Anything beyond that is considered a zero.</span></span>
<span data-ttu-id="a5a7e-202">例如, `2019-07-26T00:00:00.1234567890`將會剖析為`2019-07-26T00:00:00.1234567`。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-202">For example, `2019-07-26T00:00:00.1234567890` will be parsed as if it is `2019-07-26T00:00:00.1234567`.</span></span>
<span data-ttu-id="a5a7e-203">這是為了與<xref:System.DateTime>實施保持相容, 這僅限於此解決方案。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-203">This is to stay compatible with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>

<span data-ttu-id="a5a7e-204">不支援閏秒。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-204">Leap seconds are not supported.</span></span>

### <a name="support-for-formatting"></a><span data-ttu-id="a5a7e-205">支援格式化</span><span class="sxs-lookup"><span data-stu-id="a5a7e-205">Support for formatting</span></span>

<span data-ttu-id="a5a7e-206">下列資料細微性層級是針對格式而定義的:</span><span class="sxs-lookup"><span data-stu-id="a5a7e-206">The following levels of granularity are defined for formatting:</span></span>

1. <span data-ttu-id="a5a7e-207">「完整日期 ' 不是」 ' 部分時間 '」</span><span class="sxs-lookup"><span data-stu-id="a5a7e-207">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="a5a7e-208">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' MM ': ' ss" (可[排序 ("s") 格式規範](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="a5a7e-208">"yyyy'-'MM'-'dd'T'HH':'mm':'ss"  ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>

        <span data-ttu-id="a5a7e-209">用來格式化不<xref:System.DateTime>含小數秒的, 且不含位移資訊。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-209">Used to format a <xref:System.DateTime> without fractional seconds and without offset information.</span></span>

    2. <span data-ttu-id="a5a7e-210">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' MM ': ' ss '。 'FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="a5a7e-210">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

        <span data-ttu-id="a5a7e-211">用來格式化<xref:System.DateTime> , 並以小數秒為單位, 但不含位移資訊。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-211">Used to format a <xref:System.DateTime> with fractional seconds but without offset information.</span></span>

2. <span data-ttu-id="a5a7e-212">「日期時間」</span><span class="sxs-lookup"><span data-stu-id="a5a7e-212">'Date time'</span></span>
    1. <span data-ttu-id="a5a7e-213">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' MM ': ' ssZ"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-213">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>

        <span data-ttu-id="a5a7e-214">用來格式化<xref:System.DateTime>或<xref:System.DateTimeOffset>不含小數秒數, 但使用 UTC 時差。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-214">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a UTC offset.</span></span>

    2. <span data-ttu-id="a5a7e-215">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' MM ': ' ss '。 'SS.FFFFFFFZ</span><span class="sxs-lookup"><span data-stu-id="a5a7e-215">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>

        <span data-ttu-id="a5a7e-216">用來格式化<xref:System.DateTime>或<xref:System.DateTimeOffset> (以毫秒為單位) 和 UTC 時差。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-216">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a UTC offset.</span></span>

    3. <span data-ttu-id="a5a7e-217">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' MM ': ' ss (' + '/'-') HH ': ' MM"</span><span class="sxs-lookup"><span data-stu-id="a5a7e-217">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="a5a7e-218">用來格式化<xref:System.DateTime>或<xref:System.DateTimeOffset>不含小數秒, 但具有區域位移。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-218">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a local offset.</span></span>

    4. <span data-ttu-id="a5a7e-219">"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh ': ' MM ': ' ss '。 'FFFFFFF (' + '/'-') HH ': ' mm "</span><span class="sxs-lookup"><span data-stu-id="a5a7e-219">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="a5a7e-220">用來格式化<xref:System.DateTime>或<xref:System.DateTimeOffset> (以小數秒為單位), 並使用本機位移。</span><span class="sxs-lookup"><span data-stu-id="a5a7e-220">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a local offset.</span></span>
