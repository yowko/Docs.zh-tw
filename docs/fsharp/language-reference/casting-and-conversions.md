---
title: 轉型和轉換
description: 瞭解程式F#設計語言如何為各種基本型別之間的算術轉換提供轉換運算子。
ms.date: 02/20/2020
ms.openlocfilehash: 5f9727d14a7ae070e0f0f71fa0a0abe04f662071
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543582"
---
# <a name="casting-and-conversions-f"></a>轉型和轉換 (F#)

本主題描述中F#類型轉換的支援。

## <a name="arithmetic-types"></a>算術類型

F#提供各種基本類型（例如整數和浮點類型之間）之算術轉換的轉換運算子。 整數和字元轉換運算子具有 checked 和 unchecked 形式;浮點運算子和 `enum` 轉換運算子不會。 未檢查的表單定義于 `Microsoft.FSharp.Core.Operators` 中，而檢查的表單則定義于 `Microsoft.FSharp.Core.Operators.Checked`中。 如果產生的值超出目標型別的限制，檢查的表單會檢查溢位並產生執行時間例外狀況。

每個運算子的名稱都與目的地類型的名稱相同。 例如，在下列程式碼中，已明確標注類型，`byte` 會以兩個不同的意義出現。 第一次出現的是類型，而第二個是轉換運算子。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

下表顯示在中定義的F#轉換運算子。

|運算子|描述|
|--------|-----------|
|`byte`|轉換成 byte，這是8位不帶正負號的類型。|
|`sbyte`|轉換成帶正負號的位元組。|
|`int16`|轉換為16位帶正負號的整數。|
|`uint16`|轉換成16位不帶正負號的整數。|
|`int32, int`|轉換為32位帶正負號的整數。|
|`uint32`|轉換為32位不帶正負號的整數。|
|`int64`|轉換為64位帶正負號的整數。|
|`uint64`|轉換為64位不帶正負號的整數。|
|`nativeint`|轉換成原生整數。|
|`unativeint`|轉換成不帶正負號的原生整數。|
|`float, double`|轉換成64位雙精確度 IEEE 浮點數字。|
|`float32, single`|轉換成32位單精確度 IEEE 浮點數字。|
|`decimal`|轉換成 `System.Decimal`。|
|`char`|轉換成 `System.Char`，Unicode 字元。|
|`enum`|轉換為列舉類型。|

除了內建的基本型別之外，您還可以使用這些運算子搭配以適當簽章來執行 `op_Explicit` 或 `op_Implicit` 方法的類型。 例如，`int` 轉換運算子適用于任何提供靜態方法的類型，`op_Explicit` 會採用類型做為參數，並傳回 `int`。 如需方法無法以傳回型別多載之一般規則的特殊例外狀況，您可以為 `op_Explicit` 和 `op_Implicit`執行此動作。

## <a name="enumerated-types"></a>列舉類型

`enum` 運算子是泛型運算子，接受一個代表要轉換之 `enum` 類型的類型參數。 當它轉換成列舉型別時，型別推斷會嘗試判斷您想要轉換的 `enum` 型別。 在下列範例中，變數 `col1` 不會明確地加上批註，但它的型別是從較新的等號比較測試推斷而來。 因此，編譯器可以推算您轉換成 `Color` 列舉。 或者，您也可以提供類型注釋，如同下列範例中的 `col2`。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

您也可以將目標列舉型別明確指定為型別參數，如下列程式碼所示：

```fsharp
let col3 = enum<Color> 3
```

請注意，只有在列舉的基礎類型與所轉換的類型相容時，列舉轉換才會生效。 在下列程式碼中，因為 `int32` 與 `uint32`不相符，所以轉換無法編譯。

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

如需詳細資訊，[請參閱列舉](enumerations.md)。

## <a name="casting-object-types"></a>轉換物件類型

物件階層中的類型之間的轉換是物件導向程式設計的基礎。 轉換有兩種基本類型： [向上轉換] （upcasting）和 [向下轉換] （向下檢視）。 向上轉換階層表示從衍生的物件參考轉換成基底物件參考。 只要基類位於衍生類別的繼承階層架構中，這類轉換就一定會正常執行。 將階層從基底物件參考向下轉換至衍生的物件參考時，只有在物件實際上是正確目的地（衍生）類型的實例，或衍生自目的地類型的類型時，才會成功。

F#提供這些轉換類型的運算子。 `:>` 運算子會向上轉換階層，而 `:?>` 運算子會在階層中往下轉換。

### <a name="upcasting"></a>Upcasting

在許多物件導向語言中，upcasting 都是隱含的;在F#中，規則會稍有不同。 當您將引數傳遞至物件類型上的方法時，會自動套用 Upcasting。 不過，針對模組中的 let 系結函式，除非將參數類型宣告為彈性類型，否則 upcasting 不會是自動的。 如需詳細資訊，請參閱[彈性類型](flexible-Types.md)。

`:>` 運算子會執行靜態轉換，這表示轉換成功是在編譯時期決定的。 如果使用 `:>` 的轉換成功編譯，它是有效的轉換，而且在執行時間沒有任何可能發生的失敗。

您也可以使用 `upcast` 運算子來執行這類轉換。 下列運算式會指定階層的向上轉換：

```fsharp
upcast expression
```

當您使用向上轉型運算子時，編譯器會嘗試從內容推斷您要轉換成的類型。 如果編譯器無法判斷目標型別，則編譯器會報告錯誤。 可能需要類型注釋。

### <a name="downcasting"></a>向下檢視

`:?>` 運算子會執行動態轉換，這表示在執行時間會決定轉換成功與否。 使用 `:?>` 運算子的轉換不會在編譯時期檢查;但是在執行時間，會嘗試轉換成指定的型別。 如果物件與目標型別相容，轉換就會成功。 如果物件與目標型別不相容，則執行時間會引發 `InvalidCastException`。

您也可以使用 `downcast` 運算子來執行動態類型轉換。 下列運算式會指定將階層向下轉換為從程式內容推斷的類型：

```fsharp
downcast expression
```

就 `upcast` 運算子而言，如果編譯器無法從內容推斷特定目標型別，就會報告錯誤。 可能需要類型注釋。

下列程式碼說明如何使用 `:>` 和 `:?>` 運算子。 此程式碼說明當您知道轉換會成功時，最適合使用 `:?>` 運算子，因為它會在轉換失敗時擲回 `InvalidCastException`。 如果您不知道轉換將會成功，使用 `match` 運算式的類型測試會較好，因為它可避免產生例外狀況的額外負荷。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

因為泛型運算子 `downcast` 和 `upcast` 依賴型別推斷來判斷引數和傳回型別，所以在上述程式碼中，您可以取代

```fsharp
let base1 = d1 :> Base1
```

取代為

```fsharp
let base1: Base1 = upcast d1
```

請注意，類型注釋是必要的，因為 `upcast` 本身無法判斷基類。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
