---
title: "當做優先使用值的函式 (F#)"
description: "了解如何提高函式，才能在 F # 程式語言中的第一級狀態。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6b76b93b-a141-40f4-976c-7f0c558d6d09
ms.openlocfilehash: bca0e09edbe0aa86f0db746282acd4f4b3237a03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="functions-as-first-class-values"></a><span data-ttu-id="df6d6-104">當做優先使用值的函式</span><span class="sxs-lookup"><span data-stu-id="df6d6-104">Functions as First-Class Values</span></span>

<span data-ttu-id="df6d6-105">功能性程式設計語言的定義特性在於函式第一級的狀態來提高的權限。</span><span class="sxs-lookup"><span data-stu-id="df6d6-105">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="df6d6-106">您應該能夠處理函式，無論您可以與其他內建類型值，並能夠這樣做比較投入時間的程度。</span><span class="sxs-lookup"><span data-stu-id="df6d6-106">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="df6d6-107">一般量值的第一級的狀態包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="df6d6-107">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="df6d6-108">您是否可以識別項繫結函式？</span><span class="sxs-lookup"><span data-stu-id="df6d6-108">Can you bind functions to identifiers?</span></span> <span data-ttu-id="df6d6-109">也就是可以您讓它們名稱嗎？</span><span class="sxs-lookup"><span data-stu-id="df6d6-109">That is, can you give them names?</span></span>

- <span data-ttu-id="df6d6-110">您可以儲存函式中的資料結構，例如清單中？</span><span class="sxs-lookup"><span data-stu-id="df6d6-110">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="df6d6-111">您可以做為引數函式呼叫中傳遞函式？</span><span class="sxs-lookup"><span data-stu-id="df6d6-111">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="df6d6-112">您可以從函式呼叫傳回函式？</span><span class="sxs-lookup"><span data-stu-id="df6d6-112">Can you return a function from a function call?</span></span>

<span data-ttu-id="df6d6-113">最後兩個量值定義所謂*高階 operations*或*較高順序函式*。</span><span class="sxs-lookup"><span data-stu-id="df6d6-113">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="df6d6-114">較高順序函式會接受做為引數的函式，並傳回做為值的函式呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="df6d6-114">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="df6d6-115">這些作業支援功能性程式設計，做為對應函式和函式的複合這類細節。</span><span class="sxs-lookup"><span data-stu-id="df6d6-115">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>


## <a name="give-the-value-a-name"></a><span data-ttu-id="df6d6-116">指定值的名稱</span><span class="sxs-lookup"><span data-stu-id="df6d6-116">Give the Value a Name</span></span>

<span data-ttu-id="df6d6-117">如果函式的第一級的值，您必須能夠加以命名，就如同您可以將整數、 字串和其他內建型別名稱。</span><span class="sxs-lookup"><span data-stu-id="df6d6-117">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="df6d6-118">這被指做為識別項繫結值的功能性程式設計文獻中。</span><span class="sxs-lookup"><span data-stu-id="df6d6-118">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="df6d6-119">F # 使用[`let`繫結](../language-reference/functions/let-bindings.md)繫結至值的名稱： `let <identifier> = <value>`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-119">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="df6d6-120">下列程式碼顯示兩個範例。</span><span class="sxs-lookup"><span data-stu-id="df6d6-120">The following code shows two examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="df6d6-121">您可以命名輕易地函式。</span><span class="sxs-lookup"><span data-stu-id="df6d6-121">You can name a function just as easily.</span></span> <span data-ttu-id="df6d6-122">下列範例會定義名為函式`squareIt`繫結的識別項`squareIt`至[lambda 運算式](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-122">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="df6d6-123">函式`squareIt`具有一個參數， `n`，它會傳回該參數的平方和。</span><span class="sxs-lookup"><span data-stu-id="df6d6-123">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="df6d6-124">F # 提供下列更簡潔的語法，來達到相同的結果與輸入較少。</span><span class="sxs-lookup"><span data-stu-id="df6d6-124">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="df6d6-125">請依照下列大部分的範例會使用第一個樣式， `let <function-name> = <lambda-expression>`，以強調函式的宣告和其他類型的值的宣告之間的相似性。</span><span class="sxs-lookup"><span data-stu-id="df6d6-125">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="df6d6-126">不過，所有具名函式也可以寫入使用簡潔的語法。</span><span class="sxs-lookup"><span data-stu-id="df6d6-126">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="df6d6-127">部分範例是以兩種方式撰寫。</span><span class="sxs-lookup"><span data-stu-id="df6d6-127">Some of the examples are written in both ways.</span></span>


## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="df6d6-128">將值儲存在資料結構</span><span class="sxs-lookup"><span data-stu-id="df6d6-128">Store the Value in a Data Structure</span></span>

<span data-ttu-id="df6d6-129">第一級的值可以儲存在資料結構。</span><span class="sxs-lookup"><span data-stu-id="df6d6-129">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="df6d6-130">下列程式碼會顯示於清單和 tuple 中儲存值的範例。</span><span class="sxs-lookup"><span data-stu-id="df6d6-130">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="df6d6-131">若要確認，儲存在 tuple 中的函式名稱事實上確實會評估函式，下列範例會使用`fst`和`snd`運算子的第一個和第二個項目擷取 tuple `funAndArgTuple`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-131">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="df6d6-132">Tuple 中的第一個元素是`squareIt`而第二個項目是`num`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-132">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="df6d6-133">識別項`num`整數 10，有效的引數，如前一個範例中會繫結`squareIt`函式。</span><span class="sxs-lookup"><span data-stu-id="df6d6-133">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="df6d6-134">第二個運算式套用至 tuple 中第二個元素的 tuple 中的第一個項目： `squareIt num`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-134">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="df6d6-135">同樣地，只是做為識別碼`num`而且可以是整數 10 交替使用，因此可以識別項`squareIt`和 lambda 運算式`fun n -> n * n`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-135">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="df6d6-136">將值傳遞做為引數</span><span class="sxs-lookup"><span data-stu-id="df6d6-136">Pass the Value as an Argument</span></span>

<span data-ttu-id="df6d6-137">如果某個值有一種語言中的第一級的狀態，您可以做為引數傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="df6d6-137">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="df6d6-138">例如，常會傳遞整數和字串當做引數。</span><span class="sxs-lookup"><span data-stu-id="df6d6-138">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="df6d6-139">下列程式碼顯示整數和字串做為 F # 中的引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="df6d6-139">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="df6d6-140">如果函式的第一級的狀態，您必須是能夠將其做為引數傳遞方式相同。</span><span class="sxs-lookup"><span data-stu-id="df6d6-140">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="df6d6-141">請記住，這是較高順序函式的第一個特性。</span><span class="sxs-lookup"><span data-stu-id="df6d6-141">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="df6d6-142">在下列範例中，函式`applyIt`有兩個參數，`op`和`arg`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-142">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="df6d6-143">如果您傳送的其中一個參數的函式中`op`和適當的引數的函式的`arg`，此函數會傳回套用的結果`op`至`arg`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-143">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="df6d6-144">在下列範例中，函式引數和此整數引數會傳送相同的方式，使用它們的名稱。</span><span class="sxs-lookup"><span data-stu-id="df6d6-144">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="df6d6-145">能夠將函式做為引數傳送至另一個函式做為功能性程式設計語言的詳細資訊，例如對應或篩選作業中的通用抽象概念。</span><span class="sxs-lookup"><span data-stu-id="df6d6-145">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="df6d6-146">對應 」 作業，例如，是較高順序函式可擷取共用逐步執行清單，執行某個動作，每個項目，然後傳回結果的清單的函式所計算。</span><span class="sxs-lookup"><span data-stu-id="df6d6-146">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="df6d6-147">您可能想遞增每個項目清單中的整數，或方形每個項目，或將改成大寫的字串清單中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="df6d6-147">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="df6d6-148">計算的容易發生錯誤的部分是遞迴程序，透過的清單，該步驟，並建置要傳回的結果的清單。</span><span class="sxs-lookup"><span data-stu-id="df6d6-148">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="df6d6-149">對應函式中擷取的組件。</span><span class="sxs-lookup"><span data-stu-id="df6d6-149">That part is captured in the mapping function.</span></span> <span data-ttu-id="df6d6-150">您只需要撰寫特定的應用程式是您想要個別套用至每個清單項目函式 （加入、 number、 變更大小寫）。</span><span class="sxs-lookup"><span data-stu-id="df6d6-150">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="df6d6-151">函式會傳送做為引數以對應的函式，就如同`squareIt`傳送至`applyIt`前一個範例中。</span><span class="sxs-lookup"><span data-stu-id="df6d6-151">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="df6d6-152">F # 提供的對應方法大部分的集合型別，包括[列出](../language-reference/lists.md)，[陣列](../language-reference/arrays.md)，和[序列](../language-reference/sequences.md)。</span><span class="sxs-lookup"><span data-stu-id="df6d6-152">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="df6d6-153">下列範例會使用清單。</span><span class="sxs-lookup"><span data-stu-id="df6d6-153">The following examples use lists.</span></span> <span data-ttu-id="df6d6-154">語法是`List.map <the function> <the list>`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-154">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="df6d6-155">如需詳細資訊，請參閱[列出](../language-reference/lists.md)。</span><span class="sxs-lookup"><span data-stu-id="df6d6-155">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="df6d6-156">從函式呼叫傳回值</span><span class="sxs-lookup"><span data-stu-id="df6d6-156">Return the Value from a Function Call</span></span>

<span data-ttu-id="df6d6-157">最後，如果函式具有第一級的狀態，在語言中，您必須是能夠將其傳回做為值的函式呼叫，就如同您傳回其他型別，包括像是整數和字串。</span><span class="sxs-lookup"><span data-stu-id="df6d6-157">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="df6d6-158">下列函式呼叫會傳回整數，並加以顯示。</span><span class="sxs-lookup"><span data-stu-id="df6d6-158">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="df6d6-159">下列函式呼叫傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="df6d6-159">The following function call returns a string.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="df6d6-160">下列函式呼叫，宣告為內嵌，會傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="df6d6-160">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="df6d6-161">顯示的值是`True`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-161">The value displayed is `True`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="df6d6-162">傳回做為值的函式呼叫的函式的能力是第二個特性的較高順序函式。</span><span class="sxs-lookup"><span data-stu-id="df6d6-162">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="df6d6-163">在下列範例中，`checkFor`定義為接受一個引數的函式`item`，並傳回新的函式做為其值。</span><span class="sxs-lookup"><span data-stu-id="df6d6-163">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="df6d6-164">傳回的函式接受清單做為其引數， `lst`，並搜尋`item`中`lst`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-164">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="df6d6-165">如果`item`已存在，則函數會傳回`true`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-165">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="df6d6-166">如果`item`不存在，則函數會傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-166">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="df6d6-167">下列程式碼會提供的清單的函式，使用如前一節所示[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)，若要在清單中搜尋。</span><span class="sxs-lookup"><span data-stu-id="df6d6-167">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="df6d6-168">下列程式碼會使用`checkFor`來建立新的函式採用一個引數清單，以及搜尋 7 清單中。</span><span class="sxs-lookup"><span data-stu-id="df6d6-168">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="df6d6-169">下列範例使用在 F # 第一級函式的狀態，宣告函式， `compose`，傳回兩個函式引數的組合。</span><span class="sxs-lookup"><span data-stu-id="df6d6-169">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
<span data-ttu-id="df6d6-170">即使較短的版本，請參閱下一節 < Curried 函數 >。</span><span class="sxs-lookup"><span data-stu-id="df6d6-170">For an even shorter version, see the following section, "Curried Functions."</span></span>


<span data-ttu-id="df6d6-171">下列程式碼會傳送兩個函式做為引數`compose`，這兩個的其中採用相同類型的單一引數。</span><span class="sxs-lookup"><span data-stu-id="df6d6-171">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="df6d6-172">傳回值是新的函式所組成的兩個函式引數。</span><span class="sxs-lookup"><span data-stu-id="df6d6-172">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
<span data-ttu-id="df6d6-173">F # 提供兩個運算子，`<<`和`>>`，撰寫函式。</span><span class="sxs-lookup"><span data-stu-id="df6d6-173">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="df6d6-174">例如，`let squareAndDouble2 = doubleIt << squareIt`相當於`let squareAndDouble = compose doubleIt squareIt`前一個範例中。</span><span class="sxs-lookup"><span data-stu-id="df6d6-174">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="df6d6-175">下列範例會傳回做為值的函式呼叫的函式會建立簡單的猜測遊戲。</span><span class="sxs-lookup"><span data-stu-id="df6d6-175">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="df6d6-176">若要建立的遊戲，請呼叫`makeGame`值想要其他人猜出針對傳入`target`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-176">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="df6d6-177">函式的傳回值`makeGame`是採用一個引數 （猜測），並報告猜測是否正確的函數。</span><span class="sxs-lookup"><span data-stu-id="df6d6-177">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="df6d6-178">下列程式碼會呼叫`makeGame`，傳送值`7`如`target`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-178">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="df6d6-179">識別項`playGame`繫結至傳回的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="df6d6-179">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="df6d6-180">因此，`playGame`是採用一個引數為值的函式`guess`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-180">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a><span data-ttu-id="df6d6-181">局部調用函式</span><span class="sxs-lookup"><span data-stu-id="df6d6-181">Curried Functions</span></span>

<span data-ttu-id="df6d6-182">許多上一節中的範例藉由運用隱含可以更精確地撰寫*對*F # 函式宣告中。</span><span class="sxs-lookup"><span data-stu-id="df6d6-182">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="df6d6-183">對是轉換成一系列的內嵌函式，每一個都有一個單一參數的多個參數的函式的程序。</span><span class="sxs-lookup"><span data-stu-id="df6d6-183">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="df6d6-184">在 F # 中，原本就調用函式具有一個以上的參數。</span><span class="sxs-lookup"><span data-stu-id="df6d6-184">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="df6d6-185">例如，`compose`前一節可以撰寫下列精簡樣式，有三個參數中所示。</span><span class="sxs-lookup"><span data-stu-id="df6d6-185">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="df6d6-186">不過，結果會傳回一個參數，依序傳回一個參數，另一個函式的函式中所示的一個參數的函式`compose4curried`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-186">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="df6d6-187">您可以存取此函式數種方式。</span><span class="sxs-lookup"><span data-stu-id="df6d6-187">You can access this function in several ways.</span></span> <span data-ttu-id="df6d6-188">每一個下列範例會傳回並顯示 18。</span><span class="sxs-lookup"><span data-stu-id="df6d6-188">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="df6d6-189">您可以取代`compose4`與`compose4curried`中任何的範例。</span><span class="sxs-lookup"><span data-stu-id="df6d6-189">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="df6d6-190">若要確認，函式仍能運作與以前一樣，原始的測試案例再試一次。</span><span class="sxs-lookup"><span data-stu-id="df6d6-190">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
<span data-ttu-id="df6d6-191">您可以限制對住 tuple 的參數。</span><span class="sxs-lookup"><span data-stu-id="df6d6-191">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="df6d6-192">如需詳細資訊，請參閱 < 參數模式 」 中[參數和引數](../language-reference/parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="df6d6-192">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="df6d6-193">下列範例會使用隱含對要寫入的較短`makeGame`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-193">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="df6d6-194">詳細資料請參閱`makeGame`建構及傳回`game`函式是較不明確的格式，但您可以使用原始的測試案例結果是相同檢查。</span><span class="sxs-lookup"><span data-stu-id="df6d6-194">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="df6d6-195">對的詳細資訊，請參閱 「 部分應用程式的引數 」，在[函式](../language-reference/functions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="df6d6-195">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>


## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="df6d6-196">是可互換的識別項和函式定義</span><span class="sxs-lookup"><span data-stu-id="df6d6-196">Identifier and Function Definition Are Interchangeable</span></span>
<span data-ttu-id="df6d6-197">變數的名稱`num`中上一個範例會評估為整數 10，而且不會對該位置`num`是有效，10 也是有效的。</span><span class="sxs-lookup"><span data-stu-id="df6d6-197">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="df6d6-198">函式識別項和其值也是一樣： 隨處可用的函式名稱，它繫結的 lambda 運算式可以使用。</span><span class="sxs-lookup"><span data-stu-id="df6d6-198">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="df6d6-199">下列範例會定義`Boolean`函式，呼叫`isNegative`，然後使用函式的名稱和函式定義交換使用。</span><span class="sxs-lookup"><span data-stu-id="df6d6-199">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="df6d6-200">接下來三個範例全部都會傳回並顯示`False`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-200">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="df6d6-201">若要提升其進一步，以取代值的`applyIt`就繫結至`applyIt`。</span><span class="sxs-lookup"><span data-stu-id="df6d6-201">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="df6d6-202">函式是在 F # 第一級值</span><span class="sxs-lookup"><span data-stu-id="df6d6-202">Functions Are First-Class Values in F#</span></span> #

<span data-ttu-id="df6d6-203">上一節的範例將示範在 F # 中的函式符合在 F # 第一級值的準則：</span><span class="sxs-lookup"><span data-stu-id="df6d6-203">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="df6d6-204">您可以將識別項繫結至函式定義。</span><span class="sxs-lookup"><span data-stu-id="df6d6-204">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="df6d6-205">您可以在資料結構儲存函式。</span><span class="sxs-lookup"><span data-stu-id="df6d6-205">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="df6d6-206">您可以將函式傳遞做為引數。</span><span class="sxs-lookup"><span data-stu-id="df6d6-206">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="df6d6-207">您可以傳回函式做為函式呼叫的值。</span><span class="sxs-lookup"><span data-stu-id="df6d6-207">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="df6d6-208">如需 F # 的詳細資訊，請參閱[F # 語言參考](../language-reference/index.md)。</span><span class="sxs-lookup"><span data-stu-id="df6d6-208">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="df6d6-209">範例</span><span class="sxs-lookup"><span data-stu-id="df6d6-209">Example</span></span>

### <a name="description"></a><span data-ttu-id="df6d6-210">描述</span><span class="sxs-lookup"><span data-stu-id="df6d6-210">Description</span></span>

<span data-ttu-id="df6d6-211">下列程式碼包含本主題中的所有範例。</span><span class="sxs-lookup"><span data-stu-id="df6d6-211">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="df6d6-212">程式碼</span><span class="sxs-lookup"><span data-stu-id="df6d6-212">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a><span data-ttu-id="df6d6-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df6d6-213">See Also</span></span>

[<span data-ttu-id="df6d6-214">清單</span><span class="sxs-lookup"><span data-stu-id="df6d6-214">Lists</span></span>](../language-reference/lists.md)

[<span data-ttu-id="df6d6-215">元組</span><span class="sxs-lookup"><span data-stu-id="df6d6-215">Tuples</span></span>](../language-reference/tuples.md)

[<span data-ttu-id="df6d6-216">函式</span><span class="sxs-lookup"><span data-stu-id="df6d6-216">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="df6d6-217">`let`繫結</span><span class="sxs-lookup"><span data-stu-id="df6d6-217">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)

[<span data-ttu-id="df6d6-218">Lambda 運算式：`fun`關鍵字</span><span class="sxs-lookup"><span data-stu-id="df6d6-218">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
