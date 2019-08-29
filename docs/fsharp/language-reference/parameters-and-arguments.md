---
title: 參數和引數
description: 瞭解定義F#參數的語言支援, 以及將引數傳遞至函式、方法和屬性的功能。
ms.date: 05/16/2016
ms.openlocfilehash: 67e82d031c4b22bc30a6f278d9698298ccff2e21
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106597"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="8c7b3-103">參數和引數</span><span class="sxs-lookup"><span data-stu-id="8c7b3-103">Parameters and Arguments</span></span>

<span data-ttu-id="8c7b3-104">本主題說明定義參數以及將引數傳遞至函式、方法和屬性的語言支援。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="8c7b3-105">其中包含有關如何以傳址方式傳遞的資訊, 以及如何定義和使用可接受可變數目之引數的方法。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="8c7b3-106">參數和引數</span><span class="sxs-lookup"><span data-stu-id="8c7b3-106">Parameters and Arguments</span></span>

<span data-ttu-id="8c7b3-107">詞彙*參數*是用來描述預期要提供之值的名稱。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="8c7b3-108">詞彙*引數*會用於為每個參數提供的值。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="8c7b3-109">參數可以指定于元組或擴充形式, 或兩者的某種組合中。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="8c7b3-110">您可以使用明確的參數名稱傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="8c7b3-111">方法的參數可以指定為選擇性, 並提供預設值。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="8c7b3-112">參數模式</span><span class="sxs-lookup"><span data-stu-id="8c7b3-112">Parameter Patterns</span></span>

<span data-ttu-id="8c7b3-113">在一般情況下, 提供給函式和方法的參數是以空格分隔的模式。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="8c7b3-114">這表示, 在「比對[運算式](match-expressions.md)」中所描述的任何模式, 都可以用於函式或成員的參數清單中。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="8c7b3-115">方法通常會使用傳遞引數的元組形式。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="8c7b3-116">這可從其他 .NET 語言的觀點來得到更清楚的結果, 因為元組表單符合在 .NET 方法中傳遞引數的方式。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="8c7b3-117">使用系結所建立`let`的函式最常使用「擴充表單」。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="8c7b3-118">下列虛擬代碼顯示元組和擴充引數的範例。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="8c7b3-119">當某些引數位於元組中, 而有些則不是時, 可能會結合表單。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="8c7b3-120">其他模式也可以在參數清單中使用, 但如果參數模式不符合所有可能的輸入, 則在執行時間可能會有不完整的相符項。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="8c7b3-121">當自`MatchFailureException`變數的值不符合參數清單中指定的模式時, 就會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="8c7b3-122">當參數模式允許不完整的相符專案時, 編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="8c7b3-123">至少另一個模式通常適用于參數清單, 而這是萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="8c7b3-124">當您只想要忽略所提供的任何引數時, 您可以在參數清單中使用萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="8c7b3-125">下列程式碼說明如何在引數清單中使用萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="8c7b3-126">當您不想對通常提供為字串陣列的命令列引數 (如下列程式碼所示) 時, 萬用字元模式就很有用, 因為當您不需要傳入的引數時 (例如在程式的主要進入點中)。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="8c7b3-127">有時在引數中使用的`as`其他模式是模式, 以及與不同等位和作用中模式相關聯的識別碼模式。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="8c7b3-128">您可以使用單一案例的區分聯集模式, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="8c7b3-129">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-129">The output is as follows.</span></span>

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="8c7b3-130">作用中模式可以做為參數使用, 例如, 將引數轉換成所需的格式時, 如下列範例所示:</span><span class="sxs-lookup"><span data-stu-id="8c7b3-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="8c7b3-131">您可以使用`as`模式來儲存符合的值做為區域值, 如下列程式程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="8c7b3-132">偶爾使用的另一個模式是將最後一個引數保留為未命名的函式, 方法是提供, 做為函數的主體, 此 lambda 運算式會立即執行隱含引數的模式比對。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="8c7b3-133">下面這行程式碼就是其中一個範例。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="8c7b3-134">這段程式碼會定義一個採用泛型清單的函`true`式, 並在清單是空`false`的時傳回, 否則會傳回。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="8c7b3-135">使用這類技術可能會使程式碼更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="8c7b3-136">有時候, 包含不完整相符專案的模式很有用, 例如, 如果您知道程式中的清單只有三個元素, 您可以在參數清單中使用類似下列的模式。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="8c7b3-137">使用具有不完整相符專案的模式, 最好是保留給快速原型設計和其他暫存用途。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="8c7b3-138">編譯器會發出這類程式碼的警告。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="8c7b3-139">這類模式無法涵蓋所有可能輸入的一般案例, 因此不適合元件 Api。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="8c7b3-140">具名引數</span><span class="sxs-lookup"><span data-stu-id="8c7b3-140">Named Arguments</span></span>

<span data-ttu-id="8c7b3-141">方法的引數可以透過以逗號分隔的引數清單中的位置來指定, 也可以藉由提供名稱 (後面接著等號和要傳入的值) 明確地傳遞給方法。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="8c7b3-142">如果藉由提供名稱來指定, 它們可以與宣告中使用的不同順序出現。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="8c7b3-143">具名引數可讓程式碼更容易閱讀, 並更適應 API 中特定類型的變更, 例如方法參數的重新排列。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="8c7b3-144">具名引數僅適用于方法, 不允許用於`let`系結函式、函數值或 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="8c7b3-145">下列程式碼範例示範如何使用具名引數。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="8c7b3-146">在類別函式的呼叫中, 您可以使用類似于具名引數的語法來設定類別的屬性值。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="8c7b3-147">下列範例顯示此語法。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="8c7b3-148">如需詳細資訊, 請參閱[函數 (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05)。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="8c7b3-149">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="8c7b3-149">Optional Parameters</span></span>

<span data-ttu-id="8c7b3-150">您可以使用參數名稱前面的問號來指定方法的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="8c7b3-151">選擇性參數會被F#視為選項類型, 因此您可以使用`match`運算式`Some`搭配和`None`, 以一般方式查詢選項類型。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="8c7b3-152">選擇性參數只能用於成員, 而不允許使用`let`系結所建立的函式。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="8c7b3-153">您可以使用參數名稱 (例如`?arg=None`或`?arg=Some(3)`或`?arg=arg`), 將現有的選擇性值傳遞給方法。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="8c7b3-154">建立將選擇性引數傳遞至另一個方法的方法時, 這會很有用。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="8c7b3-155">您也可以使用函數`defaultArg`來設定選擇性引數的預設值。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="8c7b3-156">`defaultArg`函式會接受選擇性參數作為第一個引數, 並使用預設值做為第二個。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="8c7b3-157">下列範例說明選擇性參數的用法。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="8c7b3-158">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-158">The output is as follows.</span></span>

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="8c7b3-159">為了讓C#和 Visual Basic interop, 您可以使用中`[<Optional; DefaultParameterValue<(...)>]` F#的屬性, 讓呼叫端將引數視為選擇性。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="8c7b3-160">這相當於在中將引數定義為C#選擇性`MyMethod(int i = 3)`的。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="8c7b3-161">您也可以指定新的物件做為預設參數值。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="8c7b3-162">例如, `Foo`成員可能會有選擇性`CancellationToken`的作為輸入, 而不是:</span><span class="sxs-lookup"><span data-stu-id="8c7b3-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="8c7b3-163">指定為引數`DefaultParameterValue`的值必須符合參數的類型。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="8c7b3-164">例如, 不允許下列情況:</span><span class="sxs-lookup"><span data-stu-id="8c7b3-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="8c7b3-165">在此情況下, 編譯器會產生警告, 並同時忽略這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="8c7b3-166">請注意, 預設值`null`必須以類型標注, 否則編譯器會推斷錯誤的類型, `[<Optional; DefaultParameterValue(null:obj)>] o:obj`亦即。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="8c7b3-167">以傳址方式傳遞</span><span class="sxs-lookup"><span data-stu-id="8c7b3-167">Passing by Reference</span></span>

<span data-ttu-id="8c7b3-168">以傳F#址方式傳遞值牽涉到[byref](byrefs.md), 也就是 managed 指標類型。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="8c7b3-169">要使用何種類型的指導方針如下:</span><span class="sxs-lookup"><span data-stu-id="8c7b3-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="8c7b3-170">如果`inref<'T>`您只需要讀取指標, 請使用。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="8c7b3-171">如果`outref<'T>`您只需要寫入指標, 請使用。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="8c7b3-172">如果`byref<'T>`您需要讀取和寫入指標, 請使用。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

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

<span data-ttu-id="8c7b3-173">由於參數是指標, 而值是可變動的, 因此在函式執行之後, 對值所做的任何變更都會保留。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="8c7b3-174">您可以使用元組做為傳回值, 以將`out`任何參數儲存在 .net 程式庫方法中。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="8c7b3-175">或者, 您可以將`out`參數`byref`視為參數。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="8c7b3-176">下列程式碼範例說明這兩種方式。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="8c7b3-177">參數陣列</span><span class="sxs-lookup"><span data-stu-id="8c7b3-177">Parameter Arrays</span></span>

<span data-ttu-id="8c7b3-178">有時候, 您必須定義一個函式, 以接受異類類型的任意數目參數。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="8c7b3-179">建立所有可能的多載方法, 以考慮所有可使用的類型, 並不可行。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="8c7b3-180">.NET 部署透過參數陣列功能提供這類方法的支援。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="8c7b3-181">在其簽章中採用參數陣列的方法, 可以使用任意數目的參數來提供。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="8c7b3-182">參數會放入陣列中。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-182">The parameters are put into an array.</span></span> <span data-ttu-id="8c7b3-183">陣列元素的類型會決定可以傳遞至函數的參數類型。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="8c7b3-184">如果您將參數陣列`System.Object`定義為做為元素類型, 則用戶端程式代碼可以傳遞任何類型的值。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="8c7b3-185">在F#中, 只能在方法中定義參數陣列。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="8c7b3-186">它們不能用於獨立函數或模組中定義的函式。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="8c7b3-187">您可以使用`ParamArray`屬性來定義參數陣列。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="8c7b3-188">`ParamArray`屬性只能套用至最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="8c7b3-189">下列程式碼說明如何呼叫採用參數陣列的 .NET 方法, 以及中F#具有接受參數陣列之方法的類型定義。</span><span class="sxs-lookup"><span data-stu-id="8c7b3-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="8c7b3-190">在專案中執行時, 上述程式碼的輸出如下所示:</span><span class="sxs-lookup"><span data-stu-id="8c7b3-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="8c7b3-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c7b3-191">See also</span></span>

- [<span data-ttu-id="8c7b3-192">成員</span><span class="sxs-lookup"><span data-stu-id="8c7b3-192">Members</span></span>](./members/index.md)
