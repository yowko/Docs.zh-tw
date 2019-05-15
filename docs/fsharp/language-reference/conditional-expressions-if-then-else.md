---
title: 條件運算式： if...then...else
description: 了解如何撰寫條件運算式F#若要執行的程式碼的不同分支。
ms.date: 05/16/2016
ms.openlocfilehash: db2d5ce5b75ecda171f2623c986878dcee1cf4d9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641983"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="70790-103">條件運算式： `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="70790-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="70790-104">`if...then...else`運算式執行的程式碼的不同分支，也會評估為不同的值，根據指定的布林運算式。</span><span class="sxs-lookup"><span data-stu-id="70790-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="70790-105">語法</span><span class="sxs-lookup"><span data-stu-id="70790-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="70790-106">備註</span><span class="sxs-lookup"><span data-stu-id="70790-106">Remarks</span></span>

<span data-ttu-id="70790-107">在先前的語法*expression1*時，則為 True 的運算式評估為執行`true`; 否則*expression2*執行。</span><span class="sxs-lookup"><span data-stu-id="70790-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="70790-108">不同於其他語言，`if...then...else`建構是運算式，不是陳述式。</span><span class="sxs-lookup"><span data-stu-id="70790-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="70790-109">也就是說，它會產生一個值，也就是執行的分支中的最後一個運算式的值。</span><span class="sxs-lookup"><span data-stu-id="70790-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="70790-110">產生每個分支中的值的類型必須相符。</span><span class="sxs-lookup"><span data-stu-id="70790-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="70790-111">如果沒有任何明確`else`分支，其型別是`unit`。</span><span class="sxs-lookup"><span data-stu-id="70790-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="70790-112">因此，如果的型別`then`分支是任何型別以外`unit`，必須要有`else`分支並具有相同的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="70790-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="70790-113">當鏈結`if...then...else`運算式在一起，您可以使用關鍵字`elif`而不是`else if`; 它們相等。</span><span class="sxs-lookup"><span data-stu-id="70790-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="70790-114">範例</span><span class="sxs-lookup"><span data-stu-id="70790-114">Example</span></span>

<span data-ttu-id="70790-115">下列範例說明如何使用`if...then...else`運算式。</span><span class="sxs-lookup"><span data-stu-id="70790-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="70790-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70790-116">See also</span></span>

- [<span data-ttu-id="70790-117">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="70790-117">F# Language Reference</span></span>](index.md)
