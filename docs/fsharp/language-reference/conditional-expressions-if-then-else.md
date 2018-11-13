---
title: 條件運算式：if... then...else (F#)
description: 了解如何撰寫 F# 來執行的程式碼的不同分支中的條件運算式。
ms.date: 05/16/2016
ms.openlocfilehash: 10e4224bef772f00520cf5a0fff2f2920147c2fc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "44177597"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="baaca-103">條件運算式： `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="baaca-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="baaca-104">`if...then...else`運算式執行的程式碼的不同分支，也會評估為不同的值，根據指定的布林運算式。</span><span class="sxs-lookup"><span data-stu-id="baaca-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="baaca-105">語法</span><span class="sxs-lookup"><span data-stu-id="baaca-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="baaca-106">備註</span><span class="sxs-lookup"><span data-stu-id="baaca-106">Remarks</span></span>

<span data-ttu-id="baaca-107">在先前的語法*expression1*時，則為 True 的運算式評估為執行`true`; 否則*expression2*執行。</span><span class="sxs-lookup"><span data-stu-id="baaca-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="baaca-108">不同於其他語言，`if...then...else`建構是運算式，不是陳述式。</span><span class="sxs-lookup"><span data-stu-id="baaca-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="baaca-109">也就是說，它會產生一個值，也就是執行的分支中的最後一個運算式的值。</span><span class="sxs-lookup"><span data-stu-id="baaca-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="baaca-110">產生每個分支中的值的類型必須相符。</span><span class="sxs-lookup"><span data-stu-id="baaca-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="baaca-111">如果沒有任何明確`else`分支，其型別是`unit`。</span><span class="sxs-lookup"><span data-stu-id="baaca-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="baaca-112">因此，如果的型別`then`分支是任何型別以外`unit`，必須要有`else`分支並具有相同的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="baaca-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="baaca-113">當鏈結`if...then...else`運算式在一起，您可以使用關鍵字`elif`而不是`else if`; 它們相等。</span><span class="sxs-lookup"><span data-stu-id="baaca-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="baaca-114">範例</span><span class="sxs-lookup"><span data-stu-id="baaca-114">Example</span></span>

<span data-ttu-id="baaca-115">下列範例說明如何使用`if...then...else`運算式。</span><span class="sxs-lookup"><span data-stu-id="baaca-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="baaca-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baaca-116">See also</span></span>

- [<span data-ttu-id="baaca-117">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="baaca-117">F# Language Reference</span></span>](index.md)
