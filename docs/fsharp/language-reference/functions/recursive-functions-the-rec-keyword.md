---
title: 遞迴函式：rec 關鍵字
description: "瞭解 F # ' rec ' 關鍵字如何與 ' let ' 關鍵字搭配使用，以定義遞迴函數。"
ms.date: 05/16/2016
ms.openlocfilehash: c9a3b7dc27f4ed86948a08b7783d7e8e8b60e57f
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2020
ms.locfileid: "87426972"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="633c1-103">遞迴函式：rec 關鍵字</span><span class="sxs-lookup"><span data-stu-id="633c1-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="633c1-104">`rec`關鍵字會與關鍵字搭配使用 `let` ，以定義遞迴函數。</span><span class="sxs-lookup"><span data-stu-id="633c1-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="633c1-105">語法</span><span class="sxs-lookup"><span data-stu-id="633c1-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="633c1-106">備註</span><span class="sxs-lookup"><span data-stu-id="633c1-106">Remarks</span></span>

<span data-ttu-id="633c1-107">遞迴函式（呼叫本身的函數）會在 F # 語言中明確識別。</span><span class="sxs-lookup"><span data-stu-id="633c1-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="633c1-108">這會讓在函式的範圍中定義的識別碼可供使用。</span><span class="sxs-lookup"><span data-stu-id="633c1-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="633c1-109">下列程式碼說明遞迴函式，該函式會使用數學定義來計算<sup>第</sup> *n*個斐的量值。</span><span class="sxs-lookup"><span data-stu-id="633c1-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="633c1-110">實際上，如同前一個範例的程式碼並不理想，因為它 unecessarily 了已計算的旁邊值。</span><span class="sxs-lookup"><span data-stu-id="633c1-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="633c1-111">這是因為它不是尾遞迴，這會在本文中進一步說明。</span><span class="sxs-lookup"><span data-stu-id="633c1-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="633c1-112">方法在型別內隱含遞迴;不需要新增 `rec` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="633c1-112">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="633c1-113">類別內的 Let 系結不會隱含遞迴。</span><span class="sxs-lookup"><span data-stu-id="633c1-113">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="633c1-114">尾遞迴</span><span class="sxs-lookup"><span data-stu-id="633c1-114">Tail recursion</span></span>

<span data-ttu-id="633c1-115">針對某些遞迴函式，必須將更多的「純」定義重構為[尾遞迴](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion)。</span><span class="sxs-lookup"><span data-stu-id="633c1-115">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="633c1-116">這可防止不必要 recomputations。</span><span class="sxs-lookup"><span data-stu-id="633c1-116">This prevents unecessary recomputations.</span></span> <span data-ttu-id="633c1-117">例如，先前的斐數列數位產生器可以重寫如下：</span><span class="sxs-lookup"><span data-stu-id="633c1-117">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

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

<span data-ttu-id="633c1-118">這是比較複雜的實作為。</span><span class="sxs-lookup"><span data-stu-id="633c1-118">This is a more complicated implementation.</span></span> <span data-ttu-id="633c1-119">產生一個大波的數位，是一種「單純」演算法的絕佳範例，其實是以數學方式來表示，但實際上沒有效率。</span><span class="sxs-lookup"><span data-stu-id="633c1-119">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="633c1-120">有幾個層面讓它在 F # 中有效率，同時仍然以遞迴方式定義：</span><span class="sxs-lookup"><span data-stu-id="633c1-120">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="633c1-121">名為的遞迴內部函 `loop` 式，這是慣用 F # 模式。</span><span class="sxs-lookup"><span data-stu-id="633c1-121">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="633c1-122">兩個累計參數，會將累積的值傳遞給遞迴呼叫。</span><span class="sxs-lookup"><span data-stu-id="633c1-122">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="633c1-123">檢查的值 `n` ，以傳回特定的累積。</span><span class="sxs-lookup"><span data-stu-id="633c1-123">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="633c1-124">如果這個範例是以迴圈反復撰寫，則程式碼看起來會類似兩個不同的值累積數位，直到符合特定條件為止。</span><span class="sxs-lookup"><span data-stu-id="633c1-124">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="633c1-125">這是尾遞迴的原因是因為遞迴呼叫不需要在呼叫堆疊上儲存任何值。</span><span class="sxs-lookup"><span data-stu-id="633c1-125">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="633c1-126">所有要計算的中繼值都會透過內建函式的輸入進行累計。</span><span class="sxs-lookup"><span data-stu-id="633c1-126">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="633c1-127">這也可讓 F # 編譯器將程式碼優化，就像您撰寫像是迴圈一樣快速 `while` 。</span><span class="sxs-lookup"><span data-stu-id="633c1-127">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="633c1-128">撰寫 F # 程式碼通常會以遞迴方式處理具有內部和外部函式的某個專案，如先前範例所示。</span><span class="sxs-lookup"><span data-stu-id="633c1-128">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="633c1-129">內部函式會使用尾遞迴，而外部函式則具有較佳的呼叫端介面。</span><span class="sxs-lookup"><span data-stu-id="633c1-129">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="633c1-130">相互遞迴函式</span><span class="sxs-lookup"><span data-stu-id="633c1-130">Mutually Recursive Functions</span></span>

<span data-ttu-id="633c1-131">有時候函式是*互斥*的，這表示呼叫會形成圓形，其中一個函式會呼叫另一個函式，然後呼叫第一個函式，而其間的呼叫數目則為。</span><span class="sxs-lookup"><span data-stu-id="633c1-131">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="633c1-132">您必須在一個系結中定義這類函式 `let` ， `and` 並使用關鍵字將它們連結在一起。</span><span class="sxs-lookup"><span data-stu-id="633c1-132">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="633c1-133">下列範例顯示兩個相互遞迴的函式。</span><span class="sxs-lookup"><span data-stu-id="633c1-133">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="633c1-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="633c1-134">See also</span></span>

- [<span data-ttu-id="633c1-135">函式</span><span class="sxs-lookup"><span data-stu-id="633c1-135">Functions</span></span>](index.md)
