---
title: 如何使用來序列化衍生類別的屬性 System.Text.Json
description: 瞭解如何在 .NET 中序列化至 JSON 並將其序列化，以序列化多型物件。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 4b99a402ea4f4c664d3bfd75627ffaf94948d493
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439922"
---
# <a name="how-to-serialize-properties-of-derived-classes-with-no-locsystemtextjson"></a>如何使用來序列化衍生類別的屬性 System.Text.Json

在本文中，您將瞭解如何使用命名空間來序列化衍生類別的屬性 `System.Text.Json` 。

## <a name="serialize-properties-of-derived-classes"></a>序列化衍生類別的屬性

_不_ 支援多型類型階層的序列化。 例如，如果屬性定義為介面或抽象類別，則只有在介面或抽象類別上定義的屬性會序列化，即使執行時間型別具有其他屬性也一樣。 本節將說明此行為的例外狀況。

例如，假設您有一個 `WeatherForecast` 類別和一個衍生的類別 `WeatherForecastDerived` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFDerived":::

並假設在編譯時期，方法的型別引數 `Serialize` 是 `WeatherForecast` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeDefault":::

在此案例中， `WindSpeed` 即使物件實際上是物件，也不會序列化屬性 `weatherForecast` `WeatherForecastDerived` 。 只有基類屬性會序列化：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

這項行為旨在協助防止在衍生的執行時間建立型別中意外曝光資料。

若要序列化上述範例中衍生類型的屬性，請使用下列其中一種方法：

* 呼叫的多載 <xref:System.Text.Json.JsonSerializer.Serialize%2A> ，可讓您在執行時間指定型別：

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeGetType":::

* 宣告要序列化為的物件 `object` 。

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeObject":::

在上述範例案例中，這兩種方法都會使 `WindSpeed` 屬性包含在 JSON 輸出中：

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> 這些方法只會針對要序列化的根物件提供多型的序列化，而不是針對該根物件的屬性提供。

如果您將物件定義為類型，則可以取得較低層級物件的多型序列化 `object` 。 例如，假設您的 `WeatherForecast` 類別具有名為 `PreviousForecast` 的屬性，該屬性可以定義為類型 `WeatherForecast` 或 `object` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPrevious":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPreviousAsObject":::

如果 `PreviousForecast` 屬性包含的實例 `WeatherForecastDerived` ：

* 序列化的 JSON 輸出 `WeatherForecastWithPrevious` **不包括在內** `WindSpeed` 。
* 序列化的 JSON 輸出 `WeatherForecastWithPreviousAsObject` **包含** `WindSpeed` 。

若要序列化 `WeatherForecastWithPreviousAsObject` ，不需要呼叫 `Serialize<object>` 或， `GetType` 因為根物件不是可能是衍生類型的物件。 下列程式碼範例不會呼叫 `Serialize<object>` 或 `GetType` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeSecondLevel":::

上述程式碼會正確地序列化 `WeatherForecastWithPreviousAsObject` ：

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

將屬性定義為 `object` 與介面搭配使用的相同方法。 假設您有下列介面和執行，而且您想要使用包含實實例的屬性來序列化類別：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/IForecast.cs":::

當您序列化的實例時 `Forecasts` ，只 `Tuesday` 會顯示 `WindSpeed` 屬性，因為 `Tuesday` 定義為 `object` ：

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeInterface":::

下列範例顯示上述程式碼所產生的 JSON：

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

如需多型序列化的詳細資訊，以及有關還原 **序列化** 的詳細 **資訊，請** 參閱 [如何從遷移 Newtonsoft.Json System.Text.Json 至](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization)。

## <a name="see-also"></a>另請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
* [具現化 JsonSerializerOptions](system-text-json-configure-options.md)
* [啟用不區分大小寫的比對](system-text-json-character-casing.md)
* [自訂屬性名稱和值](system-text-json-customize-properties.md)
* [略過屬性](system-text-json-ignore-properties.md)
* [允許不正確 JSON](system-text-json-invalid-json.md)
* [處理溢位 JSON](system-text-json-handle-overflow.md)
* [保留迴圈參考](system-text-json-preserve-references.md)
* [不可變類型和非公用存取子](system-text-json-immutability.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
