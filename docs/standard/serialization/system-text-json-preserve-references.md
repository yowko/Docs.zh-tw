---
title: 如何保留參考 System.Text.Json
description: 瞭解如何在 .NET 中的 JSON 序列化和還原序列化時保留參考並處理迴圈參考。
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
ms.openlocfilehash: 9254ca261c7d748c04c311fa56359014f752ff31
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439921"
---
# <a name="how-to-handle-circular-references-with-no-locsystemtextjson"></a>如何處理迴圈參考 System.Text.Json

在本文中，您將學習如何使用命名空間來處理迴圈參考 `System.Text.Json` 。

## <a name="preserve-references-and-handle-circular-references"></a>保留參考並處理迴圈參考

::: zone pivot="dotnet-5-0"

若要保留參考並處理迴圈參考，請將設定 <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> 為 <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> 。 這項設定會導致下列行為：

* 序列化時：

  撰寫複雜型別時，序列化程式也會將中繼資料屬性寫入 (`$id` 、 `$values` 和 `$ref`) 。

* 還原序列化時：

  雖然不是必要的) ，但還原序列化程式會嘗試瞭解中繼資料，但 (的預期。

下列程式碼說明如何使用此 `Preserve` 設定。

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

這項功能不能用來保留實數值型別或不可變的類型。 在還原序列化時，會在讀取整個裝載之後，建立不可變型別的實例。 因此，如果它的參考出現在 JSON 承載內，就不可能還原序列化相同的實例。

如果是實值型別、不可變的型別和陣列，則不會序列化任何參考中繼資料。 在還原序列化時，如果找到或，則會擲回例外狀況 `$ref` `$id` 。 不過，實值型別 `$id` 會忽略 (，而 `$values` 在集合的情況下) ，讓您可以還原序列化使用序列化的承載 Newtonsoft.Json 。  Newtonsoft.Json 會序列化這類類型的中繼資料。

若要判斷物件是否相等， System.Text.Json <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> 請使用，它會使用參考相等 (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) 而不是 <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> 在比較兩個物件實例時 (值相等。

如需如何序列化和還原序列化參考的詳細資訊，請參閱 <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> 。

<xref:System.Text.Json.Serialization.ReferenceResolver>類別會定義在序列化和還原序列化時保留參考的行為。 建立衍生類別以指定自訂行為。 如需範例，請參閱 [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs)。

::: zone-end

::: zone pivot="dotnet-core-3-1"
System.Text.Json 在 .NET Core 3.1 中，只支援以傳值方式序列化，並擲回迴圈參考的例外狀況。
::: zone-end

## <a name="see-also"></a>另請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
* [具現化 JsonSerializerOptions](system-text-json-configure-options.md)
* [啟用不區分大小寫的比對](system-text-json-character-casing.md)
* [自訂屬性名稱和值](system-text-json-customize-properties.md)
* [略過屬性](system-text-json-ignore-properties.md)
* [允許不正確 JSON](system-text-json-invalid-json.md)
* [處理溢位 JSON](system-text-json-handle-overflow.md)
* [不可變類型和非公用存取子](system-text-json-immutability.md)
* [多型序列化](system-text-json-polymorphism.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
