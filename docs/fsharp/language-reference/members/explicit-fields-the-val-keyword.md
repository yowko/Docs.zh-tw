---
title: 明確欄位：val 關鍵字
description: "深入瞭解 F # ' val ' 關鍵字，這是用來宣告在類別或結構類型中儲存值的位置，而不需要初始化型別。"
ms.date: 08/15/2020
ms.openlocfilehash: 9f5599a241f27b234eeacf48327b4ccbc46ed38c
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811778"
---
# <a name="explicit-fields-the-val-keyword"></a>明確欄位：val 關鍵字

`val` 關鍵字用來宣告位置以儲存類別中或結構類型中的值，但不初始化。 以這種方式宣告的儲存位置稱為 *明確欄位*。 `val` 關鍵字的另一種用法是搭配 `member` 關鍵字來宣告自動實作的屬性。 如需自動執行之屬性的詳細資訊，請參閱 [屬性](properties.md)。

## <a name="syntax"></a>語法

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>備註

在類別或結構類型中定義欄位通常是使用 `let` 繫結。 不過，`let` 繫結必須在類別建構函式中初始化，但不一定總是可行、必要或適合。 當您想要未初始化的欄位時，您可以使用 `val` 關鍵字。

明確欄位可以是靜態或非靜態。 *存取修飾*詞可以是 `public` 、 `private` 或 `internal` 。 根據預設，明確欄位是 public。 這不同於類別中永遠是 private 的 `let` 繫結。

具有主要的函式之類別類型中的明確欄位必須有 [DefaultValue](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-defaultvalueattribute.html) 屬性。 這個屬性指定欄位初始化為零。 欄位的類型必須支援零初始化。 下列類型支援零初始化：

- 具有零值的基本類型。
- 支援 null 值的類型，可能為正常值、異常值或值的一種表示法。 這包括類別、Tuple、記錄、函式、介面、.NET 參考類型、`unit` 類型，以及差別聯集類型。
- .NET 實值類型。
- 所有欄位都支援預設零值的一種結構。

例如，稱為 `someField` 的不可變動欄位在 .NET 編譯表示法中有一個名稱為 `someField@` 的支援欄位，您可以使用名為 `someField` 的屬性來存取儲存的值。

對於可變動欄位，.NET 編譯表示法是 .NET 欄位。

> [!WARNING]
> .NET Framework 命名空間 `System.ComponentModel` 包含具有相同名稱的屬性。 如需此屬性的詳細資訊，請參閱 <xref:System.ComponentModel.DefaultValueAttribute>。

下列程式碼示範在具有主要建構函式的類別中使用明確欄位，也示範 `let` 繫結，方便對照。 請注意，`let` 繫結的欄位 `myInt1` 是 private。 從成員方法參考 `let` 繫結欄位 `myInt1` 時，不需要自我識別項 `this`。 但是，當您參考明確欄位 `myInt2` 和 `myString` 時，需要自我識別項。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

輸出如下所示：

```console
11 12 abc
30 def
```

下列程式碼示範在沒有主要建構函式的類別中使用明確欄位。 在此例子中，`DefaultValue` 屬性不是必要的，但在類型所定義的建構函式中必須初始化所有欄位。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

輸出為 `35 22`。

下列程式碼示範在結構中使用明確欄位。 因為結構是實值型別，所以它會自動具有無參數的函式，將其欄位的值設定為零。 因此，不需要 `DefaultValue` 屬性。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

輸出為 `11 xyz`。

請**注意**，如果您要使用不含關鍵字的欄位來初始化您的結構 `mutable` `mutable` ，您的指派將會處理在指派之後將會捨棄的結構複本。 因此，您的結構不會變更。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

平常不適合使用明確欄位。 一般而言，可能的話，應該在類別中使用 `let` 繫結，而不是明確欄位。 在某些互通性案例中，例如您需要定義結構供平台叫用呼叫原生 API，或在 COM interop 案例中，明確欄位很有用。 如需詳細資訊，請參閱 [外部函數](../functions/external-functions.md)。 另一種情況是您使用 F# 程式碼產生器來產生沒有主要建構函式的類別，這時也可能需要明確欄位。 對於執行緒靜態變數或類似的建構，明確欄位也很有用。 如需詳細資訊，請參閱`System.ThreadStaticAttribute`。

當關鍵字 `member val` 一起出現在類型定義中時，這是自動實作屬性的定義。 如需詳細資訊，請參閱 [屬性](properties.md)中定義的介面的私用 C++ 專屬實作。

## <a name="see-also"></a>另請參閱

- [屬性](properties.md)
- [成員](index.md)
- [`let` 類別中的系結](let-bindings-in-classes.md)
