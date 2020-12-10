---
title: 如何使用具現化 JsonSerializerOptions System.Text.Json
description: 瞭解如何避免效能問題，以及如何針對 JsonSerializerOptions 實例使用可用的函式。
ms.date: 12/02/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 5f32e1369e58dd9550f28abc822f187dee46c022
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009829"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a>如何使用具現化 JsonSerializerOptions 實例 System.Text.Json

本文說明如何在使用時避免發生效能問題 <xref:System.Text.Json.JsonSerializerOptions> 。 它也會示範如何使用可用的參數化的函式。

## <a name="reuse-jsonserializeroptions-instances"></a>重複使用 JsonSerializerOptions 實例

如果您 `JsonSerializerOptions` 重複使用相同的選項，請勿 `JsonSerializerOptions` 在每次使用時建立新的實例。 每次呼叫時重複使用相同的實例。 本指南適用于您為自訂轉換器撰寫的程式碼，以及當您呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 或時 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 。

下列程式碼示範使用新選項實例的效能負面影響。

:::code language="csharp" source="snippets/system-text-json-configure-options/csharp/ReuseOptionsInstances.cs":::

上述程式碼會使用相同的選項實例，將小型物件100000次序列化。 然後，它會將相同的物件序列化相同次數，並每次建立新的選項實例。 相較于40140毫秒，一般的執行時間差異為190。 如果您增加反復專案的數目，則差異會更大。

當傳遞新的選項實例時，序列化程式會在物件圖形中的每個類型第一次序列化期間進行準備階段。 此準備工作包括建立序列化所需的中繼資料快取。 中繼資料包含屬性 getter、setter、函式引數、指定屬性等的委派。 此中繼資料快取會儲存在 options 實例中。 相同的準備程式和快取會套用至還原序列化。

實例中的中繼資料快取大小 `JsonSerializerOptions` 取決於要序列化的類型數目。 如果您將許多型別（例如，動態產生的型別）傳遞給序列化程式，快取大小將會持續成長，最後會導致 `OutOfMemoryException` 。

## <a name="copy-jsonserializeroptions"></a>複製 JsonSerializerOptions

::: zone pivot="dotnet-5-0"
有 [JsonSerializerOptions 的函式] (x： System.Text.Json 。JsonSerializerOptions。% 23ctor (System.Text.Json 。JsonSerializerOptions) # A3，可讓您使用與現有實例相同的選項來建立新的實例，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
`JsonSerializerOptions`在 .Net Core 3.1 中無法使用採用現有實例的函式。
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a>JsonSerializerOptions 的 Web 預設值

::: zone pivot="dotnet-5-0"
以下是針對 web 應用程式具有不同預設值的選項：

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

有一個 [JsonSerializerOptions 的函式] (x： System.Text.Json 。JsonSerializerOptions。% 23ctor (System.Text.Json 。JsonSerializerDefaults) ？ view = net-5.0&preserve-view = true) 可讓您建立新的實例，其中包含 ASP.NET Core 用於 web 應用程式的預設選項，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
以下是針對 web 應用程式具有不同預設值的選項：

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

`JsonSerializerOptions`指定一組預設值的函式在 .Net Core 3.1 中無法使用。
::: zone-end

## <a name="see-also"></a>請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
* [如何將 JSON 序列化及還原序列化](system-text-json-how-to.md)
* [啟用不區分大小寫比對](system-text-json-character-casing.md)
* [自訂屬性名稱與值](system-text-json-customize-properties.md)
* [忽略屬性](system-text-json-ignore-properties.md)
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
