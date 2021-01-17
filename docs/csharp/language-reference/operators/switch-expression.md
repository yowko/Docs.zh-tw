---
title: 'switch 運算式-c # 參考'
description: '瞭解如何使用 c # switch 運算式進行模式比對和其他資料自我檢查'
ms.date: 01/14/2021
ms.openlocfilehash: 55fef8d351b178fd0ec23847e81e6c56eb1367b0
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536082"
---
# <a name="switch-expression-c-reference"></a><span data-ttu-id="00b61-103">switch 運算式 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="00b61-103">switch expression (C# reference)</span></span>

<span data-ttu-id="00b61-104">本文涵蓋 `switch` c # 8.0 中引進的運算式。</span><span class="sxs-lookup"><span data-stu-id="00b61-104">This article covers the `switch` expression, introduced in C# 8.0.</span></span> <span data-ttu-id="00b61-105">如需語句的詳細資訊 `switch` ，請參閱[語句](../keywords/index.md)一節中有關[ `switch` 語句](../keywords/switch.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="00b61-105">For information on the `switch` statement, see the article on the [`switch` statement](../keywords/switch.md) in the [statements](../keywords/index.md) section.</span></span>

## <a name="basic-example"></a><span data-ttu-id="00b61-106">基本範例</span><span class="sxs-lookup"><span data-stu-id="00b61-106">Basic example</span></span>

<span data-ttu-id="00b61-107">`switch`運算式會 `switch` 在運算式內容中提供類似的語法。</span><span class="sxs-lookup"><span data-stu-id="00b61-107">The `switch` expression provides for `switch`-like semantics in an expression context.</span></span> <span data-ttu-id="00b61-108">當 switch arm 產生值時，它會提供簡潔的語法。</span><span class="sxs-lookup"><span data-stu-id="00b61-108">It provides a concise syntax when the switch arms produce a value.</span></span> <span data-ttu-id="00b61-109">下列範例顯示 switch 運算式的結構。</span><span class="sxs-lookup"><span data-stu-id="00b61-109">The following example shows the structure of a switch expression.</span></span> <span data-ttu-id="00b61-110">它會將 `enum` 線上地圖中表示視覺方向的值轉譯為對應的基線方向：</span><span class="sxs-lookup"><span data-stu-id="00b61-110">It translates values from an `enum` representing visual directions in an online map to the corresponding cardinal direction:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetBasicStructure":::

<span data-ttu-id="00b61-111">上述範例顯示 switch 運算式的基本元素：</span><span class="sxs-lookup"><span data-stu-id="00b61-111">The preceding sample shows the basic elements of a switch expression:</span></span>

- <span data-ttu-id="00b61-112">*範圍運算式*：上述範例會使用變數 `direction` 作為範圍運算式。</span><span class="sxs-lookup"><span data-stu-id="00b61-112">The *range expression*: The preceding example uses the variable `direction` as the range expression.</span></span>
- <span data-ttu-id="00b61-113">*交換器運算式* arm：每個 switch 運算式 arm 都包含一個 *模式*，也就是選擇性的 *案例防護*、 `=>` token 和 *運算式*。</span><span class="sxs-lookup"><span data-stu-id="00b61-113">The *switch expression arms*: Each switch expression arm contains a *pattern*, an optional *case guard*, the `=>` token, and an *expression*.</span></span>

<span data-ttu-id="00b61-114">*Switch 運算式* 的結果是第一個 *switch 運算式 arm* 的運算式 *值，其\*\*模式* 符合 *範圍運算式*，而如果有的話，則會評估為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="00b61-114">The result of the *switch expression* is the value of the expression of the first *switch expression arm* whose *pattern* matches the *range expression* and whose *case guard*, if present, evaluates to `true`.</span></span> <span data-ttu-id="00b61-115">Token 右邊的 *運算式* `=>` 不可以是運算式語句。</span><span class="sxs-lookup"><span data-stu-id="00b61-115">The *expression* on the right of the `=>` token can't be an expression statement.</span></span>

<span data-ttu-id="00b61-116">*切換運算式臂* 會以文字順序進行評估。</span><span class="sxs-lookup"><span data-stu-id="00b61-116">The *switch expression arms* are evaluated in text order.</span></span> <span data-ttu-id="00b61-117">因為較高的 *switch 運算式 arm* 符合其所有值，所以無法選擇較低的 *switch 運算式 arm* 時，編譯器會發出錯誤。</span><span class="sxs-lookup"><span data-stu-id="00b61-117">The compiler issues an error when a lower *switch expression arm* can't be chosen because a higher *switch expression arm* matches all its values.</span></span>

## <a name="patterns-and-case-guards"></a><span data-ttu-id="00b61-118">模式和案例防護</span><span class="sxs-lookup"><span data-stu-id="00b61-118">Patterns and case guards</span></span>

<span data-ttu-id="00b61-119">Switch 運算式臂支援許多模式。</span><span class="sxs-lookup"><span data-stu-id="00b61-119">Many patterns are supported in switch expression arms.</span></span> <span data-ttu-id="00b61-120">上述範例使用 *常數模式*。</span><span class="sxs-lookup"><span data-stu-id="00b61-120">The preceding example uses a *constant pattern*.</span></span> <span data-ttu-id="00b61-121">*常數模式* 會將範圍運算式與值進行比較。</span><span class="sxs-lookup"><span data-stu-id="00b61-121">A *constant pattern* compares the range expression to a value.</span></span> <span data-ttu-id="00b61-122">該值必須是編譯時間常數。</span><span class="sxs-lookup"><span data-stu-id="00b61-122">That value must be a compile-time constant.</span></span> <span data-ttu-id="00b61-123">*型別模式* 會比較範圍運算式與已知型別。</span><span class="sxs-lookup"><span data-stu-id="00b61-123">The *type pattern* compares the range expression to a known type.</span></span> <span data-ttu-id="00b61-124">下列範例會從序列中取出第三個元素。</span><span class="sxs-lookup"><span data-stu-id="00b61-124">The following example retrieves the third element from a sequence.</span></span> <span data-ttu-id="00b61-125">它會根據序列的類型使用不同的方法：</span><span class="sxs-lookup"><span data-stu-id="00b61-125">It uses different methods based on the type of the sequence:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetTypePattern":::

<span data-ttu-id="00b61-126">模式可以是遞迴，其中的模式會測試型別，而且如果該型別相符，則模式會符合範圍運算式上的一或多個屬性值。</span><span class="sxs-lookup"><span data-stu-id="00b61-126">Patterns can be recursive, where a pattern tests a type, and if that type matches, the pattern matches one or more property values on the range expression.</span></span> <span data-ttu-id="00b61-127">您可以使用遞迴模式來擴充上述範例。</span><span class="sxs-lookup"><span data-stu-id="00b61-127">You can use recursive patterns to extend the preceding example.</span></span> <span data-ttu-id="00b61-128">您可以針對擁有少於3個元素的陣列加入 switch 運算式臂。</span><span class="sxs-lookup"><span data-stu-id="00b61-128">You add switch expression arms for arrays that have fewer than 3 elements.</span></span> <span data-ttu-id="00b61-129">遞迴模式如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="00b61-129">Recursive patterns are shown in the following example:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetRecursivePattern":::

<span data-ttu-id="00b61-130">遞迴模式可以檢查範圍運算式的屬性，但是無法執行任意程式碼。</span><span class="sxs-lookup"><span data-stu-id="00b61-130">Recursive patterns can examine properties of the range expression, but can't execute arbitrary code.</span></span> <span data-ttu-id="00b61-131">您可以使用子句中指定的 *case guard* `when` ，以提供與其他序列類型類似的檢查：</span><span class="sxs-lookup"><span data-stu-id="00b61-131">You can use a *case guard*, specified in a `when` clause, to provide similar checks for other sequence types:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetGuardCase":::

<span data-ttu-id="00b61-132">最後，您可以新增 `_` 模式和模式， `null` 以攔截任何其他 switch 運算式 arm 未處理的引數。</span><span class="sxs-lookup"><span data-stu-id="00b61-132">Finally, you can add the `_` pattern and the `null` pattern to catch arguments that aren't processed by any other switch expression arm.</span></span> <span data-ttu-id="00b61-133">這會讓 switch 運算式成為 *詳盡* 的，這表示會處理任何可能的範圍運算式值。</span><span class="sxs-lookup"><span data-stu-id="00b61-133">That makes the switch expression *exhaustive*, meaning any possible value of the range expression is handled.</span></span> <span data-ttu-id="00b61-134">下列範例會新增這些運算式臂：</span><span class="sxs-lookup"><span data-stu-id="00b61-134">The following example adds those expression arms:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetExhaustive":::

<span data-ttu-id="00b61-135">上述範例會新增 `null` 模式，並將型別 `IEnumerable<T>` 模式變更為 `_` 模式。</span><span class="sxs-lookup"><span data-stu-id="00b61-135">The preceding example adds a `null` pattern, and changes the `IEnumerable<T>` type pattern to a `_` pattern.</span></span> <span data-ttu-id="00b61-136">此 `null` 模式會提供 null 檢查作為 switch 運算式 arm。</span><span class="sxs-lookup"><span data-stu-id="00b61-136">The `null` pattern provides a null check as a switch expression arm.</span></span> <span data-ttu-id="00b61-137">該 arm 的運算式會擲回 <xref:System.ArgumentNullException> 。</span><span class="sxs-lookup"><span data-stu-id="00b61-137">The expression for that arm throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="00b61-138">`_`模式會比對所有未由先前的 arm 相符的輸入。</span><span class="sxs-lookup"><span data-stu-id="00b61-138">The `_` pattern matches all inputs that haven't been matched by previous arms.</span></span> <span data-ttu-id="00b61-139">它必須在檢查之後 `null` ，否則會符合 `null` 輸入。</span><span class="sxs-lookup"><span data-stu-id="00b61-139">It must come after the `null` check, or it would match `null` inputs.</span></span>

## <a name="non-exhaustive-switch-expressions"></a><span data-ttu-id="00b61-140">非徹底的 switch 運算式</span><span class="sxs-lookup"><span data-stu-id="00b61-140">Non-exhaustive switch expressions</span></span>

<span data-ttu-id="00b61-141">如果 switch 運算式的模式都沒有攔截引數，則執行時間會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="00b61-141">If none of a switch expression's patterns catches an argument, the runtime throws an exception.</span></span> <span data-ttu-id="00b61-142">在 .NET Core 3.0 和更新版本中，例外狀況為 <xref:System.Runtime.CompilerServices.SwitchExpressionException?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="00b61-142">In .NET Core 3.0 and later versions, the exception is a <xref:System.Runtime.CompilerServices.SwitchExpressionException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="00b61-143">在 .NET Framework 中，例外狀況為 <xref:System.InvalidOperationException> 。</span><span class="sxs-lookup"><span data-stu-id="00b61-143">In .NET Framework, the exception is an <xref:System.InvalidOperationException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="00b61-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00b61-144">See also</span></span>

- [<span data-ttu-id="00b61-145">遞迴模式的 c # 語言規格提案</span><span class="sxs-lookup"><span data-stu-id="00b61-145">C# language spec proposal for recursive patterns</span></span>](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression)
- [<span data-ttu-id="00b61-146">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="00b61-146">C# reference</span></span>](../index.md)
- [<span data-ttu-id="00b61-147">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="00b61-147">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="00b61-148">模式比對</span><span class="sxs-lookup"><span data-stu-id="00b61-148">Pattern matching</span></span>](../../pattern-matching.md)
