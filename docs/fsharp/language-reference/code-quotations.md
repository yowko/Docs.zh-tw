---
title: 程式碼引號
description: 瞭解程式F#代碼報價, 這是一種語言功能, 可讓您以F#程式設計方式產生及使用程式碼運算式。
ms.date: 05/16/2016
ms.openlocfilehash: c6ec0078c685a6452f49edd289b01491dd62e3db
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630424"
---
# <a name="code-quotations"></a><span data-ttu-id="e1c5b-103">程式碼引號</span><span class="sxs-lookup"><span data-stu-id="e1c5b-103">Code Quotations</span></span>

> [!NOTE]
> <span data-ttu-id="e1c5b-104">API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-104">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="e1c5b-105">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="e1c5b-106">本主題描述程式*代碼引號*, 這是一種語言功能, 可讓您F#以程式設計方式產生及使用程式碼運算式。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-106">This topic describes *code quotations*, a language feature that enables you to generate and work with F# code expressions programmatically.</span></span> <span data-ttu-id="e1c5b-107">這項功能可讓您產生代表F#程式碼的抽象語法樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-107">This feature lets you generate an abstract syntax tree that represents F# code.</span></span> <span data-ttu-id="e1c5b-108">然後, 可以根據您的應用程式需求來進行遍歷和處理的抽象語法樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-108">The abstract syntax tree can then be traversed and processed according to the needs of your application.</span></span> <span data-ttu-id="e1c5b-109">例如, 您可以使用樹狀結構來產生F#程式碼, 或以其他語言產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-109">For example, you can use the tree to generate F# code or generate code in some other language.</span></span>

## <a name="quoted-expressions"></a><span data-ttu-id="e1c5b-110">引號運算式</span><span class="sxs-lookup"><span data-stu-id="e1c5b-110">Quoted Expressions</span></span>

<span data-ttu-id="e1c5b-111">*加上引號*的運算式F#是程式碼中的運算式, 以這種方式分隔, 而不會編譯成您的程式的一部分, 而是編譯成代表F#運算式的物件。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-111">A *quoted expression* is an F# expression in your code that is delimited in such a way that it is not compiled as part of your program, but instead is compiled into an object that represents an F# expression.</span></span> <span data-ttu-id="e1c5b-112">您可以使用下列兩種方式的其中一種來標記引號運算式: 具有類型資訊或不含類型資訊。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-112">You can mark a quoted expression in one of two ways: either with type information or without type information.</span></span> <span data-ttu-id="e1c5b-113">如果您想要包含型別資訊, 請使用符號`<@`和`@>`來分隔加上引號的運算式。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-113">If you want to include type information, you use the symbols `<@` and `@>` to delimit the quoted expression.</span></span> <span data-ttu-id="e1c5b-114">如果您不需要類型資訊, 請使用符號`<@@`和。 `@@>`</span><span class="sxs-lookup"><span data-stu-id="e1c5b-114">If you do not need type information, you use the symbols `<@@` and `@@>`.</span></span> <span data-ttu-id="e1c5b-115">下列程式碼顯示具類型和不具類型的引號。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-115">The following code shows typed and untyped quotations.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

<span data-ttu-id="e1c5b-116">如果您不包含型別資訊, 則可以更快速地遍歷大型運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-116">Traversing a large expression tree is faster if you do not include type information.</span></span> <span data-ttu-id="e1c5b-117">以具型別符號括住之運算式的結果型`Expr<'T>`別為, 其中的型別參數具有由F#編譯器類型推斷演算法所決定的運算式型別。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-117">The resulting type of an expression quoted with the typed symbols is `Expr<'T>`, where the type parameter has the type of the expression as determined by the F# compiler's type inference algorithm.</span></span> <span data-ttu-id="e1c5b-118">當您使用沒有類型資訊的程式碼引號時, 引號運算式的類型為非泛型型別[Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65)。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-118">When you use code quotations without type information, the type of the quoted expression is the non-generic type [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65).</span></span> <span data-ttu-id="e1c5b-119">您可以在具類型的`Expr`類別上呼叫 [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) 屬性, 以取得不具類型的`Expr`物件。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-119">You can call the [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) property on the typed `Expr` class to obtain the untyped `Expr` object.</span></span>

<span data-ttu-id="e1c5b-120">有各種靜態方法, 可讓您在F# `Expr`類別中以程式設計方式產生運算式物件, 而不需要使用加上引號的運算式。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-120">There are a variety of static methods that allow you to generate F# expression objects programmatically in the `Expr` class without using quoted expressions.</span></span>

<span data-ttu-id="e1c5b-121">請注意, 程式碼引號必須包含完整的運算式。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-121">Note that a code quotation must include a complete expression.</span></span> <span data-ttu-id="e1c5b-122">`let`例如, 針對系結, 您需要系結名稱的定義, 以及使用此系結的其他運算式。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-122">For a `let` binding, for example, you need both the definition of the bound name and an additional expression that uses the binding.</span></span> <span data-ttu-id="e1c5b-123">在 verbose 語法中, 這是緊接在`in`關鍵字後面的運算式。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-123">In verbose syntax, this is an expression that follows the `in` keyword.</span></span> <span data-ttu-id="e1c5b-124">在模組的頂層, 這只是模組中的下一個運算式, 但在引號中, 它是明確需要的。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-124">At the top-level in a module, this is just the next expression in the module, but in a quotation, it is explicitly required.</span></span>

<span data-ttu-id="e1c5b-125">因此, 下列運算式無效。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-125">Therefore, the following expression is not valid.</span></span>

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

<span data-ttu-id="e1c5b-126">但下列運算式是有效的。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-126">But the following expressions are valid.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

<span data-ttu-id="e1c5b-127">若要F#評估報價, 您必須使用[ F#報價評估](https://github.com/fsprojects/FSharp.Quotations.Evaluator)工具。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-127">To evaluate F# quotations, you must use the [F# Quotation Evaluator](https://github.com/fsprojects/FSharp.Quotations.Evaluator).</span></span> <span data-ttu-id="e1c5b-128">它提供了評估和執行F# expression 物件的支援。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-128">It provides support for evaluating and executing F# expression objects.</span></span>

## <a name="expr-type"></a><span data-ttu-id="e1c5b-129">Expr 類型</span><span class="sxs-lookup"><span data-stu-id="e1c5b-129">Expr Type</span></span>

<span data-ttu-id="e1c5b-130">`Expr`類型的實例代表F#運算式。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-130">An instance of the `Expr` type represents an F# expression.</span></span> <span data-ttu-id="e1c5b-131">連結F#庫檔中記載一般和非`Expr`泛型型別。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-131">Both the generic and the non-generic `Expr` types are documented in the F# library documentation.</span></span> <span data-ttu-id="e1c5b-132">如需詳細資訊, 請參閱[fsharp.core. 引號 Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d)和[引號. Expr Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-132">For more information, see [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) and [Quotations.Expr Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).</span></span>

## <a name="splicing-operators"></a><span data-ttu-id="e1c5b-133">接合運算子</span><span class="sxs-lookup"><span data-stu-id="e1c5b-133">Splicing Operators</span></span>

<span data-ttu-id="e1c5b-134">接合可讓您使用以程式設計方式或另一個程式碼引號建立的運算式, 結合常值的程式碼引號。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-134">Splicing enables you to combine literal code quotations with expressions that you have created programmatically or from another code quotation.</span></span> <span data-ttu-id="e1c5b-135">和運算子可讓您將F#運算式物件新增至程式碼引號。 `%%` `%`</span><span class="sxs-lookup"><span data-stu-id="e1c5b-135">The `%` and `%%` operators enable you to add an F# expression object into a code quotation.</span></span> <span data-ttu-id="e1c5b-136">您可以使用`%`運算子將具類型的運算式物件插入至具類型的引號中; `%%`您可以使用運算子將不具類型的運算式物件插入不具類型的引號中。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-136">You use the `%` operator to insert a typed expression object into a typed quotation; you use the `%%` operator to insert an untyped expression object into an untyped quotation.</span></span> <span data-ttu-id="e1c5b-137">這兩個運算子都是一元前置運算子。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-137">Both operators are unary prefix operators.</span></span> <span data-ttu-id="e1c5b-138">因此, `expr`如果是類型`Expr`的不具類型運算式, 則下列程式碼是有效的。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-138">Thus if `expr` is an untyped expression of type `Expr`, the following code is valid.</span></span>

```fsharp
<@@ 1 + %%expr @@>
```

<span data-ttu-id="e1c5b-139">而且, `expr`如果是類型`Expr<int>`的具類型引號, 則下列程式碼是有效的。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-139">And if `expr` is a typed quotation of type `Expr<int>`, the following code is valid.</span></span>

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a><span data-ttu-id="e1c5b-140">範例</span><span class="sxs-lookup"><span data-stu-id="e1c5b-140">Example</span></span>

### <a name="description"></a><span data-ttu-id="e1c5b-141">說明</span><span class="sxs-lookup"><span data-stu-id="e1c5b-141">Description</span></span>

<span data-ttu-id="e1c5b-142">下列範例說明如何使用程式碼引號將程式碼F#放入運算式物件中, 然後列印表示F#運算式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-142">The following example illustrates the use of code quotations to put F# code into an expression object and then print the F# code that represents the expression.</span></span> <span data-ttu-id="e1c5b-143">定義了一個函F#式, 其中包含以易記格式顯示運算式物件 (型`Expr`別為) 的遞迴函數。 `print` `println`</span><span class="sxs-lookup"><span data-stu-id="e1c5b-143">A function `println` is defined that contains a recursive function `print` that displays an F# expression object (of type `Expr`) in a friendly format.</span></span> <span data-ttu-id="e1c5b-144">[Fsharp.core](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4)中有數個使用中的模式, 可以用來分析運算式物件, 也就是[DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd)模組。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-144">There are several active patterns in the [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) and [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) modules that can be used to analyze expression objects.</span></span> <span data-ttu-id="e1c5b-145">這個範例不包含可能出現在F#運算式中的所有可能模式。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-145">This example does not include all the possible patterns that might appear in an F# expression.</span></span> <span data-ttu-id="e1c5b-146">任何無法辨識的模式都會觸發與萬用字元模式的`_`比對 (), 而且會`ToString`使用方法轉譯, 而此`Expr`方法會在型別上, 讓您知道要加入至比對運算式的現用模式。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-146">Any unrecognized pattern triggers a match to the wildcard pattern (`_`) and is rendered by using the `ToString` method, which, on the `Expr` type, lets you know the active pattern to add to your match expression.</span></span>

### <a name="code"></a><span data-ttu-id="e1c5b-147">程式碼</span><span class="sxs-lookup"><span data-stu-id="e1c5b-147">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a><span data-ttu-id="e1c5b-148">Output</span><span class="sxs-lookup"><span data-stu-id="e1c5b-148">Output</span></span>

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a><span data-ttu-id="e1c5b-149">範例</span><span class="sxs-lookup"><span data-stu-id="e1c5b-149">Example</span></span>

### <a name="description"></a><span data-ttu-id="e1c5b-150">描述</span><span class="sxs-lookup"><span data-stu-id="e1c5b-150">Description</span></span>

<span data-ttu-id="e1c5b-151">您也可以使用[exprshape.rebuildshapecombination 模組](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de)中的三個作用中模式, 以較少的現用模式來進行運算式樹狀架構的處理。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-151">You can also use the three active patterns in the [ExprShape module](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) to traverse expression trees with fewer active patterns.</span></span> <span data-ttu-id="e1c5b-152">當您想要穿越樹狀結構, 但在大部分的節點中都不需要所有資訊時, 這些現用模式可能很有用。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-152">These active patterns can be useful when you want to traverse a tree but you do not need all the information in most of the nodes.</span></span> <span data-ttu-id="e1c5b-153">當您使用這些模式時, F#任何運算式都會符合下列三種模式的`ShapeVar`其中之一: 如果運算式為變數`ShapeLambda` , 則為; 如果運算式為 lambda 運算式`ShapeCombination` , 則為, 如果運算式為任何其他專案, 則為。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-153">When you use these patterns, any F# expression matches one of the following three patterns: `ShapeVar` if the expression is a variable, `ShapeLambda` if the expression is a lambda expression, or `ShapeCombination` if the expression is anything else.</span></span> <span data-ttu-id="e1c5b-154">如果您使用上述程式碼範例中的現用模式來流覽運算式樹狀架構, 您必須使用更多的模式來處理所有可能F#的運算式類型, 而您的程式碼會更複雜。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-154">If you traverse an expression tree by using the active patterns as in the previous code example, you have to use many more patterns to handle all possible F# expression types, and your code will be more complex.</span></span> <span data-ttu-id="e1c5b-155">如需詳細資訊, 請參閱[Exprshape.rebuildshapecombination&#124;ShapeVar&#124;ShapeLambda shapecombination 現用 Active Pattern](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-155">For more information, see [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination Active Pattern](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).</span></span>

<span data-ttu-id="e1c5b-156">下列程式碼範例可用來做為更複雜周遊的基礎。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-156">The following code example can be used as a basis for more complex traversals.</span></span> <span data-ttu-id="e1c5b-157">在此程式碼中, 會針對牽涉到函式呼叫`add`的運算式建立運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-157">In this code, an expression tree is created for an expression that involves a function call, `add`.</span></span> <span data-ttu-id="e1c5b-158">[SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d)現用模式是用來偵測運算式樹狀結構`add`中的任何呼叫。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-158">The [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) active pattern is used to detect any call to `add` in the expression tree.</span></span> <span data-ttu-id="e1c5b-159">此現用模式會將呼叫`exprList`的引數指派給值。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-159">This active pattern assigns the arguments of the call to the `exprList` value.</span></span> <span data-ttu-id="e1c5b-160">在此情況下, 只會有兩個, 因此會提取這些函式, 並在引數上以遞迴方式呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-160">In this case, there are only two, so these are pulled out and the function is called recursively on the arguments.</span></span> <span data-ttu-id="e1c5b-161">結果會插入`mul`程式碼引號, 表示使用拼接運算子 (`%%`) 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-161">The results are inserted into a code quotation that represents a call to `mul` by using the splice operator (`%%`).</span></span> <span data-ttu-id="e1c5b-162">上`println`一個範例中的函式是用來顯示結果。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-162">The `println` function from the previous example is used to display the results.</span></span>

<span data-ttu-id="e1c5b-163">另一個現用模式分支中的程式碼只會重新產生相同的運算式樹狀架構, 因此, 所產生之運算式中的`add`唯一`mul`變更是從變更為。</span><span class="sxs-lookup"><span data-stu-id="e1c5b-163">The code in the other active pattern branches just regenerates the same expression tree, so the only change in the resulting expression is the change from `add` to `mul`.</span></span>

### <a name="code"></a><span data-ttu-id="e1c5b-164">程式碼</span><span class="sxs-lookup"><span data-stu-id="e1c5b-164">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a><span data-ttu-id="e1c5b-165">Output</span><span class="sxs-lookup"><span data-stu-id="e1c5b-165">Output</span></span>

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a><span data-ttu-id="e1c5b-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1c5b-166">See also</span></span>

- [<span data-ttu-id="e1c5b-167">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="e1c5b-167">F# Language Reference</span></span>](index.md)
