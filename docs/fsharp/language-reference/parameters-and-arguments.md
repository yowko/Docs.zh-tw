---
title: 參數和引數
description: 瞭解 F# 語言對定義參數和將參數傳遞給函數、方法和屬性的支援。
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400194"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="cc8d0-103">參數和引數</span><span class="sxs-lookup"><span data-stu-id="cc8d0-103">Parameters and Arguments</span></span>

<span data-ttu-id="cc8d0-104">本主題介紹定義參數和將參數傳遞給函數、方法和屬性的語言支援。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="cc8d0-105">它包括有關如何通過引用傳遞的資訊，以及如何定義和使用可以採用可變參數數的方法。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="cc8d0-106">參數和引數</span><span class="sxs-lookup"><span data-stu-id="cc8d0-106">Parameters and Arguments</span></span>

<span data-ttu-id="cc8d0-107">術語*參數*用於描述預期提供的值的名稱。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="cc8d0-108">術語*參數*用於為每個參數提供的值。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="cc8d0-109">參數可以以元組或咖喱形式指定，也可以以兩者的某些組合指定。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="cc8d0-110">可以使用顯式參數名稱傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="cc8d0-111">方法的參數可以指定為可選，並給出預設值。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="cc8d0-112">參數模式</span><span class="sxs-lookup"><span data-stu-id="cc8d0-112">Parameter Patterns</span></span>

<span data-ttu-id="cc8d0-113">提供給函數和方法的參數一般是由空格分隔的模式。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="cc8d0-114">這意味著，原則上，[匹配運算式](match-expressions.md)中描述的任何模式都可以在函數或成員的參數清單中使用。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="cc8d0-115">方法通常使用傳遞參數的元組形式。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="cc8d0-116">從其他 .NET 語言的角度來看，這可實現更清晰的結果，因為元組形式與在 .NET 方法中傳遞參數的方式匹配。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="cc8d0-117">咖喱表單最常用於使用`let`綁定創建的函數。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="cc8d0-118">下面的偽代碼顯示了元組和咖喱參數的示例。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="cc8d0-119">當某些參數位於組合中，而有些參數不是時，可以組合形式。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="cc8d0-120">其他模式也可以在參數清單中使用，但如果參數模式與所有可能的輸入不匹配，則運行時可能存在不完全符合。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="cc8d0-121">當參數`MatchFailureException`的值與參數清單中指定的模式不匹配時，將生成異常。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="cc8d0-122">當參數模式允許不完全符合時，編譯器發出警告。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="cc8d0-123">至少有一個其他模式通常可用於參數清單，即萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="cc8d0-124">當您只想忽略提供的任何參數時，在參數清單中使用萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="cc8d0-125">以下代碼說明了萬用字元模式在參數清單中的使用。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="cc8d0-126">當您不需要傳入的參數（如程式的主進入點）時，當您對通常作為字串陣列提供的命令列參數不感興趣時，萬用字元模式非常有用，如以下代碼。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="cc8d0-127">參數中有時使用的其他模式是與受歧視的聯合`as`和活動模式關聯的模式和識別碼模式。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="cc8d0-128">可以使用單例區分聯合模式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="cc8d0-129">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="cc8d0-130">活動模式可用作參數，例如，將參數轉換為所需格式時，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="cc8d0-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="cc8d0-131">可以使用`as`模式將匹配值存儲為本地值，如下程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="cc8d0-132">偶爾使用的另一種模式是一個函數，該函數通過提供 lambda 運算式（作為函數的正文）來保留最後一個參數未命名，該運算式將立即對隱式參數執行模式匹配。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="cc8d0-133">例如以下程式碼。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="cc8d0-134">此代碼定義一個函數，該函數獲取泛型清單`true`，並在清單為空時返回`false`，否則返回。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="cc8d0-135">使用此類技術會使代碼更難閱讀。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="cc8d0-136">有時，涉及不完全符合的模式很有用，例如，如果您知道程式中的清單只有三個元素，則可以在參數清單中使用如下所示的模式。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="cc8d0-137">使用匹配不完全的模式最好保留用於快速原型設計和其他臨時用途。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="cc8d0-138">編譯器將針對此類代碼發出警告。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="cc8d0-139">此類模式不能涵蓋所有可能輸入的一般情況，因此不適合元件 API。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="cc8d0-140">具名引數</span><span class="sxs-lookup"><span data-stu-id="cc8d0-140">Named Arguments</span></span>

<span data-ttu-id="cc8d0-141">方法的參數可以按逗號分隔參數清單中的位置指定，也可以通過提供名稱（後跟等符號和要傳入的值）顯式傳遞給方法。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="cc8d0-142">如果通過提供名稱指定，它們可以按與聲明中使用的順序不同的顯示順序顯示。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="cc8d0-143">具名引數可以使代碼更具可讀性，並更適應 API 中的某些類型的更改，例如方法參數的重新排序。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="cc8d0-144">具名引數僅允許用於方法，不適用於`let`綁定函數、函數值或 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="cc8d0-145">以下代碼示例演示了具名引數的使用。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="cc8d0-146">在調用類建構函式時，可以使用類似于具名引數的語法來設置類的屬性值。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="cc8d0-147">下面的示例顯示了此語法。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="cc8d0-148">有關詳細資訊，請參閱[建構函式 （F#）。](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05)</span><span class="sxs-lookup"><span data-stu-id="cc8d0-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="cc8d0-149">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="cc8d0-149">Optional Parameters</span></span>

<span data-ttu-id="cc8d0-150">可以使用參數名稱前面的問號為方法指定可選參數。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="cc8d0-151">可選參數被解釋為 F# 選項類型，因此可以使用 的`match``Some`運算式 和 ，以查詢選項類型的常規方式查詢它們。 `None`</span><span class="sxs-lookup"><span data-stu-id="cc8d0-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="cc8d0-152">可選參數僅允許在成員上，不允許使用`let`綁定創建的函數。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="cc8d0-153">可以按參數名稱將現有可選值傳遞給方法，例如`?arg=None`或`?arg=Some(3)``?arg=arg`。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="cc8d0-154">這在構建將可選參數傳遞給另一種方法的方法時非常有用。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="cc8d0-155">您還可以使用 函數`defaultArg`，它設置可選參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="cc8d0-156">函數`defaultArg`將可選參數作為第一個參數，將預設值作為第二個參數。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="cc8d0-157">下面的示例說明了可選參數的使用。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="cc8d0-158">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="cc8d0-159">出於 C# 和 Visual Basic 交互操作的目的，可以使用`[<Optional; DefaultParameterValue<(...)>]`F# 中的屬性，以便調用方將參數視為可選參數。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="cc8d0-160">這相當於在 C# 中將參數定義為可選參數，如`MyMethod(int i = 3)`在 中。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="cc8d0-161">還可以指定新物件作為預設參數值。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="cc8d0-162">例如，`Foo`成員可以改為具有可選`CancellationToken`作為輸入：</span><span class="sxs-lookup"><span data-stu-id="cc8d0-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="cc8d0-163">作為參數給出的值`DefaultParameterValue`必須與參數的類型匹配。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="cc8d0-164">例如，不允許使用以下內容：</span><span class="sxs-lookup"><span data-stu-id="cc8d0-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="cc8d0-165">在這種情況下，編譯器將生成警告，並將完全忽略這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="cc8d0-166">請注意，需要對預設值`null`進行類型注釋，否則編譯器將推斷錯誤的類型，即`[<Optional; DefaultParameterValue(null:obj)>] o:obj`。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="cc8d0-167">通過引用傳遞</span><span class="sxs-lookup"><span data-stu-id="cc8d0-167">Passing by Reference</span></span>

<span data-ttu-id="cc8d0-168">通過引用傳遞 F# 值涉及[byrefs，](byrefs.md)它們是託管指標類型。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="cc8d0-169">使用哪種類型的指南如下所示：</span><span class="sxs-lookup"><span data-stu-id="cc8d0-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="cc8d0-170">如果`inref<'T>`只需要讀取指標，請使用。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="cc8d0-171">如果`outref<'T>`只需要寫入指標，請使用。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="cc8d0-172">如果需要`byref<'T>`同時讀取指標並寫入指標，請使用。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

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

<span data-ttu-id="cc8d0-173">由於參數是指標，並且值是可變的，因此在執行函數後將保留對值的任何更改。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="cc8d0-174">可以使用元組作為傳回值，在 .NET 庫`out`方法中存儲任何參數。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="cc8d0-175">或者，您可以將參數`out`視為參數。 `byref`</span><span class="sxs-lookup"><span data-stu-id="cc8d0-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="cc8d0-176">以下代碼示例說明了這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="cc8d0-177">參數陣列</span><span class="sxs-lookup"><span data-stu-id="cc8d0-177">Parameter Arrays</span></span>

<span data-ttu-id="cc8d0-178">有時，需要定義一個函數，該函數採用異構類型的任意數量的參數。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="cc8d0-179">創建所有可能的重載方法以考慮可以使用的所有類型是不現實的。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="cc8d0-180">.NET 實現通過參數陣列功能為這些方法提供支援。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="cc8d0-181">在其簽名中採用參數陣列的方法可以提供任意數量的參數。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="cc8d0-182">參數被放入陣列中。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-182">The parameters are put into an array.</span></span> <span data-ttu-id="cc8d0-183">陣列元素的類型確定可傳遞給函數的參數類型。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="cc8d0-184">如果將參數陣列`System.Object`定義為元素類型，則用戶端代碼可以傳遞任何類型的值。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="cc8d0-185">在 F# 中，只能在方法中定義參數陣列。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="cc8d0-186">它們不能用於在模組中定義的獨立函數或函數中。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="cc8d0-187">通過使用`ParamArray`屬性定義參數陣列。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="cc8d0-188">該`ParamArray`屬性只能應用於最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="cc8d0-189">以下代碼說明了調用採用參數陣列的 .NET 方法，以及 F# 中具有採用參數陣列的方法的類型的定義。</span><span class="sxs-lookup"><span data-stu-id="cc8d0-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="cc8d0-190">在專案中運行時，前一個代碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="cc8d0-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="cc8d0-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc8d0-191">See also</span></span>

- [<span data-ttu-id="cc8d0-192">成員</span><span class="sxs-lookup"><span data-stu-id="cc8d0-192">Members</span></span>](./members/index.md)
