---
title: let 繫結
description: '瞭解如何使用 F # 「let」系結，這會將識別碼與值或函式產生關聯。'
ms.date: 05/16/2016
ms.openlocfilehash: 6f2396f480c5e6c631d0022f4732419ee5b07db6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812220"
---
# <a name="let-bindings"></a>let 繫結

系結會將識別碼與值或函數*產生關聯。* 您可以使用 `let` 關鍵字將名稱系結至值或函數。

## <a name="syntax"></a>語法

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>備註

`let`關鍵字是在系結運算式中用來定義一個或多個名稱的值或函數值。 運算式最簡單的形式會將名稱系結 `let` 至簡單的值，如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

如果您使用新的行將運算式與識別碼分開，則必須縮排運算式的每一行，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

如下列程式碼所示，您可以指定包含名稱的模式，而不只是名稱。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*主體運算式*是使用名稱的運算式。 本文運算式會出現在自己的行上，並以關鍵字中的第一個字元縮排對齊 `let` ：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

系結 `let` 可以出現在模組層級、類別類型的定義或區域範圍中，例如在函式定義中。 `let`模組或類別類型中最上層的系結不需要有內文運算式，但在其他範圍層級，則需要主體運算式。 系結名稱可在定義點之後使用，但不能在系結出現之前的任何時間點使用 `let` ，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a>函數系結

函數系結會遵循值系結的規則，但函數系結會包含函數名稱和參數，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

一般情況下，參數是模式，例如元組模式：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

系結 `let` 運算式會評估為最後一個運算式的值。 因此，在下列程式碼範例中，的值 `result` 是從 `100 * function3 (1, 2)` 評估為的計算 `300` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

如需詳細資訊，請參閱[函式](index.md)。

## <a name="type-annotations"></a>類型注釋

您可以指定參數的類型，方法是包含冒號 (： ) 後面接著類型名稱，全都以括弧括住。 您也可以在最後一個參數之後附加冒號和類型，以指定傳回值的類型。 的完整類型注釋 `function1` （使用整數做為參數類型）如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

如果沒有明確的型別參數，則會使用型別推斷來判斷函式的參數類型。 這可能包括自動將參數的類型一般化為泛型。

如需詳細資訊，請參閱 [自動一般化](../generics/automatic-generalization.md) 和 [型別推斷](../type-inference.md)。

## <a name="let-bindings-in-classes"></a>類別中的 let 繫結

系結 `let` 可以出現在類別型別中，但不能出現在結構或記錄型別中。 若要在類別型別中使用 let 系結，類別必須有主要的函式。 函式參數必須出現在類別定義中的類型名稱之後。 類別型別中的系結 `let` 會定義該類別型別的私用欄位和成員，並且與型別中的系結形成型別的系結程式 `do` 代碼。 下列程式碼範例會顯示 `MyClass` 具有私用欄位 `field1` 和的類別 `field2` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

和的範圍 `field1` `field2` 僅限於宣告它們的型別。 如需詳細資訊，請參閱類別和[類別](../classes.md) [ `let` 中](../members/let-bindings-in-classes.md)的系結。

## <a name="type-parameters-in-let-bindings"></a>Let 系結中的型別參數

在 `let` 模組層級、型別或計算運算式中的系結可以有明確的型別參數。 運算式中的 let 系結（例如在函式定義內）不能有型別參數。 如需詳細資訊，請參閱[泛型](../generics/index.md)。

## <a name="attributes-on-let-bindings"></a>Let 系結上的屬性

屬性可以套用至模組中的最上層系結 `let` ，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a>Let 系結的範圍和協助工具

以 let 系結宣告的實體範圍僅限於包含範圍 (的部分，例如函式、模組、檔案或類別在系結出現之後) 。 因此，您可以說 let 系結將名稱引入範圍中。 在模組中，只要模組可供存取，模組的用戶端就可以存取 let 系結值或函數，因為模組中的 let 系結會編譯成模組的公用函式。 相較之下，「讓類別中的系結」是類別的私用。

一般來說，當用戶端程式代碼使用模組時，模組中的函式必須以模組的名稱來限定。 例如，如果模組 `Module1` 有一個函式 `function1` ，則使用者會指定 `Module1.function1` 參考該函數。

模組的使用者可能會使用匯入宣告，讓該模組內的函式可供使用，而不會受到模組名稱的限定。 在剛才提及的範例中，模組的使用者可以在該案例中使用匯入宣告開啟模組， `Module1` 之後再參考 `function1` 直接。

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

某些模組具有 [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html)屬性，這表示它們所公開的函式必須以模組的名稱來限定。 例如，F # 清單模組有這個屬性。

如需模組和存取控制的詳細資訊，請參閱 [模組](../modules.md) 和 [存取控制](../access-control.md)。

## <a name="see-also"></a>請參閱

- [函式](index.md)
- [`let` 類別中的系結](../members/let-bindings-in-classes.md)
