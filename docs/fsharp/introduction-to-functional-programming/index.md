---
title: F# 函式程式設計簡介
description: 瞭解功能程式設計的基本概念F#。
ms.date: 10/29/2018
ms.openlocfilehash: e1a0edc61dbe13012c48e166d490e22ebc70d6a0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424703"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="de3c7-103">F\# 中的功能性程式設計簡介</span><span class="sxs-lookup"><span data-stu-id="de3c7-103">Introduction to Functional Programming in F\#</span></span>

<span data-ttu-id="de3c7-104">函式程式設計是一種程式設計風格，強調函式和不可變數據的使用。</span><span class="sxs-lookup"><span data-stu-id="de3c7-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="de3c7-105">具型別函式程式設計是指將功能程式設計與靜態型F#別（例如和）結合在一起。</span><span class="sxs-lookup"><span data-stu-id="de3c7-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="de3c7-106">一般來說，功能程式設計中會強調下列概念：</span><span class="sxs-lookup"><span data-stu-id="de3c7-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="de3c7-107">函式做為您使用的主要結構</span><span class="sxs-lookup"><span data-stu-id="de3c7-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="de3c7-108">運算式，而不是語句</span><span class="sxs-lookup"><span data-stu-id="de3c7-108">Expressions instead of statements</span></span>
* <span data-ttu-id="de3c7-109">變數上的不可變值</span><span class="sxs-lookup"><span data-stu-id="de3c7-109">Immutable values over variables</span></span>
* <span data-ttu-id="de3c7-110">透過命令式程式設計進行宣告式程式設計</span><span class="sxs-lookup"><span data-stu-id="de3c7-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="de3c7-111">在此系列中，您將使用F#來探索功能程式設計中的概念和模式。</span><span class="sxs-lookup"><span data-stu-id="de3c7-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="de3c7-112">在過程中，您也會學F#到一些。</span><span class="sxs-lookup"><span data-stu-id="de3c7-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="de3c7-113">用語</span><span class="sxs-lookup"><span data-stu-id="de3c7-113">Terminology</span></span>

<span data-ttu-id="de3c7-114">函式程式設計（如其他程式設計範例）隨附于最終需要學習的詞彙。</span><span class="sxs-lookup"><span data-stu-id="de3c7-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="de3c7-115">以下是您將會看到的一些常見詞彙：</span><span class="sxs-lookup"><span data-stu-id="de3c7-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="de3c7-116">**Function** -函式是一種結構，會在提供輸入時產生輸出。</span><span class="sxs-lookup"><span data-stu-id="de3c7-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="de3c7-117">更正式地說，它會將一個集合中的專案_對應_到另一個集合。</span><span class="sxs-lookup"><span data-stu-id="de3c7-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="de3c7-118">這個形式會以許多方式細分成具體，特別是當使用在資料集合上操作的函數時。</span><span class="sxs-lookup"><span data-stu-id="de3c7-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="de3c7-119">這是功能性程式設計中最基本（且重要）的概念。</span><span class="sxs-lookup"><span data-stu-id="de3c7-119">It is the most basic (and important) concept in functional programming.</span></span>
* <span data-ttu-id="de3c7-120">**運算式**-運算式是在程式碼中產生值的結構。</span><span class="sxs-lookup"><span data-stu-id="de3c7-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="de3c7-121">在F#中，必須系結或明確忽略此值。</span><span class="sxs-lookup"><span data-stu-id="de3c7-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="de3c7-122">運算式可以完整由函式呼叫取代。</span><span class="sxs-lookup"><span data-stu-id="de3c7-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="de3c7-123">**純度**-純度是函式的屬性，使相同的引數的傳回值一律相同，而且其評估沒有副作用。</span><span class="sxs-lookup"><span data-stu-id="de3c7-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="de3c7-124">純虛擬函式完全取決於其引數。</span><span class="sxs-lookup"><span data-stu-id="de3c7-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="de3c7-125">**參考透明度**-引用透明度是運算式的屬性，可將其取代為其輸出，而不會影響程式的行為。</span><span class="sxs-lookup"><span data-stu-id="de3c7-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="de3c7-126">不**可變性-不可變性表示**值無法就地變更。</span><span class="sxs-lookup"><span data-stu-id="de3c7-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="de3c7-127">這與可就地變更的變數相反。</span><span class="sxs-lookup"><span data-stu-id="de3c7-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="de3c7-128">範例</span><span class="sxs-lookup"><span data-stu-id="de3c7-128">Examples</span></span>

<span data-ttu-id="de3c7-129">下列範例示範這些核心概念。</span><span class="sxs-lookup"><span data-stu-id="de3c7-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="de3c7-130">函式</span><span class="sxs-lookup"><span data-stu-id="de3c7-130">Functions</span></span>

<span data-ttu-id="de3c7-131">函式程式設計中最常見和基本的結構是函數。</span><span class="sxs-lookup"><span data-stu-id="de3c7-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="de3c7-132">以下是將1新增至整數的簡單函式：</span><span class="sxs-lookup"><span data-stu-id="de3c7-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="de3c7-133">其型別簽章如下所示：</span><span class="sxs-lookup"><span data-stu-id="de3c7-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="de3c7-134">簽章可以讀取為，「`addOne` 接受名為 `x` 的 `int`，而且會產生 `int`」。</span><span class="sxs-lookup"><span data-stu-id="de3c7-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="de3c7-135">更正式地說，`addOne` 會將一組整數的值_對應_至整數集合。</span><span class="sxs-lookup"><span data-stu-id="de3c7-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="de3c7-136">`->` token 表示此對應。</span><span class="sxs-lookup"><span data-stu-id="de3c7-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="de3c7-137">在F#中，您通常可以查看函式簽章，以瞭解其用途。</span><span class="sxs-lookup"><span data-stu-id="de3c7-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="de3c7-138">那麼，簽章為什麼很重要？</span><span class="sxs-lookup"><span data-stu-id="de3c7-138">So, why is the signature important?</span></span> <span data-ttu-id="de3c7-139">在具類型的函式程式設計中，函數的執行通常比實際的類型簽章較不重要！</span><span class="sxs-lookup"><span data-stu-id="de3c7-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="de3c7-140">`addOne` 將值1新增至整數的事實在執行時間很有趣，但當您在建立程式時，它會接受並傳回 `int`，這會通知您實際使用此函數的方式。</span><span class="sxs-lookup"><span data-stu-id="de3c7-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="de3c7-141">此外，一旦您正確使用此函式（相對於其類型簽章），診斷任何問題都只能在 `addOne` 函式的主體中完成。</span><span class="sxs-lookup"><span data-stu-id="de3c7-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="de3c7-142">這是具型別功能性程式設計背後的促成。</span><span class="sxs-lookup"><span data-stu-id="de3c7-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="de3c7-143">運算式</span><span class="sxs-lookup"><span data-stu-id="de3c7-143">Expressions</span></span>

<span data-ttu-id="de3c7-144">運算式是評估為值的結構。</span><span class="sxs-lookup"><span data-stu-id="de3c7-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="de3c7-145">相對於執行動作的語句，運算式可以被視為執行動作來提供值。</span><span class="sxs-lookup"><span data-stu-id="de3c7-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="de3c7-146">運算式幾乎一律用於功能程式設計中的語句。</span><span class="sxs-lookup"><span data-stu-id="de3c7-146">Expressions are almost always used in favor of statements in functional programming.</span></span>

<span data-ttu-id="de3c7-147">請考慮先前的函式，`addOne`。</span><span class="sxs-lookup"><span data-stu-id="de3c7-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="de3c7-148">`addOne` 的主體是運算式：</span><span class="sxs-lookup"><span data-stu-id="de3c7-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="de3c7-149">這是定義 `addOne` 函數之結果類型的運算式結果。</span><span class="sxs-lookup"><span data-stu-id="de3c7-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="de3c7-150">例如，構成此函式的運算式可能會變更為不同的類型，例如 `string`：</span><span class="sxs-lookup"><span data-stu-id="de3c7-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="de3c7-151">函數的簽章現在是：</span><span class="sxs-lookup"><span data-stu-id="de3c7-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="de3c7-152">由於中F#的任何類型都可以在其上呼叫 `ToString()`，因此 `x` 的類型已成為泛型（稱為[自動一般化](../language-reference/generics/automatic-generalization.md)），而結果類型是 `string`。</span><span class="sxs-lookup"><span data-stu-id="de3c7-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="de3c7-153">運算式不只是函式的主體。</span><span class="sxs-lookup"><span data-stu-id="de3c7-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="de3c7-154">您可以擁有會產生您在其他地方使用之值的運算式。</span><span class="sxs-lookup"><span data-stu-id="de3c7-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="de3c7-155">常見的 `if`：</span><span class="sxs-lookup"><span data-stu-id="de3c7-155">A common one is `if`:</span></span>

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

<span data-ttu-id="de3c7-156">`if` 運算式會產生稱為 `result`的值。</span><span class="sxs-lookup"><span data-stu-id="de3c7-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="de3c7-157">請注意，您可以完全省略 `result`，讓 `if` 運算式成為 `addOneIfOdd` 函數的主體。</span><span class="sxs-lookup"><span data-stu-id="de3c7-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="de3c7-158">運算式的重點是要記住的是，它們會產生一個值。</span><span class="sxs-lookup"><span data-stu-id="de3c7-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="de3c7-159">有一種特殊的類型，`unit`，在沒有要傳回的內容時使用。</span><span class="sxs-lookup"><span data-stu-id="de3c7-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="de3c7-160">例如，請考慮這個簡單的函數：</span><span class="sxs-lookup"><span data-stu-id="de3c7-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn "String is: %s" str
```

<span data-ttu-id="de3c7-161">簽章看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="de3c7-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="de3c7-162">`unit` 類型表示沒有傳回實際的值。</span><span class="sxs-lookup"><span data-stu-id="de3c7-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="de3c7-163">當您有一個必須「執行工作」的常式時，雖然沒有任何值會因該工作而傳回，這項功能就很有用。</span><span class="sxs-lookup"><span data-stu-id="de3c7-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="de3c7-164">這與命令式程式設計相反，其中對等的 `if` 結構是語句，而產生值通常是透過改變變數來完成。</span><span class="sxs-lookup"><span data-stu-id="de3c7-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="de3c7-165">例如，在中C#，程式碼的撰寫方式可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="de3c7-165">For example, in C#, the code might be written like this:</span></span>

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

<span data-ttu-id="de3c7-166">值得注意的是， C#和其他 C 樣式語言都支援[三元運算式](../../csharp/language-reference/operators/conditional-operator.md)，這可允許以運算式為基礎的條件式程式設計。</span><span class="sxs-lookup"><span data-stu-id="de3c7-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="de3c7-167">在功能性程式設計中，使用語句來改變值很罕見。</span><span class="sxs-lookup"><span data-stu-id="de3c7-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="de3c7-168">雖然某些功能性語言支援語句和變化，但在函程式設計中使用這些概念並不常見。</span><span class="sxs-lookup"><span data-stu-id="de3c7-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="de3c7-169">純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="de3c7-169">Pure functions</span></span>

<span data-ttu-id="de3c7-170">如先前所述，純虛擬函式是函式：</span><span class="sxs-lookup"><span data-stu-id="de3c7-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="de3c7-171">針對相同的輸入，一律評估為相同的值。</span><span class="sxs-lookup"><span data-stu-id="de3c7-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="de3c7-172">沒有任何副作用。</span><span class="sxs-lookup"><span data-stu-id="de3c7-172">Have no side effects.</span></span>

<span data-ttu-id="de3c7-173">在此內容中考慮數學函式會很有説明。</span><span class="sxs-lookup"><span data-stu-id="de3c7-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="de3c7-174">在數學中，函式只會相依于其引數，而且沒有任何副作用。</span><span class="sxs-lookup"><span data-stu-id="de3c7-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="de3c7-175">在數學函數 `f(x) = x + 1`中，`f(x)` 的值只取決於 `x`的值。</span><span class="sxs-lookup"><span data-stu-id="de3c7-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="de3c7-176">函式程式設計中的純虛擬函式是以相同的方式運作。</span><span class="sxs-lookup"><span data-stu-id="de3c7-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="de3c7-177">撰寫純虛擬函式時，函式必須只依賴其引數，而不會執行任何會產生副作用的動作。</span><span class="sxs-lookup"><span data-stu-id="de3c7-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="de3c7-178">以下是非純虛擬函式的範例，因為它相依于全域、可變的狀態：</span><span class="sxs-lookup"><span data-stu-id="de3c7-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="de3c7-179">`addOneToValue` 函式會清楚非純虛擬，因為 `value` 可以隨時變更，使其值不同于1。</span><span class="sxs-lookup"><span data-stu-id="de3c7-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="de3c7-180">視全域值而定，這種模式可避免在功能性程式設計中使用。</span><span class="sxs-lookup"><span data-stu-id="de3c7-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="de3c7-181">以下是非純虛擬函式的另一個範例，因為它會執行副作用：</span><span class="sxs-lookup"><span data-stu-id="de3c7-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x =
    printfn "x is %d" x
    x + 1
```

<span data-ttu-id="de3c7-182">雖然此函式不會相依于全域值，但它會將 `x` 的值寫入至程式的輸出。</span><span class="sxs-lookup"><span data-stu-id="de3c7-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="de3c7-183">雖然這麼做並沒有任何問題，但這也表示該函式不是純粹的。</span><span class="sxs-lookup"><span data-stu-id="de3c7-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span> <span data-ttu-id="de3c7-184">如果程式的另一個部分相依于程式以外的某個專案（例如輸出緩衝區），則呼叫此函式可能會影響程式的其他部分。</span><span class="sxs-lookup"><span data-stu-id="de3c7-184">If another part of your program depends on something external to the program, such as the output buffer, then calling this function can affect that other part of your program.</span></span>

<span data-ttu-id="de3c7-185">移除 `printfn` 語句會讓函式成為純虛擬：</span><span class="sxs-lookup"><span data-stu-id="de3c7-185">Removing the `printfn` statement makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="de3c7-186">雖然此_函數原本就不如使用_`printfn` 語句的舊版，但它確實會保證所有此函式都會傳回值。</span><span class="sxs-lookup"><span data-stu-id="de3c7-186">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="de3c7-187">呼叫此函式會產生相同的結果：它只會產生值。</span><span class="sxs-lookup"><span data-stu-id="de3c7-187">Calling this function any number of times produces the same result: it just produces a value.</span></span> <span data-ttu-id="de3c7-188">由純度所提供的可預測性是許多功能程式設計人員所致力的。</span><span class="sxs-lookup"><span data-stu-id="de3c7-188">The predictability given by purity is something many functional programmers strive for.</span></span>

### <a name="immutability"></a><span data-ttu-id="de3c7-189">不變性</span><span class="sxs-lookup"><span data-stu-id="de3c7-189">Immutability</span></span>

<span data-ttu-id="de3c7-190">最後，具型別函式程式設計的最基本概念之一就是不可變性的。</span><span class="sxs-lookup"><span data-stu-id="de3c7-190">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="de3c7-191">在F#中，所有值預設都是不可變的。</span><span class="sxs-lookup"><span data-stu-id="de3c7-191">In F#, all values are immutable by default.</span></span> <span data-ttu-id="de3c7-192">這表示除非您明確地將它們標示為可變動，否則無法就地變動。</span><span class="sxs-lookup"><span data-stu-id="de3c7-192">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="de3c7-193">實際上，使用固定值表示您將程式設計的方法從「我需要變更某些專案」變更為「我需要產生新的值」。</span><span class="sxs-lookup"><span data-stu-id="de3c7-193">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="de3c7-194">例如，將1新增至值表示產生新的值，而不會改變現有的值：</span><span class="sxs-lookup"><span data-stu-id="de3c7-194">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="de3c7-195">在F#中，下列程式碼**不會改變**`value` 函數;相反地，它會執行相等檢查：</span><span class="sxs-lookup"><span data-stu-id="de3c7-195">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="de3c7-196">有些功能性程式設計語言根本不支援變動。</span><span class="sxs-lookup"><span data-stu-id="de3c7-196">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="de3c7-197">在F#中，這是支援的，但不是值的預設行為。</span><span class="sxs-lookup"><span data-stu-id="de3c7-197">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="de3c7-198">此概念更進一步延伸至資料結構。</span><span class="sxs-lookup"><span data-stu-id="de3c7-198">This concept extends even further to data structures.</span></span> <span data-ttu-id="de3c7-199">在功能性程式設計中，固定的資料結構（例如集合（和其他許多）會有不同于最初預期的執行方式。</span><span class="sxs-lookup"><span data-stu-id="de3c7-199">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="de3c7-200">在概念上，將專案加入至集合的作業並不會變更集合，它會產生_新_的集合，並加上值。</span><span class="sxs-lookup"><span data-stu-id="de3c7-200">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="de3c7-201">實際上，這通常是由不同的資料結構所完成，可讓您有效率地追蹤值，以便將適當的資料標記法指定為結果。</span><span class="sxs-lookup"><span data-stu-id="de3c7-201">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="de3c7-202">這種使用值和資料結構的樣式非常重要，因為它會強制您將任何修改專案的作業視為其建立新版本。</span><span class="sxs-lookup"><span data-stu-id="de3c7-202">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="de3c7-203">這可讓您的程式中的等號和可比較性保持一致。</span><span class="sxs-lookup"><span data-stu-id="de3c7-203">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="de3c7-204">後續步驟</span><span class="sxs-lookup"><span data-stu-id="de3c7-204">Next steps</span></span>

<span data-ttu-id="de3c7-205">下一節將徹底探討函式，探索可在函式程式設計中使用它們的不同方式。</span><span class="sxs-lookup"><span data-stu-id="de3c7-205">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="de3c7-206">[第一級函式](first-class-functions.md)會深入探索函式，並示範如何在各種不同的內容中使用這些功能。</span><span class="sxs-lookup"><span data-stu-id="de3c7-206">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="de3c7-207">進一步閱讀</span><span class="sxs-lookup"><span data-stu-id="de3c7-207">Further reading</span></span>

<span data-ttu-id="de3c7-208">[思考功能](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/)系列是另一個絕佳的資源，可供您瞭解F#如何使用進行功能程式設計。</span><span class="sxs-lookup"><span data-stu-id="de3c7-208">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="de3c7-209">其中涵蓋功能程式設計的基本概念，並以實用且容易閱讀的方式使用F#功能來說明概念。</span><span class="sxs-lookup"><span data-stu-id="de3c7-209">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>
