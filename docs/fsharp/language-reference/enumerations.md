---
title: 列舉
description: 瞭解如何使用F#列舉來取代常值, 讓您的程式碼更容易閱讀和維護。
ms.date: 05/16/2016
ms.openlocfilehash: 784cd9612b199e4648bb64432d3b4422ad35f649
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630345"
---
# <a name="enumerations"></a>列舉

列舉 (也稱為列舉  ) 是整數類資料類型, 其中的標籤會指派給值的子集。 列舉可用來取代常值，讓程式碼更容易閱讀及維護。

## <a name="syntax"></a>語法

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>備註

列舉看起來很像具有簡單值的區分聯集, 但可以指定值。 這些值通常是從0或1開始的整數, 或是代表位位置的整數。 如果列舉的目的是要代表位位置, 您也應該使用[Flags](xref:System.FlagsAttribute)屬性。

列舉的基礎類型取決於所使用的常值, 因此, 您可以針對不帶正負號的整數 ( `1u` `uint32`) 類型, 使用具有後置字元`2u`的常值, 例如、等等。

當您參考已命名的值時, 您必須使用列舉類型本身的名稱做為辨識符號, 也就是`enum-name.value1`, 而不`value1`只是。 此行為不同于相異聯集的行為。 這是因為列舉一律具有[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)屬性。

下列程式碼顯示列舉的宣告和使用。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

您可以使用適當的運算子, 輕鬆地將列舉轉換成基礎類型, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

列舉型別可以具有下列其中一種基礎類型`sbyte`: `byte`、 `int16` `int64`、 `uint16`、 `int32`、 `uint32`、 `uint16` `uint64`、、、和`char`。 列舉類型會在 .NET Framework 中表示為繼承自`System.Enum`的類型, 而後者又繼承自。 `System.ValueType` 因此, 它們是位於堆疊上或內嵌于包含物件中的實數值型別, 而基礎類型的任何值都是列舉的有效值。 這在使用列舉值進行模式比對時很重要, 因為您必須提供可攔截未命名值的模式。

連結`enum` F#庫中的函式可以用來產生列舉值, 甚至是其中一個預先定義的已命名值以外的值。 您可以使用`enum`函數, 如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

預設`enum`函式可與類型`int32`搭配使用。 因此, 它不能與具有其他基礎類型的列舉類型搭配使用。 相反地, 請使用下列。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

此外, 列舉的案例一律會以的`public`形式發出。 這是為了讓它們與C# .net 平臺的其餘部分一致。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [轉型和轉換](casting-and-conversions.md)
