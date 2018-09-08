---
title: 值 (F#)
description: '了解如何在 F # 中的值為具有特定類型的數量。'
ms.date: 05/16/2016
ms.openlocfilehash: f645481ce8395c11ae920aee06cbf07955aeb684
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186509"
---
# <a name="values"></a><span data-ttu-id="08042-103">值</span><span class="sxs-lookup"><span data-stu-id="08042-103">Values</span></span>

<span data-ttu-id="08042-104">F# 中的值是具有特定類型的數量；值可以是整數或浮點數、字元或文字、清單、序列、陣列、元組、差別聯集、記錄、類別類型或函式值。</span><span class="sxs-lookup"><span data-stu-id="08042-104">Values in F# are quantities that have a specific type; values can be integral or floating point numbers, characters or text, lists, sequences, arrays, tuples, discriminated unions, records, class types, or function values.</span></span>

## <a name="binding-a-value"></a><span data-ttu-id="08042-105">繫結值</span><span class="sxs-lookup"><span data-stu-id="08042-105">Binding a Value</span></span>

<span data-ttu-id="08042-106">「繫結」一詞表示建立名稱與定義的關聯。</span><span class="sxs-lookup"><span data-stu-id="08042-106">The term *binding* means associating a name with a definition.</span></span> <span data-ttu-id="08042-107">`let` 關鍵字會繫結值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="08042-107">The `let` keyword binds a value, as in the following examples:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

<span data-ttu-id="08042-108">值的類型是從定義推斷的。</span><span class="sxs-lookup"><span data-stu-id="08042-108">The type of a value is inferred from the definition.</span></span> <span data-ttu-id="08042-109">若為基本類型 (例如整數或浮點數)，則是從常值的類型來決定類型。</span><span class="sxs-lookup"><span data-stu-id="08042-109">For a primitive type, such as an integral or floating point number, the type is determined from the type of the literal.</span></span> <span data-ttu-id="08042-110">因此，在上述範例中，編譯器推斷 `b` 的類型是 `unsigned int`，而推斷 `a` 的類型是 `int`。</span><span class="sxs-lookup"><span data-stu-id="08042-110">Therefore, in the previous example, the compiler infers the type of `b` to be `unsigned int`, whereas the compiler infers the type of `a` to be `int`.</span></span> <span data-ttu-id="08042-111">函式值的類型是從函式主體中的傳回值決定。</span><span class="sxs-lookup"><span data-stu-id="08042-111">The type of a function value is determined from the return value in the function body.</span></span> <span data-ttu-id="08042-112">如需函式值類型的詳細資訊，請參閱[函式](../functions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="08042-112">For more information about function value types, see [Functions](../functions/index.md).</span></span> <span data-ttu-id="08042-113">如需常值型別的詳細資訊，請參閱[常值](../literals.md)。</span><span class="sxs-lookup"><span data-stu-id="08042-113">For more information about literal types, see [Literals](../literals.md).</span></span>

<span data-ttu-id="08042-114">根據預設，編譯器不會發出有關未使用的繫結的診斷。</span><span class="sxs-lookup"><span data-stu-id="08042-114">The compiler does not issue diagnostics about unused bindings by default.</span></span> <span data-ttu-id="08042-115">若要接收這些訊息，啟用警告 1182年，專案檔中，或叫用編譯器時 (請參閱`--warnon`底下[編譯器選項](../compiler-options.md))。</span><span class="sxs-lookup"><span data-stu-id="08042-115">To receive these messages, enable warning 1182 in your project file or when invoking the compiler (see `--warnon` under [Compiler Options](../compiler-options.md)).</span></span>

## <a name="why-immutable"></a><span data-ttu-id="08042-116">使用不可變的原因</span><span class="sxs-lookup"><span data-stu-id="08042-116">Why Immutable?</span></span>

<span data-ttu-id="08042-117">不可變的值是在程式執行過程中無法變更的值。</span><span class="sxs-lookup"><span data-stu-id="08042-117">Immutable values are values that cannot be changed throughout the course of a program's execution.</span></span> <span data-ttu-id="08042-118">若您習慣使用 C++、Visual Basic 或 C# 等語言，F# 首重不可變的值，而不是程式執行期間可指派新值的變數，這可能讓您訝異。</span><span class="sxs-lookup"><span data-stu-id="08042-118">If you are used to languages such as C++, Visual Basic, or C#, you might find it surprising that F# puts primacy over immutable values rather than variables that can be assigned new values during the execution of a program.</span></span> <span data-ttu-id="08042-119">不可變的資料是函式程式設計的重要項目。</span><span class="sxs-lookup"><span data-stu-id="08042-119">Immutable data is an important element of functional programming.</span></span> <span data-ttu-id="08042-120">在多執行緒環境中，難以管理可由許多不同的執行緒變更的共用可變變數。</span><span class="sxs-lookup"><span data-stu-id="08042-120">In a multithreaded environment, shared mutable variables that can be changed by many different threads are difficult to manage.</span></span> <span data-ttu-id="08042-121">此外，對於可變變數，有時候難以判斷變數是否會在傳遞至另一個函式時變更。</span><span class="sxs-lookup"><span data-stu-id="08042-121">Also, with mutable variables, it can sometimes be hard to tell if a variable might be changed when it is passed to another function.</span></span>

<span data-ttu-id="08042-122">在純函式語言中，沒有變數，而且函式只作為數學函式。</span><span class="sxs-lookup"><span data-stu-id="08042-122">In pure functional languages, there are no variables, and functions behave strictly as mathematical functions.</span></span> <span data-ttu-id="08042-123">程序語言中的程式碼使用變數指派來變更值，而在函式語言中的對等程式碼則有作為輸入的不可變值、不可變的函式，以及作為輸出的不同不可變值。</span><span class="sxs-lookup"><span data-stu-id="08042-123">Where code in a procedural language uses a variable assignment to alter a value, the equivalent code in a functional language has an immutable value that is the input, an immutable function, and different immutable values as the output.</span></span> <span data-ttu-id="08042-124">如此在數學方面嚴謹的程度，可以讓程式的行為更符合預期。</span><span class="sxs-lookup"><span data-stu-id="08042-124">This mathematical strictness allows for tighter reasoning about the behavior of the program.</span></span> <span data-ttu-id="08042-125">如此一來，編譯器就能更嚴格地檢查程式碼，並且在最佳化時更有效率，也有助於程式開發人員更容易了解及撰寫正確程式碼。</span><span class="sxs-lookup"><span data-stu-id="08042-125">This tighter reasoning is what enables compilers to check code more stringently and to optimize more effectively, and helps make it easier for developers to understand and write correct code.</span></span> <span data-ttu-id="08042-126">所以，比起一般程序程式碼，偵錯函式程式碼也更為容易。</span><span class="sxs-lookup"><span data-stu-id="08042-126">Functional code is therefore likely to be easier to debug than ordinary procedural code.</span></span>

<span data-ttu-id="08042-127">F# 不是純函式語言，但完全支援函式程式設計。</span><span class="sxs-lookup"><span data-stu-id="08042-127">F# is not a pure functional language, yet it fully supports functional programming.</span></span> <span data-ttu-id="08042-128">使用不可變的值是良好做法，因為這麼做可讓程式碼從函式程式設計的重要層面獲益。</span><span class="sxs-lookup"><span data-stu-id="08042-128">Using immutable values is a good practice because doing this allows your code to benefit from an important aspect of functional programming.</span></span>

## <a name="mutable-variables"></a><span data-ttu-id="08042-129">可變變數</span><span class="sxs-lookup"><span data-stu-id="08042-129">Mutable Variables</span></span>

<span data-ttu-id="08042-130">您可以使用 `mutable` 關鍵字指定可變更的變數。</span><span class="sxs-lookup"><span data-stu-id="08042-130">You can use the keyword `mutable` to specify a variable that can be changed.</span></span> <span data-ttu-id="08042-131">F# 的可變變數通常應該有限制範圍，可以是類型欄位或區域值。</span><span class="sxs-lookup"><span data-stu-id="08042-131">Mutable variables in F# should generally have a limited scope, either as a field of a type or as a local value.</span></span> <span data-ttu-id="08042-132">有限制範圍的可變變數更容易控制，同時也比較不會遭到誤改。</span><span class="sxs-lookup"><span data-stu-id="08042-132">Mutable variables with a limited scope are easier to control and are less likely to be modified in incorrect ways.</span></span>

<span data-ttu-id="08042-133">您可以透過與定義值相同的方式使用 `let` 關鍵字，將初始值指派給可變變數。</span><span class="sxs-lookup"><span data-stu-id="08042-133">You can assign an initial value to a mutable variable by using the `let` keyword in the same way as you would define a value.</span></span> <span data-ttu-id="08042-134">不過，差異在於後續可以透過 `<-` 運算子將新值指派給可變變數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="08042-134">However, the difference is that you can subsequently assign new values to mutable variables by using the `<-` operator, as in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet602.fs)]

<span data-ttu-id="08042-135">值標示`mutable`可能會自動升級為`'a ref`如果由 closure 擷取，包括建立 closure，例如的形式`seq`產生器。</span><span class="sxs-lookup"><span data-stu-id="08042-135">Values marked `mutable` may be automatically promoted to `'a ref` if captured by a closure, including forms that create closures, such as `seq` builders.</span></span> <span data-ttu-id="08042-136">如果您想要在發生這種情況時收到通知，啟用警告 3180 叫用編譯器時，或在您的專案檔。</span><span class="sxs-lookup"><span data-stu-id="08042-136">If you wish to be notified when this occurs, enable warning 3180 in your project file or when invoking the compiler.</span></span>

## <a name="related-topics"></a><span data-ttu-id="08042-137">相關主題</span><span class="sxs-lookup"><span data-stu-id="08042-137">Related Topics</span></span>

|<span data-ttu-id="08042-138">標題</span><span class="sxs-lookup"><span data-stu-id="08042-138">Title</span></span>|<span data-ttu-id="08042-139">描述</span><span class="sxs-lookup"><span data-stu-id="08042-139">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="08042-140">let 繫結</span><span class="sxs-lookup"><span data-stu-id="08042-140">let Bindings</span></span>](../functions/let-bindings.md)|<span data-ttu-id="08042-141">提供有關使用資訊`let`關鍵字將名稱繫結至值和函式。</span><span class="sxs-lookup"><span data-stu-id="08042-141">Provides information about using the `let` keyword to bind names to values and functions.</span></span>|
|[<span data-ttu-id="08042-142">函式</span><span class="sxs-lookup"><span data-stu-id="08042-142">Functions</span></span>](../functions/index.md)|<span data-ttu-id="08042-143">提供 F# 函式的概觀。</span><span class="sxs-lookup"><span data-stu-id="08042-143">Provides an overview of functions in F#.</span></span>|

## <a name="see-also"></a><span data-ttu-id="08042-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08042-144">See also</span></span>

- [<span data-ttu-id="08042-145">Null 值</span><span class="sxs-lookup"><span data-stu-id="08042-145">Null Values</span></span>](null-Values.md)
- [<span data-ttu-id="08042-146">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="08042-146">F# Language Reference</span></span>](../index.md)
