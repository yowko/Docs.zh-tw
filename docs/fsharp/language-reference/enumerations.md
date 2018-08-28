---
title: 列舉 (F#)
description: '了解如何使用 F # 列舉型別取代常值，讓程式碼，更容易讀取與維護。'
ms.date: 05/16/2016
ms.openlocfilehash: b51df53caf2e193496cb3694c913cbae08f7eaf5
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43003095"
---
# <a name="enumerations"></a>列舉

*列舉型別*也稱為*列舉*、 是整數類資料類型，將標籤指派給值的子集。 列舉可用來取代常值，讓程式碼更容易閱讀及維護。


## <a name="syntax"></a>語法

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>備註
列舉型別看起來很像已區分的聯集具有簡單的值，不同之處在於可指定的值。 值通常是 0 或 1，開始的整數或整數，表示位元位置。 如果列舉型別用來表示的位元位置，您也應該使用[旗標](xref:System.FlagsAttribute)屬性。

因此，比方說，您可以使用常值加上尾碼，例如，列舉的基礎型別從常值使用時，決定`1u`， `2u`，依此類推，不帶正負號的整數 (`uint32`) 型別。

當您參考具名的值時，您必須使用列舉型別本身的名稱與限定詞，亦即`enum-name.value1`，而非只`value1`。 此行為不同於的差別聯集。 這是因為列舉型別一定[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)屬性。

下列程式碼示範宣告和使用列舉型別。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

您可以輕鬆地轉換列舉的基礎型別使用適當的運算子，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

列舉型別可以有下列的基礎類型的其中一個： `sbyte`， `byte`， `int16`， `uint16`， `int32`， `uint32`， `int64`， `uint16`， `uint64`，以及`char`。 列舉型別以.NET framework 型別繼承自`System.Enum`，接著繼承自`System.ValueType`。 因此，它們是位於堆疊或內嵌在所包含的物件的實值型別，並且基礎型別的任何值是列舉的有效值。 這是重大時模式比對列舉值，因為您必須提供一種模式，會攔截未命名的數值。

`enum` F # 文件庫中的函式可用來產生列舉值，即使值以外的值預先定義，其中一項名為值。 您使用`enum`函式，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

預設值`enum`函式適用於類型`int32`。 因此，它不能有其他的基礎類型的列舉類型。 相反地，使用下列項目。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

此外，情況下，如列舉永遠會發出為`public`。 這是讓它們符合 C# 和.NET 平台的其餘部分。
    
## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[轉型和轉換](casting-and-conversions.md)
