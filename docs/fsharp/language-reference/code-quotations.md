---
title: 程式碼引號 (F#)
description: '了解 F # 程式碼引號，可讓您產生及以程式設計方式使用 F # 程式碼運算式的語言功能。'
ms.date: 05/16/2016
ms.openlocfilehash: 27e9cf1d99e2b5955cc6359653fc87bdbe824cc7
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577387"
---
# <a name="code-quotations"></a><span data-ttu-id="e5c8e-103">程式碼引號</span><span class="sxs-lookup"><span data-stu-id="e5c8e-103">Code Quotations</span></span>

> [!NOTE]
<span data-ttu-id="e5c8e-104">API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-104">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="e5c8e-105">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="e5c8e-106">本主題描述*程式碼引號*，可讓您產生及以程式設計方式使用 F # 程式碼運算式的語言功能。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-106">This topic describes *code quotations*, a language feature that enables you to generate and work with F# code expressions programmatically.</span></span> <span data-ttu-id="e5c8e-107">這項功能可讓您產生代表 F # 程式碼的抽象語法樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-107">This feature lets you generate an abstract syntax tree that represents F# code.</span></span> <span data-ttu-id="e5c8e-108">可以周遊的抽象語法樹狀目錄，然後根據您的應用程式的需求進行處理。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-108">The abstract syntax tree can then be traversed and processed according to the needs of your application.</span></span> <span data-ttu-id="e5c8e-109">例如，您可以使用樹狀目錄中產生 F # 程式碼，或某些其他語言產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-109">For example, you can use the tree to generate F# code or generate code in some other language.</span></span>

## <a name="quoted-expressions"></a><span data-ttu-id="e5c8e-110">加上引號的運算式</span><span class="sxs-lookup"><span data-stu-id="e5c8e-110">Quoted Expressions</span></span>

<span data-ttu-id="e5c8e-111">A*加上引號運算式*是 F # 運算式在程式碼中分隔的方式不編譯一部分您的程式，但改為會編譯成 F # 運算式所表示的物件。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-111">A *quoted expression* is an F# expression in your code that is delimited in such a way that it is not compiled as part of your program, but instead is compiled into an object that represents an F# expression.</span></span> <span data-ttu-id="e5c8e-112">您可以將標記的引號括住的運算式中有兩種： 使用型別資訊，或不具類型資訊。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-112">You can mark a quoted expression in one of two ways: either with type information or without type information.</span></span> <span data-ttu-id="e5c8e-113">如果您想要包含的型別資訊，您會使用符號`<@`和`@>`來分隔引號括住的運算式。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-113">If you want to include type information, you use the symbols `<@` and `@>` to delimit the quoted expression.</span></span> <span data-ttu-id="e5c8e-114">如果您不需要型別資訊，您會使用符號`<@@`和`@@>`。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-114">If you do not need type information, you use the symbols `<@@` and `@@>`.</span></span> <span data-ttu-id="e5c8e-115">下列程式碼顯示具型別和不具類型的引號。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-115">The following code shows typed and untyped quotations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

<span data-ttu-id="e5c8e-116">周遊大型的運算式樹狀結構會更快，如果您不會包含類型資訊。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-116">Traversing a large expression tree is faster if you do not include type information.</span></span> <span data-ttu-id="e5c8e-117">使用具類型的符號加上引號運算式的結果類型是`Expr<'T>`，而且型別參數都有運算式，由 F # 編譯器的型別推斷演算法的類型。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-117">The resulting type of an expression quoted with the typed symbols is `Expr<'T>`, where the type parameter has the type of the expression as determined by the F# compiler's type inference algorithm.</span></span> <span data-ttu-id="e5c8e-118">當您使用不具類型資訊的程式碼引號時，加上引號運算式的類型為非泛型型別[Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65)。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-118">When you use code quotations without type information, the type of the quoted expression is the non-generic type [Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65).</span></span> <span data-ttu-id="e5c8e-119">您可以呼叫[Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2)具型別的的屬性`Expr`類別來取得不具型別的`Expr`物件。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-119">You can call the [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2) property on the typed `Expr` class to obtain the untyped `Expr` object.</span></span>

<span data-ttu-id="e5c8e-120">有各種不同的靜態方法，讓您產生 F # 運算式物件以程式設計方式在`Expr`類別，而不使用加上引號的運算式。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-120">There are a variety of static methods that allow you to generate F# expression objects programmatically in the `Expr` class without using quoted expressions.</span></span>

<span data-ttu-id="e5c8e-121">請注意，程式碼引號必須包含完整的運算式。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-121">Note that a code quotation must include a complete expression.</span></span> <span data-ttu-id="e5c8e-122">針對`let`繫結，例如，您需要定義的繫結的名稱和其他運算式，使用此繫結。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-122">For a `let` binding, for example, you need both the definition of the bound name and an additional expression that uses the binding.</span></span> <span data-ttu-id="e5c8e-123">在詳細的語法中，這是遵循`in`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-123">In verbose syntax, this is an expression that follows the `in` keyword.</span></span> <span data-ttu-id="e5c8e-124">在最上層模組中，這是只在模組中下, 一個運算式，但在引號中，是明確需要。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-124">At the top-level in a module, this is just the next expression in the module, but in a quotation, it is explicitly required.</span></span>

<span data-ttu-id="e5c8e-125">因此，下列運算式不是有效的。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-125">Therefore, the following expression is not valid.</span></span>

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

<span data-ttu-id="e5c8e-126">但是，下列運算式都是有效。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-126">But the following expressions are valid.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

<span data-ttu-id="e5c8e-127">若要使用的程式碼引號，您必須新增匯入宣告 (使用`open`關鍵字)，開啟[Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2)命名空間。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-127">To use code quotations, you must add an import declaration (by using the `open` keyword) that opens the [Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2) namespace.</span></span>

<span data-ttu-id="e5c8e-128">F # PowerPack 支援用於評估和執行 F # 運算式物件。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-128">The F# PowerPack provides support for evaluating and executing F# expression objects.</span></span>

## <a name="expr-type"></a><span data-ttu-id="e5c8e-129">Expr 型別</span><span class="sxs-lookup"><span data-stu-id="e5c8e-129">Expr Type</span></span>

<span data-ttu-id="e5c8e-130">執行個體`Expr`類型代表 F # 運算式。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-130">An instance of the `Expr` type represents an F# expression.</span></span> <span data-ttu-id="e5c8e-131">泛型和非泛型`Expr`類型會記錄在 F # 程式庫文件。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-131">Both the generic and the non-generic `Expr` types are documented in the F# library documentation.</span></span> <span data-ttu-id="e5c8e-132">如需詳細資訊，請參閱 < [Microsoft.FSharp.Quotations 命名空間](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d)並[Quotations.Expr 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-132">For more information, see [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d) and [Quotations.Expr Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d).</span></span>

## <a name="splicing-operators"></a><span data-ttu-id="e5c8e-133">接合運算子</span><span class="sxs-lookup"><span data-stu-id="e5c8e-133">Splicing Operators</span></span>

<span data-ttu-id="e5c8e-134">接合，可讓您將使用您建立以程式設計方式或從另一個程式碼引號運算式的常值程式碼引號。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-134">Splicing enables you to combine literal code quotations with expressions that you have created programmatically or from another code quotation.</span></span> <span data-ttu-id="e5c8e-135">`%`和`%%`運算子可讓您將 F # 運算式物件新增至程式碼引號。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-135">The `%` and `%%` operators enable you to add an F# expression object into a code quotation.</span></span> <span data-ttu-id="e5c8e-136">您使用`%`的具類型的運算式物件插入具類型的引號的運算子; 您可以使用`%%`運算子，將不具類型的運算式物件插入不具類型的引號。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-136">You use the `%` operator to insert a typed expression object into a typed quotation; you use the `%%` operator to insert an untyped expression object into an untyped quotation.</span></span> <span data-ttu-id="e5c8e-137">這兩個運算子是一元前置運算子。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-137">Both operators are unary prefix operators.</span></span> <span data-ttu-id="e5c8e-138">因此如果`expr`是不具類型的型別運算式`Expr`，下列程式碼就有效。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-138">Thus if `expr` is an untyped expression of type `Expr`, the following code is valid.</span></span>

```fsharp
<@@ 1 + %%expr @@>
```

<span data-ttu-id="e5c8e-139">而如果`expr`是型別的具型別的引號`Expr<int>`，下列程式碼就有效。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-139">And if `expr` is a typed quotation of type `Expr<int>`, the following code is valid.</span></span>

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a><span data-ttu-id="e5c8e-140">範例</span><span class="sxs-lookup"><span data-stu-id="e5c8e-140">Example</span></span>

### <a name="description"></a><span data-ttu-id="e5c8e-141">描述</span><span class="sxs-lookup"><span data-stu-id="e5c8e-141">Description</span></span>

<span data-ttu-id="e5c8e-142">下列範例說明如何使用以 F # 程式碼置於 expression 物件，並列印表示運算式的 F # 程式碼的程式碼引號。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-142">The following example illustrates the use of code quotations to put F# code into an expression object and then print the F# code that represents the expression.</span></span> <span data-ttu-id="e5c8e-143">函式`println`定義，其中包含遞迴函式`print`顯示 F # 運算式物件 (類型的`Expr`) 的好記的格式。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-143">A function `println` is defined that contains a recursive function `print` that displays an F# expression object (of type `Expr`) in a friendly format.</span></span> <span data-ttu-id="e5c8e-144">有數個使用中的模式[Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4)並[Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd)模組，可用來分析運算式物件。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-144">There are several active patterns in the [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4) and [Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd) modules that can be used to analyze expression objects.</span></span> <span data-ttu-id="e5c8e-145">此範例不包含在 F # 運算式中可能會出現的所有可能模式。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-145">This example does not include all the possible patterns that might appear in an F# expression.</span></span> <span data-ttu-id="e5c8e-146">任何無法辨識的模式就會觸發萬用字元模式比對 (`_`)，且會使用轉換`ToString`方法，它會上`Expr`類型，可讓您知道將比對運算式中的模式。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-146">Any unrecognized pattern triggers a match to the wildcard pattern (`_`) and is rendered by using the `ToString` method, which, on the `Expr` type, lets you know the active pattern to add to your match expression.</span></span>

### <a name="code"></a><span data-ttu-id="e5c8e-147">程式碼</span><span class="sxs-lookup"><span data-stu-id="e5c8e-147">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a><span data-ttu-id="e5c8e-148">輸出</span><span class="sxs-lookup"><span data-stu-id="e5c8e-148">Output</span></span>

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a><span data-ttu-id="e5c8e-149">範例</span><span class="sxs-lookup"><span data-stu-id="e5c8e-149">Example</span></span>

### <a name="description"></a><span data-ttu-id="e5c8e-150">描述</span><span class="sxs-lookup"><span data-stu-id="e5c8e-150">Description</span></span>

<span data-ttu-id="e5c8e-151">您也可以使用中的三個作用中模式[ExprShape 模組](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de)周遊運算式樹狀架構，具有較少的使用中模式。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-151">You can also use the three active patterns in the [ExprShape module](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de) to traverse expression trees with fewer active patterns.</span></span> <span data-ttu-id="e5c8e-152">當您想要周遊樹狀結構，但您不需要大部分的節點中的所有資訊，這些作用中的模式可以很有用。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-152">These active patterns can be useful when you want to traverse a tree but you do not need all the information in most of the nodes.</span></span> <span data-ttu-id="e5c8e-153">當您使用這些模式時，任何的 F # 運算式符合下列三種模式的其中一個：`ShapeVar`變數中，運算式是否`ShapeLambda`如果運算式是 lambda 運算式，或`ShapeCombination`如果運算式可以是任何其他項目。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-153">When you use these patterns, any F# expression matches one of the following three patterns: `ShapeVar` if the expression is a variable, `ShapeLambda` if the expression is a lambda expression, or `ShapeCombination` if the expression is anything else.</span></span> <span data-ttu-id="e5c8e-154">如果您周遊運算式樹狀架構所使用的作用中的模式，如同先前的程式碼範例時，您必須使用許多更多的模式來處理所有可能 F # 運算式的類型，和您的程式碼將會更複雜。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-154">If you traverse an expression tree by using the active patterns as in the previous code example, you have to use many more patterns to handle all possible F# expression types, and your code will be more complex.</span></span> <span data-ttu-id="e5c8e-155">如需詳細資訊，請參閱 < [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination 現用模式](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-155">For more information, see [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination Active Pattern](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d).</span></span>

<span data-ttu-id="e5c8e-156">下列程式碼範例可用做為基礎的更複雜的周遊。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-156">The following code example can be used as a basis for more complex traversals.</span></span> <span data-ttu-id="e5c8e-157">在此程式碼中，牽涉到函式呼叫的運算式建立運算式樹狀架構`add`。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-157">In this code, an expression tree is created for an expression that involves a function call, `add`.</span></span> <span data-ttu-id="e5c8e-158">[SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d)作用中的模式用來偵測到的任何呼叫`add`運算式樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-158">The [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d) active pattern is used to detect any call to `add` in the expression tree.</span></span> <span data-ttu-id="e5c8e-159">此作用中的模式會指派至呼叫的引數`exprList`值。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-159">This active pattern assigns the arguments of the call to the `exprList` value.</span></span> <span data-ttu-id="e5c8e-160">在此情況下，有一些只有兩種，因此這些取出和呼叫的函式會以遞迴方式引數。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-160">In this case, there are only two, so these are pulled out and the function is called recursively on the arguments.</span></span> <span data-ttu-id="e5c8e-161">結果會插入到代表呼叫的程式碼引號`mul`使用拼接運算子 (`%%`)。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-161">The results are inserted into a code quotation that represents a call to `mul` by using the splice operator (`%%`).</span></span> <span data-ttu-id="e5c8e-162">`println`上一個範例中的函數用來顯示結果。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-162">The `println` function from the previous example is used to display the results.</span></span>

<span data-ttu-id="e5c8e-163">其他使用中模式分支中的程式碼只會重新產生相同的運算式樹狀架構，因此在產生的運算式中的唯一變更是從變更`add`至`mul`。</span><span class="sxs-lookup"><span data-stu-id="e5c8e-163">The code in the other active pattern branches just regenerates the same expression tree, so the only change in the resulting expression is the change from `add` to `mul`.</span></span>

### <a name="code"></a><span data-ttu-id="e5c8e-164">程式碼</span><span class="sxs-lookup"><span data-stu-id="e5c8e-164">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a><span data-ttu-id="e5c8e-165">輸出</span><span class="sxs-lookup"><span data-stu-id="e5c8e-165">Output</span></span>

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a><span data-ttu-id="e5c8e-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5c8e-166">See also</span></span>

- [<span data-ttu-id="e5c8e-167">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="e5c8e-167">F# Language Reference</span></span>](index.md)
