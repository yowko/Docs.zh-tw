---
title: 延遲運算式
description: '瞭解 F # 延遲運算式如何改善應用程式和程式庫的效能。'
ms.date: 08/15/2020
ms.openlocfilehash: 71c466ca3b74c9e92b81a3c268e07438ec944905
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558084"
---
# <a name="lazy-expressions"></a><span data-ttu-id="6c6db-103">延遲運算式</span><span class="sxs-lookup"><span data-stu-id="6c6db-103">Lazy Expressions</span></span>

<span data-ttu-id="6c6db-104">*延遲運算式* 是不會立即評估的運算式，而是在需要結果時進行評估。</span><span class="sxs-lookup"><span data-stu-id="6c6db-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="6c6db-105">這有助於提升程式碼的效能。</span><span class="sxs-lookup"><span data-stu-id="6c6db-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="6c6db-106">語法</span><span class="sxs-lookup"><span data-stu-id="6c6db-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="6c6db-107">備註</span><span class="sxs-lookup"><span data-stu-id="6c6db-107">Remarks</span></span>

<span data-ttu-id="6c6db-108">在先前的語法中， *expression* 是只有在需要結果時才會評估的程式碼，而 *identifier* 是儲存結果的值。</span><span class="sxs-lookup"><span data-stu-id="6c6db-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="6c6db-109">值的型別為 [`Lazy<'T>`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazy-1-0.html) ，其中使用的實際型別取決於 `'T` 運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="6c6db-109">The value is of type [`Lazy<'T>`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazy-1-0.html), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="6c6db-110">延遲運算式可讓您藉由將運算式的執行限制在需要結果的情況下，來改善效能。</span><span class="sxs-lookup"><span data-stu-id="6c6db-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="6c6db-111">若要強制執行運算式，您可以呼叫方法 `Force` 。</span><span class="sxs-lookup"><span data-stu-id="6c6db-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="6c6db-112">`Force` 只會執行一次執行。</span><span class="sxs-lookup"><span data-stu-id="6c6db-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="6c6db-113">後續呼叫 `Force` 會傳回相同的結果，但不會執行任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="6c6db-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="6c6db-114">下列程式碼說明如何使用 lazy 運算式和使用 `Force` 。</span><span class="sxs-lookup"><span data-stu-id="6c6db-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="6c6db-115">在此程式碼中，的型別 `result` 為 `Lazy<int>` ，而且方法會傳回 `Force` `int` 。</span><span class="sxs-lookup"><span data-stu-id="6c6db-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="6c6db-116">延遲評估（但不 `Lazy` 是類型）也用於序列。</span><span class="sxs-lookup"><span data-stu-id="6c6db-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="6c6db-117">如需詳細資訊，請參閱 [序列](sequences.md)。</span><span class="sxs-lookup"><span data-stu-id="6c6db-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c6db-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c6db-118">See also</span></span>

- [<span data-ttu-id="6c6db-119">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="6c6db-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="6c6db-120">LazyExtensions 模組</span><span class="sxs-lookup"><span data-stu-id="6c6db-120">LazyExtensions module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
