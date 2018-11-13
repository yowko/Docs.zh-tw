---
title: F# 函式程式設計簡介
description: 了解函式程式設計的基本概念F#。
ms.date: 10/29/2018
ms.openlocfilehash: d4a9bb0cd826b41aca96e12e2bcb5aab80c18eb4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "25724475"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="4caf4-103">F# 函式程式設計簡介</span><span class="sxs-lookup"><span data-stu-id="4caf4-103">Introduction to Functional Programming in F#</span></span> #

<span data-ttu-id="4caf4-104">功能性程式設計是程式設計的樣式的強調函式和不可變的資料使用。</span><span class="sxs-lookup"><span data-stu-id="4caf4-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="4caf4-105">具型別功能性程式設計是當函式程式設計會結合具有靜態類型，例如F#。</span><span class="sxs-lookup"><span data-stu-id="4caf4-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="4caf4-106">一般情況下，函式程式設計中強調下列概念：</span><span class="sxs-lookup"><span data-stu-id="4caf4-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="4caf4-107">為您所使用的主要建構函式</span><span class="sxs-lookup"><span data-stu-id="4caf4-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="4caf4-108">運算式，而不是陳述式</span><span class="sxs-lookup"><span data-stu-id="4caf4-108">Expressions instead of statements</span></span>
* <span data-ttu-id="4caf4-109">透過變數不可變的值</span><span class="sxs-lookup"><span data-stu-id="4caf4-109">Immutable values over variables</span></span>
* <span data-ttu-id="4caf4-110">透過命令式程式設計的宣告式程式設計</span><span class="sxs-lookup"><span data-stu-id="4caf4-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="4caf4-111">在此系列中，您將探索概念和模式中功能的程式設計使用F#。</span><span class="sxs-lookup"><span data-stu-id="4caf4-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="4caf4-112">過程中，您將了解一些F#太。</span><span class="sxs-lookup"><span data-stu-id="4caf4-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="4caf4-113">用語</span><span class="sxs-lookup"><span data-stu-id="4caf4-113">Terminology</span></span>

<span data-ttu-id="4caf4-114">功能性程式設計，類似其他程式設計典範，隨附於您最終需要了解的詞彙。</span><span class="sxs-lookup"><span data-stu-id="4caf4-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="4caf4-115">以下是時間的一些常見術語，您會看到所有:</span><span class="sxs-lookup"><span data-stu-id="4caf4-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="4caf4-116">**函式**-函式是一種建構，會產生輸出時指定的輸入。</span><span class="sxs-lookup"><span data-stu-id="4caf4-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="4caf4-117">更正式的說法，它_對應_從其中一個項目設定為另一個集合。</span><span class="sxs-lookup"><span data-stu-id="4caf4-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="4caf4-118">此形式放在許多方面，具體，尤其是當使用資料集合上的運作之函式。</span><span class="sxs-lookup"><span data-stu-id="4caf4-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="4caf4-119">它是最基本的 （且重要的） 中概念函式程式設計。</span><span class="sxs-lookup"><span data-stu-id="4caf4-119">It is the most basic (and important) concept in functional programming.</span></span> 
* <span data-ttu-id="4caf4-120">**運算式**-運算式是產生值的程式碼中的建構。</span><span class="sxs-lookup"><span data-stu-id="4caf4-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="4caf4-121">在F#，這個值必須是繫結或明確地被忽略。</span><span class="sxs-lookup"><span data-stu-id="4caf4-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="4caf4-122">運算式可透過極簡方式取代函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="4caf4-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="4caf4-123">**單純性**-單純性是函式的屬性，使其傳回值一律為適用於相同的引數，和其評估沒有任何副作用。</span><span class="sxs-lookup"><span data-stu-id="4caf4-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="4caf4-124">純虛擬函式完全取決於其引數。</span><span class="sxs-lookup"><span data-stu-id="4caf4-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="4caf4-125">**參考的透明度**-參考透明度是運算式的屬性，使得取代其輸出而不會影響程式的行為。</span><span class="sxs-lookup"><span data-stu-id="4caf4-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="4caf4-126">**不變性**-不變性，表示值不能變更就地。</span><span class="sxs-lookup"><span data-stu-id="4caf4-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="4caf4-127">這是相較於可以就地變更的變數。</span><span class="sxs-lookup"><span data-stu-id="4caf4-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="4caf4-128">範例</span><span class="sxs-lookup"><span data-stu-id="4caf4-128">Examples</span></span>

<span data-ttu-id="4caf4-129">下列範例會示範下列核心概念。</span><span class="sxs-lookup"><span data-stu-id="4caf4-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="4caf4-130">函式</span><span class="sxs-lookup"><span data-stu-id="4caf4-130">Functions</span></span>

<span data-ttu-id="4caf4-131">最常見和基本建構函式程式設計中的是函式。</span><span class="sxs-lookup"><span data-stu-id="4caf4-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="4caf4-132">以下是簡單的函式，將 1 加上整數：</span><span class="sxs-lookup"><span data-stu-id="4caf4-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="4caf4-133">其型別簽章如下所示：</span><span class="sxs-lookup"><span data-stu-id="4caf4-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="4caf4-134">簽章可讀取，為 「`addOne`接受`int`名為`x`並將產生`int`"。</span><span class="sxs-lookup"><span data-stu-id="4caf4-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="4caf4-135">更正式的說法`addOne`已_對應_整數的集合中的值，以整數的集合。</span><span class="sxs-lookup"><span data-stu-id="4caf4-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="4caf4-136">`->`語彙基元表示這個對應。</span><span class="sxs-lookup"><span data-stu-id="4caf4-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="4caf4-137">在F#，您通常可以查看函式簽章，以了解針對其用途。</span><span class="sxs-lookup"><span data-stu-id="4caf4-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="4caf4-138">因此，為何簽章重要？</span><span class="sxs-lookup"><span data-stu-id="4caf4-138">So, why is the signature important?</span></span> <span data-ttu-id="4caf4-139">在具型別功能性程式設計中，函式的實作小於通常比實際的型別簽章重要 ！</span><span class="sxs-lookup"><span data-stu-id="4caf4-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="4caf4-140">事實上，`addOne`新增為整數值 1 值得在執行階段，但當您建構的程式，在於它會接受並傳回`int`是什麼會通知您實際使用此函式方式。</span><span class="sxs-lookup"><span data-stu-id="4caf4-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="4caf4-141">此外，一旦使用此函式正確 （相對於其型別簽章中） 時，診斷任何問題可以只在主體內`addOne`函式。</span><span class="sxs-lookup"><span data-stu-id="4caf4-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="4caf4-142">這是具類型的函式程式設計背後的推動力量。</span><span class="sxs-lookup"><span data-stu-id="4caf4-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="4caf4-143">運算式</span><span class="sxs-lookup"><span data-stu-id="4caf4-143">Expressions</span></span>

<span data-ttu-id="4caf4-144">運算式是評估為值的建構。</span><span class="sxs-lookup"><span data-stu-id="4caf4-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="4caf4-145">相較於陳述式，用以執行的動作，運算式可以視為執行動作，讓傳回的值。</span><span class="sxs-lookup"><span data-stu-id="4caf4-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="4caf4-146">運算式幾乎一律會使用由函式程式設計中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="4caf4-146">Expressions are almost always used in favor of statements in functional programming.</span></span>

<span data-ttu-id="4caf4-147">請考慮先前的函式， `addOne`。</span><span class="sxs-lookup"><span data-stu-id="4caf4-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="4caf4-148">主體`addOne`運算式：</span><span class="sxs-lookup"><span data-stu-id="4caf4-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="4caf4-149">它是定義的結果型別，這個運算式的結果`addOne`函式。</span><span class="sxs-lookup"><span data-stu-id="4caf4-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="4caf4-150">比方說，此函式所組成的運算式無法變更為不同的類型，例如`string`:</span><span class="sxs-lookup"><span data-stu-id="4caf4-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="4caf4-151">函式的簽章現在是：</span><span class="sxs-lookup"><span data-stu-id="4caf4-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="4caf4-152">自中的任何類型F#可以有`ToString()`它的型別上呼叫`x`發出泛型 (稱為[自動一般化](../language-reference/generics/automatic-generalization.md))，且結果類型為`string`。</span><span class="sxs-lookup"><span data-stu-id="4caf4-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="4caf4-153">運算式不是函式的主體。</span><span class="sxs-lookup"><span data-stu-id="4caf4-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="4caf4-154">您可以產生您在其他地方使用的值的運算式。</span><span class="sxs-lookup"><span data-stu-id="4caf4-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="4caf4-155">其中一個是通用`if`:</span><span class="sxs-lookup"><span data-stu-id="4caf4-155">A common one is `if`:</span></span>

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

<span data-ttu-id="4caf4-156">`if`運算式會產生一個值，稱為`result`。</span><span class="sxs-lookup"><span data-stu-id="4caf4-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="4caf4-157">請注意，您可以省略`result`，請完全進行`if`運算式主體的`addOneIfOdd`函式。</span><span class="sxs-lookup"><span data-stu-id="4caf4-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="4caf4-158">運算式，必須注意的重點是，它們會產生值。</span><span class="sxs-lookup"><span data-stu-id="4caf4-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="4caf4-159">沒有特殊的型別， `unit`，沒有要傳回項目時使用的。</span><span class="sxs-lookup"><span data-stu-id="4caf4-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="4caf4-160">例如，請考慮這個簡單的函式：</span><span class="sxs-lookup"><span data-stu-id="4caf4-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn "String is: %s" s
```

<span data-ttu-id="4caf4-161">簽章看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="4caf4-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="4caf4-162">`unit`類型表示沒有任何傳回的實際值。</span><span class="sxs-lookup"><span data-stu-id="4caf4-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="4caf4-163">這是很有用，就必須在常式 「 運作 」 而不論是否不具有任何值，以傳回該工作的結果。</span><span class="sxs-lookup"><span data-stu-id="4caf4-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="4caf4-164">這是在程式明確對比，命令式程式設計中，其中對等項目`if`建構是一個陳述式，並產生值通常是與變更的變數。</span><span class="sxs-lookup"><span data-stu-id="4caf4-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="4caf4-165">例如，在C#，可能會撰寫程式碼，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="4caf4-165">For example, in C#, the code might be written like this:</span></span>

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

<span data-ttu-id="4caf4-166">值得注意的是， C# ，而且支援其他的 C 樣式語言[三元運算式](../../csharp/language-reference/operators/conditional-operator.md)，這可讓您以運算式為基礎的條件式程式設計。</span><span class="sxs-lookup"><span data-stu-id="4caf4-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="4caf4-167">在功能程式設計中，很少變動陳述式的值。</span><span class="sxs-lookup"><span data-stu-id="4caf4-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="4caf4-168">雖然有些功能的語言支援陳述式和變動，但是它並不常見函式程式設計中使用這些概念。</span><span class="sxs-lookup"><span data-stu-id="4caf4-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="4caf4-169">純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="4caf4-169">Pure functions</span></span>

<span data-ttu-id="4caf4-170">如先前所述，純虛擬函式是函式：</span><span class="sxs-lookup"><span data-stu-id="4caf4-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="4caf4-171">一律評估為相同的輸入相同的值。</span><span class="sxs-lookup"><span data-stu-id="4caf4-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="4caf4-172">沒有任何副作用。</span><span class="sxs-lookup"><span data-stu-id="4caf4-172">Have no side effects.</span></span>

<span data-ttu-id="4caf4-173">您最好將此內容中的數學函式。</span><span class="sxs-lookup"><span data-stu-id="4caf4-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="4caf4-174">在數學，函式只相依於其引數，而且沒有任何副作用。</span><span class="sxs-lookup"><span data-stu-id="4caf4-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="4caf4-175">數學函式中`f(x) = x + 1`，值`f(x)`僅取決於值`x`。</span><span class="sxs-lookup"><span data-stu-id="4caf4-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="4caf4-176">在函式程式設計中的純虛擬函式是相同的方式。</span><span class="sxs-lookup"><span data-stu-id="4caf4-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="4caf4-177">當撰寫純虛擬函式，函式必須只相依於其引數，並不執行任何會產生副作用的動作。</span><span class="sxs-lookup"><span data-stu-id="4caf4-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="4caf4-178">因為這取決於全域、 可變動狀態，以下是一個非純虛擬函式範例：</span><span class="sxs-lookup"><span data-stu-id="4caf4-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="4caf4-179">`addOneToValue`清楚地非純虛擬函式，是因為`value`可能有不同的值比 1，隨時變更。</span><span class="sxs-lookup"><span data-stu-id="4caf4-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="4caf4-180">是函式程式設計中避免這種模式的全域值而定。</span><span class="sxs-lookup"><span data-stu-id="4caf4-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="4caf4-181">以下是非純虛擬函式的另一個範例，因為它會執行副作用：</span><span class="sxs-lookup"><span data-stu-id="4caf4-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

<span data-ttu-id="4caf4-182">雖然此函式不依存於一個全域值，它的值寫入`x`程式的輸出。</span><span class="sxs-lookup"><span data-stu-id="4caf4-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="4caf4-183">雖然沒有任何原本就是問題，這項操作，意思函式不是純虛擬。</span><span class="sxs-lookup"><span data-stu-id="4caf4-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span>

<span data-ttu-id="4caf4-184">移除`printfn`陳述式終於使函式單純：</span><span class="sxs-lookup"><span data-stu-id="4caf4-184">Removing the `printfn` statement finally makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="4caf4-185">雖然此函式本質上並非_較佳_比使用舊版`printfn`陳述式，它可以確實保證此函式的作用是傳回值。</span><span class="sxs-lookup"><span data-stu-id="4caf4-185">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="4caf4-186">呼叫此函式一次，或 1 億次將仍產生相同的動作： 只產生值。</span><span class="sxs-lookup"><span data-stu-id="4caf4-186">Calling this function once or 1 billion times will still result in the same thing: just producing a value.</span></span> <span data-ttu-id="4caf4-187">這個可預測性是在功能性程式設計，重要，因為這表示任何純虛擬函式會參考透明。</span><span class="sxs-lookup"><span data-stu-id="4caf4-187">This predictability is valuable in functional programming, as it means that any pure function is referentially transparent.</span></span>

### <a name="referential-transparency"></a><span data-ttu-id="4caf4-188">參考的透明度</span><span class="sxs-lookup"><span data-stu-id="4caf4-188">Referential Transparency</span></span>

<span data-ttu-id="4caf4-189">參考的透明度是運算式和函式的屬性。</span><span class="sxs-lookup"><span data-stu-id="4caf4-189">Referential transparency is a property of expressions and functions.</span></span> <span data-ttu-id="4caf4-190">透明參考運算式，它必須能夠取代其產生的值，而不需要變更程式的行為。</span><span class="sxs-lookup"><span data-stu-id="4caf4-190">For an expression to be referentially transparent, it must be able to be replaced with its resulting value without changing the program's behavior.</span></span> <span data-ttu-id="4caf4-191">所有純虛擬函式會參考透明的。</span><span class="sxs-lookup"><span data-stu-id="4caf4-191">All pure functions are referentially transparent.</span></span>

<span data-ttu-id="4caf4-192">如同純虛擬函式，它可以將參考的透明度，從數學的角度來看很有幫助。</span><span class="sxs-lookup"><span data-stu-id="4caf4-192">As with pure functions, it can be helpful to think of referential transparency from a mathematical perspective.</span></span> <span data-ttu-id="4caf4-193">在數學運算式`y = f(x)`，`f(x)`可取代的函式的結果，仍然會等於`y`。</span><span class="sxs-lookup"><span data-stu-id="4caf4-193">In the mathematical expression `y = f(x)`, `f(x)` can be replaced by the result of the function and it will still be equal to `y`.</span></span> <span data-ttu-id="4caf4-194">這同樣適用於在函式程式設計參考透明度。</span><span class="sxs-lookup"><span data-stu-id="4caf4-194">This is equally true for referential transparency in functional programming.</span></span>

<span data-ttu-id="4caf4-195">請考慮呼叫先前定義`addOneIfOdd`函式兩次：</span><span class="sxs-lookup"><span data-stu-id="4caf4-195">Consider calling the previously defined `addOneIfOdd` function twice:</span></span>

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result

let res1 = addOneIffOdd 1 // Produces 2
let res2 = addOneIffOdd 2 // Produces 2
```

<span data-ttu-id="4caf4-196">我們可以取代每個函式呼叫函式主體中，以取代引數`input`與每個值：</span><span class="sxs-lookup"><span data-stu-id="4caf4-196">We can replace each function call with the function body, substituting the argument `input` with each value:</span></span>

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result

let res1 =
    let result =
        if isOdd 1 then
            1 + 1
        else
            1

    result
let res2 =
    let result =
        if isOdd 2 then
            2 + 1
        else
            2

    result
```

<span data-ttu-id="4caf4-197">兩者`res1`並`res2`有相同的值，如同呼叫函式，表示`addOneIfOdd`是參考透明 ！</span><span class="sxs-lookup"><span data-stu-id="4caf4-197">Both `res1` and `res2` have the same value as if the function was called, indicating that `addOneIfOdd` is referentially transparent!</span></span>

<span data-ttu-id="4caf4-198">此外，函式不一定要單純也是參考透明。</span><span class="sxs-lookup"><span data-stu-id="4caf4-198">Additionally, a function doesn't have to be pure to also be referentially transparent.</span></span> <span data-ttu-id="4caf4-199">先前的定義，請考慮`addOneTovalue`:</span><span class="sxs-lookup"><span data-stu-id="4caf4-199">Consider a previous definition of  `addOneTovalue`:</span></span>

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

<span data-ttu-id="4caf4-200">其主體也可以取代任何呼叫此函式和相同的項目將會每次發生：</span><span class="sxs-lookup"><span data-stu-id="4caf4-200">Any call to this function can also be replaced by its body and the same things will happen each time:</span></span>

* <span data-ttu-id="4caf4-201">之前，要加入的值，會列印到輸出</span><span class="sxs-lookup"><span data-stu-id="4caf4-201">The value, prior to being added to, is printed to the output</span></span>
* <span data-ttu-id="4caf4-202">此值有加 1</span><span class="sxs-lookup"><span data-stu-id="4caf4-202">The value has 1 added to it</span></span>

<span data-ttu-id="4caf4-203">在進行程式設計時F#，通常會是目標，而不是純正性的參考透明度。</span><span class="sxs-lookup"><span data-stu-id="4caf4-203">When programming in F#, it is often referential transparency that is the goal, rather than purity.</span></span> <span data-ttu-id="4caf4-204">不過，最好還是時您可以撰寫純虛擬函式。</span><span class="sxs-lookup"><span data-stu-id="4caf4-204">However, it is still good practice to write pure functions when you can.</span></span>

### <a name="immutability"></a><span data-ttu-id="4caf4-205">不變性</span><span class="sxs-lookup"><span data-stu-id="4caf4-205">Immutability</span></span>

<span data-ttu-id="4caf4-206">最後，其中一個具型別功能性程式設計的最基本的概念是不變性。</span><span class="sxs-lookup"><span data-stu-id="4caf4-206">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="4caf4-207">在F#，所有值都是不可變的預設值。</span><span class="sxs-lookup"><span data-stu-id="4caf4-207">In F#, all values are immutable by default.</span></span> <span data-ttu-id="4caf4-208">這表示它們不能變更，除非您將它們明確標示為可變動。</span><span class="sxs-lookup"><span data-stu-id="4caf4-208">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="4caf4-209">在實務上，使用不可變的值會表示程式設計變更您的方法，請從 「 我需要變更某些項目 」，以 「 我需要產生新的值 」。</span><span class="sxs-lookup"><span data-stu-id="4caf4-209">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="4caf4-210">例如，新增 1 的值表示產生新的值，不變更現有的憑證：</span><span class="sxs-lookup"><span data-stu-id="4caf4-210">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="4caf4-211">在F#，下列程式碼會執行**不**變動`value`函式; 相反地，它會執行相等檢查：</span><span class="sxs-lookup"><span data-stu-id="4caf4-211">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="4caf4-212">某些功能的程式設計語言並不支援變動。</span><span class="sxs-lookup"><span data-stu-id="4caf4-212">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="4caf4-213">在F#，它支援，但它不是值的預設行為。</span><span class="sxs-lookup"><span data-stu-id="4caf4-213">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="4caf4-214">這個概念延伸甚至進一步資料結構。</span><span class="sxs-lookup"><span data-stu-id="4caf4-214">This concept extends even further to data structures.</span></span> <span data-ttu-id="4caf4-215">在功能性程式設計，不可變的資料結構例如集 （和更多） 有不同的實作比您一開始可能預期。</span><span class="sxs-lookup"><span data-stu-id="4caf4-215">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="4caf4-216">就概念而言，如下的項目加入一組不會變更集，它會產生_新_設定的附加價值。</span><span class="sxs-lookup"><span data-stu-id="4caf4-216">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="4caf4-217">實際上，這是通常透過不同的資料結構，以便有效率地追蹤的值，因此，因此可以提供適當的表示法的資料。</span><span class="sxs-lookup"><span data-stu-id="4caf4-217">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="4caf4-218">這種使用值和資料結構而言很重要，因為它會強制您將修改的項目，如同它會建立新的版本的任何作業。</span><span class="sxs-lookup"><span data-stu-id="4caf4-218">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="4caf4-219">這可讓相等和比較等的項目，以便在程式中一致。</span><span class="sxs-lookup"><span data-stu-id="4caf4-219">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4caf4-220">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4caf4-220">Next steps</span></span>

<span data-ttu-id="4caf4-221">下一節會徹底探討函式中，瀏覽不同的方式，您可以在函式程式設計中使用它們。</span><span class="sxs-lookup"><span data-stu-id="4caf4-221">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="4caf4-222">[第一級函式](first-class-functions.md)將探索功能深入，顯示如何使用它們在不同內容中。</span><span class="sxs-lookup"><span data-stu-id="4caf4-222">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="4caf4-223">進一步閱讀</span><span class="sxs-lookup"><span data-stu-id="4caf4-223">Further reading</span></span>

<span data-ttu-id="4caf4-224">[功能思考](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/)系列是另一個絕佳的資源，若要了解功能性程式設計與F#。</span><span class="sxs-lookup"><span data-stu-id="4caf4-224">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="4caf4-225">它涵蓋函式程式設計的基本概念了 pragmatic 和容易閱讀的方式，使用F#功能，可說明的概念。</span><span class="sxs-lookup"><span data-stu-id="4caf4-225">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>