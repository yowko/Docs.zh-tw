---
title: 如何搭配使用不可變類型和非公用存取子 System.Text.Json
description: 瞭解如何在 .NET 中序列化和還原序列化時，使用不可變類型和非公用存取子。
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
ms.openlocfilehash: ff8ecec0d70c877b7cbbd0297b85f0d9578ab828
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008821"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-no-locsystemtextjson"></a>如何搭配使用不可變類型和非公用存取子 System.Text.Json

在本文中，您將學習如何使用不可變的類型（例如記錄）搭配 `System.Text.Json` 命名空間。

## <a name="immutable-types-and-records"></a>不可變的類型和記錄

::: zone pivot="dotnet-5-0"
`System.Text.Json` 可以使用參數化的函式，讓您可以還原序列化不可變的類別或結構。 針對類別，如果唯一的函式是參數化的，則會使用該函數。 若為結構或具有多個函式的類別，請套用 [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) 屬性，以指定要使用的類別。 未使用屬性時，一律會使用公用無參數的函式（如果有的話）。 屬性只能搭配公用的函式使用。 下列範例會使用 `[JsonConstructor]` 屬性：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

也支援 c # 9 中的記錄，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

針對不可變的類型，因為其所有屬性 setter 都非公用，請參閱下一節有關 [非公用屬性存取](#non-public-property-accessors)子的資訊。
::: zone-end

::: zone pivot="dotnet-core-3-1"
`JsonConstructorAttribute` 和 c # 9 記錄支援在 .NET Core 3.1 中無法使用。
::: zone-end

## <a name="non-public-property-accessors"></a>非公用屬性存取子

::: zone pivot="dotnet-5-0"
若要允許使用非公用屬性存取子，請使用 [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 屬性，如下列範例所示：

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
.NET Core 3.1 不支援非公用屬性存取子。 如需詳細資訊，請參閱「 [從 Newtonsoft.Json 文章遷移](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters)」。
::: zone-end

## <a name="see-also"></a>請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
* [如何將 JSON 序列化及還原序列化](system-text-json-how-to.md)
* [具現化 JsonSerializerOptions 實例](system-text-json-configure-options.md)
* [啟用不區分大小寫比對](system-text-json-character-casing.md)
* [自訂屬性名稱與值](system-text-json-customize-properties.md)
* [忽略屬性](system-text-json-ignore-properties.md)
* [允許不正確 JSON](system-text-json-invalid-json.md)
* [處理溢位 JSON](system-text-json-handle-overflow.md)
* [保留參考](system-text-json-preserve-references.md)
* [多型序列化](system-text-json-polymorphism.md)
* [從遷移 Newtonsoft.Json 至 System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [自訂字元編碼](system-text-json-character-encoding.md)
* [撰寫自訂序列化程式和還原序列化程式](write-custom-serializer-deserializer.md)
* [撰寫 JSON 序列化的自訂轉換器](system-text-json-converters-how-to.md)
* [DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
* [System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)
