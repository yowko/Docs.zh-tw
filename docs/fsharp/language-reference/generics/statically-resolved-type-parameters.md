---
title: 以統計方式解析的型別參數 (F#)
description: '了解如何使用 F # 以統計方式解析的型別參數，在編譯時期而不是在執行階段取代實際的類型。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: da730014f1c40b6c79d72e4f46a18ef36f50de36
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="ce47c-103">以統計方式解析的型別參數</span><span class="sxs-lookup"><span data-stu-id="ce47c-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="ce47c-104">A*以統計方式解析的型別參數*是型別參數，在編譯時期而不是在執行階段取代實際的類型。</span><span class="sxs-lookup"><span data-stu-id="ce47c-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="ce47c-105">它們前面附加插入號 (^) 符號。</span><span class="sxs-lookup"><span data-stu-id="ce47c-105">They are preceded by a caret (^) symbol.</span></span>


## <a name="syntax"></a><span data-ttu-id="ce47c-106">語法</span><span class="sxs-lookup"><span data-stu-id="ce47c-106">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="ce47c-107">備註</span><span class="sxs-lookup"><span data-stu-id="ce47c-107">Remarks</span></span>
<span data-ttu-id="ce47c-108">在 F # 語言中，有兩種不同的型別參數。</span><span class="sxs-lookup"><span data-stu-id="ce47c-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="ce47c-109">第一類是標準的泛型類型參數。</span><span class="sxs-lookup"><span data-stu-id="ce47c-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="ce47c-110">這些以單引號 （'），像是`'T`和`'U`。</span><span class="sxs-lookup"><span data-stu-id="ce47c-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="ce47c-111">它們是相當於其他.NET Framework 語言中的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="ce47c-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="ce47c-112">其他種類會以統計方式解析，且在插入號符號，指示`^T`和`^U`。</span><span class="sxs-lookup"><span data-stu-id="ce47c-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="ce47c-113">以統計方式解析的型別參數是主要適用於搭配成員條件約束時，也就是讓您指定型別引數，必須擁有特定成員，才能加以使用的條件約束。</span><span class="sxs-lookup"><span data-stu-id="ce47c-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="ce47c-114">沒有任何方法來建立這種條件約束使用一般的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="ce47c-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="ce47c-115">下表摘要說明兩種型別參數之間的差異與相似之處。</span><span class="sxs-lookup"><span data-stu-id="ce47c-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="ce47c-116">功能</span><span class="sxs-lookup"><span data-stu-id="ce47c-116">Feature</span></span>|<span data-ttu-id="ce47c-117">泛型</span><span class="sxs-lookup"><span data-stu-id="ce47c-117">Generic</span></span>|<span data-ttu-id="ce47c-118">以統計方式解析</span><span class="sxs-lookup"><span data-stu-id="ce47c-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="ce47c-119">語法</span><span class="sxs-lookup"><span data-stu-id="ce47c-119">Syntax</span></span>|<span data-ttu-id="ce47c-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="ce47c-120">`'T`, `'U`</span></span>|<span data-ttu-id="ce47c-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="ce47c-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="ce47c-122">解決時間</span><span class="sxs-lookup"><span data-stu-id="ce47c-122">Resolution time</span></span>|<span data-ttu-id="ce47c-123">執行階段</span><span class="sxs-lookup"><span data-stu-id="ce47c-123">Run time</span></span>|<span data-ttu-id="ce47c-124">編譯時間</span><span class="sxs-lookup"><span data-stu-id="ce47c-124">Compile time</span></span>|
|<span data-ttu-id="ce47c-125">成員條件約束</span><span class="sxs-lookup"><span data-stu-id="ce47c-125">Member constraints</span></span>|<span data-ttu-id="ce47c-126">不能與成員條件約束。</span><span class="sxs-lookup"><span data-stu-id="ce47c-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="ce47c-127">可以搭配成員條件約束。</span><span class="sxs-lookup"><span data-stu-id="ce47c-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="ce47c-128">程式碼產生</span><span class="sxs-lookup"><span data-stu-id="ce47c-128">Code generation</span></span>|<span data-ttu-id="ce47c-129">使用標準的泛型型別參數的型別 （或方法） 產生的單一泛型類型或方法。</span><span class="sxs-lookup"><span data-stu-id="ce47c-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="ce47c-130">產生的型別和方法的多個具現化，每個輸入的需要。</span><span class="sxs-lookup"><span data-stu-id="ce47c-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="ce47c-131">使用類型</span><span class="sxs-lookup"><span data-stu-id="ce47c-131">Use with types</span></span>|<span data-ttu-id="ce47c-132">可以用於型別。</span><span class="sxs-lookup"><span data-stu-id="ce47c-132">Can be used on types.</span></span>|<span data-ttu-id="ce47c-133">無法在類型上使用。</span><span class="sxs-lookup"><span data-stu-id="ce47c-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="ce47c-134">使用內嵌函式</span><span class="sxs-lookup"><span data-stu-id="ce47c-134">Use with inline functions</span></span>|<span data-ttu-id="ce47c-135">否。</span><span class="sxs-lookup"><span data-stu-id="ce47c-135">No.</span></span> <span data-ttu-id="ce47c-136">內嵌函式不能參數化，使用標準的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="ce47c-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="ce47c-137">可以。</span><span class="sxs-lookup"><span data-stu-id="ce47c-137">Yes.</span></span> <span data-ttu-id="ce47c-138">以統計方式解析的型別參數不能在函式或不是內嵌的方法。</span><span class="sxs-lookup"><span data-stu-id="ce47c-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="ce47c-139">許多 F # 核心程式庫函數，特別是運算子，具有以統計方式解析型別參數。</span><span class="sxs-lookup"><span data-stu-id="ce47c-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="ce47c-140">這些函數和運算子會以內嵌方式，並造成數值計算的有效率的程式碼產生。</span><span class="sxs-lookup"><span data-stu-id="ce47c-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="ce47c-141">內嵌方法和函式使用運算子，或具有以統計方式解析型別參數，其他函式也可以使用本身以統計方式解析的型別參數。</span><span class="sxs-lookup"><span data-stu-id="ce47c-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="ce47c-142">通常，型別推斷會推斷這類內嵌函式具有以統計方式解析型別參數。</span><span class="sxs-lookup"><span data-stu-id="ce47c-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="ce47c-143">下列範例說明被推斷為具有以統計方式解析的型別參數的運算子定義。</span><span class="sxs-lookup"><span data-stu-id="ce47c-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="ce47c-144">已解析的型別`(+@)`兩者的使用根據`(+)`和`(*)`，這兩個的而導致推斷成員以統計方式解析的型別參數條件約束的型別推斷。</span><span class="sxs-lookup"><span data-stu-id="ce47c-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="ce47c-145">解析的型別，如所示，F # 解譯器，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ce47c-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="ce47c-146">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="ce47c-146">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="ce47c-147">從 F # 4.1 開始，您也可以指定具象型別名稱以統計方式解析的型別參數簽章中。</span><span class="sxs-lookup"><span data-stu-id="ce47c-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="ce47c-148">在舊版的語言中，型別名稱實際上無法由編譯器所推斷，但無法實際指定簽章中。</span><span class="sxs-lookup"><span data-stu-id="ce47c-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="ce47c-149">為準，F # 4.1，您也可以以統計方式解析的型別參數簽章中指定的具象型別名稱。</span><span class="sxs-lookup"><span data-stu-id="ce47c-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="ce47c-150">以下為範例：</span><span class="sxs-lookup"><span data-stu-id="ce47c-150">Here's an example:</span></span>

```fsharp
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

## <a name="see-also"></a><span data-ttu-id="ce47c-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce47c-151">See Also</span></span>
[<span data-ttu-id="ce47c-152">泛型</span><span class="sxs-lookup"><span data-stu-id="ce47c-152">Generics</span></span>](index.md)

[<span data-ttu-id="ce47c-153">類型推斷</span><span class="sxs-lookup"><span data-stu-id="ce47c-153">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="ce47c-154">自動一般化</span><span class="sxs-lookup"><span data-stu-id="ce47c-154">Automatic Generalization</span></span>](automatic-generalization.md)

[<span data-ttu-id="ce47c-155">條件約束</span><span class="sxs-lookup"><span data-stu-id="ce47c-155">Constraints</span></span>](constraints.md)

[<span data-ttu-id="ce47c-156">內嵌函式</span><span class="sxs-lookup"><span data-stu-id="ce47c-156">Inline Functions</span></span>](../functions/inline-functions.md)
