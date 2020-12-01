---
title: 如何使用自訂屬性名稱和值 System.Text.Json
description: 瞭解如何在使用 .NET 進行序列化時，自訂屬性名稱和值 System.Text.Json 。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 28f7d03ae9f794f6e5ea34a95082a059451daec6
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439930"
---
# <a name="how-to-customize-property-names-and-values-with-no-locsystemtextjson"></a><span data-ttu-id="8d174-103">如何使用自訂屬性名稱和值 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="8d174-103">How to customize property names and values with System.Text.Json</span></span>

<span data-ttu-id="8d174-104">根據預設，JSON 輸出中的屬性名稱和字典索引鍵不會變更，包括大小寫。</span><span class="sxs-lookup"><span data-stu-id="8d174-104">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="8d174-105">列舉值會以數位表示。</span><span class="sxs-lookup"><span data-stu-id="8d174-105">Enum values are represented as numbers.</span></span> <span data-ttu-id="8d174-106">在本文中，您將學會如何：</span><span class="sxs-lookup"><span data-stu-id="8d174-106">In this article, you'll learn how to:</span></span>

> [!NOTE]
> <span data-ttu-id="8d174-107">[Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)為 camel 大小寫。</span><span class="sxs-lookup"><span data-stu-id="8d174-107">The [web defaults](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is camel case.</span></span>

* [<span data-ttu-id="8d174-108">自訂個別的屬性名稱</span><span class="sxs-lookup"><span data-stu-id="8d174-108">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="8d174-109">將所有屬性名稱轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="8d174-109">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="8d174-110">執行自訂屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="8d174-110">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="8d174-111">將字典索引鍵轉換成 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="8d174-111">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="8d174-112">將列舉轉換為字串和 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="8d174-112">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="8d174-113">對於需要特殊處理 JSON 屬性名稱和值的其他情況，您可以 [執行自訂的轉換器](system-text-json-converters-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="8d174-113">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

## <a name="customize-individual-property-names"></a><span data-ttu-id="8d174-114">自訂個別的屬性名稱</span><span class="sxs-lookup"><span data-stu-id="8d174-114">Customize individual property names</span></span>

<span data-ttu-id="8d174-115">若要設定個別屬性的名稱，請使用 [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="8d174-115">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="8d174-116">以下是要序列化並產生 JSON 的範例類型：</span><span class="sxs-lookup"><span data-stu-id="8d174-116">Here's an example type to serialize and resulting JSON:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="8d174-117">這個屬性所設定的屬性名稱：</span><span class="sxs-lookup"><span data-stu-id="8d174-117">The property name set by this attribute:</span></span>

* <span data-ttu-id="8d174-118">適用于雙向的序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="8d174-118">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="8d174-119">優先于屬性命名原則。</span><span class="sxs-lookup"><span data-stu-id="8d174-119">Takes precedence over property naming policies.</span></span>

## <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="8d174-120">針對所有 JSON 屬性名稱使用 camel 大小寫</span><span class="sxs-lookup"><span data-stu-id="8d174-120">Use camel case for all JSON property names</span></span>

<span data-ttu-id="8d174-121">若要對所有 JSON 屬性名稱使用 camel 大小寫，請將設定 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 為 `JsonNamingPolicy.CamelCase` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d174-121">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs" id="Serialize":::

<span data-ttu-id="8d174-122">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="8d174-122">Here's an example class to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="8d174-123">Camel 案例屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="8d174-123">The camel case property naming policy:</span></span>

* <span data-ttu-id="8d174-124">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="8d174-124">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="8d174-125">由屬性覆寫 `[JsonPropertyName]` 。</span><span class="sxs-lookup"><span data-stu-id="8d174-125">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="8d174-126">這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不是 camel 大寫字母的原因。</span><span class="sxs-lookup"><span data-stu-id="8d174-126">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

## <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="8d174-127">使用自訂 JSON 屬性命名原則</span><span class="sxs-lookup"><span data-stu-id="8d174-127">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="8d174-128">若要使用自訂 JSON 屬性命名原則，請建立一個衍生自的類別， <xref:System.Text.Json.JsonNamingPolicy> 並覆寫 <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> 方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d174-128">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs":::

<span data-ttu-id="8d174-129">然後將 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 屬性設定為命名原則類別的實例：</span><span class="sxs-lookup"><span data-stu-id="8d174-129">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs" id="Serialize":::

<span data-ttu-id="8d174-130">以下是序列化和 JSON 輸出的範例類別：</span><span class="sxs-lookup"><span data-stu-id="8d174-130">Here's an example class to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="8d174-131">JSON 屬性命名原則：</span><span class="sxs-lookup"><span data-stu-id="8d174-131">The JSON property naming policy:</span></span>

* <span data-ttu-id="8d174-132">適用于序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="8d174-132">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="8d174-133">由屬性覆寫 `[JsonPropertyName]` 。</span><span class="sxs-lookup"><span data-stu-id="8d174-133">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="8d174-134">這就是為什麼範例中的 JSON 屬性名稱 `Wind` 不是大寫的原因。</span><span class="sxs-lookup"><span data-stu-id="8d174-134">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

## <a name="camel-case-dictionary-keys"></a><span data-ttu-id="8d174-135">Camel 案例字典索引鍵</span><span class="sxs-lookup"><span data-stu-id="8d174-135">Camel case dictionary keys</span></span>

<span data-ttu-id="8d174-136">如果要序列化之物件的屬性是型別 `Dictionary<string,TValue>` ，則 `string` 可以將索引鍵轉換成 camel 大小寫。</span><span class="sxs-lookup"><span data-stu-id="8d174-136">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="8d174-137">若要這樣做，請將設定 <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> 為 `JsonNamingPolicy.CamelCase` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d174-137">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs" id="Serialize":::

<span data-ttu-id="8d174-138">使用名為的字典序列化 `TemperatureRanges` 具有索引鍵/值組的物件 `"ColdMinTemp", 20` ， `"HotMinTemp", 40` 將會產生如下列範例所示的 JSON 輸出：</span><span class="sxs-lookup"><span data-stu-id="8d174-138">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="8d174-139">字典索引鍵的 camel 大小寫命名原則僅適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="8d174-139">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="8d174-140">如果您將字典還原序列化，即使您為指定，金鑰也會與 JSON 檔案相符 `JsonNamingPolicy.CamelCase` `DictionaryKeyPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="8d174-140">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

## <a name="enums-as-strings"></a><span data-ttu-id="8d174-141">作為字串的列舉</span><span class="sxs-lookup"><span data-stu-id="8d174-141">Enums as strings</span></span>

<span data-ttu-id="8d174-142">根據預設，列舉會序列化為數字。</span><span class="sxs-lookup"><span data-stu-id="8d174-142">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="8d174-143">若要將列舉名稱序列化為字串，請使用 <xref:System.Text.Json.Serialization.JsonStringEnumConverter> 。</span><span class="sxs-lookup"><span data-stu-id="8d174-143">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="8d174-144">例如，假設您需要序列化具有列舉的下列類別：</span><span class="sxs-lookup"><span data-stu-id="8d174-144">For example, suppose you need to serialize the following class that has an enum:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnum":::

<span data-ttu-id="8d174-145">如果摘要為 `Hot` ，則序列化的 JSON 預設值為3：</span><span class="sxs-lookup"><span data-stu-id="8d174-145">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="8d174-146">下列範例程式碼會將列舉名稱（而非數值）序列化，並將名稱轉換成 camel 大小寫：</span><span class="sxs-lookup"><span data-stu-id="8d174-146">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Serialize":::

<span data-ttu-id="8d174-147">產生的 JSON 看起來如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d174-147">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="8d174-148">您也可以還原序列化列舉字串名稱，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8d174-148">Enum string names can be deserialized as well, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Deserialize":::

## <a name="see-also"></a><span data-ttu-id="8d174-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d174-149">See also</span></span>

* [<span data-ttu-id="8d174-150">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="8d174-150">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="8d174-151">具現化 JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="8d174-151">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="8d174-152">啟用不區分大小寫的比對</span><span class="sxs-lookup"><span data-stu-id="8d174-152">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="8d174-153">略過屬性</span><span class="sxs-lookup"><span data-stu-id="8d174-153">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="8d174-154">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="8d174-154">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="8d174-155">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="8d174-155">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="8d174-156">保留迴圈參考</span><span class="sxs-lookup"><span data-stu-id="8d174-156">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="8d174-157">不可變類型和非公用存取子</span><span class="sxs-lookup"><span data-stu-id="8d174-157">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="8d174-158">多型序列化</span><span class="sxs-lookup"><span data-stu-id="8d174-158">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="8d174-159">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="8d174-159">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
