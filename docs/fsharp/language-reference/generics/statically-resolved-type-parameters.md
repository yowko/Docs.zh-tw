---
title: 以統計方式解析的型別參數
description: 瞭解如何使用F#靜態解析的類型參數（在編譯時期以實際類型取代，而不是在執行時間）。
ms.date: 05/16/2016
ms.openlocfilehash: bc3310192cdaa5ae4862b8aee46b6152f61da38a
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082918"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="8e1ff-103">以統計方式解析的型別參數</span><span class="sxs-lookup"><span data-stu-id="8e1ff-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="8e1ff-104">*靜態解析的類型參數*是在編譯時期（而不是在執行時間）取代為實際類型的類型參數。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="8e1ff-105">它們前面會加上插入號（^）符號。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="8e1ff-106">語法</span><span class="sxs-lookup"><span data-stu-id="8e1ff-106">Syntax</span></span>

```fsharp
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="8e1ff-107">備註</span><span class="sxs-lookup"><span data-stu-id="8e1ff-107">Remarks</span></span>

<span data-ttu-id="8e1ff-108">在F#語言中，有兩種不同類型的型別參數。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="8e1ff-109">第一種是標準的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="8e1ff-110">這些會以單引號（'）表示，如同`'T`和。 `'U`</span><span class="sxs-lookup"><span data-stu-id="8e1ff-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="8e1ff-111">它們相當於其他 .NET Framework 語言中的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="8e1ff-112">另一種方法是以靜態方式解析，並以插入號符號表示`^T` ， `^U`如同和。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="8e1ff-113">靜態解析的類型參數主要適用于結合成員條件約束，這是條件約束，可讓您指定類型引數必須有特定成員或成員，才能使用。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="8e1ff-114">您無法使用一般泛型型別參數來建立這種條件約束。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="8e1ff-115">下表摘要說明兩種類型參數之間的相似性和差異。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="8e1ff-116">功能</span><span class="sxs-lookup"><span data-stu-id="8e1ff-116">Feature</span></span>|<span data-ttu-id="8e1ff-117">泛型</span><span class="sxs-lookup"><span data-stu-id="8e1ff-117">Generic</span></span>|<span data-ttu-id="8e1ff-118">靜態解析</span><span class="sxs-lookup"><span data-stu-id="8e1ff-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="8e1ff-119">語法</span><span class="sxs-lookup"><span data-stu-id="8e1ff-119">Syntax</span></span>|<span data-ttu-id="8e1ff-120">`'T`、 `'U`</span><span class="sxs-lookup"><span data-stu-id="8e1ff-120">`'T`, `'U`</span></span>|<span data-ttu-id="8e1ff-121">`^T`、 `^U`</span><span class="sxs-lookup"><span data-stu-id="8e1ff-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="8e1ff-122">解決時間</span><span class="sxs-lookup"><span data-stu-id="8e1ff-122">Resolution time</span></span>|<span data-ttu-id="8e1ff-123">執行階段</span><span class="sxs-lookup"><span data-stu-id="8e1ff-123">Run time</span></span>|<span data-ttu-id="8e1ff-124">編譯時間</span><span class="sxs-lookup"><span data-stu-id="8e1ff-124">Compile time</span></span>|
|<span data-ttu-id="8e1ff-125">成員條件約束</span><span class="sxs-lookup"><span data-stu-id="8e1ff-125">Member constraints</span></span>|<span data-ttu-id="8e1ff-126">不能與成員條件約束搭配使用。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="8e1ff-127">可以與成員條件約束搭配使用。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="8e1ff-128">程式碼產生</span><span class="sxs-lookup"><span data-stu-id="8e1ff-128">Code generation</span></span>|<span data-ttu-id="8e1ff-129">具有標準泛型型別參數的類型（或方法）會產生單一泛型型別或方法。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="8e1ff-130">會產生類型和方法的多個具現化，每個所需的類型各一個。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="8e1ff-131">搭配類型使用</span><span class="sxs-lookup"><span data-stu-id="8e1ff-131">Use with types</span></span>|<span data-ttu-id="8e1ff-132">可以用於類型。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-132">Can be used on types.</span></span>|<span data-ttu-id="8e1ff-133">不能用在類型上。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="8e1ff-134">搭配內嵌函數使用</span><span class="sxs-lookup"><span data-stu-id="8e1ff-134">Use with inline functions</span></span>|<span data-ttu-id="8e1ff-135">資料分割</span><span class="sxs-lookup"><span data-stu-id="8e1ff-135">No.</span></span> <span data-ttu-id="8e1ff-136">內嵌函式不能以標準泛型型別參數參數化。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="8e1ff-137">是的。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-137">Yes.</span></span> <span data-ttu-id="8e1ff-138">靜態解析的類型參數不能用於非內嵌的函式或方法。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="8e1ff-139">許多F#核心程式庫函式（尤其是運算子）都有靜態解析的類型參數。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="8e1ff-140">這些函式和運算子是內嵌的，可讓您以有效率的方式產生數值計算的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="8e1ff-141">使用運算子的內嵌方法和函式，或使用其他具有靜態解析類型參數的函式，也可以使用靜態解析的類型參數本身。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="8e1ff-142">通常，型別推斷會推斷這類內嵌函式，使其具有靜態解析的型別參數。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="8e1ff-143">下列範例說明的運算子定義，會推斷為具有靜態解析的類型參數。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="8e1ff-144">已解決的型`(+@)`別是以`(+)`和`(*)`的使用為基礎，這兩者都會導致型別推斷在靜態解析的型別參數上推斷成員條件約束。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="8e1ff-145">如F#解譯器所示，已解析的類型如下。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="8e1ff-146">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-146">The output is as follows.</span></span>

```console
2
1.500000
```

<span data-ttu-id="8e1ff-147">從F# 4.1 開始，您也可以在以靜態方式解析的類型參數簽章中指定具體的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="8e1ff-148">在舊版的語言中，編譯器實際上可以推斷類型名稱，但實際上無法在簽章中指定。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="8e1ff-149">從 4.1 F# ，您也可以在以靜態方式解析的類型參數簽章中指定具體的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="8e1ff-150">以下為範例：</span><span class="sxs-lookup"><span data-stu-id="8e1ff-150">Here's an example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8e1ff-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e1ff-151">See also</span></span>

- [<span data-ttu-id="8e1ff-152">泛型</span><span class="sxs-lookup"><span data-stu-id="8e1ff-152">Generics</span></span>](index.md)
- [<span data-ttu-id="8e1ff-153">類型推斷</span><span class="sxs-lookup"><span data-stu-id="8e1ff-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="8e1ff-154">自動一般化</span><span class="sxs-lookup"><span data-stu-id="8e1ff-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="8e1ff-155">條件約束</span><span class="sxs-lookup"><span data-stu-id="8e1ff-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="8e1ff-156">內嵌函式</span><span class="sxs-lookup"><span data-stu-id="8e1ff-156">Inline Functions</span></span>](../functions/inline-functions.md)
