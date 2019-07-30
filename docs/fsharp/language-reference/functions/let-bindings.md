---
title: let 繫結
description: 瞭解如何使用F# 「let」系結, 以將識別碼與值或函式產生關聯。
ms.date: 05/16/2016
ms.openlocfilehash: 654631c7d1c48d8737e6098c98efee54cfdd91be
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630634"
---
# <a name="let-bindings"></a>let 繫結

系  結會將識別碼與值或函數產生關聯。 您可以使用`let`關鍵字, 將名稱系結至值或函數。

## <a name="syntax"></a>語法

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>備註

`let`關鍵字是在系結運算式中用來定義一或多個名稱的值或函數值。 `let`運算式的最簡單形式會將名稱系結至簡單的值, 如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

如果您使用新的行來分隔運算式與識別碼, 則必須縮排運算式的每一行, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

如下列程式碼所示, 您可以指定包含名稱的模式, 而不只是名稱。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*主體運算式*是使用名稱的運算式。 本文運算式會顯示在它自己的行上, 並與`let`關鍵字中的第一個字元完全對齊:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

`let`系結可能會出現在模組層級、類別類型的定義中, 或在本機範圍 (如函式定義中)。 `let`在模組或類別類型中, 位於最上層的系結不需要具有主體運算式, 但在其他範圍層級, 則需要主體運算式。 系結名稱可在定義點之後使用, 但不會出現在系結之前`let`的任何時間點, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a>函數系結

函數系結會遵循值系結的規則, 不同之處在于函式系結包含函式名稱和參數, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

一般而言, 參數是模式, 例如元組模式:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

`let`系結運算式會評估為最後一個運算式的值。 因此, 在下列`result`程式碼範例中, 的值是從`100 * function3 (1, 2)` `300`計算得出的。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

如需詳細資訊，請參閱[函式](index.md)。

## <a name="type-annotations"></a>類型注釋

您可以指定參數的類型, 方法是包含冒號 (:)後面接著一個型別名稱, 並以括弧括住。 您也可以在最後一個參數之後附加冒號和類型, 藉以指定傳回值的類型。 具有整數做為參數`function1`類型的完整類型注釋, 將如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

當沒有明確型別參數時, 會使用型別推斷來判斷函數的參數類型。 這可能包括自動將參數的類型一般化為泛型。

如需詳細資訊, 請參閱[自動一般化](../generics/automatic-generalization.md)和[型別推斷](../type-inference.md)。

## <a name="let-bindings-in-classes"></a>類別中的 let 繫結

`let`系結可以出現在類別類型中, 而不是在結構或記錄類型中。 若要在類別類型中使用 let 系結, 類別必須具有主要的函式。 函式參數必須出現在類別定義中的型別名稱之後。 類別`let`類型中的系結會定義該類別類型的私用欄位和成員, `do`連同類型中的系結, 會形成該類型主要的程式碼。 下列程式碼範例顯示具有私`MyClass`用欄位`field1`和`field2`的類別。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

`field1` 和`field2`的範圍僅限於宣告它們的類型。 如需詳細資訊, 請參閱[ `let`類別](../members/let-bindings-in-classes.md)和[類別](../classes.md)中的系結。

## <a name="type-parameters-in-let-bindings"></a>Let 系結中的型別參數

`let`模組層級、類型或計算運算式中的系結可以有明確類型參數。 運算式中的 let 系結 (例如函式定義內) 不能有型別參數。 如需詳細資訊，請參閱[泛型](../generics/index.md)。

## <a name="attributes-on-let-bindings"></a>Let 系結上的屬性

屬性可以套用至模組中的最`let`上層系結, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a>Let 系結的範圍和可存取性

使用 let 系結所宣告之實體的範圍, 會在系結出現之後, 限制為包含範圍的部分 (例如函式、模組、檔案或類別)。 因此, 您可以將「let 系結」引進範圍中的名稱。 在模組中, 只要模組可供存取, 模組的用戶端就可以存取「let 系結」值或函數, 因為「let 系結」會編譯成模組的公用函式。 相反地, 類別中的 let 系結是私用的。

一般來說, 當用戶端程式代碼使用模組的名稱時, 模組中的函式必須以該模組的名稱來限定。 例如, 如果模組`Module1`具有`function1`函式, 則使用者會指定`Module1.function1`來參考該函式。

模組的使用者可以使用匯入宣告, 讓該模組內的函式可供使用, 而不需要由模組名稱限定。 在剛才所述的範例中, 模組的使用者可以在此情況下, 使用匯入`Module1`宣告開啟模組, 並在之後`function1`直接參考。

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

有些模組具有屬性[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), 這表示它們所公開的函式必須以模組的名稱來限定。 例如, F# List 模組具有這個屬性。

如需模組和存取控制的詳細資訊, 請參閱[模組](../modules.md)和[存取控制](../access-control.md)。

## <a name="see-also"></a>另請參閱

- [函式](index.md)
- [類別中的 `let` 繫結](../members/let-bindings-in-classes.md)
