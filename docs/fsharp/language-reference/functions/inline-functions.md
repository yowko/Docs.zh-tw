---
title: "內嵌函式 (F#)"
description: "了解如何使用 F # 內嵌函式，會直接整合至呼叫的程式碼。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3fa31178-08f8-463d-9d41-d29220a90027
ms.openlocfilehash: 8293a73e9468d3bc3eb51cd99860e52c48121ae3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="inline-functions"></a><span data-ttu-id="c7678-104">內嵌函式</span><span class="sxs-lookup"><span data-stu-id="c7678-104">Inline Functions</span></span>

<span data-ttu-id="c7678-105">*內嵌函式*會直接整合呼叫程式碼的函式。</span><span class="sxs-lookup"><span data-stu-id="c7678-105">*Inline functions* are functions that are integrated directly into the calling code.</span></span>


## <a name="using-inline-functions"></a><span data-ttu-id="c7678-106">使用內嵌函式</span><span class="sxs-lookup"><span data-stu-id="c7678-106">Using Inline Functions</span></span>
<span data-ttu-id="c7678-107">當您使用靜態型別參數時，會參數化的型別參數的任何函式必須是內嵌。</span><span class="sxs-lookup"><span data-stu-id="c7678-107">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="c7678-108">這可確保編譯器可以解決這些型別參數。</span><span class="sxs-lookup"><span data-stu-id="c7678-108">This guarantees that that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="c7678-109">當您使用一般的泛型型別參數時，沒有任何這類限制。</span><span class="sxs-lookup"><span data-stu-id="c7678-109">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="c7678-110">不能使用成員條件約束，內嵌函式可以在最佳化程式碼很有幫助。</span><span class="sxs-lookup"><span data-stu-id="c7678-110">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="c7678-111">不過，內嵌函式的過度使用，可能會造成較不能抵抗編譯器最佳化和程式庫函式的實作中變更您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c7678-111">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="c7678-112">基於這個理由，您應該避免使用內嵌函式的最佳化，除非您已嘗試所有其他的最佳化技術。</span><span class="sxs-lookup"><span data-stu-id="c7678-112">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="c7678-113">進行函式或方法的內嵌有時可以改善效能，但是並非永遠案例。</span><span class="sxs-lookup"><span data-stu-id="c7678-113">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="c7678-114">因此，您也應該使用的效能度量來驗證，讓任何指定的函式內嵌事實上有正面的影響。</span><span class="sxs-lookup"><span data-stu-id="c7678-114">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="c7678-115">`inline`修飾詞可以套用至函式的最上層，在模組層級，或類別中方法層級。</span><span class="sxs-lookup"><span data-stu-id="c7678-115">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="c7678-116">下列程式碼範例說明在最上層、 內嵌執行個體方法和內嵌的靜態方法的內嵌函式。</span><span class="sxs-lookup"><span data-stu-id="c7678-116">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="c7678-117">內嵌函式和類型推斷</span><span class="sxs-lookup"><span data-stu-id="c7678-117">Inline Functions and Type Inference</span></span>
<span data-ttu-id="c7678-118">與否`inline`影響型別推斷。</span><span class="sxs-lookup"><span data-stu-id="c7678-118">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="c7678-119">這是因為內嵌函式可以以統計方式解析型別參數，而非內嵌函式不能。</span><span class="sxs-lookup"><span data-stu-id="c7678-119">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="c7678-120">下列程式碼範例示範案例其中`inline`很有用，因為您使用的函式具有以統計方式解析的型別參數，`float`轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="c7678-120">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="c7678-121">不含`inline`修飾詞，型別推斷會強制函式，以在此情況下接受特定型別， `int`。</span><span class="sxs-lookup"><span data-stu-id="c7678-121">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="c7678-122">但`inline`修飾詞，此函式也被推斷為具有以統計方式解析的型別參數。</span><span class="sxs-lookup"><span data-stu-id="c7678-122">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="c7678-123">與`inline`修飾詞，類型就會推斷是如下所示：</span><span class="sxs-lookup"><span data-stu-id="c7678-123">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="c7678-124">這表示函式接受任何類型的支援轉換成**float**。</span><span class="sxs-lookup"><span data-stu-id="c7678-124">This means that the function accepts any type that supports a conversion to **float**.</span></span>


## <a name="see-also"></a><span data-ttu-id="c7678-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7678-125">See Also</span></span>
[<span data-ttu-id="c7678-126">函式</span><span class="sxs-lookup"><span data-stu-id="c7678-126">Functions</span></span>](index.md)

[<span data-ttu-id="c7678-127">條件約束</span><span class="sxs-lookup"><span data-stu-id="c7678-127">Constraints</span></span>](../generics/constraints.md)

[<span data-ttu-id="c7678-128">以統計方式解析的類型參數</span><span class="sxs-lookup"><span data-stu-id="c7678-128">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
