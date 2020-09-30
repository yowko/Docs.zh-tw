---
title: 遞迴函式：rec 關鍵字
description: "瞭解如何搭配 ' let ' 關鍵字使用 F # ' rec ' 關鍵字來定義遞迴函數。"
ms.date: 08/12/2020
ms.openlocfilehash: 1ab00ff9400129e531fd7320861b3d9625cad08c
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438070"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="37091-103">遞迴函式：rec 關鍵字</span><span class="sxs-lookup"><span data-stu-id="37091-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="37091-104">`rec`關鍵字會與關鍵字一起使用 `let` ，以定義遞迴函數。</span><span class="sxs-lookup"><span data-stu-id="37091-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="37091-105">語法</span><span class="sxs-lookup"><span data-stu-id="37091-105">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
    function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
    function1-body

and function2-nameparameter-list =
    function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="37091-106">備註</span><span class="sxs-lookup"><span data-stu-id="37091-106">Remarks</span></span>

<span data-ttu-id="37091-107">遞迴函式-呼叫本身的函式會在 F # 語言中使用關鍵字明確識別 `rec` 。</span><span class="sxs-lookup"><span data-stu-id="37091-107">Recursive functions - functions that call themselves - are identified explicitly in the F# language with the `rec` keyword.</span></span> <span data-ttu-id="37091-108">關鍵字讓系結的 `rec` 名稱 `let` 可在其主體中使用。</span><span class="sxs-lookup"><span data-stu-id="37091-108">The `rec` keyword makes the name of the `let` binding available in its body.</span></span>

<span data-ttu-id="37091-109">下列範例顯示的遞迴函式，會使用數學定義來計算<sup>第</sup> *n*個斐的量值。</span><span class="sxs-lookup"><span data-stu-id="37091-109">The following example shows a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

```fsharp
let rec fib n =
    match n with
    | 0 | 1 -> 1
    | n -> fib (n-1) + fib (n-2)
```

> [!NOTE]
> <span data-ttu-id="37091-110">在實務上，上述範例之類的程式碼並不理想，因為它 unecessarily 已計算的旁邊值。</span><span class="sxs-lookup"><span data-stu-id="37091-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="37091-111">這是因為它不是 tail 遞迴，這會在本文中進一步說明。</span><span class="sxs-lookup"><span data-stu-id="37091-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="37091-112">方法會在其定義的類型內隱含遞迴，這表示不需要加入 `rec` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="37091-112">Methods are implicitly recursive within the type they are defined in, meaning there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="37091-113">例如：</span><span class="sxs-lookup"><span data-stu-id="37091-113">For example:</span></span>

```fsharp
type MyClass() =
    member this.Fib(n) =
        match n with
        | 0 | 1 -> 1
        | n -> this.Fib(n-1) + this.Fib(n-2)
```

<span data-ttu-id="37091-114">不過，在類別中的系結並非隱含遞迴。</span><span class="sxs-lookup"><span data-stu-id="37091-114">Let bindings within classes are not implicitly recursive, though.</span></span> <span data-ttu-id="37091-115">所有系結 `let` 函數都需要 `rec` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="37091-115">All `let`-bound functions require the `rec` keyword.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="37091-116">尾遞迴</span><span class="sxs-lookup"><span data-stu-id="37091-116">Tail recursion</span></span>

<span data-ttu-id="37091-117">針對某些遞迴函式，必須將更多「單純」定義重構為 [結尾遞迴](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion)的定義。</span><span class="sxs-lookup"><span data-stu-id="37091-117">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="37091-118">這可避免不必要的 recomputations。</span><span class="sxs-lookup"><span data-stu-id="37091-118">This prevents unnecessary recomputations.</span></span> <span data-ttu-id="37091-119">例如，您可以如下所示重新撰寫先前的量值產生器：</span><span class="sxs-lookup"><span data-stu-id="37091-119">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

<span data-ttu-id="37091-120">這是更複雜的執行。</span><span class="sxs-lookup"><span data-stu-id="37091-120">This is a more complicated implementation.</span></span> <span data-ttu-id="37091-121">產生數量詞是一種非常簡單的「一般」演算法的絕佳範例，但實際上並沒有效率。</span><span class="sxs-lookup"><span data-stu-id="37091-121">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="37091-122">在 F # 中，有幾個層面會讓它有效率，但仍會以遞迴方式定義：</span><span class="sxs-lookup"><span data-stu-id="37091-122">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="37091-123">名為的遞迴內建函式 `loop` ，它是慣用 F # 模式。</span><span class="sxs-lookup"><span data-stu-id="37091-123">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="37091-124">將累積值傳遞給遞迴呼叫的兩個累積參數。</span><span class="sxs-lookup"><span data-stu-id="37091-124">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="37091-125">檢查的值 `n` ，以傳回特定的累積。</span><span class="sxs-lookup"><span data-stu-id="37091-125">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="37091-126">如果此範例是使用迴圈反復寫入，則程式碼看起來會像是兩個不同的值累積數目，直到符合特定條件為止。</span><span class="sxs-lookup"><span data-stu-id="37091-126">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="37091-127">這是結尾遞迴的原因，是因為遞迴呼叫不需要在呼叫堆疊上儲存任何值。</span><span class="sxs-lookup"><span data-stu-id="37091-127">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="37091-128">所有計算的中繼值都會透過輸入至內建函式來累積。</span><span class="sxs-lookup"><span data-stu-id="37091-128">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="37091-129">這也可讓 F # 編譯器將程式碼優化，就像您撰寫迴圈一樣快 `while` 。</span><span class="sxs-lookup"><span data-stu-id="37091-129">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="37091-130">通常會撰寫 F # 程式碼，以遞迴方式處理具有內部和外部函式的某個內容，如先前範例所示。</span><span class="sxs-lookup"><span data-stu-id="37091-130">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="37091-131">內部函式會使用尾遞迴，而外部函式則是更好的呼叫端介面。</span><span class="sxs-lookup"><span data-stu-id="37091-131">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="37091-132">相互遞迴函數</span><span class="sxs-lookup"><span data-stu-id="37091-132">Mutually Recursive Functions</span></span>

<span data-ttu-id="37091-133">有時候函式是 *相互遞迴*的，這表示呼叫會形成圓形，其中一個函式會呼叫另一個函式，而後者會呼叫另一個函式，並在其間有任意數目的呼叫。</span><span class="sxs-lookup"><span data-stu-id="37091-133">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="37091-134">您必須在一個系結中一起定義這類函數 `let` ， `and` 並使用關鍵字將它們連結在一起。</span><span class="sxs-lookup"><span data-stu-id="37091-134">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="37091-135">下列範例顯示兩個互相遞迴的函式。</span><span class="sxs-lookup"><span data-stu-id="37091-135">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="recursive-values"></a><span data-ttu-id="37091-136">遞迴值</span><span class="sxs-lookup"><span data-stu-id="37091-136">Recursive values</span></span>

<span data-ttu-id="37091-137">您也可以將系結的 `let` 值定義為遞迴。</span><span class="sxs-lookup"><span data-stu-id="37091-137">You can also define a `let`-bound value to be recursive.</span></span> <span data-ttu-id="37091-138">這有時候是為了記錄而進行的。</span><span class="sxs-lookup"><span data-stu-id="37091-138">This is sometimes done for logging.</span></span> <span data-ttu-id="37091-139">使用 F # 5 和函式 `nameof` ，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="37091-139">With F# 5 and the `nameof` function, you can do this:</span></span>

```fsharp
let rec nameDoubles = nameof nameDoubles + nameof nameDoubles
```

## <a name="see-also"></a><span data-ttu-id="37091-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="37091-140">See also</span></span>

- [<span data-ttu-id="37091-141">函式</span><span class="sxs-lookup"><span data-stu-id="37091-141">Functions</span></span>](index.md)
