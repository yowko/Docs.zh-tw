---
title: 列舉 (F#)
description: '了解如何使用 F # 列舉型別取代常值，讓程式碼更容易讀取與維護。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4b1a61fb69403f826733893667e55991d39867c6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="enumerations"></a>列舉

*列舉型別*，亦稱為*列舉*、 是整數類資料類型，其中的標籤指派給值的子集。 列舉可用來取代常值，讓程式碼更容易閱讀及維護。


## <a name="syntax"></a>語法

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>備註
列舉型別看起來很像差別聯集，其中包含簡單的值，不同之處在於您可以指定值。 值通常是從 0 或 1，開始的整數或整數，表示位元位置。 如果列舉型別用來表示的位元位置，您也應該使用[旗標](xref:System.FlagsAttribute)屬性。

列舉的基礎類型由常值使用，以便比方說，您可以使用常值加上尾碼，例如`1u`， `2u`，依此類推，針對不帶正負號的整數 (`uint32`) 型別。

當您參考具名的值時，您必須使用列舉型別本身的名稱與限定詞，也就是`enum-name.value1`，而非只`value1`。 此行為不同於差別聯集。 這是因為列舉型別一定[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)屬性。

下列程式碼顯示的宣告和使用列舉型別。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

您可以輕鬆轉換列舉的基礎型別使用適當的運算子，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

列舉型別可以有下列的基礎類型的其中一個： `sbyte`， `byte`， `int16`， `uint16`， `int32`， `uint32`， `int64`， `uint16`， `uint64`，和`char`。 列舉型別以.NET framework 型別繼承自`System.Enum`，依序繼承自`System.ValueType`。 因此，它們是實值型別上堆疊或內嵌在所包含的物件，基礎類型的任何值都是有效的列舉值。 這相當重要時模式比對列舉值，因為您必須提供的模式，攔截未命名的值。

`enum` F # 程式庫中的函式可用來產生列舉值，即使值以外的預先定義的其中一個已命名的值。 您使用`enum`函式，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

預設值`enum`函式適用於類型`int32`。 因此，它不能與其他基本類型的列舉型別。 相反地，使用下列項目。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]
    
## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[轉型和轉換](casting-and-conversions.md)
