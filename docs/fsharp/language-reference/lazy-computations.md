---
title: 延遲運算 (F#)
description: '了解 F # 延遲運算如何改善您的應用程式和程式庫的效能。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 72dc5a14a845b52ae2512314d730516ca0cf4b9d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="lazy-computations"></a><span data-ttu-id="aa0de-103">延遲運算</span><span class="sxs-lookup"><span data-stu-id="aa0de-103">Lazy Computations</span></span>

<span data-ttu-id="aa0de-104">*延遲運算*是指不會立即進行評估，但會改為評估需要結果時。</span><span class="sxs-lookup"><span data-stu-id="aa0de-104">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="aa0de-105">這可協助改善您的程式碼的效能。</span><span class="sxs-lookup"><span data-stu-id="aa0de-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa0de-106">語法</span><span class="sxs-lookup"><span data-stu-id="aa0de-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="aa0de-107">備註</span><span class="sxs-lookup"><span data-stu-id="aa0de-107">Remarks</span></span>

<span data-ttu-id="aa0de-108">在先前的語法，*運算式*是程式碼，只有當結果為必要項，會評估和*識別碼*是將結果儲存的值。</span><span class="sxs-lookup"><span data-stu-id="aa0de-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="aa0de-109">值為類型[ `Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489)其中的實際型別、 用於`'T`取決於運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="aa0de-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="aa0de-110">延遲運算可讓您藉由限制的計算結果都需要這些情況下執行改善效能。</span><span class="sxs-lookup"><span data-stu-id="aa0de-110">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="aa0de-111">若要強制執行計算，您可以呼叫方法`Force`。</span><span class="sxs-lookup"><span data-stu-id="aa0de-111">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="aa0de-112">`Force` 會執行一次只能執行。</span><span class="sxs-lookup"><span data-stu-id="aa0de-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="aa0de-113">後續呼叫`Force`傳回相同結果，但不是執行任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="aa0de-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="aa0de-114">下列程式碼說明如何使用延遲的計算，以及使用`Force`。</span><span class="sxs-lookup"><span data-stu-id="aa0de-114">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="aa0de-115">在此程式碼的型別`result`是`Lazy<int>`，而`Force`方法會傳回`int`。</span><span class="sxs-lookup"><span data-stu-id="aa0de-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="aa0de-116">延遲評估，但不是`Lazy`類型，也會使用序列 (sequence)。</span><span class="sxs-lookup"><span data-stu-id="aa0de-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="aa0de-117">如需詳細資訊，請參閱[序列](sequences.md)。</span><span class="sxs-lookup"><span data-stu-id="aa0de-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa0de-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa0de-118">See Also</span></span>

[<span data-ttu-id="aa0de-119">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="aa0de-119">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="aa0de-120">LazyExtensions 模組</span><span class="sxs-lookup"><span data-stu-id="aa0de-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
