---
title: 'switch 運算式-c # 參考'
description: '瞭解如何使用 c # switch 運算式進行模式比對和其他資料自我檢查'
ms.date: 03/19/2020
ms.openlocfilehash: 2249afc1ff1cc81e9ad423d910ebb95df8c787d4
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916661"
---
# <a name="switch-expression-c-reference"></a><span data-ttu-id="af14b-103">切換運算式 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="af14b-103">switch expression (C# reference)</span></span>

<span data-ttu-id="af14b-104">本文涵蓋 `switch` c # 8.0 中引進的運算式。</span><span class="sxs-lookup"><span data-stu-id="af14b-104">This article covers the `switch` expression, introduced in C# 8.0.</span></span> <span data-ttu-id="af14b-105">如需語句的詳細資訊 `switch` ，請參閱[語句](../keywords/index.md)一節中有關[ `switch` 語句](../keywords/switch.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="af14b-105">For information on the `switch` statement, see the article on the [`switch` statement](../keywords/switch.md) in the [statements](../keywords/index.md) section.</span></span>

## <a name="basic-example"></a><span data-ttu-id="af14b-106">基本範例</span><span class="sxs-lookup"><span data-stu-id="af14b-106">Basic example</span></span>

<span data-ttu-id="af14b-107">`switch`運算式會 `switch` 在運算式內容中提供類似的語義。</span><span class="sxs-lookup"><span data-stu-id="af14b-107">The `switch` expression provides for `switch`-like semantics in an expression context.</span></span> <span data-ttu-id="af14b-108">當交換器臂產生值時，它會提供精簡的語法。</span><span class="sxs-lookup"><span data-stu-id="af14b-108">It provides a concise syntax when the switch arms produce a value.</span></span> <span data-ttu-id="af14b-109">下列範例會顯示 switch 運算式的結構。</span><span class="sxs-lookup"><span data-stu-id="af14b-109">The following example shows the structure of a switch expression.</span></span> <span data-ttu-id="af14b-110">它會從 `enum` 線上地圖中代表視覺方向的值轉譯為對應的基線方向：</span><span class="sxs-lookup"><span data-stu-id="af14b-110">It translates values from an `enum` representing visual directions in an online map to the corresponding cardinal direction:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetBasicStructure":::

<span data-ttu-id="af14b-111">上述範例顯示 switch 運算式的基本元素：</span><span class="sxs-lookup"><span data-stu-id="af14b-111">The preceding sample shows the basic elements of a switch expression:</span></span>

- <span data-ttu-id="af14b-112">*範圍運算式*：上述範例會使用變數 `direction` 做為範圍運算式。</span><span class="sxs-lookup"><span data-stu-id="af14b-112">The *range expression*: The preceding example uses the variable `direction` as the range expression.</span></span>
- <span data-ttu-id="af14b-113">*交換器運算式*arm：每個交換器運算式 arm 包含*模式*、選擇性的*案例防護*、 `=>` 權杖和*運算式*。</span><span class="sxs-lookup"><span data-stu-id="af14b-113">The *switch expression arms*: Each switch expression arm contains a *pattern*, an optional *case guard*, the `=>` token, and an *expression*.</span></span>

<span data-ttu-id="af14b-114">*Switch 運算式*的結果是第一個*switch 運算式 arm*的運算式值，其*模式*符合*範圍運算式*，而其*case guard*（如果有的話）會評估為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="af14b-114">The result of the *switch expression* is the value of the expression of the first *switch expression arm* whose *pattern* matches the *range expression* and whose *case guard*, if present, evaluates to `true`.</span></span> <span data-ttu-id="af14b-115">Token 右邊的*運算式* `=>` 不可以是運算式語句。</span><span class="sxs-lookup"><span data-stu-id="af14b-115">The *expression* on the right of the `=>` token can't be an expression statement.</span></span>

<span data-ttu-id="af14b-116">*切換運算式臂*會以文字順序進行評估。</span><span class="sxs-lookup"><span data-stu-id="af14b-116">The *switch expression arms* are evaluated in text order.</span></span> <span data-ttu-id="af14b-117">當無法選擇較低的*交換器運算式 arm*時，編譯器會發出錯誤，因為較高的*交換器運算式 arm*符合其所有值。</span><span class="sxs-lookup"><span data-stu-id="af14b-117">The compiler issues an error when a lower *switch expression arm* can't be chosen because a higher *switch expression arm* matches all its values.</span></span>

## <a name="patterns-and-case-guards"></a><span data-ttu-id="af14b-118">模式和案例防護</span><span class="sxs-lookup"><span data-stu-id="af14b-118">Patterns and case guards</span></span>

<span data-ttu-id="af14b-119">交換器運算式臂支援許多模式。</span><span class="sxs-lookup"><span data-stu-id="af14b-119">Many patterns are supported in switch expression arms.</span></span> <span data-ttu-id="af14b-120">上述範例使用*常數模式*。</span><span class="sxs-lookup"><span data-stu-id="af14b-120">The preceding example uses a *constant pattern*.</span></span> <span data-ttu-id="af14b-121">*常數模式*會將範圍運算式與值進行比較。</span><span class="sxs-lookup"><span data-stu-id="af14b-121">A *constant pattern* compares the range expression to a value.</span></span> <span data-ttu-id="af14b-122">該值必須是編譯時期常數。</span><span class="sxs-lookup"><span data-stu-id="af14b-122">That value must be a compile-time constant.</span></span> <span data-ttu-id="af14b-123">*型別模式*會比較範圍運算式與已知型別。</span><span class="sxs-lookup"><span data-stu-id="af14b-123">The *type pattern* compares the range expression to a known type.</span></span> <span data-ttu-id="af14b-124">下列範例會從序列中抓取第三個元素。</span><span class="sxs-lookup"><span data-stu-id="af14b-124">The following example retrieves the third element from a sequence.</span></span> <span data-ttu-id="af14b-125">它會根據順序的類型來使用不同的方法：</span><span class="sxs-lookup"><span data-stu-id="af14b-125">It uses different methods based on the type of the sequence:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetTypePattern":::

<span data-ttu-id="af14b-126">模式可以是遞迴的，其中模式會測試類型，如果該類型符合，則模式會比對範圍運算式上的一或多個屬性值。</span><span class="sxs-lookup"><span data-stu-id="af14b-126">Patterns can be recursive, where a pattern tests a type, and if that type matches, the pattern matches one or more property values on the range expression.</span></span> <span data-ttu-id="af14b-127">您可以使用遞迴模式來擴充先前的範例。</span><span class="sxs-lookup"><span data-stu-id="af14b-127">You can use recursive patterns to extend the preceding example.</span></span> <span data-ttu-id="af14b-128">針對具有少於3個元素的陣列，您可以加入切換運算式臂。</span><span class="sxs-lookup"><span data-stu-id="af14b-128">You add switch expression arms for arrays that have fewer than 3 elements.</span></span> <span data-ttu-id="af14b-129">遞迴模式如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="af14b-129">Recursive patterns are shown in the following example:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetRecursivePattern":::

<span data-ttu-id="af14b-130">遞迴模式可以檢查範圍運算式的屬性，但無法執行任意程式碼。</span><span class="sxs-lookup"><span data-stu-id="af14b-130">Recursive patterns can examine properties of the range expression, but can't execute arbitrary code.</span></span> <span data-ttu-id="af14b-131">您可以使用子句中指定的「*案例防護*」 `when` ，針對其他序列類型提供類似的檢查：</span><span class="sxs-lookup"><span data-stu-id="af14b-131">You can use a *case guard*, specified in a `when` clause, to provide similar checks for other sequence types:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetGuardCase":::

<span data-ttu-id="af14b-132">最後，您可以新增 `_` 模式和模式， `null` 以攔截未由任何其他交換器運算式 arm 處理的引數。</span><span class="sxs-lookup"><span data-stu-id="af14b-132">Finally, you can add the `_` pattern and the `null` pattern to catch arguments that aren't processed by any other switch expression arm.</span></span> <span data-ttu-id="af14b-133">這會讓 switch 運算式*詳盡*，這表示會處理範圍運算式的任何可能值。</span><span class="sxs-lookup"><span data-stu-id="af14b-133">That makes the switch expression *exhaustive*, meaning any possible value of the range expression is handled.</span></span> <span data-ttu-id="af14b-134">下列範例會新增那些運算式臂：</span><span class="sxs-lookup"><span data-stu-id="af14b-134">The following example adds those expression arms:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetExhaustive":::

<span data-ttu-id="af14b-135">上述範例會加入 `null` 模式，並將 `IEnumerable<T>` 類型模式變更為 `_` 模式。</span><span class="sxs-lookup"><span data-stu-id="af14b-135">The preceding example adds a `null` pattern, and changes the `IEnumerable<T>` type pattern to a `_` pattern.</span></span> <span data-ttu-id="af14b-136">此 `null` 模式會提供 null 檢查做為交換器運算式 arm。</span><span class="sxs-lookup"><span data-stu-id="af14b-136">The `null` pattern provides a null check as a switch expression arm.</span></span> <span data-ttu-id="af14b-137">該 arm 的運算式會擲回 <xref:System.ArgumentNullException> 。</span><span class="sxs-lookup"><span data-stu-id="af14b-137">The expression for that arm throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="af14b-138">此 `_` 模式會比對先前臂未符合的所有輸入。</span><span class="sxs-lookup"><span data-stu-id="af14b-138">The `_` pattern matches all inputs that haven't been matched by previous arms.</span></span> <span data-ttu-id="af14b-139">它必須位於檢查之後 `null` ，否則會符合 `null` 輸入。</span><span class="sxs-lookup"><span data-stu-id="af14b-139">It must come after the `null` check, or it would match `null` inputs.</span></span>

<span data-ttu-id="af14b-140">您可以在[遞迴模式](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression)的 c # 語言規格提案中閱讀更多。</span><span class="sxs-lookup"><span data-stu-id="af14b-140">You can read more in the C# language spec proposal for [recursive patterns](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression).</span></span>

## <a name="see-also"></a><span data-ttu-id="af14b-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af14b-141">See also</span></span>

- [<span data-ttu-id="af14b-142">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="af14b-142">C# reference</span></span>](../index.md)
- [<span data-ttu-id="af14b-143">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="af14b-143">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="af14b-144">模式比對</span><span class="sxs-lookup"><span data-stu-id="af14b-144">Pattern matching</span></span>](../../pattern-matching.md)
