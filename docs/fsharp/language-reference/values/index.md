---
title: 值 (F#)
description: '了解如何在 F # 中的值為具有特定類型的數量。'
keywords: Visual F#, F#, 函式程式設計
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5e1e73c3-5adb-4bba-9976-d57f1ff6cd8d
ms.openlocfilehash: a1e077552ba39a483be3129c89af48b547219733
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="values"></a><span data-ttu-id="775b1-104">值</span><span class="sxs-lookup"><span data-stu-id="775b1-104">Values</span></span>

<span data-ttu-id="775b1-105">F# 中的值是具有特定類型的數量；值可以是整數或浮點數、字元或文字、清單、序列、陣列、元組、差別聯集、記錄、類別類型或函式值。</span><span class="sxs-lookup"><span data-stu-id="775b1-105">Values in F# are quantities that have a specific type; values can be integral or floating point numbers, characters or text, lists, sequences, arrays, tuples, discriminated unions, records, class types, or function values.</span></span>


## <a name="binding-a-value"></a><span data-ttu-id="775b1-106">繫結值</span><span class="sxs-lookup"><span data-stu-id="775b1-106">Binding a Value</span></span>
<span data-ttu-id="775b1-107">「繫結」一詞表示建立名稱與定義的關聯。</span><span class="sxs-lookup"><span data-stu-id="775b1-107">The term *binding* means associating a name with a definition.</span></span> <span data-ttu-id="775b1-108">`let` 關鍵字會繫結值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="775b1-108">The `let` keyword binds a value, as in the following examples:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

<span data-ttu-id="775b1-109">值的類型是從定義推斷的。</span><span class="sxs-lookup"><span data-stu-id="775b1-109">The type of a value is inferred from the definition.</span></span> <span data-ttu-id="775b1-110">若為基本類型 (例如整數或浮點數)，則是從常值的類型來決定類型。</span><span class="sxs-lookup"><span data-stu-id="775b1-110">For a primitive type, such as an integral or floating point number, the type is determined from the type of the literal.</span></span> <span data-ttu-id="775b1-111">因此，在上述範例中，編譯器推斷 `b` 的類型是 `unsigned int`，而推斷 `a` 的類型是 `int`。</span><span class="sxs-lookup"><span data-stu-id="775b1-111">Therefore, in the previous example, the compiler infers the type of `b` to be `unsigned int`, whereas the compiler infers the type of `a` to be `int`.</span></span> <span data-ttu-id="775b1-112">函式值的類型是從函式主體中的傳回值決定。</span><span class="sxs-lookup"><span data-stu-id="775b1-112">The type of a function value is determined from the return value in the function body.</span></span> <span data-ttu-id="775b1-113">如需函式值類型的詳細資訊，請參閱[函式](../functions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="775b1-113">For more information about function value types, see [Functions](../functions/index.md).</span></span> <span data-ttu-id="775b1-114">如需常值型別的詳細資訊，請參閱[常值](../literals.md)。</span><span class="sxs-lookup"><span data-stu-id="775b1-114">For more information about literal types, see [Literals](../literals.md).</span></span>


## <a name="why-immutable"></a><span data-ttu-id="775b1-115">使用不可變的原因</span><span class="sxs-lookup"><span data-stu-id="775b1-115">Why Immutable?</span></span>
<span data-ttu-id="775b1-116">不可變的值是在程式執行過程中無法變更的值。</span><span class="sxs-lookup"><span data-stu-id="775b1-116">Immutable values are values that cannot be changed throughout the course of a program's execution.</span></span> <span data-ttu-id="775b1-117">若您習慣使用 C++、Visual Basic 或 C# 等語言，F# 首重不可變的值，而不是程式執行期間可指派新值的變數，這可能讓您訝異。</span><span class="sxs-lookup"><span data-stu-id="775b1-117">If you are used to languages such as C++, Visual Basic, or C#, you might find it surprising that F# puts primacy over immutable values rather than variables that can be assigned new values during the execution of a program.</span></span> <span data-ttu-id="775b1-118">不可變的資料是函式程式設計的重要項目。</span><span class="sxs-lookup"><span data-stu-id="775b1-118">Immutable data is an important element of functional programming.</span></span> <span data-ttu-id="775b1-119">在多執行緒環境中，難以管理可由許多不同的執行緒變更的共用可變變數。</span><span class="sxs-lookup"><span data-stu-id="775b1-119">In a multithreaded environment, shared mutable variables that can be changed by many different threads are difficult to manage.</span></span> <span data-ttu-id="775b1-120">此外，對於可變變數，有時候難以判斷變數是否會在傳遞至另一個函式時變更。</span><span class="sxs-lookup"><span data-stu-id="775b1-120">Also, with mutable variables, it can sometimes be hard to tell if a variable might be changed when it is passed to another function.</span></span>

<span data-ttu-id="775b1-121">在純函式語言中，沒有變數，而且函式只作為數學函式。</span><span class="sxs-lookup"><span data-stu-id="775b1-121">In pure functional languages, there are no variables, and functions behave strictly as mathematical functions.</span></span> <span data-ttu-id="775b1-122">程序語言中的程式碼使用變數指派來變更值，而在函式語言中的對等程式碼則有作為輸入的不可變值、不可變的函式，以及作為輸出的不同不可變值。</span><span class="sxs-lookup"><span data-stu-id="775b1-122">Where code in a procedural language uses a variable assignment to alter a value, the equivalent code in a functional language has an immutable value that is the input, an immutable function, and different immutable values as the output.</span></span> <span data-ttu-id="775b1-123">如此在數學方面嚴謹的程度，可以讓程式的行為更符合預期。</span><span class="sxs-lookup"><span data-stu-id="775b1-123">This mathematical strictness allows for tighter reasoning about the behavior of the program.</span></span> <span data-ttu-id="775b1-124">如此一來，編譯器就能更嚴格地檢查程式碼，並且在最佳化時更有效率，也有助於程式開發人員更容易了解及撰寫正確程式碼。</span><span class="sxs-lookup"><span data-stu-id="775b1-124">This tighter reasoning is what enables compilers to check code more stringently and to optimize more effectively, and helps make it easier for developers to understand and write correct code.</span></span> <span data-ttu-id="775b1-125">所以，比起一般程序程式碼，偵錯函式程式碼也更為容易。</span><span class="sxs-lookup"><span data-stu-id="775b1-125">Functional code is therefore likely to be easier to debug than ordinary procedural code.</span></span>

<span data-ttu-id="775b1-126">F# 不是純函式語言，但完全支援函式程式設計。</span><span class="sxs-lookup"><span data-stu-id="775b1-126">F# is not a pure functional language, yet it fully supports functional programming.</span></span> <span data-ttu-id="775b1-127">使用不可變的值是良好做法，因為這麼做可讓程式碼從函式程式設計的重要層面獲益。</span><span class="sxs-lookup"><span data-stu-id="775b1-127">Using immutable values is a good practice because doing this allows your code to benefit from an important aspect of functional programming.</span></span>


## <a name="mutable-variables"></a><span data-ttu-id="775b1-128">可變變數</span><span class="sxs-lookup"><span data-stu-id="775b1-128">Mutable Variables</span></span>
<span data-ttu-id="775b1-129">您可以使用 `mutable` 關鍵字指定可變更的變數。</span><span class="sxs-lookup"><span data-stu-id="775b1-129">You can use the keyword `mutable` to specify a variable that can be changed.</span></span> <span data-ttu-id="775b1-130">F# 的可變變數通常應該有限制範圍，可以是類型欄位或區域值。</span><span class="sxs-lookup"><span data-stu-id="775b1-130">Mutable variables in F# should generally have a limited scope, either as a field of a type or as a local value.</span></span> <span data-ttu-id="775b1-131">有限制範圍的可變變數更容易控制，同時也比較不會遭到誤改。</span><span class="sxs-lookup"><span data-stu-id="775b1-131">Mutable variables with a limited scope are easier to control and are less likely to be modified in incorrect ways.</span></span>

<span data-ttu-id="775b1-132">您可以透過與定義值相同的方式使用 `let` 關鍵字，將初始值指派給可變變數。</span><span class="sxs-lookup"><span data-stu-id="775b1-132">You can assign an initial value to a mutable variable by using the `let` keyword in the same way as you would define a value.</span></span> <span data-ttu-id="775b1-133">不過，差異在於後續可以透過 `<-` 運算子將新值指派給可變變數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="775b1-133">However, the difference is that you can subsequently assign new values to mutable variables by using the `<-` operator, as in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet602.fs)]
    
## <a name="related-topics"></a><span data-ttu-id="775b1-134">相關主題</span><span class="sxs-lookup"><span data-stu-id="775b1-134">Related Topics</span></span>


|<span data-ttu-id="775b1-135">標題</span><span class="sxs-lookup"><span data-stu-id="775b1-135">Title</span></span>|<span data-ttu-id="775b1-136">說明</span><span class="sxs-lookup"><span data-stu-id="775b1-136">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="775b1-137">let 繫結</span><span class="sxs-lookup"><span data-stu-id="775b1-137">let Bindings</span></span>](../functions/let-bindings.md)|<span data-ttu-id="775b1-138">提供使用資訊`let`關鍵字來將名稱繫結至值和函式。</span><span class="sxs-lookup"><span data-stu-id="775b1-138">Provides information about using the `let` keyword to bind names to values and functions.</span></span>|
|[<span data-ttu-id="775b1-139">函式</span><span class="sxs-lookup"><span data-stu-id="775b1-139">Functions</span></span>](../functions/index.md)|<span data-ttu-id="775b1-140">提供 F# 函式的概觀。</span><span class="sxs-lookup"><span data-stu-id="775b1-140">Provides an overview of functions in F#.</span></span>|

## <a name="see-also"></a><span data-ttu-id="775b1-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="775b1-141">See Also</span></span>
[<span data-ttu-id="775b1-142">Null 值</span><span class="sxs-lookup"><span data-stu-id="775b1-142">Null Values</span></span>](null-Values.md)

[<span data-ttu-id="775b1-143">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="775b1-143">F# Language Reference</span></span>](../index.md)
