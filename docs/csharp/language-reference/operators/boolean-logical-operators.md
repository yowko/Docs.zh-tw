---
title: 布林值邏輯運算子 - C# 參考
description: 了解能搭配布林值運算元執行邏輯否定、結合 (AND) 及內含和互斥分離 (OR) 作業的 C# 運算子。
ms.date: 09/27/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: 930329b922f585ac4763e6a66d3b192ae839f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399494"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="810d3-103">布林值邏輯運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="810d3-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="810d3-104">以下運算子使用[布林](../builtin-types/bool.md)運算元執行邏輯操作：</span><span class="sxs-lookup"><span data-stu-id="810d3-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="810d3-105">一元[`!`（邏輯否定）](#logical-negation-operator-)運算子。</span><span class="sxs-lookup"><span data-stu-id="810d3-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="810d3-106">二進位[`&`（邏輯 AND）、（](#logical-and-operator-)[`|`邏輯 OR）](#logical-or-operator-)和[`^`（邏輯獨佔 OR）](#logical-exclusive-or-operator-)運算子。</span><span class="sxs-lookup"><span data-stu-id="810d3-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="810d3-107">那些運算子一律會評估兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="810d3-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="810d3-108">二進位[`&&`（條件邏輯 AND）](#conditional-logical-and-operator-)和[`||`（條件邏輯 OR）](#conditional-logical-or-operator-)運算子。</span><span class="sxs-lookup"><span data-stu-id="810d3-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="810d3-109">那些運算子只會在必要時才評估右邊的運算元。</span><span class="sxs-lookup"><span data-stu-id="810d3-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="810d3-110">對於[積分數數值型別的](../builtin-types/integral-numeric-types.md)運算元，`&`和`|``^`運算子執行位邏輯操作。</span><span class="sxs-lookup"><span data-stu-id="810d3-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="810d3-111">如需詳細資訊，請參閱[位元與移位運算子](bitwise-and-shift-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="810d3-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="810d3-112">邏輯否定運算子 !</span><span class="sxs-lookup"><span data-stu-id="810d3-112">Logical negation operator !</span></span>

<span data-ttu-id="810d3-113">未處理的首碼`!`運算子計算其運算元的邏輯否定。</span><span class="sxs-lookup"><span data-stu-id="810d3-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="810d3-114">也就是說，它會在運算元評估為 `false` 時產生 `true`，並在運算元評估為 `true` 時產生 `false`：</span><span class="sxs-lookup"><span data-stu-id="810d3-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="810d3-115">從 C# 8.0 開始，未修復`!`後運算子是[空寬恕運算子](null-forgiving.md)。</span><span class="sxs-lookup"><span data-stu-id="810d3-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="810d3-116">邏輯和運算子&amp;</span><span class="sxs-lookup"><span data-stu-id="810d3-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="810d3-117">`&` 運算子會計算其運算元的邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="810d3-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="810d3-118">若 `x` 及 `y` 皆求出 `true`，那麼 `x & y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="810d3-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="810d3-119">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="810d3-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="810d3-120">`&`運算子計算兩個運算元，即使左側運算元計算到`false`，以便操作結果與`false`右側運算元的值無關。</span><span class="sxs-lookup"><span data-stu-id="810d3-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="810d3-121">在下列範例中，`&` 運算子的右邊運算元是方法呼叫；無論左邊運算元的值為何，系統都會執行該呼叫：</span><span class="sxs-lookup"><span data-stu-id="810d3-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="810d3-122">[條件邏輯 AND 運算子](#conditional-logical-and-operator-) `&&` 也會計算其運算元的邏輯 AND，但如果右邊運算元的值評估為 `false`，系統便不會評估左邊運算元。</span><span class="sxs-lookup"><span data-stu-id="810d3-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="810d3-123">對於[積分數數值型別的](../builtin-types/integral-numeric-types.md)運算元，`&`運算子計算其運算元的[位邏輯 AND。](bitwise-and-shift-operators.md#logical-and-operator-)</span><span class="sxs-lookup"><span data-stu-id="810d3-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="810d3-124">一元的 `&` 運算子是 [address-of 運算子](pointer-related-operators.md#address-of-operator-)。</span><span class="sxs-lookup"><span data-stu-id="810d3-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="810d3-125">邏輯互斥 OR 運算子 ^</span><span class="sxs-lookup"><span data-stu-id="810d3-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="810d3-126">`^` 運算子會計算其運算元的邏輯互斥 OR，其也稱為邏輯 XOR。</span><span class="sxs-lookup"><span data-stu-id="810d3-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="810d3-127">如果 `x` 評估為 `true` 且 `y` 評估為 `false`，或是 `x` 評估為 `false` 且 `y` 評估為 `true` 時，`x ^ y` 的結果將會為 `true`。</span><span class="sxs-lookup"><span data-stu-id="810d3-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="810d3-128">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="810d3-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="810d3-129">也就是說，針對 `bool` 運算元，`^` 運算子的計算結果會與[不等比較運算子](equality-operators.md#inequality-operator-) `!=` 相同。</span><span class="sxs-lookup"><span data-stu-id="810d3-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="810d3-130">對於[積分數數值型別的](../builtin-types/integral-numeric-types.md)運算元，`^`運算子計算其運算元的[位邏輯獨佔 OR。](bitwise-and-shift-operators.md#logical-exclusive-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="810d3-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="810d3-131">邏輯 OR 運算子 |</span><span class="sxs-lookup"><span data-stu-id="810d3-131">Logical OR operator |</span></span>

<span data-ttu-id="810d3-132">`|` 運算子會計算其運算元的邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="810d3-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="810d3-133">若 `x` 或 `y` 其中一項的值為 `true`，`x | y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="810d3-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="810d3-134">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="810d3-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="810d3-135">`|`運算子計算兩個運算元，即使左側運算元計算到`true`，以便操作結果與`true`右側運算元的值無關。</span><span class="sxs-lookup"><span data-stu-id="810d3-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="810d3-136">在下列範例中，`|` 運算子的右邊運算元是方法呼叫；無論左邊運算元的值為何，系統都會執行該呼叫：</span><span class="sxs-lookup"><span data-stu-id="810d3-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="810d3-137">[條件式邏輯 OR 運算子](#conditional-logical-or-operator-) `||` 也會計算其運算元的邏輯 OR，但如果左邊運算元的值評估為 `true`，系統便不會評估右邊運算元。</span><span class="sxs-lookup"><span data-stu-id="810d3-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="810d3-138">對於[積分數數值型別的](../builtin-types/integral-numeric-types.md)運算元，`|`運算子計算其運算元的[位邏輯 OR。](bitwise-and-shift-operators.md#logical-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="810d3-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="810d3-139">條件邏輯 AND 運算子&amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="810d3-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="810d3-140">條件邏輯 AND 運算子 `&&`，也稱為「捷徑運算」邏輯 AND 運算子，會計算其運算元的邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="810d3-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="810d3-141">若 `x` 及 `y` 皆求出 `true`，那麼 `x && y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="810d3-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="810d3-142">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="810d3-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="810d3-143">如果 `x` 評估為 `false`，則不會評估 `y`。</span><span class="sxs-lookup"><span data-stu-id="810d3-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="810d3-144">在下列範例中，`&&` 運算子的右邊運算元是方法呼叫；如果左邊運算元的值評估為 `false`，系統便不會執行該呼叫：</span><span class="sxs-lookup"><span data-stu-id="810d3-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="810d3-145">[邏輯 AND 運算子](#logical-and-operator-)`&`還計算其運算元的邏輯 AND，但始終計算兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="810d3-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="810d3-146">條件邏輯 OR 運算子 ||</span><span class="sxs-lookup"><span data-stu-id="810d3-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="810d3-147">條件邏輯 OR 運算子 `||`，也稱為「捷徑運算」邏輯 OR 運算子，會計算其運算元的邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="810d3-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="810d3-148">若 `x` 或 `y` 其中一項的值為 `true`，`x || y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="810d3-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="810d3-149">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="810d3-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="810d3-150">如果 `x` 評估為 `true`，則不會評估 `y`。</span><span class="sxs-lookup"><span data-stu-id="810d3-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="810d3-151">在下列範例中，`||` 運算子的右邊運算元是方法呼叫；如果左邊運算元的值評估為 `true`，系統便不會執行該呼叫：</span><span class="sxs-lookup"><span data-stu-id="810d3-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="810d3-152">[邏輯 OR 運算子](#logical-or-operator-)`|`還計算其運算元的邏輯 OR，但始終計算兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="810d3-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="810d3-153">可為 Null 的布林值邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="810d3-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="810d3-154">對於`bool?`運算元，`&`和`|`運算子支援三值邏輯。</span><span class="sxs-lookup"><span data-stu-id="810d3-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="810d3-155">這些運算子的語意是由下列表格定義的：</span><span class="sxs-lookup"><span data-stu-id="810d3-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="810d3-156">x</span><span class="sxs-lookup"><span data-stu-id="810d3-156">x</span></span>|<span data-ttu-id="810d3-157">y</span><span class="sxs-lookup"><span data-stu-id="810d3-157">y</span></span>|<span data-ttu-id="810d3-158">x&y</span><span class="sxs-lookup"><span data-stu-id="810d3-158">x&y</span></span>|<span data-ttu-id="810d3-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="810d3-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="810d3-160">true</span><span class="sxs-lookup"><span data-stu-id="810d3-160">true</span></span>|<span data-ttu-id="810d3-161">true</span><span class="sxs-lookup"><span data-stu-id="810d3-161">true</span></span>|<span data-ttu-id="810d3-162">true</span><span class="sxs-lookup"><span data-stu-id="810d3-162">true</span></span>|<span data-ttu-id="810d3-163">true</span><span class="sxs-lookup"><span data-stu-id="810d3-163">true</span></span>|  
|<span data-ttu-id="810d3-164">true</span><span class="sxs-lookup"><span data-stu-id="810d3-164">true</span></span>|<span data-ttu-id="810d3-165">false</span><span class="sxs-lookup"><span data-stu-id="810d3-165">false</span></span>|<span data-ttu-id="810d3-166">false</span><span class="sxs-lookup"><span data-stu-id="810d3-166">false</span></span>|<span data-ttu-id="810d3-167">true</span><span class="sxs-lookup"><span data-stu-id="810d3-167">true</span></span>|  
|<span data-ttu-id="810d3-168">true</span><span class="sxs-lookup"><span data-stu-id="810d3-168">true</span></span>|<span data-ttu-id="810d3-169">null</span><span class="sxs-lookup"><span data-stu-id="810d3-169">null</span></span>|<span data-ttu-id="810d3-170">null</span><span class="sxs-lookup"><span data-stu-id="810d3-170">null</span></span>|<span data-ttu-id="810d3-171">true</span><span class="sxs-lookup"><span data-stu-id="810d3-171">true</span></span>|  
|<span data-ttu-id="810d3-172">false</span><span class="sxs-lookup"><span data-stu-id="810d3-172">false</span></span>|<span data-ttu-id="810d3-173">true</span><span class="sxs-lookup"><span data-stu-id="810d3-173">true</span></span>|<span data-ttu-id="810d3-174">false</span><span class="sxs-lookup"><span data-stu-id="810d3-174">false</span></span>|<span data-ttu-id="810d3-175">true</span><span class="sxs-lookup"><span data-stu-id="810d3-175">true</span></span>|  
|<span data-ttu-id="810d3-176">false</span><span class="sxs-lookup"><span data-stu-id="810d3-176">false</span></span>|<span data-ttu-id="810d3-177">false</span><span class="sxs-lookup"><span data-stu-id="810d3-177">false</span></span>|<span data-ttu-id="810d3-178">false</span><span class="sxs-lookup"><span data-stu-id="810d3-178">false</span></span>|<span data-ttu-id="810d3-179">false</span><span class="sxs-lookup"><span data-stu-id="810d3-179">false</span></span>|  
|<span data-ttu-id="810d3-180">false</span><span class="sxs-lookup"><span data-stu-id="810d3-180">false</span></span>|<span data-ttu-id="810d3-181">null</span><span class="sxs-lookup"><span data-stu-id="810d3-181">null</span></span>|<span data-ttu-id="810d3-182">false</span><span class="sxs-lookup"><span data-stu-id="810d3-182">false</span></span>|<span data-ttu-id="810d3-183">null</span><span class="sxs-lookup"><span data-stu-id="810d3-183">null</span></span>|  
|<span data-ttu-id="810d3-184">null</span><span class="sxs-lookup"><span data-stu-id="810d3-184">null</span></span>|<span data-ttu-id="810d3-185">true</span><span class="sxs-lookup"><span data-stu-id="810d3-185">true</span></span>|<span data-ttu-id="810d3-186">null</span><span class="sxs-lookup"><span data-stu-id="810d3-186">null</span></span>|<span data-ttu-id="810d3-187">true</span><span class="sxs-lookup"><span data-stu-id="810d3-187">true</span></span>|  
|<span data-ttu-id="810d3-188">null</span><span class="sxs-lookup"><span data-stu-id="810d3-188">null</span></span>|<span data-ttu-id="810d3-189">false</span><span class="sxs-lookup"><span data-stu-id="810d3-189">false</span></span>|<span data-ttu-id="810d3-190">false</span><span class="sxs-lookup"><span data-stu-id="810d3-190">false</span></span>|<span data-ttu-id="810d3-191">null</span><span class="sxs-lookup"><span data-stu-id="810d3-191">null</span></span>|  
|<span data-ttu-id="810d3-192">null</span><span class="sxs-lookup"><span data-stu-id="810d3-192">null</span></span>|<span data-ttu-id="810d3-193">null</span><span class="sxs-lookup"><span data-stu-id="810d3-193">null</span></span>|<span data-ttu-id="810d3-194">null</span><span class="sxs-lookup"><span data-stu-id="810d3-194">null</span></span>|<span data-ttu-id="810d3-195">null</span><span class="sxs-lookup"><span data-stu-id="810d3-195">null</span></span>|  

<span data-ttu-id="810d3-196">那些運算子的行為和具有可為 Null 實值類型之一般運算子的行為並不相同。</span><span class="sxs-lookup"><span data-stu-id="810d3-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="810d3-197">一般而言，已針對某個實值類型之運算元定義的運算子，也可以搭配相對應可為 Null 實值類型的運算元使用。</span><span class="sxs-lookup"><span data-stu-id="810d3-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="810d3-198">如果該運算子的任何`null`運算元評估為`null`，則生成。</span><span class="sxs-lookup"><span data-stu-id="810d3-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="810d3-199">但是，`&`和`|`運算子可以生成非 null，即使其中一個運算元評估為`null`。</span><span class="sxs-lookup"><span data-stu-id="810d3-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="810d3-200">有關具有空數值型別的運算子行為的詳細資訊，請參閱["可取消數值型別"](../builtin-types/nullable-value-types.md)一文的["提升運算子"](../builtin-types/nullable-value-types.md#lifted-operators)部分。</span><span class="sxs-lookup"><span data-stu-id="810d3-200">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="810d3-201">您還可以使用`!`和`^`運算子與`bool?`運算元，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="810d3-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="810d3-202">條件邏輯運算子`&&`，`||`不支援`bool?`運算元。</span><span class="sxs-lookup"><span data-stu-id="810d3-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="810d3-203">複合指派</span><span class="sxs-lookup"><span data-stu-id="810d3-203">Compound assignment</span></span>

<span data-ttu-id="810d3-204">若是二元運算子 `op`，表單的複合指派運算式</span><span class="sxs-lookup"><span data-stu-id="810d3-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="810d3-205">相當於</span><span class="sxs-lookup"><span data-stu-id="810d3-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="810d3-206">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="810d3-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="810d3-207">`&`、`|` 和 `^` 運算子支援複合指派，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="810d3-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="810d3-208">條件邏輯運算子 `&&` 和 `||` 不支援複合指派。</span><span class="sxs-lookup"><span data-stu-id="810d3-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="810d3-209">運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="810d3-209">Operator precedence</span></span>

<span data-ttu-id="810d3-210">下列清單會依優先順序將邏輯運算子排序 (從最高到最低)：</span><span class="sxs-lookup"><span data-stu-id="810d3-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="810d3-211">邏輯否定運算子 `!`</span><span class="sxs-lookup"><span data-stu-id="810d3-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="810d3-212">邏輯 AND 運算子 `&`</span><span class="sxs-lookup"><span data-stu-id="810d3-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="810d3-213">邏輯互斥 OR 運算子 `^`</span><span class="sxs-lookup"><span data-stu-id="810d3-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="810d3-214">邏輯 OR 運算子 `|`</span><span class="sxs-lookup"><span data-stu-id="810d3-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="810d3-215">條件邏輯 AND 運算子 `&&`</span><span class="sxs-lookup"><span data-stu-id="810d3-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="810d3-216">條件邏輯 OR 運算子 `||`</span><span class="sxs-lookup"><span data-stu-id="810d3-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="810d3-217">使用括號 `()` 來變更由運算子優先順序所強制執行的評估順序：</span><span class="sxs-lookup"><span data-stu-id="810d3-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="810d3-218">有關按優先順序排序的 C# 運算子的完整清單，請參閱[C# 運算子](index.md)一文中的[運算子優先順序](index.md#operator-precedence)部分。</span><span class="sxs-lookup"><span data-stu-id="810d3-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="810d3-219">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="810d3-219">Operator overloadability</span></span>

<span data-ttu-id="810d3-220">使用者定義的類型可以[重載](operator-overloading.md) `!`、`&`和`|``^`運算子。</span><span class="sxs-lookup"><span data-stu-id="810d3-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="810d3-221">當二元運算子多載時，對應的複合指派運算子也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="810d3-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="810d3-222">使用者定義型別無法明確地多載複合指派運算子。</span><span class="sxs-lookup"><span data-stu-id="810d3-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="810d3-223">使用者定義類型無法多載條件邏輯運算子 `&&` 和 `||`。</span><span class="sxs-lookup"><span data-stu-id="810d3-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="810d3-224">不過，若使用者定義類型以某種方式多載 [True 和 False 運算子](true-false-operators.md)以及 `&` 或 `|` 運算子，就可以針對該類型的運算元個別評估 `&&` 或 `||` 作業。</span><span class="sxs-lookup"><span data-stu-id="810d3-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="810d3-225">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="810d3-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="810d3-226">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="810d3-226">C# language specification</span></span>

<span data-ttu-id="810d3-227">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="810d3-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="810d3-228">邏輯否定運算子</span><span class="sxs-lookup"><span data-stu-id="810d3-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="810d3-229">邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="810d3-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="810d3-230">條件邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="810d3-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="810d3-231">複合指派</span><span class="sxs-lookup"><span data-stu-id="810d3-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="810d3-232">另請參閱</span><span class="sxs-lookup"><span data-stu-id="810d3-232">See also</span></span>

- [<span data-ttu-id="810d3-233">C# 參考</span><span class="sxs-lookup"><span data-stu-id="810d3-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="810d3-234">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="810d3-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="810d3-235">位元與移位運算子</span><span class="sxs-lookup"><span data-stu-id="810d3-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
