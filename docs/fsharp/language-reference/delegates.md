---
title: 委派 (F#)
description: '了解如何使用 F # 中的委派。'
ms.date: 05/16/2016
ms.openlocfilehash: be58997dffe8fcd949bbc2d47d86ffccc157d43e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45517085"
---
# <a name="delegates"></a><span data-ttu-id="f6063-103">委派</span><span class="sxs-lookup"><span data-stu-id="f6063-103">Delegates</span></span>

<span data-ttu-id="f6063-104">委派為物件，表示函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="f6063-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="f6063-105">在 F # 中，您通常應該使用函式值來表示函式做為第一級值;不過，委派會在.NET Framework 和您預期的 Api 與交互操作時，因此需要。</span><span class="sxs-lookup"><span data-stu-id="f6063-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="f6063-106">此外，它們也可能使用專為撰寫的程式庫會使用從其他.NET Framework 語言時。</span><span class="sxs-lookup"><span data-stu-id="f6063-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>

## <a name="syntax"></a><span data-ttu-id="f6063-107">語法</span><span class="sxs-lookup"><span data-stu-id="f6063-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="f6063-108">備註</span><span class="sxs-lookup"><span data-stu-id="f6063-108">Remarks</span></span>

<span data-ttu-id="f6063-109">在先前的語法`type1`表示的引數型別或型別和`type2`表示傳回型別。</span><span class="sxs-lookup"><span data-stu-id="f6063-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="f6063-110">引數類型表示的`type1`自動局部調用。</span><span class="sxs-lookup"><span data-stu-id="f6063-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="f6063-111">這可能表示，您會使用 tuple 形式，如果目標函式的引數局部調用，此類型與已在 tuple 形式的引數的括號括住 tuple。</span><span class="sxs-lookup"><span data-stu-id="f6063-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="f6063-112">自動調用移除一組括號，保留的元組引數，符合目標方法。</span><span class="sxs-lookup"><span data-stu-id="f6063-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="f6063-113">請參閱每個案例中，您應該使用的語法的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="f6063-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="f6063-114">委派可以附加至 F # 函式值，與靜態或執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="f6063-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="f6063-115">F # 函式值可以直接當做委派建構函式的引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="f6063-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="f6063-116">是靜態的方法中，您可以建構委派使用類別和方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6063-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="f6063-117">執行個體方法，為您提供的物件執行個體和一個引數中的方法。</span><span class="sxs-lookup"><span data-stu-id="f6063-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="f6063-118">在這兩種情況下，成員存取運算子 (`.`) 使用。</span><span class="sxs-lookup"><span data-stu-id="f6063-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="f6063-119">`Invoke`的委派類型的方法呼叫的封裝函式。</span><span class="sxs-lookup"><span data-stu-id="f6063-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="f6063-120">此外，委派可以藉由參考沒有括號的 Invoke 方法名稱傳遞為函式值。</span><span class="sxs-lookup"><span data-stu-id="f6063-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="f6063-121">下列程式碼顯示建立代表類別中的各種方法的委派的語法。</span><span class="sxs-lookup"><span data-stu-id="f6063-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="f6063-122">根據是否方法為靜態方法或執行個體方法，以及是否有 tuple 或局部調用的表單中的引數，宣告和指派委派的語法是有點不同。</span><span class="sxs-lookup"><span data-stu-id="f6063-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="f6063-123">下列程式碼顯示一些不同的方式，您可以使用委派。</span><span class="sxs-lookup"><span data-stu-id="f6063-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="f6063-124">上述程式碼範例的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="f6063-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="f6063-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6063-125">See also</span></span>

- [<span data-ttu-id="f6063-126">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="f6063-126">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="f6063-127">參數和引數</span><span class="sxs-lookup"><span data-stu-id="f6063-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="f6063-128">事件</span><span class="sxs-lookup"><span data-stu-id="f6063-128">Events</span></span>](members/events.md)
