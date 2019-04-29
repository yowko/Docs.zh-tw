---
title: 以統計方式解析的型別參數
description: 了解如何使用F#以統計方式解析的型別參數，它會取代在編譯時期而不是在執行階段的實際型別。
ms.date: 05/16/2016
ms.openlocfilehash: 9ad23a881e644dfe2bccd56fa04d3c219b51cf7d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937484"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="792a9-103">以統計方式解析的型別參數</span><span class="sxs-lookup"><span data-stu-id="792a9-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="792a9-104">A*以統計方式解析的型別參數*是型別參數，在編譯時期而不是在執行階段取代實際的型別。</span><span class="sxs-lookup"><span data-stu-id="792a9-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="792a9-105">它們前面附加的插入號 (^) 符號。</span><span class="sxs-lookup"><span data-stu-id="792a9-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="792a9-106">語法</span><span class="sxs-lookup"><span data-stu-id="792a9-106">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="792a9-107">備註</span><span class="sxs-lookup"><span data-stu-id="792a9-107">Remarks</span></span>

<span data-ttu-id="792a9-108">在F#語言中，有兩種不同的型別參數。</span><span class="sxs-lookup"><span data-stu-id="792a9-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="792a9-109">第一類是標準的泛型類型參數。</span><span class="sxs-lookup"><span data-stu-id="792a9-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="792a9-110">這些會以單引號 （'），如同`'T`和`'U`。</span><span class="sxs-lookup"><span data-stu-id="792a9-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="792a9-111">它們是相當於其他.NET Framework 語言中的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="792a9-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="792a9-112">其他類型是以統計方式解析和是插入號以符號表示，如同`^T`和`^U`。</span><span class="sxs-lookup"><span data-stu-id="792a9-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="792a9-113">以統計方式解析的型別參數是主要適用於搭配成員條件約束，也就是可讓您指定型別引數，必須擁有的特定成員，才能使用的條件約束。</span><span class="sxs-lookup"><span data-stu-id="792a9-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="792a9-114">沒有建立使用一般的泛型類型參數的條件約束的這類方法。</span><span class="sxs-lookup"><span data-stu-id="792a9-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="792a9-115">下表摘要說明這兩種型別參數之間的差異與相似之處。</span><span class="sxs-lookup"><span data-stu-id="792a9-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="792a9-116">功能</span><span class="sxs-lookup"><span data-stu-id="792a9-116">Feature</span></span>|<span data-ttu-id="792a9-117">泛型</span><span class="sxs-lookup"><span data-stu-id="792a9-117">Generic</span></span>|<span data-ttu-id="792a9-118">以統計方式解析</span><span class="sxs-lookup"><span data-stu-id="792a9-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="792a9-119">語法</span><span class="sxs-lookup"><span data-stu-id="792a9-119">Syntax</span></span>|<span data-ttu-id="792a9-120">`'T`、 `'U`</span><span class="sxs-lookup"><span data-stu-id="792a9-120">`'T`, `'U`</span></span>|<span data-ttu-id="792a9-121">`^T`、 `^U`</span><span class="sxs-lookup"><span data-stu-id="792a9-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="792a9-122">解決時間</span><span class="sxs-lookup"><span data-stu-id="792a9-122">Resolution time</span></span>|<span data-ttu-id="792a9-123">執行階段</span><span class="sxs-lookup"><span data-stu-id="792a9-123">Run time</span></span>|<span data-ttu-id="792a9-124">編譯時間</span><span class="sxs-lookup"><span data-stu-id="792a9-124">Compile time</span></span>|
|<span data-ttu-id="792a9-125">成員的條件約束</span><span class="sxs-lookup"><span data-stu-id="792a9-125">Member constraints</span></span>|<span data-ttu-id="792a9-126">無法搭配成員條件約束。</span><span class="sxs-lookup"><span data-stu-id="792a9-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="792a9-127">可以搭配成員條件約束。</span><span class="sxs-lookup"><span data-stu-id="792a9-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="792a9-128">程式碼產生</span><span class="sxs-lookup"><span data-stu-id="792a9-128">Code generation</span></span>|<span data-ttu-id="792a9-129">使用標準泛型型別參數的型別 （或方法） 會導致單一泛型類型或方法的產生。</span><span class="sxs-lookup"><span data-stu-id="792a9-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="792a9-130">產生的型別和方法的多個具現化，其中的每個型別。</span><span class="sxs-lookup"><span data-stu-id="792a9-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="792a9-131">使用類型</span><span class="sxs-lookup"><span data-stu-id="792a9-131">Use with types</span></span>|<span data-ttu-id="792a9-132">可用類型。</span><span class="sxs-lookup"><span data-stu-id="792a9-132">Can be used on types.</span></span>|<span data-ttu-id="792a9-133">無法在類型上使用。</span><span class="sxs-lookup"><span data-stu-id="792a9-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="792a9-134">使用內嵌函式</span><span class="sxs-lookup"><span data-stu-id="792a9-134">Use with inline functions</span></span>|<span data-ttu-id="792a9-135">否。</span><span class="sxs-lookup"><span data-stu-id="792a9-135">No.</span></span> <span data-ttu-id="792a9-136">無法參數化的內嵌函式，使用標準泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="792a9-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="792a9-137">可以。</span><span class="sxs-lookup"><span data-stu-id="792a9-137">Yes.</span></span> <span data-ttu-id="792a9-138">以統計方式解析的型別參數不能在函式或不是內嵌的方法。</span><span class="sxs-lookup"><span data-stu-id="792a9-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="792a9-139">許多F#核心程式庫函式，特別是運算子，有以統計方式解析型別參數。</span><span class="sxs-lookup"><span data-stu-id="792a9-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="792a9-140">這些函式和運算子會以內嵌方式，並導致數值計算的高效率的程式碼產生。</span><span class="sxs-lookup"><span data-stu-id="792a9-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="792a9-141">內嵌方法和函式，使用運算子，或使用其他函式，必須以統計方式解析型別參數，也可以使用以統計方式解析的型別參數本身。</span><span class="sxs-lookup"><span data-stu-id="792a9-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="792a9-142">通常，型別推斷會推斷這類的內嵌函式，以靜態方式解析型別參數。</span><span class="sxs-lookup"><span data-stu-id="792a9-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="792a9-143">下列範例說明被推斷為具有以統計方式解析的型別參數的運算子定義。</span><span class="sxs-lookup"><span data-stu-id="792a9-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="792a9-144">已解析的型別`(+@)`兩者的使用根據`(+)`和`(*)`，這兩個的這會導致類型推斷來推斷成員以統計方式解析的型別參數條件約束。</span><span class="sxs-lookup"><span data-stu-id="792a9-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="792a9-145">解析的型別，如下所示的F#的解譯器，如下所示。</span><span class="sxs-lookup"><span data-stu-id="792a9-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="792a9-146">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="792a9-146">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="792a9-147">開頭為F#4.1，您也可以以統計方式解析的型別參數簽章中指定的具象型別名稱。</span><span class="sxs-lookup"><span data-stu-id="792a9-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="792a9-148">在舊版的語言中，實際上無法由編譯器推斷的型別名稱，但無法實際指定簽章中。</span><span class="sxs-lookup"><span data-stu-id="792a9-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="792a9-149">從F#4.1，您也可以以統計方式解析的型別參數簽章中指定的具象型別名稱。</span><span class="sxs-lookup"><span data-stu-id="792a9-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="792a9-150">以下為範例：</span><span class="sxs-lookup"><span data-stu-id="792a9-150">Here's an example:</span></span>

```fsharp
let inline konst x _ = x

type CFunctor() = 
    static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
    static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

    // default implementation of replace
    static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

    // call overridden replace if present
    static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
        ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a><span data-ttu-id="792a9-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="792a9-151">See also</span></span>

- [<span data-ttu-id="792a9-152">泛型</span><span class="sxs-lookup"><span data-stu-id="792a9-152">Generics</span></span>](index.md)
- [<span data-ttu-id="792a9-153">類型推斷</span><span class="sxs-lookup"><span data-stu-id="792a9-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="792a9-154">自動一般化</span><span class="sxs-lookup"><span data-stu-id="792a9-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="792a9-155">條件約束</span><span class="sxs-lookup"><span data-stu-id="792a9-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="792a9-156">內嵌函式</span><span class="sxs-lookup"><span data-stu-id="792a9-156">Inline Functions</span></span>](../functions/inline-functions.md)