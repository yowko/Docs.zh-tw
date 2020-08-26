---
title: 列舉
description: '瞭解如何使用 F # 列舉來取代常值，讓您的程式碼更容易讀取和維護。'
ms.date: 08/15/2020
ms.openlocfilehash: 5f298691ce48a06c203930c7742cf007c819dc33
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812103"
---
# <a name="enumerations"></a>列舉

列舉也稱為*列舉，這*是將標籤指派給值子集的整數類資料類型。 *enums* 列舉可用來取代常值，讓程式碼更容易閱讀及維護。

## <a name="syntax"></a>語法

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>備註

列舉看起來很像是具有簡單值的差異聯集，不同之處在于可以指定值。 這些值通常是從0或1開始的整數，或是代表位位置的整數。 如果列舉的目的是要代表位位置，您也應該使用 [旗標](xref:System.FlagsAttribute) 屬性。

列舉的基礎類型取決於所使用的常值，因此，例如，您可以針對不帶正負號的 `1u` `2u` 整數 () 類型，使用具有尾碼的常值（例如、等） `uint32` 。

當您參考命名值時，您必須使用列舉型別本身的名稱做為辨識符號，也就是，而 `enum-name.value1` 不只是 `value1` 。 這種行為與不同聯集的行為不同。 這是因為列舉一律具有 [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) 屬性。

下列程式碼顯示列舉和使用列舉。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

您可以使用適當的運算子輕鬆地將列舉轉換成基礎型別，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

列舉類型可以具有下列其中一個基礎類型： `sbyte` 、 `byte` 、 `int16` 、 `uint16` 、、、、、 `int32` `uint32` `int64` `uint16` `uint64` 和 `char` 。 列舉型別會在 .NET Framework 中表示為繼承自的型別，而繼承自的類型 `System.Enum` `System.ValueType` 。 因此，它們是位於堆疊上或內嵌于包含物件中的實值型別，而基礎類型的任何值都是列舉的有效值。 這在對列舉值進行模式比對時很重要，因為您必須提供可攔截未命名值的模式。

`enum`F # 程式庫中的函式可用來產生列舉值，甚至是除了其中一個預先定義的命名值以外的值。 您可以使用 `enum` 如下所示的函數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

預設 `enum` 函數適用于類型 `int32` 。 因此，它不能搭配具有其他基礎類型的列舉類型使用。 請改用下列各項。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

此外，列舉的案例一律會發出為 `public` 。 這是為了使其符合 c # 和 .NET 平臺的其餘部分。

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [轉型和轉換](casting-and-conversions.md)
