---
title: 內嵌函式
description: 瞭解如何使用F#直接整合到呼叫程式碼中的內嵌函式。
ms.date: 05/16/2016
ms.openlocfilehash: 2830d1ada5b3005c3fcae975a44e85a7c84554f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630673"
---
# <a name="inline-functions"></a><span data-ttu-id="6e900-103">內嵌函式</span><span class="sxs-lookup"><span data-stu-id="6e900-103">Inline Functions</span></span>

<span data-ttu-id="6e900-104">*內嵌*函式是直接整合到呼叫程式碼中的函式。</span><span class="sxs-lookup"><span data-stu-id="6e900-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>

## <a name="using-inline-functions"></a><span data-ttu-id="6e900-105">使用內嵌函數</span><span class="sxs-lookup"><span data-stu-id="6e900-105">Using Inline Functions</span></span>

<span data-ttu-id="6e900-106">當您使用靜態類型參數時, 以類型參數參數化的任何函式都必須是內嵌的。</span><span class="sxs-lookup"><span data-stu-id="6e900-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="6e900-107">這可保證編譯器可以解析這些型別參數。</span><span class="sxs-lookup"><span data-stu-id="6e900-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="6e900-108">當您使用一般泛型型別參數時, 沒有這類限制。</span><span class="sxs-lookup"><span data-stu-id="6e900-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="6e900-109">除了啟用成員條件約束以外, 內嵌函數也有助於優化程式碼。</span><span class="sxs-lookup"><span data-stu-id="6e900-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="6e900-110">不過, 過度利用內嵌函式可能會導致您的程式碼較不能抵抗編譯器優化和程式庫函式的變更。</span><span class="sxs-lookup"><span data-stu-id="6e900-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="6e900-111">基於這個理由, 您應該避免使用內嵌函式進行優化, 除非您已經嘗試過所有其他的優化技術。</span><span class="sxs-lookup"><span data-stu-id="6e900-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="6e900-112">讓函式或方法內嵌的作業有時可以改善效能, 但不一定都是如此。</span><span class="sxs-lookup"><span data-stu-id="6e900-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="6e900-113">因此, 您也應該使用效能測量來確認讓任何指定的函式內嵌確實具有正面的效果。</span><span class="sxs-lookup"><span data-stu-id="6e900-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="6e900-114">`inline`修飾詞可以套用至最上層的函式、模組層級, 或類別中的方法層級。</span><span class="sxs-lookup"><span data-stu-id="6e900-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="6e900-115">下列程式碼範例說明最上層的內嵌函式、內嵌實例方法, 以及內嵌的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="6e900-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="6e900-116">內嵌函式和型別推斷</span><span class="sxs-lookup"><span data-stu-id="6e900-116">Inline Functions and Type Inference</span></span>

<span data-ttu-id="6e900-117">的存在`inline`會影響型別推斷。</span><span class="sxs-lookup"><span data-stu-id="6e900-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="6e900-118">這是因為內嵌函式可以有靜態解析的類型參數, 而非內嵌函數則不能。</span><span class="sxs-lookup"><span data-stu-id="6e900-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="6e900-119">下列`inline`程式碼範例顯示的案例很有用`float` , 因為您使用的函式具有靜態解析的類型參數, 也就是轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="6e900-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="6e900-120">如果沒有`int`修飾詞, 型別推斷會強制函式採用特定的型別, 在此案例中為。 `inline`</span><span class="sxs-lookup"><span data-stu-id="6e900-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="6e900-121">但是使用`inline`修飾詞時, 函式也會推斷為具有靜態解析的類型參數。</span><span class="sxs-lookup"><span data-stu-id="6e900-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="6e900-122">`inline`使用修飾詞時, 會推斷型別, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="6e900-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="6e900-123">這表示函式會接受任何支援轉換成**float**的類型。</span><span class="sxs-lookup"><span data-stu-id="6e900-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e900-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e900-124">See also</span></span>

- [<span data-ttu-id="6e900-125">函式</span><span class="sxs-lookup"><span data-stu-id="6e900-125">Functions</span></span>](index.md)
- [<span data-ttu-id="6e900-126">條件約束</span><span class="sxs-lookup"><span data-stu-id="6e900-126">Constraints</span></span>](../generics/constraints.md)
- [<span data-ttu-id="6e900-127">以統計方式解析的類型參數</span><span class="sxs-lookup"><span data-stu-id="6e900-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
