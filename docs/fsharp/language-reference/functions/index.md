---
title: 函式 (F#)
description: '深入了解以 F # 和 F # 如何支援常見的函式程式設計建構函式。'
ms.date: 05/16/2016
ms.openlocfilehash: 717eba7e69398048d229173e07ccc376797171bb
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514447"
---
# <a name="functions"></a><span data-ttu-id="59774-103">函式</span><span class="sxs-lookup"><span data-stu-id="59774-103">Functions</span></span>

<span data-ttu-id="59774-104">函式是所有程式設計語言的基礎程式執行單位。</span><span class="sxs-lookup"><span data-stu-id="59774-104">Functions are the fundamental unit of program execution in any programming language.</span></span> <span data-ttu-id="59774-105">如同其他語言，F# 函式有名稱、可以有參數並且接受引數，而且也有主體。</span><span class="sxs-lookup"><span data-stu-id="59774-105">As in other languages, an F# function has a name, can have parameters and take arguments, and has a body.</span></span> <span data-ttu-id="59774-106">F# 也支援函式程式設計建構，例如將函式視為值、在運算式中使用不具名函式、組合函式以形成新函式、局部調用函式，以及透過部分套用函式引數的隱含定義函式。</span><span class="sxs-lookup"><span data-stu-id="59774-106">F# also supports functional programming constructs such as treating functions as values, using unnamed functions in expressions, composition of functions to form new functions, curried functions, and the implicit definition of functions by way of the partial application of function arguments.</span></span>

<span data-ttu-id="59774-107">您可以使用 `let` 關鍵字定義函式，若是遞迴函式，則可以使用 `let rec` 關鍵字組合來定義函式。</span><span class="sxs-lookup"><span data-stu-id="59774-107">You define functions by using the `let` keyword, or, if the function is recursive, the `let rec` keyword combination.</span></span>

## <a name="syntax"></a><span data-ttu-id="59774-108">語法</span><span class="sxs-lookup"><span data-stu-id="59774-108">Syntax</span></span>

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a><span data-ttu-id="59774-109">備註</span><span class="sxs-lookup"><span data-stu-id="59774-109">Remarks</span></span>

<span data-ttu-id="59774-110">*function-name* 表示函式的識別項。</span><span class="sxs-lookup"><span data-stu-id="59774-110">The *function-name* is an identifier that represents the function.</span></span> <span data-ttu-id="59774-111">*parameter-list* 由以空格分隔的連續參數所組成。</span><span class="sxs-lookup"><span data-stu-id="59774-111">The *parameter-list* consists of successive parameters that are separated by spaces.</span></span> <span data-ttu-id="59774-112">您可以指定每個參數的明確類型，如＜參數＞一節中所述。</span><span class="sxs-lookup"><span data-stu-id="59774-112">You can specify an explicit type for each parameter, as described in the Parameters section.</span></span> <span data-ttu-id="59774-113">若未指定特定的引數類型，編譯器會嘗試從函式主體推斷類型。</span><span class="sxs-lookup"><span data-stu-id="59774-113">If you do not specify a specific argument type, the compiler attempts to infer the type from the function body.</span></span> <span data-ttu-id="59774-114">*function-body* 由運算式組成。</span><span class="sxs-lookup"><span data-stu-id="59774-114">The *function-body* consists of an expression.</span></span> <span data-ttu-id="59774-115">函式主體通常是由組合運算式組成，其中包含數個會產生最終運算式作為傳回值的運算式。</span><span class="sxs-lookup"><span data-stu-id="59774-115">The expression that makes up the function body is typically a compound expression consisting of a number of expressions that culminate in a final expression that is the return value.</span></span> <span data-ttu-id="59774-116">*return-type* 是選擇性項目，包含後面接著類型的冒號。</span><span class="sxs-lookup"><span data-stu-id="59774-116">The *return-type* is a colon followed by a type and is optional.</span></span> <span data-ttu-id="59774-117">若您沒有明確指定傳回值的類型，則編譯器會從最終運算式判斷傳回型別。</span><span class="sxs-lookup"><span data-stu-id="59774-117">If you do not specify the type of the return value explicitly, the compiler determines the return type from the final expression.</span></span>

<span data-ttu-id="59774-118">簡單的函式定義如下所示：</span><span class="sxs-lookup"><span data-stu-id="59774-118">A simple function definition resembles the following:</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="59774-119">在上述範例中，函式名稱為 `f`，引數是類型為 `int` 的 `x`，函式主體為 `x + 1`，而傳回值的類型為 `int`。</span><span class="sxs-lookup"><span data-stu-id="59774-119">In the previous example, the function name is `f`, the argument is `x`, which has type `int`, the function body is `x + 1`, and the return value is of type `int`.</span></span>

<span data-ttu-id="59774-120">函式可以標記為 `inline`。</span><span class="sxs-lookup"><span data-stu-id="59774-120">Functions can be marked `inline`.</span></span> <span data-ttu-id="59774-121">如需 `inline` 的資訊，請參閱[內嵌函式](../functions/inline-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="59774-121">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

## <a name="scope"></a><span data-ttu-id="59774-122">範圍</span><span class="sxs-lookup"><span data-stu-id="59774-122">Scope</span></span>

<span data-ttu-id="59774-123">在模組範圍以外的任何範圍層級，重複使用值或函式名稱並非錯誤。</span><span class="sxs-lookup"><span data-stu-id="59774-123">At any level of scope other than module scope, it is not an error to reuse a value or function name.</span></span> <span data-ttu-id="59774-124">若重複使用名稱，後面宣告的名稱會遮蔽前面宣告的名稱。</span><span class="sxs-lookup"><span data-stu-id="59774-124">If you reuse a name, the name declared later shadows the name declared earlier.</span></span> <span data-ttu-id="59774-125">不過，在模組中的最上層範圍，名稱必須是唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="59774-125">However, at the top level scope in a module, names must be unique.</span></span> <span data-ttu-id="59774-126">例如，下列程式碼出現在模組範圍時會產生錯誤，但在函式內時則不會：</span><span class="sxs-lookup"><span data-stu-id="59774-126">For example, the following code produces an error when it appears at module scope, but not when it appears inside a function:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

<span data-ttu-id="59774-127">但是，下列程式碼在任何範圍層級都可以使用：</span><span class="sxs-lookup"><span data-stu-id="59774-127">But the following code is acceptable at any level of scope:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a><span data-ttu-id="59774-128">參數</span><span class="sxs-lookup"><span data-stu-id="59774-128">Parameters</span></span>

<span data-ttu-id="59774-129">參數名稱必須列於函式名稱後面。</span><span class="sxs-lookup"><span data-stu-id="59774-129">Names of parameters are listed after the function name.</span></span> <span data-ttu-id="59774-130">您可以指定參數的類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="59774-130">You can specify a type for a parameter, as shown in the following example:</span></span>

```fsharp
let f (x : int) = x + 1
```

<span data-ttu-id="59774-131">若您指定類型，請將它放在參數名稱之後，並且以冒號來分隔類型與名稱。</span><span class="sxs-lookup"><span data-stu-id="59774-131">If you specify a type, it follows the name of the parameter and is separated from the name by a colon.</span></span> <span data-ttu-id="59774-132">若您省略此參數的類型，編譯器便會推斷參數類型。</span><span class="sxs-lookup"><span data-stu-id="59774-132">If you omit the type for the parameter, the parameter type is inferred by the compiler.</span></span> <span data-ttu-id="59774-133">例如，在下列函式定義中，引數 `x` 經推斷為 `int` 類型，因為 1 是 `int` 類型 。</span><span class="sxs-lookup"><span data-stu-id="59774-133">For example, in the following function definition, the argument `x` is inferred to be of type `int` because 1 is of type `int`.</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="59774-134">不過，編譯器會嘗試將函式盡可能推斷成為泛型。</span><span class="sxs-lookup"><span data-stu-id="59774-134">However, the compiler will attempt to make the function as generic as possible.</span></span> <span data-ttu-id="59774-135">例如，請注意下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="59774-135">For example, note the following code:</span></span>

```fsharp
let f x = (x, x)
```

<span data-ttu-id="59774-136">函式會從任何類型的一個引數建立元組。</span><span class="sxs-lookup"><span data-stu-id="59774-136">The function creates a tuple from one argument of any type.</span></span> <span data-ttu-id="59774-137">因為沒有指定類型，所以函式可以與任何引數類型搭配使用。</span><span class="sxs-lookup"><span data-stu-id="59774-137">Because the type is not specified, the function can be used with any argument type.</span></span> <span data-ttu-id="59774-138">如需詳細資訊，請參閱[自動產生](../generics/automatic-generalization.md)。</span><span class="sxs-lookup"><span data-stu-id="59774-138">For more information, see [Automatic Generalization](../generics/automatic-generalization.md).</span></span>

## <a name="function-bodies"></a><span data-ttu-id="59774-139">函式主體</span><span class="sxs-lookup"><span data-stu-id="59774-139">Function Bodies</span></span>

<span data-ttu-id="59774-140">函式主體可以包含區域變數和函式的定義。</span><span class="sxs-lookup"><span data-stu-id="59774-140">A function body can contain definitions of local variables and functions.</span></span> <span data-ttu-id="59774-141">這類變數和函式是在目前函式主體的範圍內，而不是在主體以外。</span><span class="sxs-lookup"><span data-stu-id="59774-141">Such variables and functions are in scope in the body of the current function but not outside it.</span></span> <span data-ttu-id="59774-142">啟用輕量型語法選項時，必須使用縮排來表示定義是在函式主體中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="59774-142">When you have the lightweight syntax option enabled, you must use indentation to indicate that a definition is in a function body, as shown in the following example:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

<span data-ttu-id="59774-143">如需詳細資訊，請參閱[程式碼格式化方針](../code-formatting-guidelines.md)和[詳細語法](../verbose-syntax.md)。</span><span class="sxs-lookup"><span data-stu-id="59774-143">For more information, see [Code Formatting Guidelines](../code-formatting-guidelines.md) and [Verbose Syntax](../verbose-syntax.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="59774-144">傳回值</span><span class="sxs-lookup"><span data-stu-id="59774-144">Return Values</span></span>

<span data-ttu-id="59774-145">編譯器會使用函式主體中的最終運算式，來判斷傳回值和類型。</span><span class="sxs-lookup"><span data-stu-id="59774-145">The compiler uses the final expression in a function body to determine the return value and type.</span></span> <span data-ttu-id="59774-146">編譯器可能會從先前的運算式推斷最終運算式的類型。</span><span class="sxs-lookup"><span data-stu-id="59774-146">The compiler might infer the type of the final expression from previous expressions.</span></span> <span data-ttu-id="59774-147">在上節示範的 `cylinderVolume` 函式中，`pi` 的類型是從常值 `3.14159` 的類型經判斷為 `float`。</span><span class="sxs-lookup"><span data-stu-id="59774-147">In the function `cylinderVolume`, shown in the previous section, the type of `pi` is determined from the type of the literal `3.14159` to be `float`.</span></span> <span data-ttu-id="59774-148">編譯器會使用 `pi` 的類型，判斷運算式 `h * pi * r * r` 的類型為 `float`。</span><span class="sxs-lookup"><span data-stu-id="59774-148">The compiler uses the type of `pi` to determine the type of the expression `h * pi * r * r` to be `float`.</span></span> <span data-ttu-id="59774-149">因此，函式的整體傳回型別為 `float`。</span><span class="sxs-lookup"><span data-stu-id="59774-149">Therefore, the overall return type of the function is `float`.</span></span>

<span data-ttu-id="59774-150">若要明確指定傳回值，請撰寫如下的程式碼：</span><span class="sxs-lookup"><span data-stu-id="59774-150">To specify the return value explicitly, write the code as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

<span data-ttu-id="59774-151">撰寫如上所示的程式碼時，編譯器會將 **float** 套用至整個函式。若您也要將它套用至參數類型，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="59774-151">As the code is written above, the compiler applies **float** to the entire function; if you mean to apply it to the parameter types as well, use the following code:</span></span>

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a><span data-ttu-id="59774-152">呼叫函式</span><span class="sxs-lookup"><span data-stu-id="59774-152">Calling a Function</span></span>

<span data-ttu-id="59774-153">您可以指定函式名稱，後面接著空格，再接著以空格分隔的任何引數來呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="59774-153">You call functions by specifying the function name followed by a space and then any arguments separated by spaces.</span></span> <span data-ttu-id="59774-154">例如，若要呼叫函式 **cylinderVolume** 並將結果指派給值 **vol**，您可以撰寫下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="59774-154">For example, to call the function **cylinderVolume** and assign the result to the value **vol**, you write the following code:</span></span>

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a><span data-ttu-id="59774-155">部分套用引數</span><span class="sxs-lookup"><span data-stu-id="59774-155">Partial Application of Arguments</span></span>

<span data-ttu-id="59774-156">若您提供的引數數目比指定的數目更少，則必須建立需要其餘引數的新函式。</span><span class="sxs-lookup"><span data-stu-id="59774-156">If you supply fewer than the specified number of arguments, you create a new function that expects the remaining arguments.</span></span> <span data-ttu-id="59774-157">這個處理引數的方法稱為「局部調用」，是 F# 這類函式程式設計語言的特色。</span><span class="sxs-lookup"><span data-stu-id="59774-157">This method of handling arguments is referred to as *currying* and is a characteristic of functional programming languages like F#.</span></span> <span data-ttu-id="59774-158">例如，假設您要使用兩種大小的管子，其中一個半徑為 **2.0**，另一個半徑為 **3.0**。</span><span class="sxs-lookup"><span data-stu-id="59774-158">For example, suppose you are working with two sizes of pipe: one has a radius of **2.0** and the other has a radius of **3.0**.</span></span> <span data-ttu-id="59774-159">您可以建立會判斷管子容量的函式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="59774-159">You could create functions that determine the volume of pipe as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

<span data-ttu-id="59774-160">接著，視需要為兩個不同大小的各種管子長度提供其他引數：</span><span class="sxs-lookup"><span data-stu-id="59774-160">You would then supply the additional argument as needed for various lengths of pipe of the two different sizes:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a><span data-ttu-id="59774-161">遞迴函式</span><span class="sxs-lookup"><span data-stu-id="59774-161">Recursive Functions</span></span>

<span data-ttu-id="59774-162">「遞迴函式」是會自我呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="59774-162">*Recursive functions* are functions that call themselves.</span></span> <span data-ttu-id="59774-163">您必須在 **let** 關鍵字後面指定 **rec** 關鍵字來使用遞迴函式。</span><span class="sxs-lookup"><span data-stu-id="59774-163">They require that you specify the **rec** keyword following the **let** keyword.</span></span> <span data-ttu-id="59774-164">請從函式主體中叫用遞迴函式，就像叫用任何函式呼叫一樣。</span><span class="sxs-lookup"><span data-stu-id="59774-164">Invoke the recursive function from within the body of the function just as you would invoke any function call.</span></span> <span data-ttu-id="59774-165">下列遞迴函式會計算*n*<sup>th</sup> Fibonacci 數字。</span><span class="sxs-lookup"><span data-stu-id="59774-165">The following recursive function computes the *n*<sup>th</sup> Fibonacci number.</span></span> <span data-ttu-id="59774-166">Fibonacci 數字序列自古聞名，此序列中的每個連續數字都是前兩個數字的總和。</span><span class="sxs-lookup"><span data-stu-id="59774-166">The Fibonacci number sequence has been known since antiquity and is a sequence in which each successive number is the sum of the previous two numbers in the sequence.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

<span data-ttu-id="59774-167">若不謹慎撰寫遞迴函式，而且也不了解特殊技巧 (例如累計值和接續符號的用法)，某些遞迴函式便可能會使程式堆疊溢位，或導致執行時沒有效率。</span><span class="sxs-lookup"><span data-stu-id="59774-167">Some recursive functions might overflow the program stack or perform inefficiently if you do not write them with care and with awareness of special techniques, such as the use of accumulators and continuations.</span></span>

## <a name="function-values"></a><span data-ttu-id="59774-168">函式值</span><span class="sxs-lookup"><span data-stu-id="59774-168">Function Values</span></span>

<span data-ttu-id="59774-169">在 F# 中，所有函式都視為值，而實際上它們稱為「函式值」。</span><span class="sxs-lookup"><span data-stu-id="59774-169">In F#, all functions are considered values; in fact, they are known as *function values*.</span></span> <span data-ttu-id="59774-170">由於函式都是值，因此可以作為其他函式的引數，或在其他會用到這些值的內容中使用。</span><span class="sxs-lookup"><span data-stu-id="59774-170">Because functions are values, they can be used as arguments to other functions or in other contexts where values are used.</span></span> <span data-ttu-id="59774-171">以下是接受函式值作為引數的函式範例：</span><span class="sxs-lookup"><span data-stu-id="59774-171">Following is an example of a function that takes a function value as an argument:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

<span data-ttu-id="59774-172">您可以使用 `->` 語彙基元來指定函式值的類型。</span><span class="sxs-lookup"><span data-stu-id="59774-172">You specify the type of a function value by using the `->` token.</span></span> <span data-ttu-id="59774-173">在此語彙基元左邊是引數的類型，右邊則是傳回值。</span><span class="sxs-lookup"><span data-stu-id="59774-173">On the left side of this token is the type of the argument, and on the right side is the return value.</span></span> <span data-ttu-id="59774-174">在上述範例中，`apply1` 函式會接受 `transform` 函式作為引數，其中 `transform` 是接受整數並傳回另一個整數的函式。</span><span class="sxs-lookup"><span data-stu-id="59774-174">In the previous example, `apply1` is a function that takes a function `transform` as an argument, where `transform` is a function that takes an integer and returns another integer.</span></span> <span data-ttu-id="59774-175">在下列範例程式碼中，會示範 `apply1` 的用法：</span><span class="sxs-lookup"><span data-stu-id="59774-175">The following code shows how to use `apply1`:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

<span data-ttu-id="59774-176">在上述程式碼執行之後，`result` 的值會是 101。</span><span class="sxs-lookup"><span data-stu-id="59774-176">The value of `result` will be 101 after the previous code runs.</span></span>

<span data-ttu-id="59774-177">多個引數是以連續 `->` 語彙基元分隔，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="59774-177">Multiple arguments are separated by successive `->` tokens, as shown in the following example:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

<span data-ttu-id="59774-178">結果為 200。</span><span class="sxs-lookup"><span data-stu-id="59774-178">The result is 200.</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="59774-179">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="59774-179">Lambda Expressions</span></span>

<span data-ttu-id="59774-180">「Lambda 運算式」是不具名函式。</span><span class="sxs-lookup"><span data-stu-id="59774-180">A *lambda expression* is an unnamed function.</span></span> <span data-ttu-id="59774-181">在上述範例中，您可以使用 Lambda 運算式，而不定義具名函式 **increment** 和 **mul**，如下所示：</span><span class="sxs-lookup"><span data-stu-id="59774-181">In the previous examples, instead of defining named functions **increment** and **mul**, you could use lambda expressions as follows:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

<span data-ttu-id="59774-182">您可以透過 `fun` 關鍵字定義 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="59774-182">You define lambda expressions by using the `fun` keyword.</span></span> <span data-ttu-id="59774-183">Lambda 運算式類似函式定義，但是它使用 `->` 語彙基元來分隔引數清單與函式主體，而不是 `=` 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="59774-183">A lambda expression resembles a function definition, except that instead of the `=` token, the `->` token is used to separate the argument list from the function body.</span></span> <span data-ttu-id="59774-184">如同一般函式定義，您可以推斷或明確指定引數類型，而 Lambda 運算式的傳回型別是從主體中最後一個運算式的類型來推斷。</span><span class="sxs-lookup"><span data-stu-id="59774-184">As in a regular function definition, the argument types can be inferred or specified explicitly, and the return type of the lambda expression is inferred from the type of the last expression in the body.</span></span> <span data-ttu-id="59774-185">如需詳細資訊，請參閱 [Lambda 運算式：`fun` 關鍵字](../functions/lambda-expressions-the-fun-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="59774-185">For more information, see [Lambda Expressions: The `fun` Keyword](../functions/lambda-expressions-the-fun-keyword.md).</span></span>

## <a name="function-composition-and-pipelining"></a><span data-ttu-id="59774-186">函式組合和管線</span><span class="sxs-lookup"><span data-stu-id="59774-186">Function Composition and Pipelining</span></span>

<span data-ttu-id="59774-187">F# 中的函式可以從其他函式組合。</span><span class="sxs-lookup"><span data-stu-id="59774-187">Functions in F# can be composed from other functions.</span></span> <span data-ttu-id="59774-188">兩個函式 **function1** 和 **function2** 會組合成另一個函式，表示先套用 **function1**，接著套用 **function2**：</span><span class="sxs-lookup"><span data-stu-id="59774-188">The composition of two functions **function1** and **function2** is another function that represents the application of **function1** followed the application of **function2**:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

<span data-ttu-id="59774-189">結果為 202。</span><span class="sxs-lookup"><span data-stu-id="59774-189">The result is 202.</span></span>

<span data-ttu-id="59774-190">管線可讓函式呼叫鏈結在一起成為連續作業。</span><span class="sxs-lookup"><span data-stu-id="59774-190">Pipelining enables function calls to be chained together as successive operations.</span></span> <span data-ttu-id="59774-191">管線運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="59774-191">Pipelining works as follows:</span></span>

```fsharp
let result = 100 |> function1 |> function2
```

<span data-ttu-id="59774-192">結果同樣是 202。</span><span class="sxs-lookup"><span data-stu-id="59774-192">The result is again 202.</span></span>

<span data-ttu-id="59774-193">組合運算子會採用兩個函式，並傳回一個函式。相較之下，管線運算子則採用一個函式與一個引數，並傳回一個值。</span><span class="sxs-lookup"><span data-stu-id="59774-193">The composition operators take two functions and return a function; by contrast, the pipeline operators take a function and an argument and return a value.</span></span> <span data-ttu-id="59774-194">下列程式碼範例可透過示範函式簽章和使用方式的不同，顯示管線和組合運算子之間的差異。</span><span class="sxs-lookup"><span data-stu-id="59774-194">The following code example shows the difference between the pipeline and composition operators by showing the differences in the function signatures and usage.</span></span>

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a><span data-ttu-id="59774-195">多載函式</span><span class="sxs-lookup"><span data-stu-id="59774-195">Overloading Functions</span></span>

<span data-ttu-id="59774-196">您可以多載類型的方法，但不是函式的方法。</span><span class="sxs-lookup"><span data-stu-id="59774-196">You can overload methods of a type but not functions.</span></span> <span data-ttu-id="59774-197">如需詳細資訊，請參閱[方法](../members/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="59774-197">For more information, see [Methods](../members/methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59774-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59774-198">See also</span></span>

- [<span data-ttu-id="59774-199">值</span><span class="sxs-lookup"><span data-stu-id="59774-199">Values</span></span>](../values/index.md)
- [<span data-ttu-id="59774-200">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="59774-200">F# Language Reference</span></span>](../index.md)
