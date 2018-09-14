---
title: 彈性類型 (F#)
description: '了解如何使用 F # 彈性類型註解，這表示參數、 變數或值具有與指定的型別相容的類型。'
ms.date: 05/16/2016
ms.openlocfilehash: b6c97c3cc19f15b2c8db74b2c55660a16b2858f7
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615556"
---
# <a name="flexible-types"></a><span data-ttu-id="cbae0-103">彈性類型</span><span class="sxs-lookup"><span data-stu-id="cbae0-103">Flexible Types</span></span>

<span data-ttu-id="cbae0-104">A*彈性類型註解*表示參數、 變數或值具有相容類型使用指定的型別，其中的相容性由類別或介面的物件導向階層中的位置。</span><span class="sxs-lookup"><span data-stu-id="cbae0-104">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="cbae0-105">彈性類型很有用，特別是當時不會發生自動轉換為型別階層架構中較高的類型，但您仍想要啟用您使用階層中的任何型別或實作介面的任何類型的功能。</span><span class="sxs-lookup"><span data-stu-id="cbae0-105">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="cbae0-106">語法</span><span class="sxs-lookup"><span data-stu-id="cbae0-106">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="cbae0-107">備註</span><span class="sxs-lookup"><span data-stu-id="cbae0-107">Remarks</span></span>

<span data-ttu-id="cbae0-108">在先前的語法*型別*表示基底類型或介面。</span><span class="sxs-lookup"><span data-stu-id="cbae0-108">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="cbae0-109">彈性類型相當於泛型型別具有條件約束，以限制允許的類型與基底或介面類型相容的類型。</span><span class="sxs-lookup"><span data-stu-id="cbae0-109">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="cbae0-110">也就是下列兩行程式碼是相等的。</span><span class="sxs-lookup"><span data-stu-id="cbae0-110">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="cbae0-111">彈性類型可用於數種類型的情況。</span><span class="sxs-lookup"><span data-stu-id="cbae0-111">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="cbae0-112">比方說，當您有較高順序函式 （接受做為引數的函式的函式） 時，通常很有用的函式傳回具彈性的類型。</span><span class="sxs-lookup"><span data-stu-id="cbae0-112">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="cbae0-113">在下列範例中，使用彈性的型別中有順序引數與`iterate2`可讓要產生序列、 陣列、 清單和任何其他可列舉類型的函式所使用的較高順序函式。</span><span class="sxs-lookup"><span data-stu-id="cbae0-113">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="cbae0-114">請考慮下列兩個函式，其中的序列傳回，其中另傳回具彈性的類型。</span><span class="sxs-lookup"><span data-stu-id="cbae0-114">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="cbae0-115">另舉一例，請考慮[Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712)程式庫函式：</span><span class="sxs-lookup"><span data-stu-id="cbae0-115">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="cbae0-116">您可以傳遞任何下列的可列舉序列，此函式：</span><span class="sxs-lookup"><span data-stu-id="cbae0-116">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="cbae0-117">一份清單</span><span class="sxs-lookup"><span data-stu-id="cbae0-117">A list of lists</span></span>
- <span data-ttu-id="cbae0-118">陣列清單</span><span class="sxs-lookup"><span data-stu-id="cbae0-118">A list of arrays</span></span>
- <span data-ttu-id="cbae0-119">清單陣列</span><span class="sxs-lookup"><span data-stu-id="cbae0-119">An array of lists</span></span>
- <span data-ttu-id="cbae0-120">陣列的序列</span><span class="sxs-lookup"><span data-stu-id="cbae0-120">An array of sequences</span></span>
- <span data-ttu-id="cbae0-121">可列舉序列的任何其他組合</span><span class="sxs-lookup"><span data-stu-id="cbae0-121">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="cbae0-122">下列程式碼會使用`Seq.concat`示範您可以使用彈性類型支援的案例。</span><span class="sxs-lookup"><span data-stu-id="cbae0-122">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="cbae0-123">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="cbae0-123">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="cbae0-124">在 F # 中，如同其他物件導向語言中，有在其中衍生型別或實作介面的型別會自動轉換成基底類型或介面類型的內容。</span><span class="sxs-lookup"><span data-stu-id="cbae0-124">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="cbae0-125">直接的引數中，而不是當類型是在次級的位置，做為一部分的更複雜的類型，例如函式類型，傳回型別或型別引數的時候，就會發生這些自動轉換。</span><span class="sxs-lookup"><span data-stu-id="cbae0-125">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="cbae0-126">因此，彈性的型別標記法時，主要是您會將它套用至型別是更複雜類型的組件。</span><span class="sxs-lookup"><span data-stu-id="cbae0-126">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbae0-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbae0-127">See also</span></span>

- [<span data-ttu-id="cbae0-128">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="cbae0-128">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="cbae0-129">泛型</span><span class="sxs-lookup"><span data-stu-id="cbae0-129">Generics</span></span>](generics/index.md)
