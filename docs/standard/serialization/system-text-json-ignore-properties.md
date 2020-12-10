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
ms.openlocfilehash: 6d703156d50a3e00a33cea5e15be2df911ed7c1b
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008808"
---
# <a name="how-to-ignore-properties-with-no-locsystemtextjson"></a>如何忽略屬性 System.Text.Json

將 c # 物件序列化為 JavaScript 物件標記法 (JSON) 時，根據預設，所有公用屬性都會進行序列化。 如果您不想讓某些部分出現在產生的 JSON 中，您有數個選項。 在本文中，您將瞭解如何根據各種準則略過屬性：

::: zone pivot="dotnet-5-0"

* [個別屬性](#ignore-individual-properties)
* [所有唯讀屬性](#ignore-all-read-only-properties)
* [所有 null 值屬性](#ignore-all-null-value-properties)
* [所有預設值屬性](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [個別屬性](#ignore-individual-properties)
* [所有唯讀屬性](#ignore-all-read-only-properties)
* [所有 null 值屬性](#ignore-all-null-value-properties)
::: zone-end

## <a name="ignore-individual-properties"></a>略過個別屬性

若要忽略個別的屬性，請使用 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 屬性。

以下是序列化和 JSON 輸出的範例類型：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithIgnoreAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
您可以藉由設定 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 屬性的屬性來指定條件排除 `Condition` 。 <xref:System.Text.Json.Serialization.JsonIgnoreCondition>列舉提供下列選項：

* `Always` -一律會忽略屬性。 如果未 `Condition` 指定，則會假設為這個選項。
* `Never` -無論 `DefaultIgnoreCondition` 、 `IgnoreReadOnlyProperties` 和全域設定為何，一律會將屬性序列化和還原序列化 `IgnoreReadOnlyFields` 。
* `WhenWritingDefault` -如果是參考型別 `null` 、可為 null 的實值型別 `null` 或實值型別，則會忽略序列化的屬性 `default` 。
* `WhenWritingNull` -如果是參考型別 `null` 或可為 null 的實值型別，則會忽略序列化的屬性 `null` 。

下列範例說明如何使用 [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) 屬性的 `Condition` 屬性：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

## <a name="ignore-all-read-only-properties"></a>忽略所有唯讀屬性

如果屬性包含公用 getter 而非公用 setter，則該屬性為唯讀。 若要在序列化時忽略所有唯讀屬性，請將設定 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> 為 `true` ，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs" id="Serialize":::

以下是序列化和 JSON 輸出的範例類型：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithROProperty":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

此選項只適用于序列化。 在還原序列化期間，預設會忽略唯讀屬性。

::: zone pivot="dotnet-5-0"
此選項只適用于屬性。 若要在序列化 [欄位](system-text-json-how-to.md#include-fields)時忽略唯讀欄位，請使用 <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> 全域設定。
::: zone-end

## <a name="ignore-all-null-value-properties"></a>忽略所有 null 值屬性

::: zone pivot="dotnet-5-0"
若要忽略所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> 屬性設定為 <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> ，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
若要在序列化時忽略所有 null 值屬性，請將 <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> 屬性設定為 `true` ，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs" id="Serialize":::

以下是序列化和 JSON 輸出的範例物件：

| 屬性             | 值                         |
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

## <a name="ignore-all-default-value-properties"></a>略過所有預設值屬性

::: zone pivot="dotnet-5-0"
若要避免在數值型別屬性中序列化預設值，請將 <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> 屬性設定為 <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> ，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

這 <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> 項設定也會防止 null 值的參考型別和可為 null 的實值型別屬性的序列化。

::: zone pivot="dotnet-core-3-1"
沒有內建的方法可防止序列化 .NET Core 3.1 中具有值型別預設值的屬性 `System.Text.Json` 。
::: zone-end

## <a name="see-also"></a>請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
* [如何將 JSON 序列化及還原序列化](system-text-json-how-to.md)
* [具現化 JsonSerializerOptions 實例](system-text-json-configure-options.md)
* [啟用不區分大小寫比對](system-text-json-character-casing.md)
* [自訂屬性名稱與值](system-text-json-customize-properties.md)
* [允許不正確 JSON](system-text-json-invalid-json.md)
* [處理溢位 JSON](system-text-json-handle-overflow.md)
* [保留參考](system-text-json-preserve-references.md)
* [不可變型別及非公用存取子](system-text-json-immutability.md)
* [多型序列化](system-text-json-polymorphism.md)
* [從遷移 Newtonsoft.Json 至 System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [自訂字元編碼](system-text-json-character-encoding.md)
* [撰寫自訂序列化程式和還原序列化程式](write-custom-serializer-deserializer.md)
* [撰寫 JSON 序列化的自訂轉換器](system-text-json-converters-how-to.md)
* [DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
* [System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)
