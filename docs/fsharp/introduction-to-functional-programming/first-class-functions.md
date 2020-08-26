---
title: 一級函式
description: '瞭解第一級函式，以及它們對於 F # 中的函式程式設計有何重要性。'
ms.date: 10/29/2018
ms.openlocfilehash: 1dc8eae1655187282f05bf4e9501ecc8a17deba8
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810907"
---
# <a name="first-class-functions"></a><span data-ttu-id="00709-103">一級函式</span><span class="sxs-lookup"><span data-stu-id="00709-103">First-class functions</span></span>

<span data-ttu-id="00709-104">函式程式設計語言的定義特性是將函式提升為第一級狀態的功能。</span><span class="sxs-lookup"><span data-stu-id="00709-104">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="00709-105">您應該能夠使用函式來處理其他內建類型的值，而且能夠以相當程度的投入量來進行。</span><span class="sxs-lookup"><span data-stu-id="00709-105">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="00709-106">第一個類別狀態的典型量值包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="00709-106">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="00709-107">您可以將函式系結至識別碼嗎？</span><span class="sxs-lookup"><span data-stu-id="00709-107">Can you bind functions to identifiers?</span></span> <span data-ttu-id="00709-108">也就是說，您可以為它們命名嗎？</span><span class="sxs-lookup"><span data-stu-id="00709-108">That is, can you give them names?</span></span>

- <span data-ttu-id="00709-109">您可以將函數儲存在資料結構中，例如清單中？</span><span class="sxs-lookup"><span data-stu-id="00709-109">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="00709-110">您可以在函式呼叫中傳遞函式作為引數嗎？</span><span class="sxs-lookup"><span data-stu-id="00709-110">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="00709-111">您可以從函式呼叫傳回函數嗎？</span><span class="sxs-lookup"><span data-stu-id="00709-111">Can you return a function from a function call?</span></span>

<span data-ttu-id="00709-112">最後兩個量值會定義所謂的 *高階作業* 或 *更高順序*的函式。</span><span class="sxs-lookup"><span data-stu-id="00709-112">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="00709-113">高階函式接受函數做為引數，並傳回函式作為函式呼叫的值。</span><span class="sxs-lookup"><span data-stu-id="00709-113">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="00709-114">這些作業支援將函數設計支柱為對應函式和函式組合。</span><span class="sxs-lookup"><span data-stu-id="00709-114">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>

## <a name="give-the-value-a-name"></a><span data-ttu-id="00709-115">為值命名</span><span class="sxs-lookup"><span data-stu-id="00709-115">Give the Value a Name</span></span>

<span data-ttu-id="00709-116">如果函式是第一級的值，您必須能夠命名它，就像您可以命名整數、字串和其他內建類型一樣。</span><span class="sxs-lookup"><span data-stu-id="00709-116">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="00709-117">這在功能程式設計文獻中稱為將識別碼系結至值。</span><span class="sxs-lookup"><span data-stu-id="00709-117">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="00709-118">F # 使用系結將名稱系[ `let` 結至值](../language-reference/functions/let-bindings.md)： `let <identifier> = <value>` 。</span><span class="sxs-lookup"><span data-stu-id="00709-118">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="00709-119">下列程式碼顯示兩個範例。</span><span class="sxs-lookup"><span data-stu-id="00709-119">The following code shows two examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="00709-120">您可以輕鬆地將函數命名。</span><span class="sxs-lookup"><span data-stu-id="00709-120">You can name a function just as easily.</span></span> <span data-ttu-id="00709-121">下列範例會定義名為的函式，該函式會將識別碼系結 `squareIt` `squareIt` 至 [lambda 運算式](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n` 。</span><span class="sxs-lookup"><span data-stu-id="00709-121">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="00709-122">函式 `squareIt` 有一個參數， `n` 而它會傳回該參數的平方。</span><span class="sxs-lookup"><span data-stu-id="00709-122">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="00709-123">F # 提供下列更簡潔的語法，以較少的輸入來達成相同的結果。</span><span class="sxs-lookup"><span data-stu-id="00709-123">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="00709-124">接下來的範例會使用第一個樣式， `let <function-name> = <lambda-expression>` 以強調函式宣告和其他類型值的宣告之間的相似之處。</span><span class="sxs-lookup"><span data-stu-id="00709-124">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="00709-125">不過，所有命名的函式也可以使用精簡的語法來撰寫。</span><span class="sxs-lookup"><span data-stu-id="00709-125">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="00709-126">其中一些範例是以這兩種方式撰寫的。</span><span class="sxs-lookup"><span data-stu-id="00709-126">Some of the examples are written in both ways.</span></span>

## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="00709-127">將值儲存在資料結構中</span><span class="sxs-lookup"><span data-stu-id="00709-127">Store the Value in a Data Structure</span></span>

<span data-ttu-id="00709-128">第一個類別的值可以儲存在資料結構中。</span><span class="sxs-lookup"><span data-stu-id="00709-128">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="00709-129">下列程式碼顯示在清單和元組中儲存值的範例。</span><span class="sxs-lookup"><span data-stu-id="00709-129">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="00709-130">為了確認儲存在元組中的函式名稱確實是評估為函式，下列範例會使用 `fst` 和 `snd` 運算子來解壓縮元組中的第一個和第二個元素 `funAndArgTuple` 。</span><span class="sxs-lookup"><span data-stu-id="00709-130">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="00709-131">元組中的第一個專案是 `squareIt` ，而第二個元素是 `num` 。</span><span class="sxs-lookup"><span data-stu-id="00709-131">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="00709-132">`num`在先前的範例中，識別碼會系結至整數10，此為函數的有效引數 `squareIt` 。</span><span class="sxs-lookup"><span data-stu-id="00709-132">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="00709-133">第二個運算式會將元組中的第一個專案套用至元組中的第二個元素： `squareIt num` 。</span><span class="sxs-lookup"><span data-stu-id="00709-133">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="00709-134">同樣地，如同識別碼 `num` 和整數10可以交替使用，因此可以使用識別碼 `squareIt` 和 lambda 運算式 `fun n -> n * n` 。</span><span class="sxs-lookup"><span data-stu-id="00709-134">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="00709-135">傳遞值做為引數</span><span class="sxs-lookup"><span data-stu-id="00709-135">Pass the Value as an Argument</span></span>

<span data-ttu-id="00709-136">如果某個值在語言中具有第一級的狀態，您可以將它當作引數傳遞給函式。</span><span class="sxs-lookup"><span data-stu-id="00709-136">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="00709-137">例如，通常會將整數和字串當作引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="00709-137">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="00709-138">下列程式碼顯示在 F # 中做為引數傳遞的整數和字串。</span><span class="sxs-lookup"><span data-stu-id="00709-138">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="00709-139">如果函式具有頂級狀態，您必須能夠以同樣的方式將它們當作引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="00709-139">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="00709-140">請記住，這是較高順序函式的第一個特性。</span><span class="sxs-lookup"><span data-stu-id="00709-140">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="00709-141">在下列範例中，函數 `applyIt` 有兩個參數： `op` 和 `arg` 。</span><span class="sxs-lookup"><span data-stu-id="00709-141">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="00709-142">如果您在有一個參數的函式中傳送，並將函 `op` 式的適當引數傳送至，函數會傳回套用 `arg` 至的結果 `op` `arg` 。</span><span class="sxs-lookup"><span data-stu-id="00709-142">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="00709-143">在下列範例中，函式引數和整數引數都會以相同的方式傳送，方法是使用它們的名稱。</span><span class="sxs-lookup"><span data-stu-id="00709-143">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="00709-144">將函式作為引數傳送至另一個函式的能力，是以函式程式設計語言（例如地圖或篩選作業）的常見抽象概念為基礎。</span><span class="sxs-lookup"><span data-stu-id="00709-144">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="00709-145">例如，對應作業是較高階的函式，它會捕捉逐步執行清單的函式所共用的計算、對每個元素執行某些動作，然後傳回結果清單。</span><span class="sxs-lookup"><span data-stu-id="00709-145">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="00709-146">您可能會想要遞增整數清單中的每個專案，或每個元素的平方，或是將字串清單中的每個專案變更為大寫。</span><span class="sxs-lookup"><span data-stu-id="00709-146">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="00709-147">計算容易出錯的部分是遞迴程式，它會逐步執行此清單，並建立要傳回的結果清單。</span><span class="sxs-lookup"><span data-stu-id="00709-147">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="00709-148">該元件是在對應函式中所捕捉。</span><span class="sxs-lookup"><span data-stu-id="00709-148">That part is captured in the mapping function.</span></span> <span data-ttu-id="00709-149">您必須為特定應用程式撰寫的所有專案，都是您想要個別套用至每個清單專案的函式， (新增、求大小寫) 。</span><span class="sxs-lookup"><span data-stu-id="00709-149">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="00709-150">該函式會以引數的形式傳送至對應函式，就像 `squareIt` `applyIt` 在先前的範例中所傳送的一樣。</span><span class="sxs-lookup"><span data-stu-id="00709-150">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="00709-151">F # 為大部分的集合類型（包括 [清單](../language-reference/lists.md)、 [陣列](../language-reference/arrays.md)和 [序列](../language-reference/sequences.md)）提供對應方法。</span><span class="sxs-lookup"><span data-stu-id="00709-151">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="00709-152">下列範例使用清單。</span><span class="sxs-lookup"><span data-stu-id="00709-152">The following examples use lists.</span></span> <span data-ttu-id="00709-153">語法是 `List.map <the function> <the list>`。</span><span class="sxs-lookup"><span data-stu-id="00709-153">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="00709-154">如需詳細資訊，請參閱 [清單](../language-reference/lists.md)。</span><span class="sxs-lookup"><span data-stu-id="00709-154">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="00709-155">從函式呼叫傳回值</span><span class="sxs-lookup"><span data-stu-id="00709-155">Return the Value from a Function Call</span></span>

<span data-ttu-id="00709-156">最後，如果函式在語言中具有第一級的狀態，您就必須能夠將它傳回做為函式呼叫的值，就像您傳回其他類型（例如整數和字串）一樣。</span><span class="sxs-lookup"><span data-stu-id="00709-156">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="00709-157">下列函式呼叫會傳回整數並加以顯示。</span><span class="sxs-lookup"><span data-stu-id="00709-157">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="00709-158">下列函式呼叫會傳回字串。</span><span class="sxs-lookup"><span data-stu-id="00709-158">The following function call returns a string.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="00709-159">下列函式呼叫（宣告為 inline）會傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="00709-159">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="00709-160">顯示的值為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="00709-160">The value displayed is `True`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="00709-161">以函式呼叫的值傳回函式的能力，是較高順序函數的第二個特性。</span><span class="sxs-lookup"><span data-stu-id="00709-161">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="00709-162">在下列範例中， `checkFor` 定義為採用一個引數的函式， `item` 並傳回新的函式作為其值。</span><span class="sxs-lookup"><span data-stu-id="00709-162">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="00709-163">傳回的函式會接受清單作為其引數， `lst` 並 `item` 在中搜尋 `lst` 。</span><span class="sxs-lookup"><span data-stu-id="00709-163">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="00709-164">如果 `item` 存在，則函數會傳回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="00709-164">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="00709-165">如果 `item` 不存在，則函數會傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="00709-165">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="00709-166">如上一節所示，下列程式碼會使用提供的清單函式 [list. exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists)來搜尋清單。</span><span class="sxs-lookup"><span data-stu-id="00709-166">As in the previous section, the following code uses a provided list function, [List.exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists), to search the list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="00709-167">下列程式碼會使用來建立新的函式，該函式 `checkFor` 會接受一個引數、一個清單，並在清單中搜尋7。</span><span class="sxs-lookup"><span data-stu-id="00709-167">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="00709-168">下列範例會使用 F # 中函式的第一個類別狀態來宣告函式， `compose` 此函式會傳回兩個函式引數的組合。</span><span class="sxs-lookup"><span data-stu-id="00709-168">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> <span data-ttu-id="00709-169">如需更短的版本，請參閱下一節「擴充函數」。</span><span class="sxs-lookup"><span data-stu-id="00709-169">For an even shorter version, see the following section, "Curried Functions."</span></span>

<span data-ttu-id="00709-170">下列程式碼會將兩個函式作為引數傳送至，這兩個函式 `compose` 都會採用相同類型的單一引數。</span><span class="sxs-lookup"><span data-stu-id="00709-170">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="00709-171">傳回值是新的函式，這是兩個函式引數的組合。</span><span class="sxs-lookup"><span data-stu-id="00709-171">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> <span data-ttu-id="00709-172">F # 提供兩個運算子， `<<` 以及 `>>` 撰寫函數。</span><span class="sxs-lookup"><span data-stu-id="00709-172">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="00709-173">例如， `let squareAndDouble2 = doubleIt << squareIt` `let squareAndDouble = compose doubleIt squareIt` 在上一個範例中相當於。</span><span class="sxs-lookup"><span data-stu-id="00709-173">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="00709-174">下列範例會傳回函式作為函式呼叫的值，以建立簡單的猜測遊戲。</span><span class="sxs-lookup"><span data-stu-id="00709-174">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="00709-175">若要建立遊戲，請 `makeGame` 使用您希望他人猜測的值來呼叫 `target` 。</span><span class="sxs-lookup"><span data-stu-id="00709-175">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="00709-176">函式的傳回值 `makeGame` 是接受一個引數 (猜測) 的函式，並報告猜測是否正確。</span><span class="sxs-lookup"><span data-stu-id="00709-176">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="00709-177">下列程式碼會呼叫，並傳送 `makeGame` 的值 `7` `target` 。</span><span class="sxs-lookup"><span data-stu-id="00709-177">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="00709-178">識別碼 `playGame` 會系結至傳回的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="00709-178">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="00709-179">因此，是一種函式，它會將的 `playGame` 值作為其一個引數 `guess` 。</span><span class="sxs-lookup"><span data-stu-id="00709-179">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a><span data-ttu-id="00709-180">擴充函數</span><span class="sxs-lookup"><span data-stu-id="00709-180">Curried Functions</span></span>

<span data-ttu-id="00709-181">您可以利用 F # 函式宣告中的隱含 *currying* ，更簡潔地撰寫上一節中的許多範例。</span><span class="sxs-lookup"><span data-stu-id="00709-181">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="00709-182">Currying 是一種程式，可將具有多個參數的函式轉換為一系列的內嵌函式，其中每個函式都有單一參數。</span><span class="sxs-lookup"><span data-stu-id="00709-182">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="00709-183">在 F # 中，有多個參數的函式在本質上是局部的。</span><span class="sxs-lookup"><span data-stu-id="00709-183">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="00709-184">例如，在 `compose` 上一節中，您可以使用三個參數，以下列簡潔的樣式來撰寫。</span><span class="sxs-lookup"><span data-stu-id="00709-184">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="00709-185">不過，結果是一個參數的函式，它會傳回一個參數的函式，而後者接著會傳回一個參數的另一個函式，如下所示 `compose4curried` 。</span><span class="sxs-lookup"><span data-stu-id="00709-185">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="00709-186">您可以透過數種方式來存取此函式。</span><span class="sxs-lookup"><span data-stu-id="00709-186">You can access this function in several ways.</span></span> <span data-ttu-id="00709-187">下列每個範例都會傳回並顯示18。</span><span class="sxs-lookup"><span data-stu-id="00709-187">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="00709-188">您可以 `compose4` 使用 `compose4curried` 中的任何範例取代。</span><span class="sxs-lookup"><span data-stu-id="00709-188">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="00709-189">若要確認函式的運作方式仍與之前相同，請再次嘗試原來的測試案例。</span><span class="sxs-lookup"><span data-stu-id="00709-189">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> <span data-ttu-id="00709-190">您可以藉由將元組中的參數括住來限制 currying。</span><span class="sxs-lookup"><span data-stu-id="00709-190">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="00709-191">如需詳細資訊，請參閱 [參數和引數](../language-reference/parameters-and-arguments.md)中的「參數模式」。</span><span class="sxs-lookup"><span data-stu-id="00709-191">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="00709-192">下列範例會使用隱含 currying 來寫入較短的版本 `makeGame` 。</span><span class="sxs-lookup"><span data-stu-id="00709-192">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="00709-193">結構和傳回函式的詳細資料 `makeGame` `game` ，在此格式中較不明確，但您可以使用原始測試案例來確認結果是相同的。</span><span class="sxs-lookup"><span data-stu-id="00709-193">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="00709-194">如需 currying 的詳細資訊，請參閱函 [式中的](../language-reference/functions/index.md)「部分引數應用程式」。</span><span class="sxs-lookup"><span data-stu-id="00709-194">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>

## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="00709-195">識別碼和函式定義是可互換的</span><span class="sxs-lookup"><span data-stu-id="00709-195">Identifier and Function Definition Are Interchangeable</span></span>

<span data-ttu-id="00709-196">`num`先前範例中的變數名稱會評估為整數10，而且如果 `num` 有效，則10也是有效的。</span><span class="sxs-lookup"><span data-stu-id="00709-196">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="00709-197">函式識別碼和其值也是如此：可以使用函式名稱的任何位置，都可以使用它所系結的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="00709-197">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="00709-198">下列範例會定義名為的函式 `Boolean` `isNegative` ，然後使用函數的名稱和函式的定義。</span><span class="sxs-lookup"><span data-stu-id="00709-198">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="00709-199">接下來的三個範例都會傳回並顯示 `False` 。</span><span class="sxs-lookup"><span data-stu-id="00709-199">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="00709-200">若要進一步進行，請將系結的值取代為 `applyIt` `applyIt` 。</span><span class="sxs-lookup"><span data-stu-id="00709-200">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="00709-201">函數是 F 中的第一個類別值\#</span><span class="sxs-lookup"><span data-stu-id="00709-201">Functions Are First-Class Values in F\#</span></span>

<span data-ttu-id="00709-202">上述各節中的範例會示範 F # 中的函式符合 F # 中第一個類別值的準則：</span><span class="sxs-lookup"><span data-stu-id="00709-202">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="00709-203">您可以將識別碼系結至函式定義。</span><span class="sxs-lookup"><span data-stu-id="00709-203">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="00709-204">您可以將函數儲存在資料結構中。</span><span class="sxs-lookup"><span data-stu-id="00709-204">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="00709-205">您可以將函數當作引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="00709-205">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="00709-206">您可以傳回函數作為函式呼叫的值。</span><span class="sxs-lookup"><span data-stu-id="00709-206">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="00709-207">如需 F # 的詳細資訊，請參閱 [f # 語言參考](../language-reference/index.md)。</span><span class="sxs-lookup"><span data-stu-id="00709-207">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="00709-208">範例</span><span class="sxs-lookup"><span data-stu-id="00709-208">Example</span></span>

### <a name="description"></a><span data-ttu-id="00709-209">描述</span><span class="sxs-lookup"><span data-stu-id="00709-209">Description</span></span>

<span data-ttu-id="00709-210">下列程式碼包含本主題中的所有範例。</span><span class="sxs-lookup"><span data-stu-id="00709-210">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="00709-211">程式碼</span><span class="sxs-lookup"><span data-stu-id="00709-211">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a><span data-ttu-id="00709-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00709-212">See also</span></span>

- [<span data-ttu-id="00709-213">清單</span><span class="sxs-lookup"><span data-stu-id="00709-213">Lists</span></span>](../language-reference/lists.md)
- [<span data-ttu-id="00709-214">元組</span><span class="sxs-lookup"><span data-stu-id="00709-214">Tuples</span></span>](../language-reference/tuples.md)
- [<span data-ttu-id="00709-215">函式</span><span class="sxs-lookup"><span data-stu-id="00709-215">Functions</span></span>](../language-reference/functions/index.md)
- [<span data-ttu-id="00709-216">`let` 綁定</span><span class="sxs-lookup"><span data-stu-id="00709-216">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)
- [<span data-ttu-id="00709-217">Lambda 運算式： `fun` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="00709-217">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
