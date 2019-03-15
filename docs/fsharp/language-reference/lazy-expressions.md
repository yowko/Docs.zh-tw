---
title: 延遲的運算式
description: 了解如何F#延遲運算式可以改善您的應用程式和程式庫的效能。
ms.date: 03/13/2019
ms.openlocfilehash: 6d53d53093f4e93f53e1c956b94e2f1e4a1bbd55
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57853320"
---
# <a name="lazy-expressions"></a><span data-ttu-id="8eaec-103">延遲的運算式</span><span class="sxs-lookup"><span data-stu-id="8eaec-103">Lazy Expressions</span></span>

<span data-ttu-id="8eaec-104">*延遲運算式*是不會立即進行評估，但改為會在需要結果時所評估的運算式。</span><span class="sxs-lookup"><span data-stu-id="8eaec-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="8eaec-105">這可協助改善您的程式碼的效能。</span><span class="sxs-lookup"><span data-stu-id="8eaec-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="8eaec-106">語法</span><span class="sxs-lookup"><span data-stu-id="8eaec-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="8eaec-107">備註</span><span class="sxs-lookup"><span data-stu-id="8eaec-107">Remarks</span></span>

<span data-ttu-id="8eaec-108">在先前語法中，*運算式*是結果為必要項時，才會評估的程式碼並*識別碼*是將結果儲存的值。</span><span class="sxs-lookup"><span data-stu-id="8eaec-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="8eaec-109">值為類型[ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489)，其中的實際型別用於`'T`會從運算式的結果來決定。</span><span class="sxs-lookup"><span data-stu-id="8eaec-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="8eaec-110">延遲的運算式可讓您藉由限制執行的運算式結果所需的情況來改善效能。</span><span class="sxs-lookup"><span data-stu-id="8eaec-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="8eaec-111">若要強制執行的運算式，您可以呼叫方法`Force`。</span><span class="sxs-lookup"><span data-stu-id="8eaec-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="8eaec-112">`Force` 會導致執行一次只能執行。</span><span class="sxs-lookup"><span data-stu-id="8eaec-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="8eaec-113">後續呼叫`Force`傳回相同結果，但不是執行任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="8eaec-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="8eaec-114">下列程式碼說明如何使用消極式運算式以及使用`Force`。</span><span class="sxs-lookup"><span data-stu-id="8eaec-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="8eaec-115">在此程式碼的型別`result`已`Lazy<int>`，而`Force`方法會傳回`int`。</span><span class="sxs-lookup"><span data-stu-id="8eaec-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="8eaec-116">延遲評估，而非`Lazy`類型，也可用於序列。</span><span class="sxs-lookup"><span data-stu-id="8eaec-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="8eaec-117">如需詳細資訊，請參閱 <<c0> [ 序列](sequences.md)。</span><span class="sxs-lookup"><span data-stu-id="8eaec-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8eaec-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8eaec-118">See also</span></span>

- [<span data-ttu-id="8eaec-119">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="8eaec-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="8eaec-120">LazyExtensions 模組</span><span class="sxs-lookup"><span data-stu-id="8eaec-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
