---
title: 如何忽略屬性 System.Text.Json
description: 瞭解如何在 .NET 中使用序列化時忽略屬性 System.Text.Json 。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: ed7ef8509d6660bbbbaf194a87aa9d4815143507
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439899"
---
# <a name="how-to-ignore-properties-with-no-locsystemtextjson"></a><span data-ttu-id="338a7-103">如何忽略屬性 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="338a7-103">How to ignore properties with System.Text.Json</span></span>

<span data-ttu-id="338a7-104">將 c # 物件序列化為 JavaScript 物件標記法 (JSON) 時，根據預設，所有公用屬性都會進行序列化。</span><span class="sxs-lookup"><span data-stu-id="338a7-104">When serializing C# objects to JavaScript Object Notation (JSON), by default, all public properties are serialized.</span></span> <span data-ttu-id="338a7-105">如果您不想讓某些部分出現在產生的 JSON 中，您有數個選項。</span><span class="sxs-lookup"><span data-stu-id="338a7-105">If you don't want some of them to appear in the resulting JSON, you have several options.</span></span> <span data-ttu-id="338a7-106">在本文中，您將瞭解如何根據各種準則略過屬性：</span><span class="sxs-lookup"><span data-stu-id="338a7-106">In this article you learn how to ignore properties based on various criteria:</span></span>

::: zone pivot="dotnet-5-0"

* [<span data-ttu-id="338a7-107">個別屬性</span><span class="sxs-lookup"><span data-stu-id="338a7-107">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="338a7-108">所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="338a7-108">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="338a7-109">所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="338a7-109">All null-value properties</span></span>](#ignore-all-null-value-properties)
* [<span data-ttu-id="338a7-110">所有預設值屬性</span><span class="sxs-lookup"><span data-stu-id="338a7-110">All default-value properties</span></span>](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [<span data-ttu-id="338a7-111">個別屬性</span><span class="sxs-lookup"><span data-stu-id="338a7-111">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="338a7-112">所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="338a7-112">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="338a7-113">所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="338a7-113">All null-value properties</span></span>](#ignore-all-null-value-properties)
::: zone-end

## <a name="ignore-individual-properties"></a><span data-ttu-id="338a7-114">略過個別屬性</span><span class="sxs-lookup"><span data-stu-id="338a7-114">Ignore individual properties</span></span>

<span data-ttu-id="338a7-115">若要忽略個別的屬性，請使用 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="338a7-115">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="338a7-116">以下是序列化和 JSON 輸出的範例類型：</span><span class="sxs-lookup"><span data-stu-id="338a7-116">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithIgnoreAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
<span data-ttu-id="338a7-117">您可以藉由設定 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 屬性的屬性來指定條件排除 `Condition` 。</span><span class="sxs-lookup"><span data-stu-id="338a7-117">You can specify conditional exclusion by setting the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property.</span></span> <span data-ttu-id="338a7-118"><xref:System.Text.Json.Serialization.JsonIgnoreCondition>列舉提供下列選項：</span><span class="sxs-lookup"><span data-stu-id="338a7-118">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition> enum provides the following options:</span></span>

* <span data-ttu-id="338a7-119">`Always` -一律會忽略屬性。</span><span class="sxs-lookup"><span data-stu-id="338a7-119">`Always` - The property is always ignored.</span></span> <span data-ttu-id="338a7-120">如果未 `Condition` 指定，則會假設為這個選項。</span><span class="sxs-lookup"><span data-stu-id="338a7-120">If no `Condition` is specified, this option is assumed.</span></span>
* <span data-ttu-id="338a7-121">`Never` -無論 `DefaultIgnoreCondition` 、 `IgnoreReadOnlyProperties` 和全域設定為何，一律會將屬性序列化和還原序列化 `IgnoreReadOnlyFields` 。</span><span class="sxs-lookup"><span data-stu-id="338a7-121">`Never` - The property is always serialized and deserialized, regardless of the `DefaultIgnoreCondition`, `IgnoreReadOnlyProperties`, and `IgnoreReadOnlyFields` global settings.</span></span>
* <span data-ttu-id="338a7-122">`WhenWritingDefault` -如果是參考型別 `null` 、可為 null 的實值型別 `null` 或實值型別，則會忽略序列化的屬性 `default` 。</span><span class="sxs-lookup"><span data-stu-id="338a7-122">`WhenWritingDefault` - The property is ignored on serialization if it's a reference type `null`, a nullable value type `null`, or a value type `default`.</span></span>
* <span data-ttu-id="338a7-123">`WhenWritingNull` -如果是參考型別 `null` 或可為 null 的實值型別，則會忽略序列化的屬性 `null` 。</span><span class="sxs-lookup"><span data-stu-id="338a7-123">`WhenWritingNull` - The property is ignored on serialization if it's a reference type `null`, or a nullable value type `null`.</span></span>

<span data-ttu-id="338a7-124">下列範例說明如何使用 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 屬性的 `Condition` 屬性：</span><span class="sxs-lookup"><span data-stu-id="338a7-124">The following example illustrates use of the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

## <a name="ignore-all-read-only-properties"></a><span data-ttu-id="338a7-125">忽略所有唯讀屬性</span><span class="sxs-lookup"><span data-stu-id="338a7-125">Ignore all read-only properties</span></span>

<span data-ttu-id="338a7-126">如果屬性包含公用 getter 而非公用 setter，則該屬性為唯讀。</span><span class="sxs-lookup"><span data-stu-id="338a7-126">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="338a7-127">若要在序列化時忽略所有唯讀屬性，請將設定 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> 為 `true` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="338a7-127">To ignore all read-only properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs" id="Serialize":::

<span data-ttu-id="338a7-128">以下是序列化和 JSON 輸出的範例類型：</span><span class="sxs-lookup"><span data-stu-id="338a7-128">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithROProperty":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="338a7-129">此選項只適用于序列化。</span><span class="sxs-lookup"><span data-stu-id="338a7-129">This option applies only to serialization.</span></span> <span data-ttu-id="338a7-130">在還原序列化期間，預設會忽略唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="338a7-130">During deserialization, read-only properties are ignored by default.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="338a7-131">此選項只適用于屬性。</span><span class="sxs-lookup"><span data-stu-id="338a7-131">This option applies only to properties.</span></span> <span data-ttu-id="338a7-132">若要在序列化 [欄位](system-text-json-how-to.md#include-fields)時忽略唯讀欄位，請使用 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> 全域設定。</span><span class="sxs-lookup"><span data-stu-id="338a7-132">To ignore read-only fields when [serializing fields](system-text-json-how-to.md#include-fields), use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

## <a name="ignore-all-null-value-properties"></a><span data-ttu-id="338a7-133">忽略所有 null 值屬性</span><span class="sxs-lookup"><span data-stu-id="338a7-133">Ignore all null-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="338a7-134">若要忽略所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> 屬性設定為 <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="338a7-134">To ignore all null-value properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="338a7-135">若要在序列化時忽略所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> 屬性設定為 `true` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="338a7-135">To ignore all null-value properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs" id="Serialize":::

<span data-ttu-id="338a7-136">以下是序列化和 JSON 輸出的範例物件：</span><span class="sxs-lookup"><span data-stu-id="338a7-136">Here's an example object to serialize and JSON output:</span></span>

| <span data-ttu-id="338a7-137">屬性</span><span class="sxs-lookup"><span data-stu-id="338a7-137">Property</span></span>             | <span data-ttu-id="338a7-138">值</span><span class="sxs-lookup"><span data-stu-id="338a7-138">Value</span></span>                         |
|----------------------|-------------------------------|
| `Date`               | `8/1/2019 12:00:00 AM -07:00` |
| `TemperatureCelsius` | `25`                          |
| `Summary`            | `null`                        |

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

## <a name="ignore-all-default-value-properties"></a><span data-ttu-id="338a7-139">略過所有預設值屬性</span><span class="sxs-lookup"><span data-stu-id="338a7-139">Ignore all default-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="338a7-140">若要避免在數值型別屬性中序列化預設值，請將 <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> 屬性設定為 <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="338a7-140">To prevent serialization of default values in value type properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

<span data-ttu-id="338a7-141">這 <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> 項設定也會防止 null 值的參考型別和可為 null 的實值型別屬性的序列化。</span><span class="sxs-lookup"><span data-stu-id="338a7-141">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> setting also prevents serialization of null-value reference type and nullable value type properties.</span></span>

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="338a7-142">沒有內建的方法可防止序列化 .NET Core 3.1 中具有值型別預設值的屬性 `System.Text.Json` 。</span><span class="sxs-lookup"><span data-stu-id="338a7-142">There is no built-in way to prevent serialization of properties with value type defaults in `System.Text.Json` in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="338a7-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="338a7-143">See also</span></span>

* [<span data-ttu-id="338a7-144">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="338a7-144">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="338a7-145">具現化 JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="338a7-145">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="338a7-146">啟用不區分大小寫的比對</span><span class="sxs-lookup"><span data-stu-id="338a7-146">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="338a7-147">自訂屬性名稱和值</span><span class="sxs-lookup"><span data-stu-id="338a7-147">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="338a7-148">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="338a7-148">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="338a7-149">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="338a7-149">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="338a7-150">保留迴圈參考</span><span class="sxs-lookup"><span data-stu-id="338a7-150">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="338a7-151">不可變類型和非公用存取子</span><span class="sxs-lookup"><span data-stu-id="338a7-151">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="338a7-152">多型序列化</span><span class="sxs-lookup"><span data-stu-id="338a7-152">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="338a7-153">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="338a7-153">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
