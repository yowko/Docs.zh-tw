---
title: '比對運算式 （F #）'
description: '了解如何將 F # 比對運算式提供分支運算式的比較，使用一組模式為基礎的控制項。'
ms.date: 04/19/2018
ms.openlocfilehash: e4cb82f20fe82bff562736557c2346562c557f59
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44047671"
---
# <a name="match-expressions"></a><span data-ttu-id="f2ecf-103">比對運算式</span><span class="sxs-lookup"><span data-stu-id="f2ecf-103">Match expressions</span></span>

<span data-ttu-id="f2ecf-104">`match`運算式提供分支運算式的比較，使用一組模式為基礎的控制項。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2ecf-105">語法</span><span class="sxs-lookup"><span data-stu-id="f2ecf-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="f2ecf-106">備註</span><span class="sxs-lookup"><span data-stu-id="f2ecf-106">Remarks</span></span>

<span data-ttu-id="f2ecf-107">允許根據比較結果的測試運算式與一組模式設定的分支複雜模式比對運算式。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="f2ecf-108">在`match`運算式中，*測試運算式*相較於每個模式中開啟，並找到相符項目時，對應*結果運算式*評估及產生的值傳回做為比對運算式的值。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="f2ecf-109">模式比對前一個語法中顯示的函式是在哪個模式比對會立即執行的引數的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="f2ecf-110">模式比對前一個語法中顯示的函式就相當於下列項目。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="f2ecf-111">如需有關 lambda 運算式的詳細資訊，請參閱[Lambda 運算式：`fun`關鍵字](functions/lambda-expressions-the-fun-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="f2ecf-112">模式的完整集合應該涵蓋所有可能的相符項目輸入變數。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="f2ecf-113">通常，您可以使用萬用字元模式 (`_`) 與最後一個模式來比對任何先前不相符的輸入的值。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="f2ecf-114">下列程式碼說明的方式的一些`match`運算式的使用方式。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="f2ecf-115">參考和可用的所有可能模式的範例，請參閱[模式比對](pattern-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="f2ecf-116">模式的成立條件</span><span class="sxs-lookup"><span data-stu-id="f2ecf-116">Guards on patterns</span></span>

<span data-ttu-id="f2ecf-117">您可以使用`when`子句來指定其他條件變數必須滿足才能符合模式。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="f2ecf-118">這類子句指*防護*。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="f2ecf-119">後面的運算式`when`關鍵字不會評估除非相符項目對該防護相關聯的模式。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="f2ecf-120">下列範例說明如何使用成立條件來指定數字的範圍變數的模式。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="f2ecf-121">請注意，使用布林運算子來合併多個條件。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="f2ecf-122">請注意，因為常值以外的值不能用在模式中，您必須使用`when`子句，如果您有要比較的輸入，針對某個值的某個部分。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="f2ecf-123">這是由下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="f2ecf-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="f2ecf-124">請注意，當等位模式都會受到防護，成立條件會套用至**所有**模式，而不只是最後一個。</span><span class="sxs-lookup"><span data-stu-id="f2ecf-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="f2ecf-125">例如，假設下列程式碼防護`when a > 12`同時適用於`A a`和`B a`:</span><span class="sxs-lookup"><span data-stu-id="f2ecf-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f2ecf-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2ecf-126">See also</span></span>

- [<span data-ttu-id="f2ecf-127">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="f2ecf-127">F# Language Reference</span></span>](index.md)  
- [<span data-ttu-id="f2ecf-128">使用中模式</span><span class="sxs-lookup"><span data-stu-id="f2ecf-128">Active Patterns</span></span>](active-patterns.md)  
- [<span data-ttu-id="f2ecf-129">模式比對</span><span class="sxs-lookup"><span data-stu-id="f2ecf-129">Pattern Matching</span></span>](pattern-matching.md)  
