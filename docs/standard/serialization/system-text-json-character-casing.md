---
title: 如何啟用不區分大小寫的屬性名稱比對 System.Text.Json
description: 瞭解如何在 .NET 中序列化至 JSON 並進行序列化時，啟用不區分大小寫的屬性名稱比對。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 4bd57d32120f51ffd1ff09c9817edbafa28a3f19
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439896"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a>如何啟用不區分大小寫的屬性名稱比對 System.Text.Json

在本文中，您將瞭解如何使用命名空間來啟用不區分大小寫的屬性名稱比對 `System.Text.Json` 。

## <a name="case-insensitive-property-matching"></a>不區分大小寫的屬性比對

根據預設，還原序列化會尋找 JSON 與目標物件屬性之間是否有區分大小寫的屬性名稱相符專案。 若要變更此行為，請將設定 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> 為 `true` ：

> [!NOTE]
> [Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)不區分大小寫。

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

以下是使用 camel 大小寫屬性名稱的範例 JSON。 您可以將它還原序列化為具有 Pascal 案例屬性名稱的下列型別。

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a>另請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
* [具現化 JsonSerializerOptions](system-text-json-configure-options.md)
* [自訂屬性名稱和值](system-text-json-customize-properties.md)
* [略過屬性](system-text-json-ignore-properties.md)
* [允許不正確 JSON](system-text-json-invalid-json.md)
* [處理溢位 JSON](system-text-json-handle-overflow.md)
* [保留迴圈參考](system-text-json-preserve-references.md)
* [不可變類型和非公用存取子](system-text-json-immutability.md)
* [多型序列化](system-text-json-polymorphism.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
