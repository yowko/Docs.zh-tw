---
title: 程式碼引號
description: '瞭解 F # 程式碼引號，這是一種語言功能，可讓您以程式設計方式產生和使用 F # 程式碼運算式。'
ms.date: 08/13/2020
ms.openlocfilehash: 070e127397a5da7d70281d08ef7cafdb9b4f4fe5
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558331"
---
# <a name="code-quotations"></a><span data-ttu-id="60d6d-103">程式碼引號</span><span class="sxs-lookup"><span data-stu-id="60d6d-103">Code quotations</span></span>

<span data-ttu-id="60d6d-104">本文描述程式 *代碼引號*，這是一種語言功能，可讓您以程式設計方式產生和使用 F # 程式碼運算式。</span><span class="sxs-lookup"><span data-stu-id="60d6d-104">This article describes *code quotations*, a language feature that enables you to generate and work with F# code expressions programmatically.</span></span> <span data-ttu-id="60d6d-105">這項功能可讓您產生表示 F # 程式碼的抽象語法樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="60d6d-105">This feature lets you generate an abstract syntax tree that represents F# code.</span></span> <span data-ttu-id="60d6d-106">然後，您可以根據應用程式的需求來進行和處理抽象語法樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="60d6d-106">The abstract syntax tree can then be traversed and processed according to the needs of your application.</span></span> <span data-ttu-id="60d6d-107">例如，您可以使用樹狀結構來產生 F # 程式碼，或以某些其他語言產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="60d6d-107">For example, you can use the tree to generate F# code or generate code in some other language.</span></span>

## <a name="quoted-expressions"></a><span data-ttu-id="60d6d-108">引號運算式</span><span class="sxs-lookup"><span data-stu-id="60d6d-108">Quoted Expressions</span></span>

<span data-ttu-id="60d6d-109">以 *引號括* 住的運算式是程式碼中的 F # 運算式，以不是編譯為程式一部分的方式來分隔，而是編譯成代表 F # 運算式的物件。</span><span class="sxs-lookup"><span data-stu-id="60d6d-109">A *quoted expression* is an F# expression in your code that is delimited in such a way that it is not compiled as part of your program, but instead is compiled into an object that represents an F# expression.</span></span> <span data-ttu-id="60d6d-110">您可以使用下列兩種方式的其中一種來標記引號運算式：使用類型資訊或不使用類型資訊。</span><span class="sxs-lookup"><span data-stu-id="60d6d-110">You can mark a quoted expression in one of two ways: either with type information or without type information.</span></span> <span data-ttu-id="60d6d-111">如果您想要包含型別資訊，請使用符號 `<@` 和 `@>` 來分隔加上引號的運算式。</span><span class="sxs-lookup"><span data-stu-id="60d6d-111">If you want to include type information, you use the symbols `<@` and `@>` to delimit the quoted expression.</span></span> <span data-ttu-id="60d6d-112">如果您不需要類型資訊，您可以使用符號 `<@@` 和 `@@>` 。</span><span class="sxs-lookup"><span data-stu-id="60d6d-112">If you do not need type information, you use the symbols `<@@` and `@@>`.</span></span> <span data-ttu-id="60d6d-113">下列程式碼顯示型別和不具類型的引號。</span><span class="sxs-lookup"><span data-stu-id="60d6d-113">The following code shows typed and untyped quotations.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

<span data-ttu-id="60d6d-114">如果您不包含型別資訊，則遍歷大型運算式樹狀結構會比較快速。</span><span class="sxs-lookup"><span data-stu-id="60d6d-114">Traversing a large expression tree is faster if you do not include type information.</span></span> <span data-ttu-id="60d6d-115">以具型別符號括住的運算式產生型別是 `Expr<'T>` ，其中型別參數的運算式類型是由 F # 編譯器的型別推斷演算法所決定。</span><span class="sxs-lookup"><span data-stu-id="60d6d-115">The resulting type of an expression quoted with the typed symbols is `Expr<'T>`, where the type parameter has the type of the expression as determined by the F# compiler's type inference algorithm.</span></span> <span data-ttu-id="60d6d-116">當您使用不含類型資訊的程式碼引號時，引號運算式 [的類型為](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html)非泛型型別的運算式。</span><span class="sxs-lookup"><span data-stu-id="60d6d-116">When you use code quotations without type information, the type of the quoted expression is the non-generic type [Expr](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html).</span></span> <span data-ttu-id="60d6d-117">您可以呼叫具類型類別上的 [Raw](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr-1.html#Raw) 屬性 `Expr` 來取得不具類型的 `Expr` 物件。</span><span class="sxs-lookup"><span data-stu-id="60d6d-117">You can call the [Raw](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr-1.html#Raw) property on the typed `Expr` class to obtain the untyped `Expr` object.</span></span>

<span data-ttu-id="60d6d-118">有各種靜態方法，可讓您以程式設計方式在類別中產生 F # 運算式物件， `Expr` 而不需要使用加上引號的運算式。</span><span class="sxs-lookup"><span data-stu-id="60d6d-118">There are a variety of static methods that allow you to generate F# expression objects programmatically in the `Expr` class without using quoted expressions.</span></span>

<span data-ttu-id="60d6d-119">請注意，程式碼引號必須包含完整的運算式。</span><span class="sxs-lookup"><span data-stu-id="60d6d-119">Note that a code quotation must include a complete expression.</span></span> <span data-ttu-id="60d6d-120">例如，針對系結 `let` ，您需要系結名稱的定義，以及使用此系結的其他運算式。</span><span class="sxs-lookup"><span data-stu-id="60d6d-120">For a `let` binding, for example, you need both the definition of the bound name and an additional expression that uses the binding.</span></span> <span data-ttu-id="60d6d-121">在詳細資訊語法中，這是緊接在關鍵字後面的運算式 `in` 。</span><span class="sxs-lookup"><span data-stu-id="60d6d-121">In verbose syntax, this is an expression that follows the `in` keyword.</span></span> <span data-ttu-id="60d6d-122">在模組的最上層，這只是模組中的下一個運算式，但在引號中，它是明確需要的。</span><span class="sxs-lookup"><span data-stu-id="60d6d-122">At the top-level in a module, this is just the next expression in the module, but in a quotation, it is explicitly required.</span></span>

<span data-ttu-id="60d6d-123">因此，下列運算式無效。</span><span class="sxs-lookup"><span data-stu-id="60d6d-123">Therefore, the following expression is not valid.</span></span>

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

<span data-ttu-id="60d6d-124">但下列運算式是有效的。</span><span class="sxs-lookup"><span data-stu-id="60d6d-124">But the following expressions are valid.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

<span data-ttu-id="60d6d-125">若要評估 F # 引號，您必須使用 [f # 引號評估](https://github.com/fsprojects/FSharp.Quotations.Evaluator)工具。</span><span class="sxs-lookup"><span data-stu-id="60d6d-125">To evaluate F# quotations, you must use the [F# Quotation Evaluator](https://github.com/fsprojects/FSharp.Quotations.Evaluator).</span></span> <span data-ttu-id="60d6d-126">它可支援評估和執行 F # 運算式物件。</span><span class="sxs-lookup"><span data-stu-id="60d6d-126">It provides support for evaluating and executing F# expression objects.</span></span>

## <a name="expr-type"></a><span data-ttu-id="60d6d-127">Expr 類型</span><span class="sxs-lookup"><span data-stu-id="60d6d-127">Expr Type</span></span>

<span data-ttu-id="60d6d-128">型別的實例 `Expr` 代表 F # 運算式。</span><span class="sxs-lookup"><span data-stu-id="60d6d-128">An instance of the `Expr` type represents an F# expression.</span></span> <span data-ttu-id="60d6d-129">`Expr`F # 程式庫檔中記載了泛型和非泛型型別。</span><span class="sxs-lookup"><span data-stu-id="60d6d-129">Both the generic and the non-generic `Expr` types are documented in the F# library documentation.</span></span> <span data-ttu-id="60d6d-130">如需詳細資訊，請參閱 [fsharp.core。引號命名空間](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations.html) 和 [引號. Expr 類別](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html)。</span><span class="sxs-lookup"><span data-stu-id="60d6d-130">For more information, see [FSharp.Quotations Namespace](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations.html) and [Quotations.Expr Class](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html).</span></span>

## <a name="splicing-operators"></a><span data-ttu-id="60d6d-131">接合運算子</span><span class="sxs-lookup"><span data-stu-id="60d6d-131">Splicing Operators</span></span>

<span data-ttu-id="60d6d-132">接合可讓您將常值程式碼引號與您以程式設計方式或另一個程式碼引號建立的運算式結合。</span><span class="sxs-lookup"><span data-stu-id="60d6d-132">Splicing enables you to combine literal code quotations with expressions that you have created programmatically or from another code quotation.</span></span> <span data-ttu-id="60d6d-133">`%`And `%%` 運算子可讓您將 F # 運算式物件加入至程式碼引號中。</span><span class="sxs-lookup"><span data-stu-id="60d6d-133">The `%` and `%%` operators enable you to add an F# expression object into a code quotation.</span></span> <span data-ttu-id="60d6d-134">您可以使用 `%` 運算子將具類型的運算式物件插入類型的引號中; 您可以使用 `%%` 運算子將不具類型的運算式物件插入不具類型的引號中。</span><span class="sxs-lookup"><span data-stu-id="60d6d-134">You use the `%` operator to insert a typed expression object into a typed quotation; you use the `%%` operator to insert an untyped expression object into an untyped quotation.</span></span> <span data-ttu-id="60d6d-135">這兩個運算子都是一元前置運算子。</span><span class="sxs-lookup"><span data-stu-id="60d6d-135">Both operators are unary prefix operators.</span></span> <span data-ttu-id="60d6d-136">因此，如果是類型的不具類型的 `expr` 運算式 `Expr` ，則下列程式碼是有效的。</span><span class="sxs-lookup"><span data-stu-id="60d6d-136">Thus if `expr` is an untyped expression of type `Expr`, the following code is valid.</span></span>

```fsharp
<@@ 1 + %%expr @@>
```

<span data-ttu-id="60d6d-137">如果 `expr` 是類型的類型引號 `Expr<int>` ，則下列程式碼是有效的。</span><span class="sxs-lookup"><span data-stu-id="60d6d-137">And if `expr` is a typed quotation of type `Expr<int>`, the following code is valid.</span></span>

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a><span data-ttu-id="60d6d-138">範例</span><span class="sxs-lookup"><span data-stu-id="60d6d-138">Example</span></span>

### <a name="description"></a><span data-ttu-id="60d6d-139">描述</span><span class="sxs-lookup"><span data-stu-id="60d6d-139">Description</span></span>

<span data-ttu-id="60d6d-140">下列範例說明如何使用程式碼引號將 F # 程式碼放入 expression 物件中，然後列印代表運算式的 F # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="60d6d-140">The following example illustrates the use of code quotations to put F# code into an expression object and then print the F# code that represents the expression.</span></span> <span data-ttu-id="60d6d-141">定義的函 `println` 式包含遞迴函 `print` 式，該函式會 `Expr` 以易記格式顯示) 類型的 F # 運算式物件 (。</span><span class="sxs-lookup"><span data-stu-id="60d6d-141">A function `println` is defined that contains a recursive function `print` that displays an F# expression object (of type `Expr`) in a friendly format.</span></span> <span data-ttu-id="60d6d-142">[Fsharp.core](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-patternsmodule.html)中有數個使用中的[模式，可以](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html)用來分析運算式的物件。</span><span class="sxs-lookup"><span data-stu-id="60d6d-142">There are several active patterns in the [FSharp.Quotations.Patterns](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-patternsmodule.html) and [FSharp.Quotations.DerivedPatterns](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html) modules that can be used to analyze expression objects.</span></span> <span data-ttu-id="60d6d-143">這個範例不包含可能出現在 F # 運算式中的所有可能模式。</span><span class="sxs-lookup"><span data-stu-id="60d6d-143">This example does not include all the possible patterns that might appear in an F# expression.</span></span> <span data-ttu-id="60d6d-144">任何無法辨識的模式都會觸發與萬用字元模式的相符 (`_`) 並且會使用方法來呈現，而此 `ToString` 方法會在型別上 `Expr` 讓您知道要加入至比對運算式的現用模式。</span><span class="sxs-lookup"><span data-stu-id="60d6d-144">Any unrecognized pattern triggers a match to the wildcard pattern (`_`) and is rendered by using the `ToString` method, which, on the `Expr` type, lets you know the active pattern to add to your match expression.</span></span>

### <a name="code"></a><span data-ttu-id="60d6d-145">程式碼</span><span class="sxs-lookup"><span data-stu-id="60d6d-145">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a><span data-ttu-id="60d6d-146">輸出</span><span class="sxs-lookup"><span data-stu-id="60d6d-146">Output</span></span>

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a><span data-ttu-id="60d6d-147">範例</span><span class="sxs-lookup"><span data-stu-id="60d6d-147">Example</span></span>

### <a name="description"></a><span data-ttu-id="60d6d-148">描述</span><span class="sxs-lookup"><span data-stu-id="60d6d-148">Description</span></span>

<span data-ttu-id="60d6d-149">您也可以使用 [exprshape.rebuildshapecombination 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html) 中的三個作用中模式，以較少的現用模式來流覽運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="60d6d-149">You can also use the three active patterns in the [ExprShape module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html) to traverse expression trees with fewer active patterns.</span></span> <span data-ttu-id="60d6d-150">當您想要遍歷樹狀結構，但在大部分的節點中都不需要所有資訊時，這些作用中的模式會很有用。</span><span class="sxs-lookup"><span data-stu-id="60d6d-150">These active patterns can be useful when you want to traverse a tree but you do not need all the information in most of the nodes.</span></span> <span data-ttu-id="60d6d-151">當您使用這些模式時，任何 F # 運算式都會符合下列三種模式的其中一種： `ShapeVar` 如果運算式為變數，則為，如果運算式是 `ShapeLambda` lambda 運算式，或 `ShapeCombination` 運算式為任何其他專案，則為。</span><span class="sxs-lookup"><span data-stu-id="60d6d-151">When you use these patterns, any F# expression matches one of the following three patterns: `ShapeVar` if the expression is a variable, `ShapeLambda` if the expression is a lambda expression, or `ShapeCombination` if the expression is anything else.</span></span> <span data-ttu-id="60d6d-152">如果您使用先前程式碼範例中的作用中模式來遍歷運算式樹狀架構，則必須使用更多的模式來處理所有可能的 F # 運算式類型，而且您的程式碼會比較複雜。</span><span class="sxs-lookup"><span data-stu-id="60d6d-152">If you traverse an expression tree by using the active patterns as in the previous code example, you have to use many more patterns to handle all possible F# expression types, and your code will be more complex.</span></span> <span data-ttu-id="60d6d-153">如需詳細資訊，請參閱 [exprshape.rebuildshapecombination. ShapeVar&#124;ShapeLambda&#124;Shapecombination 現用現用模式](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html#(%20|ShapeVar|ShapeLambda|ShapeCombination|%20))。</span><span class="sxs-lookup"><span data-stu-id="60d6d-153">For more information, see [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination Active Pattern](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html#(%20|ShapeVar|ShapeLambda|ShapeCombination|%20)).</span></span>

<span data-ttu-id="60d6d-154">下列程式碼範例可作為更複雜周遊的基礎。</span><span class="sxs-lookup"><span data-stu-id="60d6d-154">The following code example can be used as a basis for more complex traversals.</span></span> <span data-ttu-id="60d6d-155">在此程式碼中，會針對涉及函式呼叫的運算式建立運算式樹狀架構 `add` 。</span><span class="sxs-lookup"><span data-stu-id="60d6d-155">In this code, an expression tree is created for an expression that involves a function call, `add`.</span></span> <span data-ttu-id="60d6d-156">[SpecificCall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html#(%20|SpecificCall|_|%20))現用模式可用來偵測運算式樹狀架構中的任何呼叫 `add` 。</span><span class="sxs-lookup"><span data-stu-id="60d6d-156">The [SpecificCall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html#(%20|SpecificCall|_|%20)) active pattern is used to detect any call to `add` in the expression tree.</span></span> <span data-ttu-id="60d6d-157">此現用模式會將呼叫的引數指派給 `exprList` 值。</span><span class="sxs-lookup"><span data-stu-id="60d6d-157">This active pattern assigns the arguments of the call to the `exprList` value.</span></span> <span data-ttu-id="60d6d-158">在此情況下，只有兩個，因此會提取這些函式，並在引數上以遞迴方式呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="60d6d-158">In this case, there are only two, so these are pulled out and the function is called recursively on the arguments.</span></span> <span data-ttu-id="60d6d-159">結果會插入至程式碼引號，表示 `mul` 使用拼接運算子 () 的呼叫 `%%` 。</span><span class="sxs-lookup"><span data-stu-id="60d6d-159">The results are inserted into a code quotation that represents a call to `mul` by using the splice operator (`%%`).</span></span> <span data-ttu-id="60d6d-160">`println`上一個範例中的函式是用來顯示結果。</span><span class="sxs-lookup"><span data-stu-id="60d6d-160">The `println` function from the previous example is used to display the results.</span></span>

<span data-ttu-id="60d6d-161">其他現用模式分支中的程式碼只會重新產生相同的運算式樹狀架構，所以產生的運算式中唯一的變更就是從變更 `add` 為 `mul` 。</span><span class="sxs-lookup"><span data-stu-id="60d6d-161">The code in the other active pattern branches just regenerates the same expression tree, so the only change in the resulting expression is the change from `add` to `mul`.</span></span>

### <a name="code"></a><span data-ttu-id="60d6d-162">程式碼</span><span class="sxs-lookup"><span data-stu-id="60d6d-162">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a><span data-ttu-id="60d6d-163">輸出</span><span class="sxs-lookup"><span data-stu-id="60d6d-163">Output</span></span>

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a><span data-ttu-id="60d6d-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60d6d-164">See also</span></span>

- [<span data-ttu-id="60d6d-165">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="60d6d-165">F# Language Reference</span></span>](index.md)
