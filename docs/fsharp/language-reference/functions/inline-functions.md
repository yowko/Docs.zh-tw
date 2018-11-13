---
title: 內嵌函式 (F#)
description: 了解如何使用 F# 內嵌函式會直接整合至呼叫端程式碼。
ms.date: 05/16/2016
ms.openlocfilehash: 47fca0fe34630792aeb0908b0cee02a927e2567d
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "45745941"
---
# <a name="inline-functions"></a><span data-ttu-id="02728-103">內嵌函式</span><span class="sxs-lookup"><span data-stu-id="02728-103">Inline Functions</span></span>

<span data-ttu-id="02728-104">*內嵌函式*是會直接整合至呼叫端程式碼的函式。</span><span class="sxs-lookup"><span data-stu-id="02728-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>

## <a name="using-inline-functions"></a><span data-ttu-id="02728-105">使用內嵌函式</span><span class="sxs-lookup"><span data-stu-id="02728-105">Using Inline Functions</span></span>

<span data-ttu-id="02728-106">當您使用靜態型別參數時，則為型別參數所參數化的任何函式必須是內嵌。</span><span class="sxs-lookup"><span data-stu-id="02728-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="02728-107">這可確保編譯器可以解決這些型別參數。</span><span class="sxs-lookup"><span data-stu-id="02728-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="02728-108">當您使用一般的泛型型別參數時，但也沒有任何這類限制。</span><span class="sxs-lookup"><span data-stu-id="02728-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="02728-109">不會啟用之成員的條件約束，內嵌函式能幫助您最佳化程式碼。</span><span class="sxs-lookup"><span data-stu-id="02728-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="02728-110">不過，過度使用的內嵌函式可能會導致您的程式碼，是較能抵抗編譯器最佳化和程式庫函式的實作中的變更。</span><span class="sxs-lookup"><span data-stu-id="02728-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="02728-111">基於這個理由，您應該避免使用內嵌函式的最佳化，除非您已試過所有其他的最佳化技術。</span><span class="sxs-lookup"><span data-stu-id="02728-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="02728-112">進行內嵌的函式或方法有時可以改善效能，但這不一定如此。</span><span class="sxs-lookup"><span data-stu-id="02728-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="02728-113">因此，您也應該使用的效能度量來驗證，讓任何指定的函式內嵌事實上有正面的影響。</span><span class="sxs-lookup"><span data-stu-id="02728-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="02728-114">`inline`修飾詞可以套用至函式的最上層，在模組層級或類別中的方法層級。</span><span class="sxs-lookup"><span data-stu-id="02728-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="02728-115">下列程式碼範例說明在最高層級、 內嵌執行個體方法和內嵌的靜態方法的內嵌函式。</span><span class="sxs-lookup"><span data-stu-id="02728-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="02728-116">內嵌函式和型別推斷</span><span class="sxs-lookup"><span data-stu-id="02728-116">Inline Functions and Type Inference</span></span>

<span data-ttu-id="02728-117">是否存在`inline`影響型別推斷。</span><span class="sxs-lookup"><span data-stu-id="02728-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="02728-118">這是因為內嵌函式可以以統計方式解析型別參數，而非內嵌函式不能。</span><span class="sxs-lookup"><span data-stu-id="02728-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="02728-119">下列程式碼範例所示的範例位置`inline`很有用，因為您使用具有以統計方式解析的類型參數的函式`float`轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="02728-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="02728-120">不含`inline`修飾詞，型別推斷會強制函式，在此情況下採用特定的型別， `int`。</span><span class="sxs-lookup"><span data-stu-id="02728-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="02728-121">但`inline`修飾詞，此函式也推斷為具有以統計方式解析的型別參數。</span><span class="sxs-lookup"><span data-stu-id="02728-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="02728-122">使用`inline`修飾詞，型別推斷為下列：</span><span class="sxs-lookup"><span data-stu-id="02728-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="02728-123">這表示函式會接受任何支援的轉換的型別**浮點數**。</span><span class="sxs-lookup"><span data-stu-id="02728-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>

## <a name="see-also"></a><span data-ttu-id="02728-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02728-124">See also</span></span>

- [<span data-ttu-id="02728-125">函式</span><span class="sxs-lookup"><span data-stu-id="02728-125">Functions</span></span>](index.md)
- [<span data-ttu-id="02728-126">條件約束</span><span class="sxs-lookup"><span data-stu-id="02728-126">Constraints</span></span>](../generics/constraints.md)
- [<span data-ttu-id="02728-127">以統計方式解析的類型參數</span><span class="sxs-lookup"><span data-stu-id="02728-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
