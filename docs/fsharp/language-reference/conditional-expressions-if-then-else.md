---
title: '條件運算式: if .。。然後 .。。東西'
description: 瞭解如何在中F#撰寫條件運算式, 以執行程式碼的不同分支。
ms.date: 05/16/2016
ms.openlocfilehash: 825149bf296eded3cc2b4d8847ba4d82bea40cdc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630388"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="91d08-103">條件運算式:`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="91d08-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="91d08-104">`if...then...else`運算式會執行不同的程式碼分支, 也會根據指定的布林運算式, 評估為不同的值。</span><span class="sxs-lookup"><span data-stu-id="91d08-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="91d08-105">語法</span><span class="sxs-lookup"><span data-stu-id="91d08-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="91d08-106">備註</span><span class="sxs-lookup"><span data-stu-id="91d08-106">Remarks</span></span>

<span data-ttu-id="91d08-107">在先前的語法中,*運算式*會在布林運算式評估為`true`時執行, 否則會執行*運算式*2。</span><span class="sxs-lookup"><span data-stu-id="91d08-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="91d08-108">不同于其他語言, `if...then...else`結構是運算式, 而不是語句。</span><span class="sxs-lookup"><span data-stu-id="91d08-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="91d08-109">這表示它會產生值, 這是執行之分支中最後一個運算式的值。</span><span class="sxs-lookup"><span data-stu-id="91d08-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="91d08-110">每個分支中產生的數值型別必須相符。</span><span class="sxs-lookup"><span data-stu-id="91d08-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="91d08-111">如果沒有明確`else`分支, 其類型為`unit`。</span><span class="sxs-lookup"><span data-stu-id="91d08-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="91d08-112">因此, 如果`then`分支的型別是`unit`以外的任何型別`else` , 則必須有一個具有相同傳回型別的分支。</span><span class="sxs-lookup"><span data-stu-id="91d08-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="91d08-113">將運算式`if...then...else`連結在一起時, 您可以使用`elif`關鍵字, `else if`而不是, 它們是相等的。</span><span class="sxs-lookup"><span data-stu-id="91d08-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="91d08-114">範例</span><span class="sxs-lookup"><span data-stu-id="91d08-114">Example</span></span>

<span data-ttu-id="91d08-115">下列範例說明如何使用`if...then...else`運算式。</span><span class="sxs-lookup"><span data-stu-id="91d08-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="91d08-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91d08-116">See also</span></span>

- [<span data-ttu-id="91d08-117">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="91d08-117">F# Language Reference</span></span>](index.md)
