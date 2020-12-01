---
title: 如何允許某些種類的無效 JSON 搭配 System.Text.Json
description: 瞭解如何在 .NET 中序列化和還原序列化時，允許批註、尾端逗號和引號數位。
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
ms.openlocfilehash: 60cbb98bb65ee5c1ffdd3043e42a04004530a115
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439898"
---
# <a name="how-to-allow-some-kinds-of-invalid-json-with-no-locsystemtextjson"></a>如何允許某些種類的無效 JSON 搭配 System.Text.Json

在本文中，您將瞭解如何在 JSON 中允許批註、尾端逗號和引號數位，以及如何以字串的形式寫入數位。

## <a name="allow-comments-and-trailing-commas"></a>允許批註和尾端逗號

根據預設，JSON 中不允許批註和結尾的逗號。 若要允許 JSON 中的批註，請將 <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> 屬性設定為 `JsonCommentHandling.Skip` 。
若要允許尾端逗號，請將 <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> 屬性設定為 `true` 。 下列範例顯示如何允許兩者：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs" id="Deserialize":::

以下是包含批註和尾端逗號的範例 JSON：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="allow-or-write-numbers-in-quotes"></a>以引號允許或寫入數位

::: zone pivot="dotnet-5-0"

某些序列化程式會將數位編碼為 JSON 字串， (以引號括住) 。

例如：

```json
{
    "DegreesCelsius": "23"
}
```

不要這樣撰寫：

```json
{
    "DegreesCelsius": 23
}
```

若要序列化引號中的數位，或在整個輸入物件圖形中接受以引號括住的數位，請設定 <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> 如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-29":::

當您 `System.Text.Json` 透過 ASP.NET Core 間接使用時，當還原序列化時，會允許括住的數位，因為 ASP.NET Core 指定 [web 預設選項](xref:System.Text.Json.JsonSerializerDefaults.Web)。

若要允許或寫入特定屬性、欄位或類型的引號號碼，請使用 [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) 屬性。
::: zone-end

::: zone pivot="dotnet-core-3-1"
`System.Text.Json` 在 .NET Core 3.1 中，不支援序列化或還原序列化以引號括住的數位。 如需詳細資訊，請參閱 [允許或寫入以引號括](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes)住的數位。
::: zone-end

## <a name="see-also"></a>另請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
* [具現化 JsonSerializerOptions](system-text-json-configure-options.md)
* [啟用不區分大小寫的比對](system-text-json-character-casing.md)
* [自訂屬性名稱和值](system-text-json-customize-properties.md)
* [略過屬性](system-text-json-ignore-properties.md)
* [處理溢位 JSON](system-text-json-handle-overflow.md)
* [保留迴圈參考](system-text-json-preserve-references.md)
* [不可變類型和非公用存取子](system-text-json-immutability.md)
* [多型序列化](system-text-json-polymorphism.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
