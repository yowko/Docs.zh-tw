---
title: 程式碼引號
description: '瞭解 F # 程式碼報價，這是一種語言功能，可讓您以程式設計方式產生及使用 F # 程式碼運算式。'
ms.date: 05/16/2016
ms.openlocfilehash: bb5c03edd180c42667731bb90d7a1f624ed2e522
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855387"
---
# <a name="code-quotations"></a>程式碼引號

本文描述程式*代碼引號*，這是一種語言功能，可讓您以程式設計方式產生及使用 F # 程式碼運算式。 這項功能可讓您產生代表 F # 程式碼的抽象語法樹狀結構。 然後，可以根據您的應用程式需求來進行遍歷和處理的抽象語法樹狀結構。 例如，您可以使用樹狀結構來產生 F # 程式碼，或以其他語言產生程式碼。

> [!NOTE]
> F # 的 docs.microsoft.com API 參考不完整。 如果您遇到任何中斷的連結，請改為參考[F # 核心程式庫檔](https://fsharp.github.io/fsharp-core-docs/)。

## <a name="quoted-expressions"></a>引號運算式

*加上引號的運算式*是您程式碼中的 F # 運算式，其分隔方式為不會編譯為程式的一部分，而是編譯成代表 F # 運算式的物件。 您可以使用下列兩種方式的其中一種來標記引號運算式：具有類型資訊或不含類型資訊。 如果您想要包含型別資訊，請使用符號 `<@` 和 `@>` 來分隔加上引號的運算式。 如果您不需要類型資訊，請使用符號 `<@@` 和 `@@>` 。 下列程式碼顯示具類型和不具類型的引號。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

如果您不包含型別資訊，則可以更快速地遍歷大型運算式樹狀架構。 以具型別符號括住之運算式的結果型別為 `Expr<'T>` ，其中的型別參數具有 F # 編譯器的型別推斷演算法所決定的運算式型別。 當您使用沒有類型資訊的程式碼引號時，引號運算式的類型為非泛型型別[Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65)。 您可以在具類型的類別上呼叫[Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2)屬性 `Expr` ，以取得不具類型的 `Expr` 物件。

有各種靜態方法，可讓您在類別中以程式設計方式產生 F # 運算式物件， `Expr` 而不需要使用加上引號的運算式。

請注意，程式碼引號必須包含完整的運算式。 例如，針對系結 `let` ，您需要系結名稱的定義，以及使用此系結的其他運算式。 在 verbose 語法中，這是緊接在關鍵字後面的運算式 `in` 。 在模組的頂層，這只是模組中的下一個運算式，但在引號中，它是明確需要的。

因此，下列運算式無效。

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

但下列運算式是有效的。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

若要評估 F # 報價，您必須使用[f # 引號評估](https://github.com/fsprojects/FSharp.Quotations.Evaluator)工具。 它提供評估和執行 F # 運算式物件的支援。

## <a name="expr-type"></a>Expr 類型

類型的實例 `Expr` 代表 F # 運算式。 一般和非泛型 `Expr` 類型都記載于 F # 程式庫檔中。 如需詳細資訊，請參閱[fsharp.core. 引號 Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d)和[引號. Expr Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d)。

## <a name="splicing-operators"></a>接合運算子

接合可讓您使用以程式設計方式或另一個程式碼引號建立的運算式，結合常值的程式碼引號。 `%`和 `%%` 運算子可讓您將 F # 運算式物件新增至程式碼引號。 您可以使用 `%` 運算子將具類型的運算式物件插入至具類型的引號中; 您可以使用 `%%` 運算子將不具類型的運算式物件插入不具類型的引號中。 這兩個運算子都是一元前置運算子。 因此 `expr` ，如果是類型的不具類型運算式 `Expr` ，則下列程式碼是有效的。

```fsharp
<@@ 1 + %%expr @@>
```

而且，如果是類型的具類型 `expr` 引號 `Expr<int>` ，則下列程式碼是有效的。

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例說明如何使用程式碼引號將 F # 程式碼放入運算式物件中，然後列印代表運算式的 F # 程式碼。 定義的函 `println` 式包含遞迴函 `print` 式，會以易記的格式顯示) 類型的 F # 運算式物件 (`Expr` 。 [Fsharp.core](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4)中有數個使用中的模式，可以用來分析運算式物件，也就是[DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd)模組。 這個範例不包含可能出現在 F # 運算式中的所有可能模式。 任何無法辨識的模式都會觸發與萬用字元模式 (`_`) 的比對，而則是使用 `ToString` 方法轉譯，而在型別上，則可 `Expr` 讓您知道要加入至 match 運算式的現用模式。

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

您也可以使用[exprshape.rebuildshapecombination 模組](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de)中的三個作用中模式，以較少的現用模式來進行運算式樹狀架構的處理。 當您想要穿越樹狀結構，但在大部分的節點中都不需要所有資訊時，這些現用模式可能很有用。 當您使用這些模式時，任何 F # 運算式都會符合下列三種模式之一： `ShapeVar` 如果運算式為變數，則為，如果運算式是 `ShapeLambda` lambda 運算式，則為， `ShapeCombination` 如果運算式為任何其他專案，則為。 如果您使用上述程式碼範例中的現用模式來流覽運算式樹狀架構，您必須使用更多的模式來處理所有可能的 F # 運算式類型，而您的程式碼會更複雜。 如需詳細資訊，請參閱[exprshape.rebuildshapecombination. ShapeVar&#124;ShapeLambda&#124;Shapecombination 現用現用模式](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d)。

下列程式碼範例可用來做為更複雜周遊的基礎。 在此程式碼中，會針對牽涉到函式呼叫的運算式建立運算式樹狀架構 `add` 。 [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d)現用模式是用來偵測 `add` 運算式樹狀結構中的任何呼叫。 此現用模式會將呼叫的引數指派給 `exprList` 值。 在此情況下，只會有兩個，因此會提取這些函式，並在引數上以遞迴方式呼叫函數。 系統會將結果插入程式碼引號中，表示 `mul` 使用拼接運算子 () 的呼叫 `%%` 。 `println`上一個範例中的函式是用來顯示結果。

另一個現用模式分支中的程式碼只會重新產生相同的運算式樹狀架構，因此，所產生之運算式中的唯一變更是從變更為 `add` `mul` 。

### <a name="code"></a>程式碼

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>輸出

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
