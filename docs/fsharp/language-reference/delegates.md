---
title: 委派 (F#)
description: '了解如何使用 F # 中的委派。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 56520cc631d889f390a7d4300be1cb3185306be9
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="delegates"></a><span data-ttu-id="79e83-103">委派</span><span class="sxs-lookup"><span data-stu-id="79e83-103">Delegates</span></span>

<span data-ttu-id="79e83-104">委派以物件表示函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="79e83-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="79e83-105">在 F # 中，您通常應該使用函式值來表示函式做為第一級值;不過，委派會使用.NET Framework 中，而且當您希望他們的應用程式開發介面與交互操作時，因此需要。</span><span class="sxs-lookup"><span data-stu-id="79e83-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="79e83-106">此外，它們也可能使用時撰寫的程式庫針對使用其他.NET Framework 語言。</span><span class="sxs-lookup"><span data-stu-id="79e83-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>


## <a name="syntax"></a><span data-ttu-id="79e83-107">語法</span><span class="sxs-lookup"><span data-stu-id="79e83-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="79e83-108">備註</span><span class="sxs-lookup"><span data-stu-id="79e83-108">Remarks</span></span>
<span data-ttu-id="79e83-109">在先前的語法，`type1`表示的引數類型和`type2`表示的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="79e83-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="79e83-110">引數型別以表示`type1`自動局部調用。</span><span class="sxs-lookup"><span data-stu-id="79e83-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="79e83-111">這可能表示，此類型局部調用目標函式的引數，如果您使用了 tuple 表單和括號括住 tuple 已 tuple 形式的引數。</span><span class="sxs-lookup"><span data-stu-id="79e83-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="79e83-112">自動對移除一組括號，讓符合目標方法的 tuple 引數。</span><span class="sxs-lookup"><span data-stu-id="79e83-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="79e83-113">請參閱程式碼範例，您應該在每個案例中使用的語法。</span><span class="sxs-lookup"><span data-stu-id="79e83-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="79e83-114">委派可以附加至 F # 函式值，與靜態或執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="79e83-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="79e83-115">F # 函式值可以直接做為委派建構函式引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="79e83-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="79e83-116">對於靜態方法，您可以建構委派使用類別和方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="79e83-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="79e83-117">執行個體方法，為您提供的物件執行個體和一個引數中的方法。</span><span class="sxs-lookup"><span data-stu-id="79e83-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="79e83-118">在這兩種情況下，成員存取運算子 (`.`) 使用。</span><span class="sxs-lookup"><span data-stu-id="79e83-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="79e83-119">`Invoke`委派型別上的方法會呼叫封裝函式。</span><span class="sxs-lookup"><span data-stu-id="79e83-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="79e83-120">此外，委派可以藉由參考沒有括號叫用方法名稱傳遞做為函式值。</span><span class="sxs-lookup"><span data-stu-id="79e83-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="79e83-121">下列程式碼顯示的語法建立代表類別中的各種方法的委派。</span><span class="sxs-lookup"><span data-stu-id="79e83-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="79e83-122">根據是否方法為靜態方法或執行個體方法，以及是否有 tuple 或局部調用的表單中的引數，宣告並指派委派的語法會稍有不同。</span><span class="sxs-lookup"><span data-stu-id="79e83-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="79e83-123">下列程式碼顯示一些不同的方式，您可以使用委派。</span><span class="sxs-lookup"><span data-stu-id="79e83-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="79e83-124">上述程式碼範例的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="79e83-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="79e83-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79e83-125">See Also</span></span>
[<span data-ttu-id="79e83-126">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="79e83-126">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="79e83-127">參數和引數</span><span class="sxs-lookup"><span data-stu-id="79e83-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="79e83-128">事件</span><span class="sxs-lookup"><span data-stu-id="79e83-128">Events</span></span>](members/events.md)
