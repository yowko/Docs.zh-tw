---
title: 委派
description: 瞭解如何在中F#使用委派。
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630364"
---
# <a name="delegates"></a><span data-ttu-id="c5bd5-103">委派</span><span class="sxs-lookup"><span data-stu-id="c5bd5-103">Delegates</span></span>

<span data-ttu-id="c5bd5-104">委派代表當做物件的函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="c5bd5-105">在F#中, 您通常應該使用函式值來將函式表示為第一類的值;不過, 委派會在 .NET Framework 中使用, 因此當您與預期它們的 Api 互通時, 需要用到。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="c5bd5-106">撰寫專供其他 .NET Framework 語言使用的程式庫時, 也可能會使用它們。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>

## <a name="syntax"></a><span data-ttu-id="c5bd5-107">語法</span><span class="sxs-lookup"><span data-stu-id="c5bd5-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="c5bd5-108">備註</span><span class="sxs-lookup"><span data-stu-id="c5bd5-108">Remarks</span></span>

<span data-ttu-id="c5bd5-109">在先前的語法中`type1` , 代表引數類型或類型`type2` , 而表示傳回類型。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="c5bd5-110">所表示`type1`的引數類型會自動進行擴充。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="c5bd5-111">這表示針對此類型, 如果目標函式的引數是已擴充的, 而且已經在元組表單中的引數有括弧的元組, 您就可以使用元組表單。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="c5bd5-112">自動 currying 會移除一組括弧, 並保留符合目標方法的元組引數。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="c5bd5-113">請參閱程式碼範例, 以瞭解您在每個案例中應該使用的語法。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="c5bd5-114">委派可以附加至F#函數值, 以及靜態或實例方法。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="c5bd5-115">F#函數值可以直接當做引數傳遞至委派的函式。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="c5bd5-116">若為靜態方法, 您可以使用類別的名稱和方法來建立委派。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="c5bd5-117">若為實例方法, 您可以在一個引數中提供物件實例和方法。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="c5bd5-118">在這兩種情況下, 都會使用`.`成員存取運算子 ()。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="c5bd5-119">委派`Invoke`類型上的方法會呼叫封裝的函式。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="c5bd5-120">此外, 委派可以藉由參考不含括弧的叫用方法名稱, 以函式值的方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="c5bd5-121">下列程式碼顯示用來建立委派的語法, 代表類別中的各種方法。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="c5bd5-122">根據該方法是靜態方法或實例方法, 以及它在元組形式或擴充形式中是否有引數, 宣告和指派委派的語法稍有不同。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="c5bd5-123">下列程式碼顯示一些您可以使用委派的不同方式。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="c5bd5-124">先前程式碼範例的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c5bd5-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="c5bd5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5bd5-125">See also</span></span>

- [<span data-ttu-id="c5bd5-126">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="c5bd5-126">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c5bd5-127">參數和引數</span><span class="sxs-lookup"><span data-stu-id="c5bd5-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="c5bd5-128">事件</span><span class="sxs-lookup"><span data-stu-id="c5bd5-128">Events</span></span>](./members/events.md)
