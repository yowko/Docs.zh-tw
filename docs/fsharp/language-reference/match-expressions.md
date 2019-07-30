---
title: Match 運算式
description: 瞭解比對F#運算式如何提供以運算式與一組模式的比較為基礎的分支控制。
ms.date: 04/19/2018
ms.openlocfilehash: 222cb0604300039d86ed0c80293651631d212eb6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627617"
---
# <a name="match-expressions"></a><span data-ttu-id="6a908-103">Match 運算式</span><span class="sxs-lookup"><span data-stu-id="6a908-103">Match expressions</span></span>

<span data-ttu-id="6a908-104">`match`運算式提供的分支控制是以運算式與一組模式的比較為基礎。</span><span class="sxs-lookup"><span data-stu-id="6a908-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="6a908-105">語法</span><span class="sxs-lookup"><span data-stu-id="6a908-105">Syntax</span></span>

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a><span data-ttu-id="6a908-106">備註</span><span class="sxs-lookup"><span data-stu-id="6a908-106">Remarks</span></span>

<span data-ttu-id="6a908-107">模式比對運算式可根據測試運算式與一組模式的比較, 來進行複雜的分支。</span><span class="sxs-lookup"><span data-stu-id="6a908-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="6a908-108">在運算式中, 會依序將*測試運算式*與每個模式進行比較, 當找到相符的結果時, 就會評估對應的*結果運算式*, 並傳回產生的值做為 match 運算式的值。 `match`</span><span class="sxs-lookup"><span data-stu-id="6a908-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="6a908-109">前面的語法中所顯示的模式比對函式, 是在引數上立即執行模式比對的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="6a908-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="6a908-110">先前語法中所顯示的模式比對函式相當於下列。</span><span class="sxs-lookup"><span data-stu-id="6a908-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="6a908-111">如需 lambda 運算式的詳細資訊, [請參閱 lambda 運算式:`fun`關鍵字。](./functions/lambda-expressions-the-fun-keyword.md)</span><span class="sxs-lookup"><span data-stu-id="6a908-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](./functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="6a908-112">一整組模式應涵蓋輸入變數的所有可能相符專案。</span><span class="sxs-lookup"><span data-stu-id="6a908-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="6a908-113">通常, 您會使用萬用字元模式 (`_`) 做為最後一個模式, 以比對任何先前不相符的輸入值。</span><span class="sxs-lookup"><span data-stu-id="6a908-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="6a908-114">下列程式碼說明使用`match`運算式的一些方式。</span><span class="sxs-lookup"><span data-stu-id="6a908-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="6a908-115">如需可使用之所有可能模式的參考和範例, 請參閱[模式](pattern-matching.md)比對。</span><span class="sxs-lookup"><span data-stu-id="6a908-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="6a908-116">保護模式</span><span class="sxs-lookup"><span data-stu-id="6a908-116">Guards on patterns</span></span>

<span data-ttu-id="6a908-117">您可以使用`when`子句來指定其他條件, 讓變數必須滿足以符合模式。</span><span class="sxs-lookup"><span data-stu-id="6a908-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="6a908-118">這類子句稱為「*防護*」。</span><span class="sxs-lookup"><span data-stu-id="6a908-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="6a908-119">除非對與該`when`防護相關聯的模式進行比對, 否則不會評估緊接在關鍵字後面的運算式。</span><span class="sxs-lookup"><span data-stu-id="6a908-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="6a908-120">下列範例說明如何使用 guard 來指定變數模式的數值範圍。</span><span class="sxs-lookup"><span data-stu-id="6a908-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="6a908-121">請注意, 您可以使用布林運算子來結合多個條件。</span><span class="sxs-lookup"><span data-stu-id="6a908-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="6a908-122">請注意, 因為不能在模式中使用常值以外的值, 所以如果`when`您必須將輸入的某些部分與值進行比較, 則必須使用子句。</span><span class="sxs-lookup"><span data-stu-id="6a908-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="6a908-123">這會以下列程式碼顯示：</span><span class="sxs-lookup"><span data-stu-id="6a908-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="6a908-124">請注意, 當「聯集」模式受到防護的涵蓋時, 此防護會套用至**所有**模式, 而不只是最後一個。</span><span class="sxs-lookup"><span data-stu-id="6a908-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="6a908-125">例如, 假設有下列程式碼, 則此`when a > 12`防護適用`A a`于和`B a`:</span><span class="sxs-lookup"><span data-stu-id="6a908-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a><span data-ttu-id="6a908-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a908-126">See also</span></span>

- [<span data-ttu-id="6a908-127">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="6a908-127">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="6a908-128">使用中模式</span><span class="sxs-lookup"><span data-stu-id="6a908-128">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="6a908-129">模式比對</span><span class="sxs-lookup"><span data-stu-id="6a908-129">Pattern Matching</span></span>](pattern-matching.md)
