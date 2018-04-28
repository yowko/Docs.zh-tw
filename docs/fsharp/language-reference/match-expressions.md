---
title: '符合運算式 （F #）'
description: '了解如何在 F # 比對運算式提供分支運算式的比較，以一組模式為基礎的控制項。'
author: cartermp
ms.author: phcart
ms.date: 04/19/2018
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f6930f782384464f0d44b205ea77cbaf43898213
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="match-expressions"></a><span data-ttu-id="cd2ac-103">比對運算式</span><span class="sxs-lookup"><span data-stu-id="cd2ac-103">Match expressions</span></span>

<span data-ttu-id="cd2ac-104">`match`運算式提供分支運算式的比較，以一組模式為基礎的控制項。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd2ac-105">語法</span><span class="sxs-lookup"><span data-stu-id="cd2ac-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="cd2ac-106">備註</span><span class="sxs-lookup"><span data-stu-id="cd2ac-106">Remarks</span></span>

<span data-ttu-id="cd2ac-107">模式比對運算式允許複雜分支根據比較結果的測試運算式與一組模式。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="cd2ac-108">在`match`運算式，*測試運算式*與進行比較，每個模式中開啟，並找到相符項目時，對應*結果運算式*評估及產生的值傳回做為比對運算式的值。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="cd2ac-109">模式比對上一個語法中顯示的函式是在哪個模式中執行比對立即的引數的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="cd2ac-110">模式比對上一個語法中顯示的函式就相當於下列項目。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="cd2ac-111">如需 lambda 運算式的詳細資訊，請參閱[Lambda 運算式：`fun`關鍵字](functions/lambda-expressions-the-fun-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="cd2ac-112">完整的模式設定應該涵蓋所有可能的相符的輸入變數。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="cd2ac-113">通常，您可以使用萬用字元模式 (`_`) 來比對任何先前不相符的輸入的值與上一個模式。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="cd2ac-114">下列程式碼將說明部分的方式`match`運算式使用。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="cd2ac-115">參考資料和可用的所有可能模式的範例，請參閱[模式比對](pattern-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="cd2ac-116">模式成立條件</span><span class="sxs-lookup"><span data-stu-id="cd2ac-116">Guards on patterns</span></span>

<span data-ttu-id="cd2ac-117">您可以使用`when`子句指定的變數必須符合才能符合模式的其他條件。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="cd2ac-118">這類子句指*防護*。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="cd2ac-119">後面的運算式`when`除非相符項目對該保護與相關聯的模式，將不評估關鍵字。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="cd2ac-120">下列範例說明如何使用指定的數值範圍變數模式的成立條件。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="cd2ac-121">請注意，多個條件會組合使用布林運算子。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="cd2ac-122">請注意，因為常值以外的值不能用在模式中，您必須使用`when`子句，如果您有要比較的輸入，針對某個值的某些部分。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="cd2ac-123">下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="cd2ac-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="cd2ac-124">請注意，當一個成立條件所涵蓋的等位的模式，成立條件會套用至**所有**的模式，而不只是最後一個。</span><span class="sxs-lookup"><span data-stu-id="cd2ac-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="cd2ac-125">例如，假設下列程式碼防護`when a > 12`同時適用於`A a`和`B a`:</span><span class="sxs-lookup"><span data-stu-id="cd2ac-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cd2ac-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd2ac-126">See also</span></span>

[<span data-ttu-id="cd2ac-127">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="cd2ac-127">F# Language Reference</span></span>](index.md)  
[<span data-ttu-id="cd2ac-128">使用中模式</span><span class="sxs-lookup"><span data-stu-id="cd2ac-128">Active Patterns</span></span>](active-patterns.md)  
[<span data-ttu-id="cd2ac-129">模式比對</span><span class="sxs-lookup"><span data-stu-id="cd2ac-129">Pattern Matching</span></span>](pattern-matching.md)  
