---
title: 程式碼引號
description: '瞭解 F # 程式碼引號，這是一種語言功能，可讓您以程式設計方式產生和使用 F # 程式碼運算式。'
ms.date: 08/13/2020
ms.openlocfilehash: dc37fdbd6cd29e5ee94e5c0186dfe2bfeb666f32
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557190"
---
# <a name="code-quotations"></a>程式碼引號

本文描述程式 *代碼引號* ，這是一種語言功能，可讓您以程式設計方式產生和使用 F # 程式碼運算式。 這項功能可讓您產生表示 F # 程式碼的抽象語法樹狀目錄。 然後，您可以根據應用程式的需求來進行和處理抽象語法樹狀結構。 例如，您可以使用樹狀結構來產生 F # 程式碼，或以某些其他語言產生程式碼。

## <a name="quoted-expressions"></a>引號運算式

以 *引號括* 住的運算式是程式碼中的 F # 運算式，以不是編譯為程式一部分的方式來分隔，而是編譯成代表 F # 運算式的物件。 您可以使用下列兩種方式的其中一種來標記引號運算式：使用類型資訊或不使用類型資訊。 如果您想要包含型別資訊，請使用符號 `<@` 和 `@>` 來分隔加上引號的運算式。 如果您不需要類型資訊，您可以使用符號 `<@@` 和 `@@>` 。 下列程式碼顯示型別和不具類型的引號。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

如果您不包含型別資訊，則遍歷大型運算式樹狀結構會比較快速。 以具型別符號括住的運算式產生型別是 `Expr<'T>` ，其中型別參數的運算式類型是由 F # 編譯器的型別推斷演算法所決定。 當您使用不含類型資訊的程式碼引號時，引號運算式 [的類型為](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html)非泛型型別的運算式。 您可以呼叫具類型類別上的 [Raw](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr-1.html#Raw) 屬性 `Expr` 來取得不具類型的 `Expr` 物件。

有各種靜態方法，可讓您以程式設計方式在類別中產生 F # 運算式物件， `Expr` 而不需要使用加上引號的運算式。

請注意，程式碼引號必須包含完整的運算式。 例如，針對系結 `let` ，您需要系結名稱的定義，以及使用此系結的其他運算式。 在詳細資訊語法中，這是緊接在關鍵字後面的運算式 `in` 。 在模組的最上層，這只是模組中的下一個運算式，但在引號中，它是明確需要的。

因此，下列運算式無效。

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

但下列運算式是有效的。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

若要評估 F # 引號，您必須使用 [f # 引號評估](https://github.com/fsprojects/FSharp.Quotations.Evaluator)工具。 它可支援評估和執行 F # 運算式物件。

F # 引號也會保留類型條件約束資訊。 請考慮下列範例：

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

函數所產生的條件約束 `inline` 會保留在程式碼 qutoation 中。 `negate`現在可以評估函數的 quotated 表單。

## <a name="expr-type"></a>Expr 類型

型別的實例 `Expr` 代表 F # 運算式。 `Expr`F # 程式庫檔中記載了泛型和非泛型型別。 如需詳細資訊，請參閱 [fsharp.core。引號命名空間](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations.html) 和 [引號. Expr 類別](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html)。

## <a name="splicing-operators"></a>接合運算子

接合可讓您將常值程式碼引號與您以程式設計方式或另一個程式碼引號建立的運算式結合。 `%`And `%%` 運算子可讓您將 F # 運算式物件加入至程式碼引號中。 您可以使用 `%` 運算子將具類型的運算式物件插入類型的引號中; 您可以使用 `%%` 運算子將不具類型的運算式物件插入不具類型的引號中。 這兩個運算子都是一元前置運算子。 因此，如果是類型的不具類型的 `expr` 運算式 `Expr` ，則下列程式碼是有效的。

```fsharp
<@@ 1 + %%expr @@>
```

如果 `expr` 是類型的類型引號 `Expr<int>` ，則下列程式碼是有效的。

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例說明如何使用程式碼引號將 F # 程式碼放入 expression 物件中，然後列印代表運算式的 F # 程式碼。 定義的函 `println` 式包含遞迴函 `print` 式，該函式會 `Expr` 以易記格式顯示) 類型的 F # 運算式物件 (。 [Fsharp.core](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-patternsmodule.html)中有數個使用中的[模式，可以](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html)用來分析運算式的物件。 這個範例不包含可能出現在 F # 運算式中的所有可能模式。 任何無法辨識的模式都會觸發與萬用字元模式的相符 (`_`) 並且會使用方法來呈現，而此 `ToString` 方法會在型別上 `Expr` 讓您知道要加入至比對運算式的現用模式。

### <a name="code"></a>程式碼

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>輸出

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>範例

### <a name="description"></a>描述

您也可以使用 [exprshape.rebuildshapecombination 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html) 中的三個作用中模式，以較少的現用模式來流覽運算式樹狀架構。 當您想要遍歷樹狀結構，但在大部分的節點中都不需要所有資訊時，這些作用中的模式會很有用。 當您使用這些模式時，任何 F # 運算式都會符合下列三種模式的其中一種： `ShapeVar` 如果運算式為變數，則為，如果運算式是 `ShapeLambda` lambda 運算式，或 `ShapeCombination` 運算式為任何其他專案，則為。 如果您使用先前程式碼範例中的作用中模式來遍歷運算式樹狀架構，則必須使用更多的模式來處理所有可能的 F # 運算式類型，而且您的程式碼會比較複雜。 如需詳細資訊，請參閱 [exprshape.rebuildshapecombination. ShapeVar&#124;ShapeLambda&#124;Shapecombination 現用現用模式](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html#(%20|ShapeVar|ShapeLambda|ShapeCombination|%20))。

下列程式碼範例可作為更複雜周遊的基礎。 在此程式碼中，會針對涉及函式呼叫的運算式建立運算式樹狀架構 `add` 。 [SpecificCall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html#(%20|SpecificCall|_|%20))現用模式可用來偵測運算式樹狀架構中的任何呼叫 `add` 。 此現用模式會將呼叫的引數指派給 `exprList` 值。 在此情況下，只有兩個，因此會提取這些函式，並在引數上以遞迴方式呼叫函式。 結果會插入至程式碼引號，表示 `mul` 使用拼接運算子 () 的呼叫 `%%` 。 `println`上一個範例中的函式是用來顯示結果。

其他現用模式分支中的程式碼只會重新產生相同的運算式樹狀架構，所以產生的運算式中唯一的變更就是從變更 `add` 為 `mul` 。

### <a name="code"></a>程式碼

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>輸出

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
