---
title: "彈性類型 (F#)"
description: "了解如何使用 F # 彈性類型註釋，用於指出參數、 變數或值都有類型與指定的型別相容。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c8b510f2-3405-4cc9-b55b-e47b35e2b15b
ms.openlocfilehash: 7c5e4eb97791b9c6c56fe2847755866e8240e038
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2017
---
# <a name="flexible-types"></a><span data-ttu-id="eaeaf-104">彈性類型</span><span class="sxs-lookup"><span data-stu-id="eaeaf-104">Flexible Types</span></span>

<span data-ttu-id="eaeaf-105">A*彈性類型註釋*表示參數、 變數或值具有相容的類型使用指定的型別，其中的相容性由類別或介面的物件導向的階層中的位置。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-105">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="eaeaf-106">彈性類型適合，特別是當時不會發生自動轉換為型別階層架構中較高的類型，但您仍然想要啟用您要使用的階層架構中任何類型或實作介面的任何類型的功能。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-106">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="eaeaf-107">語法</span><span class="sxs-lookup"><span data-stu-id="eaeaf-107">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="eaeaf-108">備註</span><span class="sxs-lookup"><span data-stu-id="eaeaf-108">Remarks</span></span>

<span data-ttu-id="eaeaf-109">在先前的語法，*類型*表示基底類型或介面。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-109">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="eaeaf-110">彈性類型相當於泛型類型條件約束，以限制所允許的類型與基底或介面類型相容的類型。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-110">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="eaeaf-111">也就是下列兩行程式碼是相等的。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-111">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="eaeaf-112">彈性類型可用於數種類型的情況。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-112">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="eaeaf-113">例如，當您有較高順序函式 （使用做為引數的函式的函式），通常很有用的彈性的型別傳回的函式。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-113">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="eaeaf-114">在下列範例中，使用彈性的型別中有順序引數與`iterate2`啟用較高順序函式處理順序、 陣列、 清單和任何其他可列舉型別所產生的函式。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-114">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="eaeaf-115">請考慮下列兩個函式，其中的序列傳回，其中另傳回彈性的型別。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-115">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="eaeaf-116">另舉一例，請考慮[Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712)程式庫函式：</span><span class="sxs-lookup"><span data-stu-id="eaeaf-116">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="eaeaf-117">您可以傳遞任何下列的可列舉順序的這個函式：</span><span class="sxs-lookup"><span data-stu-id="eaeaf-117">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="eaeaf-118">清單的清單</span><span class="sxs-lookup"><span data-stu-id="eaeaf-118">A list of lists</span></span>
- <span data-ttu-id="eaeaf-119">陣列的清單</span><span class="sxs-lookup"><span data-stu-id="eaeaf-119">A list of arrays</span></span>
- <span data-ttu-id="eaeaf-120">陣列的清單</span><span class="sxs-lookup"><span data-stu-id="eaeaf-120">An array of lists</span></span>
- <span data-ttu-id="eaeaf-121">陣列的順序</span><span class="sxs-lookup"><span data-stu-id="eaeaf-121">An array of sequences</span></span>
- <span data-ttu-id="eaeaf-122">任何其他組合的可列舉的序列</span><span class="sxs-lookup"><span data-stu-id="eaeaf-122">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="eaeaf-123">下列程式碼會使用`Seq.concat`示範您可以透過使用彈性類型支援的案例。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-123">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="eaeaf-124">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-124">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="eaeaf-125">在 F # 中，如同其他物件導向語言中，有在其中衍生型別或實作介面的型別會自動轉換成基底類型或介面類型的內容。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-125">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="eaeaf-126">直接引數中，則不在型別是在次級的位置，一部分的更複雜的類型，例如函式類型的傳回型別或型別引數時，就會發生這些自動轉換。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-126">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="eaeaf-127">因此，彈性的型別標記法時，主要是要套用至它的類型是複雜類型的一部分。</span><span class="sxs-lookup"><span data-stu-id="eaeaf-127">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="eaeaf-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaeaf-128">See Also</span></span>

[<span data-ttu-id="eaeaf-129">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="eaeaf-129">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="eaeaf-130">泛型</span><span class="sxs-lookup"><span data-stu-id="eaeaf-130">Generics</span></span>](generics/index.md)
