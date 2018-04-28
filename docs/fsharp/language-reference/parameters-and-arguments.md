---
title: 參數和引數 (F#)
description: '深入了解 F # 語言定義參數及支援將引數傳遞至函式、 方法和屬性。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: e146ec4e877bb89f10e2f3daad2d8356c29fa81f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="4382d-103">參數和引數</span><span class="sxs-lookup"><span data-stu-id="4382d-103">Parameters and Arguments</span></span>

<span data-ttu-id="4382d-104">本主題描述針對定義參數並將引數傳遞給函式、 方法和屬性的語言支援。</span><span class="sxs-lookup"><span data-stu-id="4382d-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="4382d-105">其中包括如何以傳參考，以及如何定義和使用可變數目的引數的方法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4382d-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>


## <a name="parameters-and-arguments"></a><span data-ttu-id="4382d-106">參數和引數</span><span class="sxs-lookup"><span data-stu-id="4382d-106">Parameters and Arguments</span></span>
<span data-ttu-id="4382d-107">詞彙*參數*用來描述應提供的值的名稱。</span><span class="sxs-lookup"><span data-stu-id="4382d-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="4382d-108">詞彙*引數*用於提供每個參數的值。</span><span class="sxs-lookup"><span data-stu-id="4382d-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="4382d-109">Tuple 或局部調用的表單，或兩者的組合，可以指定參數。</span><span class="sxs-lookup"><span data-stu-id="4382d-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="4382d-110">您可以使用明確的參數名稱傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="4382d-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="4382d-111">方法的參數可以指定為選擇性，並指定預設值。</span><span class="sxs-lookup"><span data-stu-id="4382d-111">Parameters of methods can be specified as optional and given a default value.</span></span>


## <a name="parameter-patterns"></a><span data-ttu-id="4382d-112">參數模式</span><span class="sxs-lookup"><span data-stu-id="4382d-112">Parameter Patterns</span></span>
<span data-ttu-id="4382d-113">提供給函式和方法的參數，在一般情況下，模式會以空格分隔。</span><span class="sxs-lookup"><span data-stu-id="4382d-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="4382d-114">這表示，在一般的原則中的任何模式中所述[比對運算式](match-expressions.md)可用參數清單中的函式或成員。</span><span class="sxs-lookup"><span data-stu-id="4382d-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="4382d-115">方法通常會使用傳遞引數的 tuple 形式。</span><span class="sxs-lookup"><span data-stu-id="4382d-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="4382d-116">由於 tuple 形式比對引數會傳入的.NET 方法的方式，這就會達到從其他.NET 語言的觀點來看更清楚結果。</span><span class="sxs-lookup"><span data-stu-id="4382d-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="4382d-117">局部調用的表單最常搭配使用所建立的函式`let`繫結。</span><span class="sxs-lookup"><span data-stu-id="4382d-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="4382d-118">下列虛擬程式碼顯示 tuple 和局部調用引數的範例。</span><span class="sxs-lookup"><span data-stu-id="4382d-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="4382d-119">結合的表單可能會當某些引數的 tuple 而某些則不會。</span><span class="sxs-lookup"><span data-stu-id="4382d-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="4382d-120">其他模式也可用在參數清單中，但如果參數模式不符合所有可能的輸入，可能有不完整的相符項目在執行階段。</span><span class="sxs-lookup"><span data-stu-id="4382d-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="4382d-121">例外狀況`MatchFailureException`引數的值與參數清單中指定的模式不相符時產生。</span><span class="sxs-lookup"><span data-stu-id="4382d-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="4382d-122">參數模式允許不完整的相符項目時，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="4382d-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="4382d-123">至少一個其他的模式是常用於參數清單，而這是萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="4382d-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="4382d-124">當您只想要忽略會提供任何引數時，您可以使用參數清單中的萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="4382d-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="4382d-125">下列程式碼說明如何使用引數清單中的萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="4382d-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="4382d-126">萬用字元模式可能會很有用，每當您不需要在傳遞的引數，例如主要進入點至程式中，您不感興趣通常會提供以字串陣列，如下列程式碼所示的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="4382d-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="4382d-127">偶爾會用在引數的其他模式為`as`模式，以及差別等位和作用中的模式與相關聯的識別項模式。</span><span class="sxs-lookup"><span data-stu-id="4382d-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="4382d-128">您可以使用單一案例差別等位模式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="4382d-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="4382d-129">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="4382d-129">The output is as follows.</span></span>

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="4382d-130">現用模式相當適合做為參數，例如，將引數轉換成所需的格式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4382d-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="4382d-131">您可以使用`as`將相符的值做為本機的值，如下列程式碼所示的模式。</span><span class="sxs-lookup"><span data-stu-id="4382d-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="4382d-132">偶爾使用的另一種模式是離開藉由提供，做為函式的主體未命名的最後一個引數的函式、 lambda 運算式的隱含引數會立即執行模式比對。</span><span class="sxs-lookup"><span data-stu-id="4382d-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="4382d-133">舉例來說，這是下列程式碼行。</span><span class="sxs-lookup"><span data-stu-id="4382d-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="4382d-134">此程式碼定義的函式採用的泛型清單，並傳回`true`如果清單是空的與`false`否則。</span><span class="sxs-lookup"><span data-stu-id="4382d-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="4382d-135">使用這類技術可讓程式碼更難閱讀。</span><span class="sxs-lookup"><span data-stu-id="4382d-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="4382d-136">有時候，牽涉到未完成的比對的模式會很有用，例如，如果您知道您的程式中的清單有只有三個項目，您可能會使用如下所示的模式參數清單中。</span><span class="sxs-lookup"><span data-stu-id="4382d-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="4382d-137">使用具有不完整的比對的模式最，保留供快速原型化和其他暫時性使用。</span><span class="sxs-lookup"><span data-stu-id="4382d-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="4382d-138">編譯器會發出這類程式碼的警告。</span><span class="sxs-lookup"><span data-stu-id="4382d-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="4382d-139">這類模式無法涵蓋所有可能的輸入值的一般情況下，因此不是適用於應用程式開發介面的元件。</span><span class="sxs-lookup"><span data-stu-id="4382d-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="4382d-140">具名引數</span><span class="sxs-lookup"><span data-stu-id="4382d-140">Named Arguments</span></span>
<span data-ttu-id="4382d-141">方法的引數可以指定在以逗號分隔的引數清單中的位置，或它們可以傳遞至方法明確地提供的名稱，後面接著等號和傳入的值。</span><span class="sxs-lookup"><span data-stu-id="4382d-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="4382d-142">如果指定藉由提供名稱，可以在宣告中所使用的不同順序顯示。</span><span class="sxs-lookup"><span data-stu-id="4382d-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="4382d-143">具名引數可讓程式碼更容易閱讀及可調整至特定類型的 API，例如重新排列方法參數中的變更。</span><span class="sxs-lookup"><span data-stu-id="4382d-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="4382d-144">若是方法，只允許具名引數不適用於`let`-繫結函式、 函式值或 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="4382d-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="4382d-145">下列程式碼範例示範如何使用具名引數。</span><span class="sxs-lookup"><span data-stu-id="4382d-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="4382d-146">在類別建構函式呼叫中，您可以使用類似的具名引數的語法來設定類別的屬性值。</span><span class="sxs-lookup"><span data-stu-id="4382d-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="4382d-147">下列範例會顯示此語法。</span><span class="sxs-lookup"><span data-stu-id="4382d-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="4382d-148">如需詳細資訊，請參閱[建構函式 （F #）](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05)。</span><span class="sxs-lookup"><span data-stu-id="4382d-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="4382d-149">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="4382d-149">Optional Parameters</span></span>
<span data-ttu-id="4382d-150">您可以使用參數名稱前面的問號，來指定方法的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="4382d-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="4382d-151">選擇性參數會被解譯為 F # 選項類型，因此您可以查詢它們，查詢的選項類型，使用的一般方式`match`運算式`Some`和`None`。</span><span class="sxs-lookup"><span data-stu-id="4382d-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="4382d-152">只有在成員，使用所建立的函式上不允許選擇性參數`let`繫結。</span><span class="sxs-lookup"><span data-stu-id="4382d-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="4382d-153">您也可以使用函式`defaultArg`，它會設定預設值是選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="4382d-153">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="4382d-154">`defaultArg`函數接受選擇性參數做為第一個引數，而且預設值為第二個。</span><span class="sxs-lookup"><span data-stu-id="4382d-154">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="4382d-155">下列範例說明如何使用選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="4382d-155">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="4382d-156">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="4382d-156">The output is as follows.</span></span>

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a><span data-ttu-id="4382d-157">傳址方式傳遞</span><span class="sxs-lookup"><span data-stu-id="4382d-157">Passing by Reference</span></span>
<span data-ttu-id="4382d-158">F # 支援`byref`關鍵字可指定傳址方式傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="4382d-158">F# supports the `byref` keyword, which specifies that a parameter is passed by reference.</span></span> <span data-ttu-id="4382d-159">這表示值的任何變更會保留在執行函式之後。</span><span class="sxs-lookup"><span data-stu-id="4382d-159">This means that any changes to the value are retained after the execution of the function.</span></span> <span data-ttu-id="4382d-160">值提供給`byref`參數必須是可變動。</span><span class="sxs-lookup"><span data-stu-id="4382d-160">Values provided to a `byref` parameter must be mutable.</span></span> <span data-ttu-id="4382d-161">或者，您可以傳遞的適當類型的參考儲存格。</span><span class="sxs-lookup"><span data-stu-id="4382d-161">Alternatively, you can pass reference cells of the appropriate type.</span></span>

<span data-ttu-id="4382d-162">依用來從函式傳回一個以上的值，進而發展的.NET 語言中的參考傳遞。</span><span class="sxs-lookup"><span data-stu-id="4382d-162">Passing by reference in .NET languages evolved as a way to return more than one value from a function.</span></span> <span data-ttu-id="4382d-163">在 F # 中，您可以傳回 tuple，以供此目的，或使用做為參數的可變動參考儲存格。</span><span class="sxs-lookup"><span data-stu-id="4382d-163">In F#, you can return a tuple for this purpose, or use a mutable reference cell as a parameter.</span></span> <span data-ttu-id="4382d-164">`byref`之互通性的.NET 程式庫主要是提供的參數。</span><span class="sxs-lookup"><span data-stu-id="4382d-164">The `byref` parameter is mainly provided for interoperability with .NET libraries.</span></span>

<span data-ttu-id="4382d-165">下列範例說明使用`byref`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4382d-165">The following examples illustrate the use of the `byref` keyword.</span></span> <span data-ttu-id="4382d-166">請注意，當您使用做為參數的參考儲存格，您必須建立參考儲存格一個具名值為和用來做為參數，不只是加入`ref`運算子的第一個呼叫中所示`Increment`下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="4382d-166">Note that when you use a reference cell as a parameter, you must create a reference cell as a named value and use that as the parameter, not just add the `ref` operator as shown in the first call to `Increment` in the following code.</span></span> <span data-ttu-id="4382d-167">建立參考儲存格建立基礎值的複本，因為第一次呼叫只會遞增暫時的值。</span><span class="sxs-lookup"><span data-stu-id="4382d-167">Because creating a reference cell creates a copy of the underlying value, the first call just increments a temporary value.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

<span data-ttu-id="4382d-168">您也可以做為傳回值使用 tuple，儲存任何`out`.NET 程式庫方法中的參數。</span><span class="sxs-lookup"><span data-stu-id="4382d-168">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="4382d-169">或者，您可以將視為`out`參數做為`byref`參數。</span><span class="sxs-lookup"><span data-stu-id="4382d-169">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="4382d-170">下列程式碼範例將說明這兩種方式。</span><span class="sxs-lookup"><span data-stu-id="4382d-170">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="4382d-171">參數陣列</span><span class="sxs-lookup"><span data-stu-id="4382d-171">Parameter Arrays</span></span>
<span data-ttu-id="4382d-172">有時候會需要 」 定義接受任意數目的異質的型別參數的函式。</span><span class="sxs-lookup"><span data-stu-id="4382d-172">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="4382d-173">它不會實際建立無法使用的所有類型的所有可能多載的方法。</span><span class="sxs-lookup"><span data-stu-id="4382d-173">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="4382d-174">.NET 實作這類方法，透過參數陣列功能提供支援。</span><span class="sxs-lookup"><span data-stu-id="4382d-174">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="4382d-175">採用其簽章中的參數陣列的方法可供任意數目的參數使用。</span><span class="sxs-lookup"><span data-stu-id="4382d-175">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="4382d-176">參數會放入陣列。</span><span class="sxs-lookup"><span data-stu-id="4382d-176">The parameters are put into an array.</span></span> <span data-ttu-id="4382d-177">陣列項目的類型會決定可以傳遞至函數的參數類型。</span><span class="sxs-lookup"><span data-stu-id="4382d-177">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="4382d-178">如果您定義的參數陣列`System.Object`做為項目類型，然後用戶端程式碼可以傳遞任何類型的值。</span><span class="sxs-lookup"><span data-stu-id="4382d-178">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="4382d-179">在 F # 中，參數陣列只可以定義在方法中。</span><span class="sxs-lookup"><span data-stu-id="4382d-179">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="4382d-180">它們不能在獨立函式或模組中定義的函式。</span><span class="sxs-lookup"><span data-stu-id="4382d-180">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="4382d-181">您可以使用定義的參數陣列`ParamArray`屬性。</span><span class="sxs-lookup"><span data-stu-id="4382d-181">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="4382d-182">`ParamArray`屬性只能套用至最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="4382d-182">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="4382d-183">下列程式碼說明這兩個呼叫.NET 方法在 F # 具有採用參數陣列的方法會採用一個參數陣列和類型的定義。</span><span class="sxs-lookup"><span data-stu-id="4382d-183">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="4382d-184">專案中執行時，先前的程式碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="4382d-184">When run in a project, the output of the previous code is as follows:</span></span>

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="4382d-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4382d-185">See Also</span></span>
[<span data-ttu-id="4382d-186">成員</span><span class="sxs-lookup"><span data-stu-id="4382d-186">Members</span></span>](members/index.md)
