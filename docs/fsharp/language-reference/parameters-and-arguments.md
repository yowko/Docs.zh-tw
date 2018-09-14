---
title: 參數和引數 (F#)
description: '深入了解 F # 語言支援對定義參數，以及將引數傳遞至函式、 方法和屬性。'
ms.date: 05/16/2016
ms.openlocfilehash: a1e2a70ca560bbb09d2cd10f47485cbe5c5e029d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591655"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="c8b54-103">參數和引數</span><span class="sxs-lookup"><span data-stu-id="c8b54-103">Parameters and Arguments</span></span>

<span data-ttu-id="c8b54-104">本主題描述針對定義參數，以及將引數傳遞至函式、 方法和屬性的語言支援。</span><span class="sxs-lookup"><span data-stu-id="c8b54-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="c8b54-105">它包含如何傳遞的參考，以及如何定義和使用方法可接受可變數目的引數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c8b54-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="c8b54-106">參數和引數</span><span class="sxs-lookup"><span data-stu-id="c8b54-106">Parameters and Arguments</span></span>

<span data-ttu-id="c8b54-107">詞彙*參數*用來描述應提供的值的名稱。</span><span class="sxs-lookup"><span data-stu-id="c8b54-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="c8b54-108">詞彙*引數*用於提供每個參數的值。</span><span class="sxs-lookup"><span data-stu-id="c8b54-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="c8b54-109">在 tuple、 局部調用的形式，或兩者的一些組合，可以指定參數。</span><span class="sxs-lookup"><span data-stu-id="c8b54-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="c8b54-110">您可以使用明確的參數名稱傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="c8b54-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="c8b54-111">方法的參數可以指定為選擇性，並指定預設值。</span><span class="sxs-lookup"><span data-stu-id="c8b54-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="c8b54-112">參數模式</span><span class="sxs-lookup"><span data-stu-id="c8b54-112">Parameter Patterns</span></span>

<span data-ttu-id="c8b54-113">提供給函式和方法的參數在一般情況下，是以空格分隔的模式。</span><span class="sxs-lookup"><span data-stu-id="c8b54-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="c8b54-114">這表示，基本上，任何模式中所述[比對運算式](match-expressions.md)可用參數清單中的函式或成員。</span><span class="sxs-lookup"><span data-stu-id="c8b54-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="c8b54-115">方法通常會使用傳遞引數的 tuple 形式。</span><span class="sxs-lookup"><span data-stu-id="c8b54-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="c8b54-116">這也可達到更清楚的結果從其他.NET 語言的觀點來看，因為 tuple 形式符合.NET 方法中傳遞引數的方式。</span><span class="sxs-lookup"><span data-stu-id="c8b54-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="c8b54-117">局部調用的形式最常搭配使用所建立的函式`let`繫結。</span><span class="sxs-lookup"><span data-stu-id="c8b54-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="c8b54-118">下列虛擬程式碼會示範 tuple 和局部調用引數的範例。</span><span class="sxs-lookup"><span data-stu-id="c8b54-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="c8b54-119">結合的表單時，某些引數是在 tuple，而有些則不。</span><span class="sxs-lookup"><span data-stu-id="c8b54-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="c8b54-120">其他模式也可用在參數清單中，但如果參數模式不符合所有可能的輸入，可能會有不完整的相符項目在執行階段。</span><span class="sxs-lookup"><span data-stu-id="c8b54-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="c8b54-121">例外狀況`MatchFailureException`引數的值不符合指定的參數清單中的模式時，會產生。</span><span class="sxs-lookup"><span data-stu-id="c8b54-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="c8b54-122">參數模式允許不完全相符的項目時，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="c8b54-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="c8b54-123">至少一個其他的模式是常用的參數清單和萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="c8b54-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="c8b54-124">當您只想要忽略所提供的任何引數時，您可以使用在參數清單中的萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="c8b54-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="c8b54-125">下列程式碼說明如何使用引數清單中的萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="c8b54-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="c8b54-126">萬用字元模式時您不感興趣通常會提供以字串陣列，如下列程式碼所示的命令列引數，可能會很有用，每當您不需要傳入的引數，例如程式的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="c8b54-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="c8b54-127">有時會用於引數的其他模式是`as`模式和差別聯的集和作用中的模式與相關聯的識別項模式。</span><span class="sxs-lookup"><span data-stu-id="c8b54-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="c8b54-128">您可以使用單一案例的已區分聯集模式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="c8b54-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="c8b54-129">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="c8b54-129">The output is as follows.</span></span>

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="c8b54-130">作用中的模式有助於進行做為參數，例如，將引數轉換成所需的格式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c8b54-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="c8b54-131">您可以使用`as`模式來儲存為本機值時，相符的值，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c8b54-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="c8b54-132">偶爾使用的另一種模式是會保留最後一個未命名的提供，做為主體的函式的引數的函式、 lambda 運算式的隱含引數會立即執行模式比對。</span><span class="sxs-lookup"><span data-stu-id="c8b54-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="c8b54-133">其中一個範例就是下列程式碼行。</span><span class="sxs-lookup"><span data-stu-id="c8b54-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="c8b54-134">此程式碼定義的函式會採用泛型清單，並傳回`true`如果清單是空的、 和`false`否則。</span><span class="sxs-lookup"><span data-stu-id="c8b54-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="c8b54-135">使用這類技術可以讓程式碼更難讀取。</span><span class="sxs-lookup"><span data-stu-id="c8b54-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="c8b54-136">有時候，模式，牽涉到不完整的相符項目很有用，例如，如果您知道您的程式中的清單有三個項目，您可能使用如下所示的模式參數清單中。</span><span class="sxs-lookup"><span data-stu-id="c8b54-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="c8b54-137">有未完成的比對的模式使用適合快速建立原型和其他暫存的用途。</span><span class="sxs-lookup"><span data-stu-id="c8b54-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="c8b54-138">編譯器會發出這類程式碼的警告。</span><span class="sxs-lookup"><span data-stu-id="c8b54-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="c8b54-139">這種模式無法涵蓋所有可能的輸入的一般情況下，因此不適合元件 Api。</span><span class="sxs-lookup"><span data-stu-id="c8b54-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="c8b54-140">具名引數</span><span class="sxs-lookup"><span data-stu-id="c8b54-140">Named Arguments</span></span>

<span data-ttu-id="c8b54-141">方法的引數可以指定以逗號分隔的引數清單中的位置，或可以將它們傳遞至方法明確地提供的名稱，後面接著等號和要傳入的值。</span><span class="sxs-lookup"><span data-stu-id="c8b54-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="c8b54-142">如果指定藉由提供名稱，它們可以出現在宣告中所使用的不同的順序。</span><span class="sxs-lookup"><span data-stu-id="c8b54-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="c8b54-143">具名引數可讓程式碼更容易讀取和可調整某些類型的 API，例如重新排列方法參數中的變更。</span><span class="sxs-lookup"><span data-stu-id="c8b54-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="c8b54-144">對於方法，只允許具名引數不適用於`let`-繫結函式、 函式值或 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="c8b54-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="c8b54-145">下列程式碼範例示範如何使用具名引數。</span><span class="sxs-lookup"><span data-stu-id="c8b54-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="c8b54-146">在類別建構函式呼叫中，您可以使用類似的具名引數的語法設定類別的屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c8b54-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="c8b54-147">下列範例會顯示此語法。</span><span class="sxs-lookup"><span data-stu-id="c8b54-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="c8b54-148">如需詳細資訊，請參閱 <<c0> [ 建構函式 （F #）](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05)。</span><span class="sxs-lookup"><span data-stu-id="c8b54-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="c8b54-149">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="c8b54-149">Optional Parameters</span></span>

<span data-ttu-id="c8b54-150">您可以使用參數名稱前面的問號，以指定方法的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="c8b54-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="c8b54-151">選擇性參數會被解譯為 F # 選項類型，因此您可以按照一般方式，查詢選項類型，藉由查詢`match`運算式具有`Some`和`None`。</span><span class="sxs-lookup"><span data-stu-id="c8b54-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="c8b54-152">只有在成員，使用所建立的函式上不允許選擇性參數`let`繫結。</span><span class="sxs-lookup"><span data-stu-id="c8b54-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="c8b54-153">您也可以使用函式`defaultArg`，可設定預設值是選擇性的引數。</span><span class="sxs-lookup"><span data-stu-id="c8b54-153">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="c8b54-154">`defaultArg`函數接受選擇性的參數做為第一個引數和預設值為第二個。</span><span class="sxs-lookup"><span data-stu-id="c8b54-154">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="c8b54-155">下列範例說明如何使用選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="c8b54-155">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="c8b54-156">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="c8b54-156">The output is as follows.</span></span>

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a><span data-ttu-id="c8b54-157">傳址方式傳遞</span><span class="sxs-lookup"><span data-stu-id="c8b54-157">Passing by Reference</span></span>

<span data-ttu-id="c8b54-158">傳址方式傳遞 F # 值涉及[byref](byrefs.md)，這是 managed 的指標類型。</span><span class="sxs-lookup"><span data-stu-id="c8b54-158">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="c8b54-159">若要使用哪種類型時，如下所示的指引：</span><span class="sxs-lookup"><span data-stu-id="c8b54-159">Guidance for which type to use is as follows:</span></span>

* <span data-ttu-id="c8b54-160">使用`inref<'T>`如果您只需要讀取的指標。</span><span class="sxs-lookup"><span data-stu-id="c8b54-160">Use `inref<'T>` if you only need to read the pointer.</span></span>
* <span data-ttu-id="c8b54-161">使用`outref<'T>`如果您只需要撰寫的指標。</span><span class="sxs-lookup"><span data-stu-id="c8b54-161">Use `outref<'T>` if you only need to write to the pointer.</span></span>
* <span data-ttu-id="c8b54-162">使用`byref<'T>`如果您需要從讀取和寫入的指標。</span><span class="sxs-lookup"><span data-stu-id="c8b54-162">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

// No need to make it mutable, since it's read-only
let x = 1
example1 &x

// Needs to be mutable, since we write to it
let mutable y = 2
example2 &y
example3 &y // Now 'y' is 3
```

<span data-ttu-id="c8b54-163">因為參數是指標，且值是可變動，仍會保留值的任何變更之後執行的函式。</span><span class="sxs-lookup"><span data-stu-id="c8b54-163">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="c8b54-164">您可以做為傳回值使用 tuple，來儲存任何`out`.NET 程式庫方法中的參數。</span><span class="sxs-lookup"><span data-stu-id="c8b54-164">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="c8b54-165">或者，您可以將視為`out`參數做為`byref`參數。</span><span class="sxs-lookup"><span data-stu-id="c8b54-165">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="c8b54-166">下列程式碼範例說明這兩種方式。</span><span class="sxs-lookup"><span data-stu-id="c8b54-166">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="c8b54-167">參數陣列</span><span class="sxs-lookup"><span data-stu-id="c8b54-167">Parameter Arrays</span></span>

<span data-ttu-id="c8b54-168">偶爾也會需要定義任意數目的異質的型別參數的函式。</span><span class="sxs-lookup"><span data-stu-id="c8b54-168">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="c8b54-169">它不會實際建立所有可能多載的方法來處理所有可用的類型。</span><span class="sxs-lookup"><span data-stu-id="c8b54-169">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="c8b54-170">.NET 實作提供這類方法，透過參數陣列功能的支援。</span><span class="sxs-lookup"><span data-stu-id="c8b54-170">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="c8b54-171">採用在其簽章的參數陣列的方法可供任意數目的參數使用。</span><span class="sxs-lookup"><span data-stu-id="c8b54-171">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="c8b54-172">參數會放入陣列。</span><span class="sxs-lookup"><span data-stu-id="c8b54-172">The parameters are put into an array.</span></span> <span data-ttu-id="c8b54-173">陣列元素的類型會決定可以傳遞至函式的參數型別。</span><span class="sxs-lookup"><span data-stu-id="c8b54-173">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="c8b54-174">如果您定義的參數陣列`System.Object`做為項目類型，則用戶端程式碼可以傳遞任何類型的值。</span><span class="sxs-lookup"><span data-stu-id="c8b54-174">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="c8b54-175">在 F # 中，參數陣列只能在方法中定義。</span><span class="sxs-lookup"><span data-stu-id="c8b54-175">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="c8b54-176">它們不能在獨立函式或模組中定義的函式。</span><span class="sxs-lookup"><span data-stu-id="c8b54-176">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="c8b54-177">您可以使用定義的參數陣列`ParamArray`屬性。</span><span class="sxs-lookup"><span data-stu-id="c8b54-177">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="c8b54-178">`ParamArray`屬性只能套用至最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="c8b54-178">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="c8b54-179">下列程式碼說明這兩個呼叫的.NET 方法，會採用參數陣列和定義型別的 F # 可採用的參數陣列的方法。</span><span class="sxs-lookup"><span data-stu-id="c8b54-179">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="c8b54-180">當執行在專案中，先前的程式碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="c8b54-180">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="c8b54-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8b54-181">See also</span></span>

- [<span data-ttu-id="c8b54-182">成員</span><span class="sxs-lookup"><span data-stu-id="c8b54-182">Members</span></span>](members/index.md)
