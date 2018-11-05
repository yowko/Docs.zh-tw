---
title: 第一級函式
description: 深入了解第一級函式以及它們的重要函式程式設計的方式F#。
ms.date: 10/29/2018
ms.openlocfilehash: 1459049c9c1c77f4eefd2a83945335b33ca22ab9
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "50744629"
---
# <a name="first-class-functions"></a><span data-ttu-id="81940-103">第一級函式</span><span class="sxs-lookup"><span data-stu-id="81940-103">First-class functions</span></span>

<span data-ttu-id="81940-104">功能性程式設計語言的一項定義特性是提高至頂級狀態的函式。</span><span class="sxs-lookup"><span data-stu-id="81940-104">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="81940-105">您應該能夠執行的函式，任何您可以與其他內建類型值，並能夠這樣做相當高的投入時間。</span><span class="sxs-lookup"><span data-stu-id="81940-105">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="81940-106">下面是一般的量值的第一等狀態：</span><span class="sxs-lookup"><span data-stu-id="81940-106">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="81940-107">您是否可以識別項繫結函式？</span><span class="sxs-lookup"><span data-stu-id="81940-107">Can you bind functions to identifiers?</span></span> <span data-ttu-id="81940-108">也就是你可以提供這些名稱？</span><span class="sxs-lookup"><span data-stu-id="81940-108">That is, can you give them names?</span></span>

- <span data-ttu-id="81940-109">您可以儲存函式中的資料結構，例如清單中？</span><span class="sxs-lookup"><span data-stu-id="81940-109">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="81940-110">您可以做為引數，函式呼叫中傳遞函式？</span><span class="sxs-lookup"><span data-stu-id="81940-110">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="81940-111">您可以從函式呼叫傳回的函式？</span><span class="sxs-lookup"><span data-stu-id="81940-111">Can you return a function from a function call?</span></span>

<span data-ttu-id="81940-112">最後兩個量值定義所謂*高階 operations*或*較高順序函式*。</span><span class="sxs-lookup"><span data-stu-id="81940-112">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="81940-113">較高順序函式會接受做為引數的函式，並傳回做為值的函式呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="81940-113">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="81940-114">這些作業都支援這類從函式程式設計，做為對應函式和函式的組合。</span><span class="sxs-lookup"><span data-stu-id="81940-114">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>

## <a name="give-the-value-a-name"></a><span data-ttu-id="81940-115">指定值的名稱</span><span class="sxs-lookup"><span data-stu-id="81940-115">Give the Value a Name</span></span>

<span data-ttu-id="81940-116">如果函式為第一級的值，您必須能夠加以命名，就如同您可以命名整數、 字串和其他內建類型。</span><span class="sxs-lookup"><span data-stu-id="81940-116">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="81940-117">這被指在功能性程式設計文獻中做為繫結至值的識別項。</span><span class="sxs-lookup"><span data-stu-id="81940-117">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="81940-118">F# 會使用[`let`繫結](../language-reference/functions/let-bindings.md)繫結到值的名稱： `let <identifier> = <value>`。</span><span class="sxs-lookup"><span data-stu-id="81940-118">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="81940-119">下列程式碼顯示兩個範例。</span><span class="sxs-lookup"><span data-stu-id="81940-119">The following code shows two examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="81940-120">您可以命名輕鬆地為函式。</span><span class="sxs-lookup"><span data-stu-id="81940-120">You can name a function just as easily.</span></span> <span data-ttu-id="81940-121">下列範例會定義名為函式`squareIt`繫結識別碼`squareIt`要[lambda 運算式](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`。</span><span class="sxs-lookup"><span data-stu-id="81940-121">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="81940-122">函式`squareIt`有一個參數， `n`，並傳回該參數的平方。</span><span class="sxs-lookup"><span data-stu-id="81940-122">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="81940-123">F# 提供下列更簡潔的語法，來達到相同的結果，少打一些字。</span><span class="sxs-lookup"><span data-stu-id="81940-123">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="81940-124">請依照下列大部分的範例會使用第一個樣式， `let <function-name> = <lambda-expression>`，以強調函式的宣告和其他類型之值的宣告之間的相似性。</span><span class="sxs-lookup"><span data-stu-id="81940-124">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="81940-125">不過，所有具名函式也可以撰寫使用簡潔的語法。</span><span class="sxs-lookup"><span data-stu-id="81940-125">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="81940-126">有些範例會以兩種方式。</span><span class="sxs-lookup"><span data-stu-id="81940-126">Some of the examples are written in both ways.</span></span>

## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="81940-127">將值儲存在資料結構</span><span class="sxs-lookup"><span data-stu-id="81940-127">Store the Value in a Data Structure</span></span>

<span data-ttu-id="81940-128">第一級的值可以儲存在資料結構。</span><span class="sxs-lookup"><span data-stu-id="81940-128">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="81940-129">下列程式碼顯示於清單和 tuple 中儲存值的範例。</span><span class="sxs-lookup"><span data-stu-id="81940-129">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="81940-130">若要確認函式名稱儲存在事實上確實會評估為函式，下列範例會使用`fst`並`snd`運算子來擷取 tuple 的第一個和第二個項目`funAndArgTuple`。</span><span class="sxs-lookup"><span data-stu-id="81940-130">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="81940-131">Tuple 中的第一個元素是`squareIt`，而第二個元素是`num`。</span><span class="sxs-lookup"><span data-stu-id="81940-131">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="81940-132">識別項`num`在上述範例中為整數 10 的有效引數繫結`squareIt`函式。</span><span class="sxs-lookup"><span data-stu-id="81940-132">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="81940-133">第二個運算式套用至 tuple 中第二個元素的 tuple 中的第一個項目： `squareIt num`。</span><span class="sxs-lookup"><span data-stu-id="81940-133">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="81940-134">同樣地，只是做為識別碼`num`而且可以是整數 10 交替使用，因此可以識別項`squareIt`lambda 運算式和`fun n -> n * n`。</span><span class="sxs-lookup"><span data-stu-id="81940-134">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="81940-135">將值傳遞做為引數</span><span class="sxs-lookup"><span data-stu-id="81940-135">Pass the Value as an Argument</span></span>

<span data-ttu-id="81940-136">如果某個值有一種語言中的第一等狀態，您可以做為引數傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="81940-136">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="81940-137">比方說，常會傳遞做為引數的整數和字串。</span><span class="sxs-lookup"><span data-stu-id="81940-137">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="81940-138">下列程式碼顯示整數和 F# 中的引數傳遞的字串。</span><span class="sxs-lookup"><span data-stu-id="81940-138">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="81940-139">如果函式的第一等狀態，您必須能夠將它們傳遞為引數中，相同的方式。</span><span class="sxs-lookup"><span data-stu-id="81940-139">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="81940-140">請記住，這是較高順序函式的第一個特性。</span><span class="sxs-lookup"><span data-stu-id="81940-140">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="81940-141">在下列範例中，函式`applyIt`有兩個參數，`op`和`arg`。</span><span class="sxs-lookup"><span data-stu-id="81940-141">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="81940-142">如果您傳送具有一個參數的函式中`op`和適當的引數的函式`arg`，此函數會傳回套用的結果`op`至`arg`。</span><span class="sxs-lookup"><span data-stu-id="81940-142">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="81940-143">在下列範例中，函式引數和整數引數會傳送相同的方式，使用其名稱。</span><span class="sxs-lookup"><span data-stu-id="81940-143">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="81940-144">能夠將函式做為引數傳送至另一個函式是功能性程式設計語言的詳細資訊，例如對應或篩選作業中的通用抽象概念的基礎。</span><span class="sxs-lookup"><span data-stu-id="81940-144">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="81940-145">對應作業，比方說，是較高順序函式可擷取共用的逐步執行清單，執行某個動作，每個項目，然後傳回結果的清單的函式的計算。</span><span class="sxs-lookup"><span data-stu-id="81940-145">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="81940-146">您可能想要遞增的整數，清單中的每個項目或正方形每個項目，或變更為大寫的字串清單中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="81940-146">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="81940-147">計算出錯部分是遞迴程序的逐步說明的清單，並建置一份要傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="81940-147">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="81940-148">對應函式中擷取該部分。</span><span class="sxs-lookup"><span data-stu-id="81940-148">That part is captured in the mapping function.</span></span> <span data-ttu-id="81940-149">您只需要撰寫特定的應用程式是您想要個別套用至每個清單項目函式 （新增、 number、 變更大小寫）。</span><span class="sxs-lookup"><span data-stu-id="81940-149">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="81940-150">函式會傳送做為引數以對應的函式，就如同`squareIt`傳送至`applyIt`在上述範例中。</span><span class="sxs-lookup"><span data-stu-id="81940-150">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="81940-151">F# 提供對應方法的大部分集合型別，包括[列出](../language-reference/lists.md)，[陣列](../language-reference/arrays.md)，並[序列](../language-reference/sequences.md)。</span><span class="sxs-lookup"><span data-stu-id="81940-151">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="81940-152">下列範例會使用清單。</span><span class="sxs-lookup"><span data-stu-id="81940-152">The following examples use lists.</span></span> <span data-ttu-id="81940-153">語法是`List.map <the function> <the list>`。</span><span class="sxs-lookup"><span data-stu-id="81940-153">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="81940-154">如需詳細資訊，請參閱 <<c0> [ 列出](../language-reference/lists.md)。</span><span class="sxs-lookup"><span data-stu-id="81940-154">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="81940-155">從函式呼叫中傳回值</span><span class="sxs-lookup"><span data-stu-id="81940-155">Return the Value from a Function Call</span></span>

<span data-ttu-id="81940-156">最後，如果函式語言中第一等狀態，您必須是能夠傳回做為值的函式呼叫，就像您傳回其他類型，例如整數和字串。</span><span class="sxs-lookup"><span data-stu-id="81940-156">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="81940-157">下列函式呼叫會傳回整數，並加以顯示。</span><span class="sxs-lookup"><span data-stu-id="81940-157">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="81940-158">下列函式呼叫傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="81940-158">The following function call returns a string.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="81940-159">下列函式呼叫，宣告內嵌及傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="81940-159">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="81940-160">顯示的值是`True`。</span><span class="sxs-lookup"><span data-stu-id="81940-160">The value displayed is `True`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="81940-161">傳回做為值的函式呼叫的函式的功能是較高順序函式的第二個特性。</span><span class="sxs-lookup"><span data-stu-id="81940-161">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="81940-162">在下列範例中，`checkFor`定義為接受一個引數的函式`item`，並傳回新的函式，做為其值。</span><span class="sxs-lookup"><span data-stu-id="81940-162">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="81940-163">傳回的函式接受清單作為其引數， `lst`，並搜尋`item`在`lst`。</span><span class="sxs-lookup"><span data-stu-id="81940-163">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="81940-164">如果`item`已存在，則函數會傳回`true`。</span><span class="sxs-lookup"><span data-stu-id="81940-164">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="81940-165">如果`item`不存在，則函數會傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="81940-165">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="81940-166">上一節中，下列程式碼會使用提供的清單函式[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)，以搜尋清單。</span><span class="sxs-lookup"><span data-stu-id="81940-166">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="81940-167">下列程式碼會使用`checkFor`來建立新的函式採用一個引數，清單中，並搜尋 7 在清單中。</span><span class="sxs-lookup"><span data-stu-id="81940-167">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="81940-168">下列範例使用在 F# 第一級函式的狀態，宣告函式， `compose`，傳回兩個函式引數的組合。</span><span class="sxs-lookup"><span data-stu-id="81940-168">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]

>[!NOTE]
<span data-ttu-id="81940-169">即使較短的版本，請參閱下列區段中，「 Curried 函式。 」</span><span class="sxs-lookup"><span data-stu-id="81940-169">For an even shorter version, see the following section, "Curried Functions."</span></span>

<span data-ttu-id="81940-170">下列程式碼會傳送兩個函式做為引數`compose`，這兩個的其中採用相同型別的單一引數。</span><span class="sxs-lookup"><span data-stu-id="81940-170">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="81940-171">傳回的值是新的函式所組成的兩個函式引數。</span><span class="sxs-lookup"><span data-stu-id="81940-171">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]

>[!NOTE]
<span data-ttu-id="81940-172">F# 提供兩個運算子`<<`和`>>`，撰寫函式。</span><span class="sxs-lookup"><span data-stu-id="81940-172">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="81940-173">例如，`let squareAndDouble2 = doubleIt << squareIt`相當於`let squareAndDouble = compose doubleIt squareIt`在上述範例中。</span><span class="sxs-lookup"><span data-stu-id="81940-173">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="81940-174">傳回做為值的函式呼叫的函式的下列範例會建立簡單的猜測遊戲。</span><span class="sxs-lookup"><span data-stu-id="81940-174">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="81940-175">若要建立的遊戲，呼叫`makeGame`值與想要其他人猜出傳入`target`。</span><span class="sxs-lookup"><span data-stu-id="81940-175">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="81940-176">函式的傳回值`makeGame`是採用一個引數 （猜測），並報告猜測是否正確的函式。</span><span class="sxs-lookup"><span data-stu-id="81940-176">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="81940-177">下列程式碼會呼叫`makeGame`，值傳送`7`如`target`。</span><span class="sxs-lookup"><span data-stu-id="81940-177">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="81940-178">識別項`playGame`繫結至傳回的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="81940-178">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="81940-179">因此，`playGame`是採用一個引數為值的函式`guess`。</span><span class="sxs-lookup"><span data-stu-id="81940-179">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a><span data-ttu-id="81940-180">局部調用函式</span><span class="sxs-lookup"><span data-stu-id="81940-180">Curried Functions</span></span>

<span data-ttu-id="81940-181">許多在上一節中的範例藉由運用隱含可以更精確撰寫*調用*F# 函式宣告中。</span><span class="sxs-lookup"><span data-stu-id="81940-181">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="81940-182">調用是轉換成一系列的內嵌函式，其中每一個具有單一參數的多個參數的函式的程序。</span><span class="sxs-lookup"><span data-stu-id="81940-182">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="81940-183">在 F# 中，有多個參數的函式原本就是局部調用。</span><span class="sxs-lookup"><span data-stu-id="81940-183">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="81940-184">比方說，`compose`上一節可以撰寫下列簡潔樣式，使用三個參數中所示。</span><span class="sxs-lookup"><span data-stu-id="81940-184">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="81940-185">不過，結果會傳回一個參數，依序傳回的一個參數，另一個函式的函式中所示的一個參數的函式`compose4curried`。</span><span class="sxs-lookup"><span data-stu-id="81940-185">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="81940-186">您可以存取數種方式中的此函式。</span><span class="sxs-lookup"><span data-stu-id="81940-186">You can access this function in several ways.</span></span> <span data-ttu-id="81940-187">每個下列範例會傳回，並顯示 18。</span><span class="sxs-lookup"><span data-stu-id="81940-187">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="81940-188">您可以取代`compose4`與`compose4curried`任何範例。</span><span class="sxs-lookup"><span data-stu-id="81940-188">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="81940-189">若要確認函式仍可如以前一樣，再試一次原始的測試案例。</span><span class="sxs-lookup"><span data-stu-id="81940-189">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]

>[!NOTE]
<span data-ttu-id="81940-190">您可以限制對住 tuple 中的參數。</span><span class="sxs-lookup"><span data-stu-id="81940-190">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="81940-191">如需詳細資訊，請參閱 < 參數模式 」 中[參數和引數](../language-reference/parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="81940-191">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="81940-192">下列範例會使用隱含調用撰寫的較短`makeGame`。</span><span class="sxs-lookup"><span data-stu-id="81940-192">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="81940-193">詳細方式`makeGame`建構並傳回`game`函式是較不明確的格式如下，但您可以確認使用原始的測試案例的結果都會相同。</span><span class="sxs-lookup"><span data-stu-id="81940-193">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="81940-194">更多對的詳細資訊，請參閱 「 部分應用程式的引數 」，在[函式](../language-reference/functions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="81940-194">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>

## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="81940-195">是可互換的識別項和函式定義</span><span class="sxs-lookup"><span data-stu-id="81940-195">Identifier and Function Definition Are Interchangeable</span></span>

<span data-ttu-id="81940-196">變數的名稱`num`在上一個範例會評估為 10 的整數，而且毫無意外地，其中`num`是有效的 10 也是有效。</span><span class="sxs-lookup"><span data-stu-id="81940-196">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="81940-197">函式識別項和其值也是一樣： 隨處可用的函式名稱，它繫結的 lambda 運算式可以使用。</span><span class="sxs-lookup"><span data-stu-id="81940-197">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="81940-198">下列範例會定義`Boolean`函式，呼叫`isNegative`，然後交替使用 函式的名稱和函式的定義。</span><span class="sxs-lookup"><span data-stu-id="81940-198">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="81940-199">接下來的三個範例都會傳回並顯示`False`。</span><span class="sxs-lookup"><span data-stu-id="81940-199">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="81940-200">若要它進一步採取步驟，以取代值，`applyIt`繫結至如`applyIt`。</span><span class="sxs-lookup"><span data-stu-id="81940-200">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="81940-201">函式是 F# 第一級值\#</span><span class="sxs-lookup"><span data-stu-id="81940-201">Functions Are First-Class Values in F\#</span></span>

<span data-ttu-id="81940-202">在先前章節中的範例將示範 F# 函式滿足的準則中 F# 第一級值：</span><span class="sxs-lookup"><span data-stu-id="81940-202">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="81940-203">您可以將識別項繫結至函式定義。</span><span class="sxs-lookup"><span data-stu-id="81940-203">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="81940-204">您可以在資料結構儲存函式。</span><span class="sxs-lookup"><span data-stu-id="81940-204">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="81940-205">您可以傳遞函式做為引數。</span><span class="sxs-lookup"><span data-stu-id="81940-205">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="81940-206">您可以傳回函式的函式呼叫的值。</span><span class="sxs-lookup"><span data-stu-id="81940-206">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="81940-207">如需 F# 的詳細資訊，請參閱[F# 語言參考](../language-reference/index.md)。</span><span class="sxs-lookup"><span data-stu-id="81940-207">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="81940-208">範例</span><span class="sxs-lookup"><span data-stu-id="81940-208">Example</span></span>

### <a name="description"></a><span data-ttu-id="81940-209">描述</span><span class="sxs-lookup"><span data-stu-id="81940-209">Description</span></span>

<span data-ttu-id="81940-210">下列程式碼包含本主題中的所有範例。</span><span class="sxs-lookup"><span data-stu-id="81940-210">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="81940-211">程式碼</span><span class="sxs-lookup"><span data-stu-id="81940-211">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a><span data-ttu-id="81940-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81940-212">See also</span></span>

- [<span data-ttu-id="81940-213">清單</span><span class="sxs-lookup"><span data-stu-id="81940-213">Lists</span></span>](../language-reference/lists.md)
- [<span data-ttu-id="81940-214">元組</span><span class="sxs-lookup"><span data-stu-id="81940-214">Tuples</span></span>](../language-reference/tuples.md)
- [<span data-ttu-id="81940-215">函式</span><span class="sxs-lookup"><span data-stu-id="81940-215">Functions</span></span>](../language-reference/functions/index.md)
- [<span data-ttu-id="81940-216">`let` 繫結</span><span class="sxs-lookup"><span data-stu-id="81940-216">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)
- [<span data-ttu-id="81940-217">Lambda 運算式：`fun`關鍵字</span><span class="sxs-lookup"><span data-stu-id="81940-217">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
