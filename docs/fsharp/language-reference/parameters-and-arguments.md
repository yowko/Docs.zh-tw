---
title: 參數和引數
description: '深入瞭解 F # 語言支援以定義參數，以及將引數傳遞至函式、方法和屬性。'
ms.date: 08/15/2020
ms.openlocfilehash: 6564fd31105427683af8fc6280672e638737e9b5
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811518"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="8bc6e-103">參數和引數</span><span class="sxs-lookup"><span data-stu-id="8bc6e-103">Parameters and Arguments</span></span>

<span data-ttu-id="8bc6e-104">本主題說明定義參數以及將引數傳遞至函式、方法和屬性的語言支援。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="8bc6e-105">其中包含如何以傳址方式傳遞的資訊，以及如何定義和使用可採用可變動數目之引數的方法。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="8bc6e-106">參數和引數</span><span class="sxs-lookup"><span data-stu-id="8bc6e-106">Parameters and Arguments</span></span>

<span data-ttu-id="8bc6e-107">詞彙 *參數* 是用來描述預期要提供之值的名稱。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="8bc6e-108">詞彙 *引數* 用於每個參數所提供的值。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="8bc6e-109">您可以在元組或局部合併形式中指定參數，或以兩者的某種組合來指定參數。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="8bc6e-110">您可以使用明確的參數名稱傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="8bc6e-111">方法的參數可以指定為選擇性，並指定預設值。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="8bc6e-112">參數模式</span><span class="sxs-lookup"><span data-stu-id="8bc6e-112">Parameter Patterns</span></span>

<span data-ttu-id="8bc6e-113">提供給函式和方法的參數通常是以空格分隔的模式。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="8bc6e-114">這表示，在主體中，比對 [運算式](match-expressions.md) 中所述的任何模式都可以用於函數或成員的參數清單中。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="8bc6e-115">方法通常會使用傳遞引數的元組形式。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="8bc6e-116">因為元組格式符合在 .NET 方法中傳遞引數的方式，所以這可讓您從其他 .NET 語言的觀點來看得到更清楚的結果。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="8bc6e-117">局部加表單最常用於使用系結所建立的函式 `let` 。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="8bc6e-118">下列虛擬程式碼會顯示元組和引數的範例。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="8bc6e-119">當某些引數位於元組中，而有些引數不是時，可能會合並形成。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="8bc6e-120">其他模式也可以在參數清單中使用，但如果參數模式不符合所有可能的輸入，則執行時間可能會有不完整的相符項。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="8bc6e-121">`MatchFailureException`當引數的值與參數清單中指定的模式不相符時，就會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="8bc6e-122">當參數模式允許不完整的相符專案時，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="8bc6e-123">至少有一個其他模式通常適用于參數清單，也就是萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="8bc6e-124">當您只想要忽略任何提供的引數時，請在參數清單中使用萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="8bc6e-125">下列程式碼說明如何在引數清單中使用萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="8bc6e-126">當您不想要使用通常以字串陣列形式提供的命令列引數時（如下列程式碼所示），當您不需要傳入的引數（例如在程式的主要進入點中）時，萬用字元模式會很有用。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="8bc6e-127">有時在引數中使用的其他模式是 `as` 模式，以及與差異聯集和作用中模式相關聯的識別碼模式。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="8bc6e-128">您可以使用單一案例的差異聯集模式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="8bc6e-129">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="8bc6e-130">使用中的模式可作為參數，例如，將引數轉換為所需的格式時，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8bc6e-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="8bc6e-131">您可以使用 `as` 模式來儲存相符的值作為區域值，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="8bc6e-132">偶爾使用的另一個模式是一個函式，此函式會將最後一個引數保留為未命名的函式，該函式是在隱含引數上立即執行模式比對之 lambda 運算式的功能。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="8bc6e-133">以下是這行程式碼的範例。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="8bc6e-134">這段程式碼會定義一個函式，此函式會採用泛型清單，並 `true` 在清單空白時傳回，否則會傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="8bc6e-135">使用這類技術可能使程式碼更難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="8bc6e-136">有時候，牽涉到不完整相符專案的模式會很有用，例如，如果您知道程式中的清單只有三個元素，您可能會在參數清單中使用如下的模式。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="8bc6e-137">使用具有不完整相符專案的模式最適合用於快速原型設計和其他暫存用途。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="8bc6e-138">編譯器會發出這類程式碼的警告。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="8bc6e-139">這類模式無法涵蓋所有可能輸入的一般案例，因此不適合元件 Api。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="8bc6e-140">具名引數</span><span class="sxs-lookup"><span data-stu-id="8bc6e-140">Named Arguments</span></span>

<span data-ttu-id="8bc6e-141">方法的引數可以使用以逗號分隔的引數清單中的位置來指定，也可以藉由提供名稱，並在後面加上等號和要傳入的值，明確地傳遞給方法。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="8bc6e-142">如果是藉由提供名稱所指定，則其顯示方式可能會與宣告中使用的順序不同。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="8bc6e-143">具名引數可以讓程式碼更容易閱讀，而且可更適應 API 中特定類型的變更，例如重新排列方法參數的順序。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="8bc6e-144">只有方法可以使用具名引數，而不是針對系結函 `let` 式、函數值或 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="8bc6e-145">下列程式碼範例示範如何使用具名引數。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="8bc6e-146">在呼叫類別的函式時，您可以使用類似具名引數的語法來設定類別的屬性值。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="8bc6e-147">下列範例顯示此語法。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="8bc6e-148">如需詳細資訊，請參閱 [ (F # ) ](members/constructors.md)的函式。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-148">For more information, see [Constructors (F#)](members/constructors.md).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="8bc6e-149">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="8bc6e-149">Optional Parameters</span></span>

<span data-ttu-id="8bc6e-150">您可以使用參數名稱前面的問號來指定方法的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="8bc6e-151">選擇性參數會被解釋為 F # 選項類型，因此您可以使用具有和的運算式，以定期查詢選項類型的方式來查詢它們 `match` `Some` `None` 。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="8bc6e-152">只有成員可以使用選擇性參數，而不允許在使用系結所建立的函式上使用 `let` 。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="8bc6e-153">您可以透過參數名稱將現有的選擇性值傳遞給方法，例如 `?arg=None` 或 `?arg=Some(3)` 或 `?arg=arg` 。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="8bc6e-154">當您建立的方法會將選擇性引數傳遞給另一個方法時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="8bc6e-155">您也可以使用函 `defaultArg` 式，此函式會設定選擇性引數的預設值。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="8bc6e-156">`defaultArg`函數會採用選擇性參數做為第一個引數，並使用預設值做為第二個引數。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="8bc6e-157">下列範例說明選用參數的用法。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="8bc6e-158">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="8bc6e-159">基於 c # 和 Visual Basic interop 的用途，您可以使用 `[<Optional; DefaultParameterValue<(...)>]` F # 中的屬性，讓呼叫端將引數視為選擇性。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="8bc6e-160">這相當於在 c # 中將引數定義為選擇性，如中所示 `MyMethod(int i = 3)` 。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="8bc6e-161">您也可以將新的物件指定為預設參數值。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="8bc6e-162">例如， `Foo` 成員可以改為使用選擇性的 `CancellationToken` 作為輸入：</span><span class="sxs-lookup"><span data-stu-id="8bc6e-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="8bc6e-163">提供做為引數的值 `DefaultParameterValue` 必須符合參數的類型。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="8bc6e-164">例如，不允許下列動作：</span><span class="sxs-lookup"><span data-stu-id="8bc6e-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="8bc6e-165">在這種情況下，編譯器會產生警告，而且會完全忽略這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="8bc6e-166">請注意，預設值 `null` 必須以類型標注，否則編譯器會推斷錯誤的型別，亦即 `[<Optional; DefaultParameterValue(null:obj)>] o:obj` 。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="8bc6e-167">以傳址方式傳遞</span><span class="sxs-lookup"><span data-stu-id="8bc6e-167">Passing by Reference</span></span>

<span data-ttu-id="8bc6e-168">以傳址方式傳遞 F # 值牽涉到 [byref](byrefs.md)，也就是 managed 指標類型。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="8bc6e-169">應使用何種類型的指引如下：</span><span class="sxs-lookup"><span data-stu-id="8bc6e-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="8bc6e-170">`inref<'T>`如果您只需要讀取指標，請使用。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="8bc6e-171">`outref<'T>`如果您只需要寫入指標，請使用。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="8bc6e-172">`byref<'T>`如果您需要讀取和寫入指標，請使用。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

<span data-ttu-id="8bc6e-173">因為參數是指標，且值是可變動的，所以在執行函式之後，會保留值的任何變更。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="8bc6e-174">您可以使用元組作為傳回值，以 `out` 在 .net 程式庫方法中儲存任何參數。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="8bc6e-175">或者，您可以將 `out` 參數視為 `byref` 參數。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="8bc6e-176">下列程式碼範例說明這兩種方式。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="8bc6e-177">參數陣列</span><span class="sxs-lookup"><span data-stu-id="8bc6e-177">Parameter Arrays</span></span>

<span data-ttu-id="8bc6e-178">有時候，您必須定義一個函式，該函式會接受任意數量的異類類型參數。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="8bc6e-179">建立所有可能的多載方法，以考慮可使用的所有類型，並不是很實用的做法。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="8bc6e-180">.NET 執行可透過參數陣列功能提供這類方法的支援。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="8bc6e-181">在其簽章中接受參數陣列的方法可以提供任意數目的參數。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="8bc6e-182">參數會放入陣列中。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-182">The parameters are put into an array.</span></span> <span data-ttu-id="8bc6e-183">陣列元素的類型會決定可以傳遞給函式的參數類型。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="8bc6e-184">如果您使用 `System.Object` 做為元素類型來定義參數陣列，則用戶端程式代碼可以傳遞任何類型的值。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="8bc6e-185">在 F # 中，只能在方法中定義參數陣列。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="8bc6e-186">它們不能用在模組中定義的獨立函式或函數中。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="8bc6e-187">您可以使用屬性定義參數陣列 `ParamArray` 。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="8bc6e-188">`ParamArray`屬性只能套用至最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="8bc6e-189">下列程式碼說明如何呼叫採用參數陣列的 .NET 方法，以及 F # 中具有接受參數陣列之方法的型別定義。</span><span class="sxs-lookup"><span data-stu-id="8bc6e-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="8bc6e-190">在專案中執行時，上述程式碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="8bc6e-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="8bc6e-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bc6e-191">See also</span></span>

- [<span data-ttu-id="8bc6e-192">成員</span><span class="sxs-lookup"><span data-stu-id="8bc6e-192">Members</span></span>](./members/index.md)
