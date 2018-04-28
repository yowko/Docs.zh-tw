---
title: 條件運算式：if... then...else (F#)
description: '了解如何撰寫 F # 執行程式碼的不同分支中的條件式運算式。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bfb985f09be91034894e1d3eba88cebef6bb3fd4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="10aaa-103">條件運算式： `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="10aaa-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="10aaa-104">`if...then...else`運算式執行不同的分支程式碼，也會評估為不同的值，根據給定的布林運算式。</span><span class="sxs-lookup"><span data-stu-id="10aaa-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>


## <a name="syntax"></a><span data-ttu-id="10aaa-105">語法</span><span class="sxs-lookup"><span data-stu-id="10aaa-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="10aaa-106">備註</span><span class="sxs-lookup"><span data-stu-id="10aaa-106">Remarks</span></span>
<span data-ttu-id="10aaa-107">在先前的語法， *expression1*時評估為的布林運算式執行`true`，否則*expression2*執行。</span><span class="sxs-lookup"><span data-stu-id="10aaa-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="10aaa-108">不同於其他語言，`if...then...else`建構是一個運算式，而不是陳述式。</span><span class="sxs-lookup"><span data-stu-id="10aaa-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="10aaa-109">也就是說，它會產生的值，這是在執行的分支中的最後一個運算式的值。</span><span class="sxs-lookup"><span data-stu-id="10aaa-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="10aaa-110">產生每個分支中的值的類型必須相符。</span><span class="sxs-lookup"><span data-stu-id="10aaa-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="10aaa-111">如果沒有任何明確`else`分支中，它的類型是`unit`。</span><span class="sxs-lookup"><span data-stu-id="10aaa-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="10aaa-112">因此，如果類型`then`分支不是任何類型`unit`，必須要有`else`分支與相同的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="10aaa-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="10aaa-113">當鏈結`if...then...else`運算式組合在一起，您可以使用關鍵字`elif`而不是`else if`; 它們相等。</span><span class="sxs-lookup"><span data-stu-id="10aaa-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="10aaa-114">範例</span><span class="sxs-lookup"><span data-stu-id="10aaa-114">Example</span></span>
<span data-ttu-id="10aaa-115">下列範例說明如何使用`if...then...else`運算式。</span><span class="sxs-lookup"><span data-stu-id="10aaa-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="10aaa-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10aaa-116">See Also</span></span>
[<span data-ttu-id="10aaa-117">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="10aaa-117">F# Language Reference</span></span>](index.md)

