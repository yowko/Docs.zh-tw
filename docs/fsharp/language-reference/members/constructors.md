---
title: 建構函式
description: 瞭解如何在中F#定義和使用函數, 以建立和初始化類別和結構物件。
ms.date: 05/16/2016
ms.openlocfilehash: 6769ec7fc6768090d8ae68e21946a58829b6eea0
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736841"
---
# <a name="constructors"></a>建構函式

本文說明如何定義和使用函式來建立和初始化類別和結構物件。

## <a name="construction-of-class-objects"></a>類別物件的結構

類別類型的物件具有函數。 有兩種類型的函數。 其中一個是主要的函式, 其參數會出現在型別名稱後面的括弧中。 您可以使用`new`關鍵字來指定其他選擇性的其他函式。 任何這類額外的函式都必須呼叫主要的函式。

主要的函式`let`包含`do`和系結, 它會出現在類別定義的開頭。 系結會宣告類別`do`的私用欄位和方法, 系結會執行程式碼。 `let` 如需類別函`let`式中系結的詳細資訊, 請參閱[ `let`類別中的](let-bindings-in-classes.md)系結。 如需有關`do`在函式中系結的詳細資訊, 請參閱[ `do`類別中的](do-bindings-in-classes.md)系結。

不論您想要呼叫的是主要的函式或其他的函數, 您都可以使用`new`運算式來建立物件, 並搭配或不搭配選擇性`new`關鍵字。 您可以使用函式引數來初始化您的物件, 方法是依序列出引數, 並以逗號分隔並括在括弧中, 或使用括弧中的具名引數和值。 您也可以在物件的結構中, 使用屬性名稱和指派值來設定物件的屬性, 就如同使用命名的函式引數一樣。

下列程式碼說明具有函式和各種建立物件方法的類別：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

其輸出如下：

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>結構結構

結構會遵循類別的所有規則。 因此, 您可以擁有主要的函式, 也可以使用`new`來提供其他的函式。 不過, 結構和類別之間有一個重要的差異: 結構可以有無參數的函式 (也就是沒有引數的函式), 即使未定義主要的函式。 無參數的函式會將所有欄位初始化為該類型的預設值, 通常為零或其相等。 您為結構定義的任何函式都必須至少有一個引數，才不會與無參數的處理常式衝突。

此外, 結構通常會有使用`val`關鍵字建立的欄位; 類別也可以有這些欄位。 具有使用`val`關鍵字定義之欄位的結構和類別, 也可以使用記錄運算式在其他的函式中進行初始化, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

如需詳細資訊, [請參閱明確欄位:`val`關鍵字。](explicit-fields-the-val-keyword.md)

## <a name="executing-side-effects-in-constructors"></a>在函式中執行副作用

類別中的主要函式可以在系結中`do`執行程式碼。 不過, 如果您必須在不使用`do`系結的其他函式中執行程式碼, 該怎麼辦？ 若要這麼做, 請使用`then`關鍵字。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

主要的函式的副作用仍會執行。 因此，輸出如下所示：

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>函式中的自我識別碼

在其他成員中, 您會在每個成員的定義中提供目前物件的名稱。 您也可以使用緊接在函式參數後面的`as`關鍵字, 將自我識別碼放在類別定義的第一行。 下列範例說明此語法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

在其他的函式中, 您也可以將`as`子句放在函式參數後面, 以定義自我識別碼。 下列範例說明這個語法：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

當您嘗試在完全定義物件之前使用它, 可能會發生問題。 因此, 使用自我識別碼可能會導致編譯器發出警告, 並插入額外的檢查, 以確保物件的成員在初始化之前不會被存取。 您應該只在`do`主要函式的系結中, 或在其他函式中的`then`關鍵字之後, 使用自我識別碼。

本身識別碼的名稱不一定要是`this`。 它可以是任何有效的識別碼。

## <a name="assigning-values-to-properties-at-initialization"></a>在初始化時將值指派給屬性

您可以將表單`property = value`指派清單附加至函式的引數清單, 以將值指派給初始化程式碼中的類別物件屬性。 如下列程式碼範例所示：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

下列版本的舊版程式碼說明了一般引數、選擇性引數和屬性設定在一個函式呼叫中的組合：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>繼承類別中的函式

從具有函數的基類繼承時, 您必須在繼承子句中指定其引數。 如需詳細資訊, 請參閱[函數和繼承](../inheritance.md#constructors-and-inheritance)。

## <a name="static-constructors-or-type-constructors"></a>靜態的函式或類型的構造函式

除了指定建立物件的程式碼之外, 也`let`可以`do`在第一次使用類型來執行類型層級的初始化之前, 在執行的類別類型中撰寫靜態和系結。 如需詳細資訊, [ `let` ](let-bindings-in-classes.md)請參閱類別中[ `do` ](do-bindings-in-classes.md)類別和系結中的系結。

## <a name="see-also"></a>另請參閱

- [成員](index.md)
