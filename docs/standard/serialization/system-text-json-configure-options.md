---
title: 如何使用具現化 JsonSerializerOptions System.Text.Json
description: 瞭解如何藉由複製現有的實例或使用 web 預設值，來具現化 JsonSerializerOptions 實例。
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
ms.openlocfilehash: 0febfe15f36856f10699fd327fb17c146277eb9b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439942"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a>如何使用具現化 JsonSerializerOptions 實例 System.Text.Json

在本文中，您將瞭解如何藉 <xref:System.Text.Json.JsonSerializerOptions> 由複製現有的實例或使用 web 預設值來具現化實例。

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

## <a name="see-also"></a>另請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
* [啟用不區分大小寫的比對](system-text-json-character-casing.md)
* [自訂屬性名稱和值](system-text-json-customize-properties.md)
* [略過屬性](system-text-json-ignore-properties.md)
* [允許不正確 JSON](system-text-json-invalid-json.md)
* [處理溢位 JSON](system-text-json-handle-overflow.md)
* [保留迴圈參考](system-text-json-preserve-references.md)
* [不可變類型和非公用存取子](system-text-json-immutability.md)
* [多型序列化](system-text-json-polymorphism.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
