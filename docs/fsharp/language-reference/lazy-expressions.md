---
title: 延遲運算式
description: 瞭解延遲F#運算式如何改善應用程式和程式庫的效能。
ms.date: 03/13/2019
ms.openlocfilehash: 97429e9a4c3838cbaa2ead197db4443e0820e8b3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630746"
---
# <a name="lazy-expressions"></a><span data-ttu-id="42002-103">延遲運算式</span><span class="sxs-lookup"><span data-stu-id="42002-103">Lazy Expressions</span></span>

<span data-ttu-id="42002-104">*延遲運算式*是不會立即評估的運算式, 而是在需要結果時進行評估。</span><span class="sxs-lookup"><span data-stu-id="42002-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="42002-105">這有助於改善程式碼的效能。</span><span class="sxs-lookup"><span data-stu-id="42002-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="42002-106">語法</span><span class="sxs-lookup"><span data-stu-id="42002-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="42002-107">備註</span><span class="sxs-lookup"><span data-stu-id="42002-107">Remarks</span></span>

<span data-ttu-id="42002-108">在先前的語法中, *expression*是只在需要結果時才會評估的程式碼, 而*identifier*則是儲存結果的值。</span><span class="sxs-lookup"><span data-stu-id="42002-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="42002-109">值的型[`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489)別為, 其中`'T`用於的實際型別是從運算式的結果決定。</span><span class="sxs-lookup"><span data-stu-id="42002-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="42002-110">延遲運算式可讓您藉由將運算式的執行限制為只需要結果的情況, 來改善效能。</span><span class="sxs-lookup"><span data-stu-id="42002-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="42002-111">若要強制執行運算式, 請呼叫方法`Force`。</span><span class="sxs-lookup"><span data-stu-id="42002-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="42002-112">`Force`導致執行只執行一次。</span><span class="sxs-lookup"><span data-stu-id="42002-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="42002-113">後續呼叫`Force`會傳回相同的結果, 但不會執行任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="42002-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="42002-114">下列程式碼說明如何使用延遲運算式和使用`Force`。</span><span class="sxs-lookup"><span data-stu-id="42002-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="42002-115">在此`result`程式碼中, 的型`Lazy<int>`別是, `Force` `int`而方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="42002-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="42002-116">延遲評估 (但不`Lazy`是類型) 也會用於序列。</span><span class="sxs-lookup"><span data-stu-id="42002-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="42002-117">如需詳細資訊, 請參閱[序列](sequences.md)。</span><span class="sxs-lookup"><span data-stu-id="42002-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42002-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42002-118">See also</span></span>

- [<span data-ttu-id="42002-119">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="42002-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="42002-120">LazyExtensions 模組</span><span class="sxs-lookup"><span data-stu-id="42002-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
