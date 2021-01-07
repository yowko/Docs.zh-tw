---
title: 中支援的集合類型 System.Text.Json
description: 瞭解命名空間中的 Api 支援哪些集合類型進行序列化 System.Text.Json 。
ms.date: 01/06/2021
no-loc:
- System.Text.Json
ms.topic: reference
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 48033689e844dd29c999395255b5a1565fa2996e
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970988"
---
# <a name="supported-collection-types-in-no-locsystemtextjson"></a>中支援的集合類型 System.Text.Json

本文概述哪些集合支援序列化和還原序列化。 <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> 支援序列化的集合類型（如果有的話）：

* 衍生自 <xref:System.Collections.IEnumerable>。
* 包含可序列化的元素。

序列化程式會呼叫 <xref:System.Collections.IEnumerable.GetEnumerator> 方法，並寫入元素。

還原序列化較為複雜，且不支援某些集合類型。

下列章節依命名空間進行組織，並顯示支援序列化和還原序列化的類型。

## <a name="systemcollections-namespace"></a>System.Collections 命名空間

| 類型                                      | 序列化 | 還原序列化 |
|-------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ArrayList>       | ✔️           | ✔️              |
| <xref:System.Collections.BitArray>        | ✔️           | ❌              |
| <xref:System.Collections.DictionaryEntry> | ✔️           | ✔️              |
| <xref:System.Collections.Hashtable>       | ✔️           | ✔️              |
| <xref:System.Collections.Queue>           | ✔️           | ✔️              |
| <xref:System.Collections.SortedList>      | ✔️           | ✔️              |
| <xref:System.Collections.Stack>           | ✔️           | ✔️              |
| <xref:System.Collections.ICollection>     | ✔️           | ✔️              |
| <xref:System.Collections.IDictionary>     | ✔️           | ✔️              |
| <xref:System.Collections.IEnumerable>     | ✔️           | ✔️              |
| <xref:System.Collections.IList>           | ✔️           | ✔️              |

## <a name="systemcollectionsgeneric-namespace"></a>System.Collections.Generic 命名空間

::: zone pivot="dotnet-5-0"

| 類型                                                      | 序列化 | 還原序列化 |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Generic.Dictionary%602> \*       | ✔️           | ✔️              |
| <xref:System.Collections.Generic.HashSet%601>             | ✔️           | ✔️              |
| <xref:System.Collections.Generic.KeyValuePair%602>        | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedList%601>          | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedListNode%601>      | ✔️           | ❌              |
| <xref:System.Collections.Generic.List%601>                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Queue%601>               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedDictionary%602> \* | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedList%602> \*       | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedSet%601>           | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Stack%601>               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>    | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>         | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IDictionary%602> \*      | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IEnumerable%601>         | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IList%601>               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601> | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyDictionary%602> \* | ✔️        | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyList%601>       | ✔️           | ✔️              |
| <xref:System.Collections.Generic.ISet%601>                | ✔️           | ✔️              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| 類型                                                                                            | 序列化 | 還原序列化 |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| [字典 \<string, TValue> ](xref:System.Collections.Generic.Dictionary%602)\*                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.HashSet%601>                                                   | ✔️           | ✔️              |
| <xref:System.Collections.Generic.KeyValuePair%602>                                              | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedList%601>                                                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.LinkedListNode%601>                                            | ✔️           | ❌              |
| <xref:System.Collections.Generic.List%601>                                                      | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Queue%601>                                                     | ✔️           | ✔️              |
| [SortedDictionary \<string, TValue> ](xref:System.Collections.Generic.SortedDictionary%602)\*    | ✔️           | ✔️              |
| [SortedList \<string, TValue> ](xref:System.Collections.Generic.SortedList%602)\*                | ✔️           | ✔️              |
| <xref:System.Collections.Generic.SortedSet%601>                                                 | ✔️           | ✔️              |
| <xref:System.Collections.Generic.Stack%601>                                                     | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>                                          | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>                                               | ✔️           | ✔️              |
| [IDictionary\<string, TValue> ](xref:System.Collections.Generic.IDictionary%602) \*              | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IEnumerable%601>                                               | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IList%601>                                                     | ✔️           | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601>                                       | ✔️           | ✔️              |
| [Ireadonlydictionary<string \<string, TValue> ](xref:System.Collections.Generic.IReadOnlyDictionary%602)\* | ✔️        | ✔️              |
| <xref:System.Collections.Generic.IReadOnlyList%601>                                             | ✔️           | ✔️              |
| <xref:System.Collections.Generic.ISet%601>                                                      | ✔️           | ✔️              |

::: zone-end

\* 請參閱 [支援的金鑰類型](#supported-key-types)。

## <a name="systemcollectionsimmutable-namespace"></a>System.object 命名空間

::: zone pivot="dotnet-5-0"

| 類型                                                              | 序列化 | 還原序列化 |
|-------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*  | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>          | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\* | ✔️      | ✔️              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableStack%601> \*         | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableDictionary%602> \*\* | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>           | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableSet%601>             | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableStack%601> \*        | ✔️           | ✔️              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| 類型                                                                                                          | 序列化 | 還原序列化 |
|---------------------------------------------------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>                                                        | ✔️           | ✔️              |
| [ImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableDictionary%602)\*\*        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>                                                      | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>                                                        | ✔️           | ✔️              |
| [ImmutableSortedDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableSortedDictionary%602)\*\*| ✔️       | ✔️              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>                                                    | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.ImmutableStack%601> \*                                                     | ✔️           | ✔️              |
| [IImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.IImmutableDictionary%602)\*\*      | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>                                                       | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableSet%601>                                                         | ✔️           | ✔️              |
| <xref:System.Collections.Immutable.IImmutableStack%601> \*                                                    | ✔️           | ✔️              |

::: zone-end

\*請參閱[支援堆疊 \<T> 的往返](system-text-json-converters-how-to.md#support-round-trip-for-stackt)。

\*\* 請參閱 [支援的金鑰類型](#supported-key-types)。

## <a name="systemcollectionsspecialized-namespace"></a>System.Collections.Specialized 命名空間

| 類型                                                      | 序列化 | 還原序列化 |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Specialized.BitVector32>         | ✔️           | ❌\*            |
| <xref:System.Collections.Specialized.HybridDictionary>    | ✔️           | ✔️              |
| <xref:System.Collections.Specialized.IOrderedDictionary>  | ✔️           | ❌              |
| <xref:System.Collections.Specialized.ListDictionary>      | ✔️           | ✔️              |
| <xref:System.Collections.Specialized.StringCollection>    | ✔️           | ❌              |
| <xref:System.Collections.Specialized.StringDictionary>    | ✔️           | ❌              |
| <xref:System.Collections.Specialized.NameValueCollection> | ✔️           | ❌              |

\* 當還原序列化時 <xref:System.Collections.Specialized.BitVector32> ， <xref:System.Collections.Specialized.BitVector32.Data> 屬性會略過，因為它沒有公用 setter。 不會擲回任何例外狀況。

## <a name="systemcollectionsconcurrent-namespace"></a>System.Collections.Concurrent 命名空間

::: zone pivot="dotnet-5-0"

| 類型                                                          | 序列化 | 還原序列化 |
|---------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601>   | ✔️           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>        | ✔️           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\* | ✔️      | ✔️              |
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>      | ✔️           | ✔️              |
| <xref:System.Collections.Concurrent.ConcurrentStack%601> \*   | ✔️           | ✔️              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| 類型                                                        | 序列化 | 還原序列化 |
|-------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601> | ✔️           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>      | ✔️           | ❌              |
| [ConcurrentDictionary \<string, TValue> ](xref:System.Collections.Concurrent.ConcurrentDictionary%602)\*\* |✔️|✔️|
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>    | ✔️           | ✔️              |
| <xref:System.Collections.Concurrent.ConcurrentStack%601> \* | ✔️           | ✔️              |

::: zone-end

\*請參閱[支援堆疊 \<T> 的往返](system-text-json-converters-how-to.md#support-round-trip-for-stackt)。

\*\* 請參閱 [支援的金鑰類型](#supported-key-types)。

## <a name="systemcollectionsobjectmodel-namespace"></a>System.Collections.ObjectModel 命名空間

::: zone pivot="dotnet-5-0"

| 類型                                                           | 序列化 | 還原序列化 |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | ✔️            | ✔️             |
| [System.collections.objectmodel.keyedcollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\* |✔️|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | ✔️            | ✔️             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | ✔️            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602>   | ✔️            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601> | ✔️    | ❌             |

\*`string`不支援非索引鍵。

::: zone-end

::: zone pivot="dotnet-core-3-1"

| 類型                                                           | 序列化 | 還原序列化 |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | ✔️            | ✔️             |
| [System.collections.objectmodel.keyedcollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\* |✔️|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | ✔️            | ✔️             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | ✔️            | ❌             |
| [Readonlydictionary<tkey \<string, TValue> ](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602)\* |✔️|❌|
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601>| ✔️     | ❌             |

\* 請參閱 [支援的金鑰類型](#supported-key-types)。

::: zone-end

## <a name="custom-collections"></a>自訂集合

任何不在上述命名空間中的集合類型都會被視為自訂集合。 這類類型包括 ASP.NET Core 所定義的使用者定義型別和型別。 例如， <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> 在此群組中。

所有自訂集合 (衍生自) 的所有專案 `IEnumerable` 都支援序列化，只要支援它們的元素類型即可。

### <a name="custom-collections-with-deserialization-support"></a>具有還原序列化支援的自訂集合

自訂集合支援還原序列化（如果有的話）：

::: zone pivot="dotnet-5-0"

* 不是介面或抽象類別。
* 具有無參數的函式。
* 包含支援的元素類型 <xref:System.Text.Json.JsonSerializer> 。
* 會執行或繼承下列一或多個介面或類別：
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <xref:System.Collections.Concurrent.ConcurrentStack%601> \*
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <xref:System.Collections.Generic.IDictionary%602> \*\*
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <xref:System.Collections.Stack> \*
  * <xref:System.Collections.Generic.Stack%601> \*

::: zone-end

::: zone pivot="dotnet-core-3-1"

* 不是介面或抽象類別。
* 具有無參數的函式。
* 包含支援的元素類型 <xref:System.Text.Json.JsonSerializer> 。
* 會執行或繼承下列一或多個介面或類別：
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <xref:System.Collections.Concurrent.ConcurrentStack%601> \*
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * [IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \* \*
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <xref:System.Collections.Stack> \*
  * <xref:System.Collections.Generic.Stack%601> \*

::: zone-end

  \*請參閱[支援堆疊 \<T> 的往返](system-text-json-converters-how-to.md#support-round-trip-for-stackt)。

  \*\* 請參閱 [支援的金鑰類型](#supported-key-types)。

### <a name="custom-collections-with-known-issues"></a>具有已知問題的自訂集合

下列自訂集合有一些已知問題：

- <xref:System.Dynamic.ExpandoObject>：請參閱 [dotnet/runtime # 29690](https://github.com/dotnet/runtime/issues/29690)。
- <xref:System.Dynamic.DynamicObject>：請參閱 [dotnet/runtime # 1808](https://github.com/dotnet/runtime/issues/1808)。
- <xref:System.Data.DataTable>：請參閱 [dotnet/檔 # 21366](https://github.com/dotnet/docs/issues/21366)。
- <xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>：請參閱 [dotnet/runtime # 1559](https://github.com/dotnet/runtime/issues/1559)。
- <xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>：請參閱 [dotnet/runtime # 1559](https://github.com/dotnet/runtime/issues/1559)。

如需已知問題的詳細資訊，請參閱[ System.Text.Json 中的開啟問題](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)。

## <a name="supported-key-types"></a>支援的金鑰類型

::: zone pivot="dotnet-5-0"

和類型的索引鍵支援的類型 `Dictionary` `SortedList` 包括下列各項：

* `Boolean`
* `Byte`
* `DateTime`
* `DateTimeOffset`
* `Decimal`
* `Double`
* `Enum`
* `Guid`
* `Int16`
* `Int32`
* `Int64`
* `Object` 只有在序列化時，以及執行時間類型是否為這份清單中其中一個支援的類型時，才 (。 ) 
* `SByte`
* `Single`
* `String`
* `UInt16`
* `UInt32`
* `UInt64`

::: zone-end

::: zone pivot="dotnet-core-3-1"

\*\*`string` `Dictionary` `SortedList` .Net Core 3.1 不支援和類型的非索引鍵。

::: zone-end

## <a name="see-also"></a>請參閱

* [System.Text.Json 概述](system-text-json-overview.md)
* [具現化 JsonSerializerOptions 實例](system-text-json-configure-options.md)
* [啟用不區分大小寫比對](system-text-json-character-casing.md)
* [自訂屬性名稱與值](system-text-json-customize-properties.md)
* [忽略屬性](system-text-json-ignore-properties.md)
* [允許不正確 JSON](system-text-json-invalid-json.md)
* [處理溢位 JSON](system-text-json-handle-overflow.md)
* [保留參考](system-text-json-preserve-references.md)
* [不可變型別及非公用存取子](system-text-json-immutability.md)
* [多型序列化](system-text-json-polymorphism.md)
* [從 Newtonsoft.Js遷移至 System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [自訂字元編碼](system-text-json-character-encoding.md)
* [撰寫自訂序列化程式和還原序列化程式](write-custom-serializer-deserializer.md)
* [撰寫 JSON 序列化的自訂轉換器](system-text-json-converters-how-to.md)
* [DateTime 和 DateTimeOffset 支援](../datetime/system-text-json-support.md)
* [System.Text.Json API 參考](xref:System.Text.Json)
* [System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)
