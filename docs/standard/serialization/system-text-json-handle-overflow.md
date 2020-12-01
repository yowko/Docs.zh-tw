---
title: 如何使用來處理溢位 JSON System.Text.Json
description: 瞭解如何在 .NET 中序列化至 JSON 並進行還原序列化時，處理溢位 JSON。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 2c40d42b26bc5bd05f592cc51c6b5b9b4c6bbd9e
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439929"
---
# <a name="how-to-handle-overflow-json-with-no-locsystemtextjson"></a>如何使用來處理溢位 JSON System.Text.Json

在本文中，您將瞭解如何使用命名空間來處理溢位 JSON `System.Text.Json` 。

## <a name="handle-overflow-json"></a>處理溢位 JSON

還原序列化時，您可能會收到 JSON 中的資料，而該資料不是由目標型別的屬性所表示。 例如，假設您的目標型別是：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

而且要還原序列化的 JSON 如下所示：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

如果您將顯示的 JSON 還原序列化為顯示的類型， `DatesAvailable` 和 `SummaryWords` 屬性就不會有任何地方，而且會遺失。 若要捕獲額外的資料（例如這些屬性），請將 [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 屬性套用至類型或的屬性 `Dictionary<string,object>` `Dictionary<string,JsonElement>` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithExtensionData":::

當您將稍早所示的 JSON 還原序列化為此範例類型時，額外的資料會變成屬性的索引鍵/值組 `ExtensionData` ：

| 屬性 | 值 | 注意 |
|--|--|--|
| `Date` | `"8/1/2019 12:00:00 AM -07:00"` |  |
| `TemperatureCelsius` | `0` | JSON)  (區分大小寫不符 `temperatureCelsius` ，因此未設定屬性。 |
| `Summary` | `"Hot"` |  |
| `ExtensionData` | `temperatureCelsius: 25` | 因為大小寫不相符，所以這個 JSON 屬性是一個額外的，並且會成為字典中的索引鍵/值組。 |
| `DatesAvailable` | `[ "8/1/2019 12:00:00 AM -07:00", "8/2/2019 12:00:00 AM -07:00" ]` | JSON 中的額外屬性會變成成對的索引鍵/值，並以陣列作為值物件。 |
| `SummaryWords` | `[ "Cool", "Windy", "Humid" ]` | JSON 中的額外屬性會變成成對的索引鍵/值，並以陣列作為值物件。 |

序列化目標物件時，擴充功能資料索引鍵值組會變成 JSON 屬性，就像在傳入的 JSON 中一樣：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

請注意， `ExtensionData` 屬性名稱不會出現在 JSON 中。 此行為可讓 JSON 進行往返，而不會遺失任何額外的資料，否則不會還原序列化。

## <a name="see-also"></a>另請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
* [具現化 JsonSerializerOptions](system-text-json-configure-options.md)
* [啟用不區分大小寫的比對](system-text-json-character-casing.md)
* [自訂屬性名稱和值](system-text-json-customize-properties.md)
* [略過屬性](system-text-json-ignore-properties.md)
* [允許不正確 JSON](system-text-json-invalid-json.md)
* [保留迴圈參考](system-text-json-preserve-references.md)
* [不可變類型和非公用存取子](system-text-json-immutability.md)
* [多型序列化](system-text-json-polymorphism.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
