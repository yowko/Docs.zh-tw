---
title: 程式碼引號 (F#)
description: '了解 F # 程式碼引號，可讓您產生及以程式設計方式使用 F # 程式碼運算式的語言功能。'
ms.date: 05/16/2016
ms.openlocfilehash: 27e9cf1d99e2b5955cc6359653fc87bdbe824cc7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44191600"
---
# <a name="code-quotations"></a>程式碼引號

> [!NOTE]
API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

本主題描述*程式碼引號*，可讓您產生及以程式設計方式使用 F # 程式碼運算式的語言功能。 這項功能可讓您產生代表 F # 程式碼的抽象語法樹狀結構。 可以周遊的抽象語法樹狀目錄，然後根據您的應用程式的需求進行處理。 例如，您可以使用樹狀目錄中產生 F # 程式碼，或某些其他語言產生程式碼。

## <a name="quoted-expressions"></a>加上引號的運算式

A*加上引號運算式*是 F # 運算式在程式碼中分隔的方式不編譯一部分您的程式，但改為會編譯成 F # 運算式所表示的物件。 您可以將標記的引號括住的運算式中有兩種： 使用型別資訊，或不具類型資訊。 如果您想要包含的型別資訊，您會使用符號`<@`和`@>`來分隔引號括住的運算式。 如果您不需要型別資訊，您會使用符號`<@@`和`@@>`。 下列程式碼顯示具型別和不具類型的引號。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

周遊大型的運算式樹狀結構會更快，如果您不會包含類型資訊。 使用具類型的符號加上引號運算式的結果類型是`Expr<'T>`，而且型別參數都有運算式，由 F # 編譯器的型別推斷演算法的類型。 當您使用不具類型資訊的程式碼引號時，加上引號運算式的類型為非泛型型別[Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65)。 您可以呼叫[Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2)具型別的的屬性`Expr`類別來取得不具型別的`Expr`物件。

有各種不同的靜態方法，讓您產生 F # 運算式物件以程式設計方式在`Expr`類別，而不使用加上引號的運算式。

請注意，程式碼引號必須包含完整的運算式。 針對`let`繫結，例如，您需要定義的繫結的名稱和其他運算式，使用此繫結。 在詳細的語法中，這是遵循`in`關鍵字。 在最上層模組中，這是只在模組中下, 一個運算式，但在引號中，是明確需要。

因此，下列運算式不是有效的。

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

但是，下列運算式都是有效。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

若要使用的程式碼引號，您必須新增匯入宣告 (使用`open`關鍵字)，開啟[Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2)命名空間。

F # PowerPack 支援用於評估和執行 F # 運算式物件。

## <a name="expr-type"></a>Expr 型別

執行個體`Expr`類型代表 F # 運算式。 泛型和非泛型`Expr`類型會記錄在 F # 程式庫文件。 如需詳細資訊，請參閱 < [Microsoft.FSharp.Quotations 命名空間](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d)並[Quotations.Expr 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d)。

## <a name="splicing-operators"></a>接合運算子

接合，可讓您將使用您建立以程式設計方式或從另一個程式碼引號運算式的常值程式碼引號。 `%`和`%%`運算子可讓您將 F # 運算式物件新增至程式碼引號。 您使用`%`的具類型的運算式物件插入具類型的引號的運算子; 您可以使用`%%`運算子，將不具類型的運算式物件插入不具類型的引號。 這兩個運算子是一元前置運算子。 因此如果`expr`是不具類型的型別運算式`Expr`，下列程式碼就有效。

```fsharp
<@@ 1 + %%expr @@>
```

而如果`expr`是型別的具型別的引號`Expr<int>`，下列程式碼就有效。

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例說明如何使用以 F # 程式碼置於 expression 物件，並列印表示運算式的 F # 程式碼的程式碼引號。 函式`println`定義，其中包含遞迴函式`print`顯示 F # 運算式物件 (類型的`Expr`) 的好記的格式。 有數個使用中的模式[Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4)並[Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd)模組，可用來分析運算式物件。 此範例不包含在 F # 運算式中可能會出現的所有可能模式。 任何無法辨識的模式就會觸發萬用字元模式比對 (`_`)，且會使用轉換`ToString`方法，它會上`Expr`類型，可讓您知道將比對運算式中的模式。

### <a name="code"></a>程式碼

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a>輸出

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>範例

### <a name="description"></a>描述

您也可以使用中的三個作用中模式[ExprShape 模組](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de)周遊運算式樹狀架構，具有較少的使用中模式。 當您想要周遊樹狀結構，但您不需要大部分的節點中的所有資訊，這些作用中的模式可以很有用。 當您使用這些模式時，任何的 F # 運算式符合下列三種模式的其中一個：`ShapeVar`變數中，運算式是否`ShapeLambda`如果運算式是 lambda 運算式，或`ShapeCombination`如果運算式可以是任何其他項目。 如果您周遊運算式樹狀架構所使用的作用中的模式，如同先前的程式碼範例時，您必須使用許多更多的模式來處理所有可能 F # 運算式的類型，和您的程式碼將會更複雜。 如需詳細資訊，請參閱 < [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination 現用模式](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d)。

下列程式碼範例可用做為基礎的更複雜的周遊。 在此程式碼中，牽涉到函式呼叫的運算式建立運算式樹狀架構`add`。 [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d)作用中的模式用來偵測到的任何呼叫`add`運算式樹狀結構中。 此作用中的模式會指派至呼叫的引數`exprList`值。 在此情況下，有一些只有兩種，因此這些取出和呼叫的函式會以遞迴方式引數。 結果會插入到代表呼叫的程式碼引號`mul`使用拼接運算子 (`%%`)。 `println`上一個範例中的函數用來顯示結果。

其他使用中模式分支中的程式碼只會重新產生相同的運算式樹狀架構，因此在產生的運算式中的唯一變更是從變更`add`至`mul`。

### <a name="code"></a>程式碼

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a>輸出

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
