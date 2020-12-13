---
title: F# 函式程式設計簡介
description: '瞭解 F # 中功能性程式設計的基本概念。'
ms.date: 10/29/2018
ms.openlocfilehash: 44242a4319a331312a003a555d1483f2a3f1a90d
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110581"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="0f59a-103">F 中的功能程式設計簡介\#</span><span class="sxs-lookup"><span data-stu-id="0f59a-103">Introduction to Functional Programming in F\#</span></span>

<span data-ttu-id="0f59a-104">功能性程式設計是一種程式設計樣式，強調函式和不可變數據的使用。</span><span class="sxs-lookup"><span data-stu-id="0f59a-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="0f59a-105">具型別函式程式設計是指將函式程式設計與靜態類型（例如 F #）結合。</span><span class="sxs-lookup"><span data-stu-id="0f59a-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="0f59a-106">一般情況下，功能程式設計會強調下列概念：</span><span class="sxs-lookup"><span data-stu-id="0f59a-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="0f59a-107">作為您使用之主要結構的函式</span><span class="sxs-lookup"><span data-stu-id="0f59a-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="0f59a-108">運算式而非語句</span><span class="sxs-lookup"><span data-stu-id="0f59a-108">Expressions instead of statements</span></span>
* <span data-ttu-id="0f59a-109">變數上的不可變值</span><span class="sxs-lookup"><span data-stu-id="0f59a-109">Immutable values over variables</span></span>
* <span data-ttu-id="0f59a-110">命令式程式設計的宣告式程式設計</span><span class="sxs-lookup"><span data-stu-id="0f59a-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="0f59a-111">在本系列中，您將探索使用 F # 的功能性程式設計概念和模式。</span><span class="sxs-lookup"><span data-stu-id="0f59a-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="0f59a-112">在過程中，您也將學習一些 F #。</span><span class="sxs-lookup"><span data-stu-id="0f59a-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="0f59a-113">詞彙</span><span class="sxs-lookup"><span data-stu-id="0f59a-113">Terminology</span></span>

<span data-ttu-id="0f59a-114">功能性程式設計（如同其他程式設計架構）隨附的詞彙，您最終將需要學習。</span><span class="sxs-lookup"><span data-stu-id="0f59a-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="0f59a-115">以下是您將會看到的一些常見詞彙：</span><span class="sxs-lookup"><span data-stu-id="0f59a-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="0f59a-116">**函數** -函式是一種結構，會在指定輸入時產生輸出。</span><span class="sxs-lookup"><span data-stu-id="0f59a-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="0f59a-117">更正式來說，它會將某個專案從一個集合 _對應_ 到另一個集合。</span><span class="sxs-lookup"><span data-stu-id="0f59a-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="0f59a-118">這項形式在許多方面都是以實體方式來完成，特別是在使用資料集合的函式時。</span><span class="sxs-lookup"><span data-stu-id="0f59a-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="0f59a-119">這是功能性程式設計中最基本的 (和重要的) 概念。</span><span class="sxs-lookup"><span data-stu-id="0f59a-119">It is the most basic (and important) concept in functional programming.</span></span>
* <span data-ttu-id="0f59a-120">**運算式** -運算式是在產生值的程式碼中的結構。</span><span class="sxs-lookup"><span data-stu-id="0f59a-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="0f59a-121">在 F # 中，必須系結或明確忽略此值。</span><span class="sxs-lookup"><span data-stu-id="0f59a-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="0f59a-122">運算式可以完整由函式呼叫取代。</span><span class="sxs-lookup"><span data-stu-id="0f59a-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="0f59a-123">**純度** -純度是函數的屬性，因此相同的引數的傳回值一律相同，而且其評估沒有任何副作用。</span><span class="sxs-lookup"><span data-stu-id="0f59a-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="0f59a-124">純虛擬函式完全取決於其引數。</span><span class="sxs-lookup"><span data-stu-id="0f59a-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="0f59a-125">**參考透明度** -參考透明度是運算式的屬性，可將它們取代為其輸出，而不會影響程式的行為。</span><span class="sxs-lookup"><span data-stu-id="0f59a-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="0f59a-126">**永久性** -永久性表示無法就地變更值。</span><span class="sxs-lookup"><span data-stu-id="0f59a-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="0f59a-127">這與可以就地變更的變數相比較。</span><span class="sxs-lookup"><span data-stu-id="0f59a-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="0f59a-128">範例</span><span class="sxs-lookup"><span data-stu-id="0f59a-128">Examples</span></span>

<span data-ttu-id="0f59a-129">下列範例示範這些核心概念。</span><span class="sxs-lookup"><span data-stu-id="0f59a-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="0f59a-130">函式</span><span class="sxs-lookup"><span data-stu-id="0f59a-130">Functions</span></span>

<span data-ttu-id="0f59a-131">函式程式設計中最常見的基本結構是函數。</span><span class="sxs-lookup"><span data-stu-id="0f59a-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="0f59a-132">以下是將1加到整數的簡單函式：</span><span class="sxs-lookup"><span data-stu-id="0f59a-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="0f59a-133">其類型簽章如下所示：</span><span class="sxs-lookup"><span data-stu-id="0f59a-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="0f59a-134">簽章可以讀取為「 `addOne` 接受 `int` 已命名 `x` 且將會產生」 `int` 。</span><span class="sxs-lookup"><span data-stu-id="0f59a-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="0f59a-135">更正式 `addOne` 來說，是將一組整數的值 _對應_ 至整陣列。</span><span class="sxs-lookup"><span data-stu-id="0f59a-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="0f59a-136">`->`Token 表示此對應。</span><span class="sxs-lookup"><span data-stu-id="0f59a-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="0f59a-137">在 F # 中，您通常可以查看函式簽章，以瞭解其用途。</span><span class="sxs-lookup"><span data-stu-id="0f59a-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="0f59a-138">那麼，為什麼簽章很重要？</span><span class="sxs-lookup"><span data-stu-id="0f59a-138">So, why is the signature important?</span></span> <span data-ttu-id="0f59a-139">在具型別函式程式設計中，函數的執行通常比實際的型別簽章更不重要！</span><span class="sxs-lookup"><span data-stu-id="0f59a-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="0f59a-140">`addOne`將值1加入至整數的事實在執行時間很有趣，但是當您在建立程式時，它接受並傳回的事實 `int` 就是通知您實際使用此函式的方式。</span><span class="sxs-lookup"><span data-stu-id="0f59a-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="0f59a-141">此外，一旦您正確地使用此函式 (相對於其類型簽章) ，則診斷任何問題只能在函式主體內進行 `addOne` 。</span><span class="sxs-lookup"><span data-stu-id="0f59a-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="0f59a-142">這是具類型的功能性程式設計背後的促成。</span><span class="sxs-lookup"><span data-stu-id="0f59a-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="0f59a-143">運算式</span><span class="sxs-lookup"><span data-stu-id="0f59a-143">Expressions</span></span>

<span data-ttu-id="0f59a-144">運算式是評估為值的結構。</span><span class="sxs-lookup"><span data-stu-id="0f59a-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="0f59a-145">相較于執行動作的語句，運算式可以考慮執行可傳回值的動作。</span><span class="sxs-lookup"><span data-stu-id="0f59a-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="0f59a-146">運算式幾乎一律用於功能性程式設計，而不是語句。</span><span class="sxs-lookup"><span data-stu-id="0f59a-146">Expressions are almost always used in functional programming instead of statements.</span></span>

<span data-ttu-id="0f59a-147">請考慮先前的函數 `addOne` 。</span><span class="sxs-lookup"><span data-stu-id="0f59a-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="0f59a-148">的主體 `addOne` 為運算式：</span><span class="sxs-lookup"><span data-stu-id="0f59a-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="0f59a-149">這是定義函數結果型別的運算式結果 `addOne` 。</span><span class="sxs-lookup"><span data-stu-id="0f59a-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="0f59a-150">例如，組成此函式的運算式可能會變更為不同的類型，例如 `string` ：</span><span class="sxs-lookup"><span data-stu-id="0f59a-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="0f59a-151">函數的簽章現在是：</span><span class="sxs-lookup"><span data-stu-id="0f59a-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="0f59a-152">由於 F # 中的任何型別都可以 `ToString()` 呼叫它，因此的型別已 `x` 成為泛型 (稱為 [自動一般化](../language-reference/generics/automatic-generalization.md)) ，而結果型別為 `string` 。</span><span class="sxs-lookup"><span data-stu-id="0f59a-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="0f59a-153">運算式不只是函數的主體。</span><span class="sxs-lookup"><span data-stu-id="0f59a-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="0f59a-154">您可以有運算式來產生您在其他地方使用的值。</span><span class="sxs-lookup"><span data-stu-id="0f59a-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="0f59a-155">其中一個常見的情況是 `if` ：</span><span class="sxs-lookup"><span data-stu-id="0f59a-155">A common one is `if`:</span></span>

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

<span data-ttu-id="0f59a-156">`if`運算式會產生名為的 `result` 值。</span><span class="sxs-lookup"><span data-stu-id="0f59a-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="0f59a-157">請注意，您可以 `result` 完全省略，讓 `if` 運算式成為 `addOneIfOdd` 函數主體。</span><span class="sxs-lookup"><span data-stu-id="0f59a-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="0f59a-158">要記住運算式的重點在於它們會產生一個值。</span><span class="sxs-lookup"><span data-stu-id="0f59a-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="0f59a-159">有一種特殊的型 `unit` 別，會在沒有要傳回的專案時使用。</span><span class="sxs-lookup"><span data-stu-id="0f59a-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="0f59a-160">例如，請考慮這個簡單的函式：</span><span class="sxs-lookup"><span data-stu-id="0f59a-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn $"String is: {str}"
```

<span data-ttu-id="0f59a-161">簽章看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="0f59a-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="0f59a-162">`unit`型別指出沒有傳回實際值。</span><span class="sxs-lookup"><span data-stu-id="0f59a-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="0f59a-163">當您的常式必須「執行工作」，但因為該工作不會傳回任何值時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="0f59a-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="0f59a-164">這與命令式程式設計相反，其中對等的 `if` 結構是語句，而產生值通常是透過變動變數來完成。</span><span class="sxs-lookup"><span data-stu-id="0f59a-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="0f59a-165">例如，在 c # 中，程式碼的撰寫方式可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="0f59a-165">For example, in C#, the code might be written like this:</span></span>

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

<span data-ttu-id="0f59a-166">值得注意的是，c # 和其他 C 樣式的語言都支援 [三元運算式](../../csharp/language-reference/operators/conditional-operator.md)，這種運算式允許以運算式為基礎的條件式程式設計。</span><span class="sxs-lookup"><span data-stu-id="0f59a-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="0f59a-167">在功能性程式設計中，使用語句來改變值是很罕見的。</span><span class="sxs-lookup"><span data-stu-id="0f59a-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="0f59a-168">雖然有些功能性語言支援語句和變化，但是在功能性程式設計中使用這些概念並不常見。</span><span class="sxs-lookup"><span data-stu-id="0f59a-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="0f59a-169">純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="0f59a-169">Pure functions</span></span>

<span data-ttu-id="0f59a-170">如先前所述，純虛擬函式是函式，其功能如下：</span><span class="sxs-lookup"><span data-stu-id="0f59a-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="0f59a-171">針對相同的輸入，一律評估為相同的值。</span><span class="sxs-lookup"><span data-stu-id="0f59a-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="0f59a-172">沒有副作用。</span><span class="sxs-lookup"><span data-stu-id="0f59a-172">Have no side effects.</span></span>

<span data-ttu-id="0f59a-173">在此內容中考慮數學函數很有説明。</span><span class="sxs-lookup"><span data-stu-id="0f59a-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="0f59a-174">在數學中，函式只會依賴其引數，而且沒有任何副作用。</span><span class="sxs-lookup"><span data-stu-id="0f59a-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="0f59a-175">在數學函數中 `f(x) = x + 1` ，的值 `f(x)` 只取決於的值 `x` 。</span><span class="sxs-lookup"><span data-stu-id="0f59a-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="0f59a-176">函式程式設計中的純虛擬函式是一樣的。</span><span class="sxs-lookup"><span data-stu-id="0f59a-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="0f59a-177">撰寫純虛擬函式時，函式只能相依于其引數，而不會執行任何會產生副作用的動作。</span><span class="sxs-lookup"><span data-stu-id="0f59a-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="0f59a-178">以下是非純虛擬函式的範例，因為它相依于全域、可變動的狀態：</span><span class="sxs-lookup"><span data-stu-id="0f59a-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="0f59a-179">此函式 `addOneToValue` 很清楚地 impure，因為 `value` 可以隨時變更為具有不同于1的值。</span><span class="sxs-lookup"><span data-stu-id="0f59a-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="0f59a-180">這種以全域值為依據的模式，可避免在功能性程式設計中使用。</span><span class="sxs-lookup"><span data-stu-id="0f59a-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="0f59a-181">以下是非純虛擬函式的另一個範例，因為它會執行副作用：</span><span class="sxs-lookup"><span data-stu-id="0f59a-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x =
    printfn $"x is %d{x}"
    x + 1
```

<span data-ttu-id="0f59a-182">雖然此函式不會相依于全域值，但它會將的值寫入 `x` 程式的輸出。</span><span class="sxs-lookup"><span data-stu-id="0f59a-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="0f59a-183">雖然這樣做並不會發生任何錯誤，但這表示此函式不是單純的。</span><span class="sxs-lookup"><span data-stu-id="0f59a-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span> <span data-ttu-id="0f59a-184">如果程式的另一個部分相依于程式外部的某個專案，例如輸出緩衝區，則呼叫此函式會影響程式的其他部分。</span><span class="sxs-lookup"><span data-stu-id="0f59a-184">If another part of your program depends on something external to the program, such as the output buffer, then calling this function can affect that other part of your program.</span></span>

<span data-ttu-id="0f59a-185">移除 `printfn` 語句會讓函數成為單純的：</span><span class="sxs-lookup"><span data-stu-id="0f59a-185">Removing the `printfn` statement makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="0f59a-186">雖然此函式在本質上並不 _優於_ 使用語句的舊版 `printfn` ，但它確實保證此函式確實會傳回值。</span><span class="sxs-lookup"><span data-stu-id="0f59a-186">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="0f59a-187">每次呼叫此函式會產生相同的結果：它只會產生值。</span><span class="sxs-lookup"><span data-stu-id="0f59a-187">Calling this function any number of times produces the same result: it just produces a value.</span></span> <span data-ttu-id="0f59a-188">由純度提供的可預測性，是許多功能程式設計人員致力於的一些功能。</span><span class="sxs-lookup"><span data-stu-id="0f59a-188">The predictability given by purity is something many functional programmers strive for.</span></span>

### <a name="immutability"></a><span data-ttu-id="0f59a-189">不變性</span><span class="sxs-lookup"><span data-stu-id="0f59a-189">Immutability</span></span>

<span data-ttu-id="0f59a-190">最後，具型別函式程式設計的其中一個最基本概念是永久性。</span><span class="sxs-lookup"><span data-stu-id="0f59a-190">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="0f59a-191">在 F # 中，所有值預設都是不可變的。</span><span class="sxs-lookup"><span data-stu-id="0f59a-191">In F#, all values are immutable by default.</span></span> <span data-ttu-id="0f59a-192">這表示，除非您將它們明確地標示為可變動，否則它們無法就地變動。</span><span class="sxs-lookup"><span data-stu-id="0f59a-192">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="0f59a-193">在實務上，使用不可變的值表示您將程式設計的方法從「我需要變更一些東西」變更為「我需要產生新的值」。</span><span class="sxs-lookup"><span data-stu-id="0f59a-193">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="0f59a-194">例如，將1加1值表示產生新的值，而不會變更現有的值：</span><span class="sxs-lookup"><span data-stu-id="0f59a-194">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="0f59a-195">在 F # 中，下列程式碼 **不會** 改變 `value` 函數; 相反地，它會執行相等檢查：</span><span class="sxs-lookup"><span data-stu-id="0f59a-195">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="0f59a-196">有些功能性程式設計語言並不支援變動。</span><span class="sxs-lookup"><span data-stu-id="0f59a-196">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="0f59a-197">在 F # 中，它是支援的，但它不是值的預設行為。</span><span class="sxs-lookup"><span data-stu-id="0f59a-197">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="0f59a-198">此概念甚至進一步延伸至資料結構。</span><span class="sxs-lookup"><span data-stu-id="0f59a-198">This concept extends even further to data structures.</span></span> <span data-ttu-id="0f59a-199">在功能性程式設計中，不可變的資料結構，例如 set (以及許多) 有不同于一開始預期的不同執行。</span><span class="sxs-lookup"><span data-stu-id="0f59a-199">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="0f59a-200">就概念而言，將專案加入至集合中的專案並不會變更集合，它會產生具有新增值的 _新_ 集合。</span><span class="sxs-lookup"><span data-stu-id="0f59a-200">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="0f59a-201">在幕後，這通常是透過不同的資料結構來完成，讓您能夠有效率地追蹤值，以便將資料的適當標記法提供給結果。</span><span class="sxs-lookup"><span data-stu-id="0f59a-201">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="0f59a-202">這種使用值和資料結構的樣式是很重要的，因為它會強制您將修改某些事物的任何作業視為建立新的版本。</span><span class="sxs-lookup"><span data-stu-id="0f59a-202">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="0f59a-203">這可讓您的程式中的等號和可比較性等專案保持一致。</span><span class="sxs-lookup"><span data-stu-id="0f59a-203">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0f59a-204">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0f59a-204">Next steps</span></span>

<span data-ttu-id="0f59a-205">下一節將徹底涵蓋函式，探索可在功能性程式設計中使用這些功能的不同方式。</span><span class="sxs-lookup"><span data-stu-id="0f59a-205">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="0f59a-206">[第](first-class-functions.md) 一級函式探索更深層的函式，並示範如何在各種內容中使用這些函數。</span><span class="sxs-lookup"><span data-stu-id="0f59a-206">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="0f59a-207">進一步閱讀</span><span class="sxs-lookup"><span data-stu-id="0f59a-207">Further reading</span></span>

<span data-ttu-id="0f59a-208">[思考功能](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/)系列是另一項絕佳的資源，可瞭解如何使用 F # 進行功能性程式設計。</span><span class="sxs-lookup"><span data-stu-id="0f59a-208">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="0f59a-209">它涵蓋功能性程式設計的基本概念，並使用 F # 功能來說明概念，以提供實用且容易閱讀的方式。</span><span class="sxs-lookup"><span data-stu-id="0f59a-209">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>
