---
title: 布林值邏輯運算子 - C# 參考
description: 了解能搭配布林值運算元執行邏輯否定、結合 (AND) 及內含和互斥分離 (OR) 作業的 C# 運算子。
ms.date: 04/08/2019
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
ms.openlocfilehash: 3ac3479de0bd3c95256741a8b3075f2e5786b65c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300106"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="cad3e-103">布林值邏輯運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="cad3e-103">Boolean logical operators (C# Reference)</span></span>

<span data-ttu-id="cad3e-104">下列運算子會搭配 [bool](../keywords/bool.md) 運算元執行邏輯作業：</span><span class="sxs-lookup"><span data-stu-id="cad3e-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="cad3e-105">一元 [`!` (邏輯否定)](#logical-negation-operator-) 運算子。</span><span class="sxs-lookup"><span data-stu-id="cad3e-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="cad3e-106">二元 [`&` (邏輯 AND)](#logical-and-operator-)、[`|` (邏輯 OR)](#logical-or-operator-) 及 [`^` (邏輯互斥 OR)](#logical-exclusive-or-operator-) 運算子。</span><span class="sxs-lookup"><span data-stu-id="cad3e-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="cad3e-107">那些運算子一律會評估兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="cad3e-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="cad3e-108">二元 [`&&` (條件邏輯 AND)](#conditional-logical-and-operator-) 及 [`||` (條件邏輯 OR)](#conditional-logical-or-operator-) 運算子。</span><span class="sxs-lookup"><span data-stu-id="cad3e-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="cad3e-109">那些運算子只會在必要時才評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="cad3e-109">Those operators evaluate the second operand only if it's necessary.</span></span>

<span data-ttu-id="cad3e-110">針對[整數](../keywords/integral-types-table.md)型別的運算元，`&`、`|` 和 `^` 運算子都會執行位元邏輯運算。</span><span class="sxs-lookup"><span data-stu-id="cad3e-110">For the operands of the [integral](../keywords/integral-types-table.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="cad3e-111">如需詳細資訊，請參閱[位元與移位運算子](bitwise-and-shift-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="cad3e-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="cad3e-112">邏輯否定運算子 !</span><span class="sxs-lookup"><span data-stu-id="cad3e-112">Logical negation operator !</span></span>

<span data-ttu-id="cad3e-113">`!` 運算子會計算其運算元的邏輯否定。</span><span class="sxs-lookup"><span data-stu-id="cad3e-113">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="cad3e-114">也就是說，它會在運算元評估為 `false` 時產生 `true`，並在運算元評估為 `true` 時產生 `false`：</span><span class="sxs-lookup"><span data-stu-id="cad3e-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Negation)]

## <a name="logical-and-operator-amp"></a><span data-ttu-id="cad3e-115">邏輯 AND 運算子 &amp;</span><span class="sxs-lookup"><span data-stu-id="cad3e-115">Logical AND operator &amp;</span></span>

<span data-ttu-id="cad3e-116">`&` 運算子會計算其運算元的邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="cad3e-116">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="cad3e-117">若 `x` 及 `y` 皆求出 `true`，那麼 `x & y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-117">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="cad3e-118">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-118">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="cad3e-119">即使第一個運算元的值為 `false`，`&` 運算子仍會求這兩個運算元的值，所以不論第二個運算元的值為何，其結果必定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-119">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span>

<span data-ttu-id="cad3e-120">在下列範例中，`&` 運算子的第二個運算元是方法呼叫；無論第一個運算元的值為何，系統都會執行該呼叫：</span><span class="sxs-lookup"><span data-stu-id="cad3e-120">In the following example, the second operand of the `&` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#And)]

<span data-ttu-id="cad3e-121">[條件邏輯 AND 運算子](#conditional-logical-and-operator-) `&&` 也會計算其運算元的邏輯 AND，但如果第一個運算元的值評估為 `false`，系統便不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="cad3e-121">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="cad3e-122">針對整數型別的運算元，`&` 運算子會計算其運算元的[位元邏輯 AND](bitwise-and-shift-operators.md#logical-and-operator-)。</span><span class="sxs-lookup"><span data-stu-id="cad3e-122">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="cad3e-123">一元的 `&` 運算子是 [address-of 運算子](pointer-related-operators.md#address-of-operator-)。</span><span class="sxs-lookup"><span data-stu-id="cad3e-123">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="cad3e-124">邏輯互斥 OR 運算子 ^</span><span class="sxs-lookup"><span data-stu-id="cad3e-124">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="cad3e-125">`^` 運算子會計算其運算元的邏輯互斥 OR，其也稱為邏輯 XOR。</span><span class="sxs-lookup"><span data-stu-id="cad3e-125">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="cad3e-126">如果 `x` 評估為 `true` 且 `y` 評估為 `false`，或是 `x` 評估為 `false` 且 `y` 評估為 `true` 時，`x ^ y` 的結果將會為 `true`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-126">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="cad3e-127">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-127">Otherwise, the result is `false`.</span></span> <span data-ttu-id="cad3e-128">也就是說，針對 `bool` 運算元，`^` 運算子的計算結果會與[不等比較運算子](equality-operators.md#inequality-operator-) `!=` 相同。</span><span class="sxs-lookup"><span data-stu-id="cad3e-128">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Xor)]

<span data-ttu-id="cad3e-129">針對整數型別的運算元，`^` 運算子會計算其運算元的[位元邏輯互斥 OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-)。</span><span class="sxs-lookup"><span data-stu-id="cad3e-129">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="cad3e-130">邏輯 OR 運算子 |</span><span class="sxs-lookup"><span data-stu-id="cad3e-130">Logical OR operator |</span></span>

<span data-ttu-id="cad3e-131">`|` 運算子會計算其運算元的邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="cad3e-131">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="cad3e-132">若 `x` 或 `y` 其中一項的值為 `true`，`x | y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-132">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="cad3e-133">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-133">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="cad3e-134">即使第一個運算元的值為 `true`，`|` 運算子仍會求這兩個運算元的值，所以不論第二個運算元的值為何，其結果必定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-134">The `|` operator evaluates both operands even if the first operand evaluates to `true`, so that the result must be `true` regardless of the value of the second operand.</span></span>

<span data-ttu-id="cad3e-135">在下列範例中，`|` 運算子的第二個運算元是方法呼叫；無論第一個運算元的值為何，系統都會執行該呼叫：</span><span class="sxs-lookup"><span data-stu-id="cad3e-135">In the following example, the second operand of the `|` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Or)]

<span data-ttu-id="cad3e-136">[條件邏輯 OR 運算子](#conditional-logical-or-operator-) `||` 也會計算其運算元的邏輯 OR，但如果第一個運算元的值評估為 `true`，系統便不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="cad3e-136">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the second operand if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="cad3e-137">針對整數型別的運算元，`|` 運算子會計算其運算元的[位元邏輯 OR](bitwise-and-shift-operators.md#logical-or-operator-)。</span><span class="sxs-lookup"><span data-stu-id="cad3e-137">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><span data-ttu-id="cad3e-138">條件邏輯 AND 運算子 &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="cad3e-138">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="cad3e-139">條件邏輯 AND 運算子 `&&`，也稱為「捷徑運算」邏輯 AND 運算子，會計算其運算元的邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="cad3e-139">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="cad3e-140">若 `x` 及 `y` 皆求出 `true`，那麼 `x && y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-140">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="cad3e-141">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-141">Otherwise, the result is `false`.</span></span> <span data-ttu-id="cad3e-142">如果第一個運算元評估值為 `false`，就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="cad3e-142">If the first operand evaluates to `false`, the second operand is not evaluated.</span></span>

<span data-ttu-id="cad3e-143">在下列範例中，`&&` 運算子的第二個運算元是方法呼叫；如果第一個運算元的值評估為 `false`，系統便不會執行該呼叫：</span><span class="sxs-lookup"><span data-stu-id="cad3e-143">In the following example, the second operand of the `&&` operator is a method call, which isn't performed if the first operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="cad3e-144">[邏輯 AND 運算子](#logical-and-operator-) `&` 也會計算其運算元的邏輯 AND，但一律會求兩個運算元的值。</span><span class="sxs-lookup"><span data-stu-id="cad3e-144">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="cad3e-145">條件邏輯 OR 運算子 ||</span><span class="sxs-lookup"><span data-stu-id="cad3e-145">Conditional logical OR operator ||</span></span>

<span data-ttu-id="cad3e-146">條件邏輯 OR 運算子 `||`，也稱為「捷徑運算」邏輯 OR 運算子，會計算其運算元的邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="cad3e-146">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="cad3e-147">若 `x` 或 `y` 其中一項的值為 `true`，`x || y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-147">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="cad3e-148">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-148">Otherwise, the result is `false`.</span></span> <span data-ttu-id="cad3e-149">如果第一個運算元評估值為 `true`，就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="cad3e-149">If the first operand evaluates to `true`, the second operand is not evaluated.</span></span>

<span data-ttu-id="cad3e-150">在下列範例中，`||` 運算子的第二個運算元是方法呼叫；如果第一個運算元的值評估為 `true`，系統便不會執行該呼叫：</span><span class="sxs-lookup"><span data-stu-id="cad3e-150">In the following example, the second operand of the `||` operator is a method call, which isn't performed if the first operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="cad3e-151">[邏輯 OR 運算子](#logical-or-operator-) `|` 也會計算其運算元的邏輯 OR，但一律會求兩個運算元的值。</span><span class="sxs-lookup"><span data-stu-id="cad3e-151">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="cad3e-152">可為 Null 的布林值邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="cad3e-152">Nullable Boolean logical operators</span></span>

<span data-ttu-id="cad3e-153">針對 `bool?` 運算元，`&` 和 `|` 運算子支援三值邏輯。</span><span class="sxs-lookup"><span data-stu-id="cad3e-153">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="cad3e-154">這些運算子的語意是由下列表格定義的：</span><span class="sxs-lookup"><span data-stu-id="cad3e-154">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="cad3e-155">x</span><span class="sxs-lookup"><span data-stu-id="cad3e-155">x</span></span>|<span data-ttu-id="cad3e-156">y</span><span class="sxs-lookup"><span data-stu-id="cad3e-156">y</span></span>|<span data-ttu-id="cad3e-157">x&y</span><span class="sxs-lookup"><span data-stu-id="cad3e-157">x&y</span></span>|<span data-ttu-id="cad3e-158">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="cad3e-158">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="cad3e-159">true</span><span class="sxs-lookup"><span data-stu-id="cad3e-159">true</span></span>|<span data-ttu-id="cad3e-160">true</span><span class="sxs-lookup"><span data-stu-id="cad3e-160">true</span></span>|<span data-ttu-id="cad3e-161">true</span><span class="sxs-lookup"><span data-stu-id="cad3e-161">true</span></span>|<span data-ttu-id="cad3e-162">true</span><span class="sxs-lookup"><span data-stu-id="cad3e-162">true</span></span>|  
|<span data-ttu-id="cad3e-163">true</span><span class="sxs-lookup"><span data-stu-id="cad3e-163">true</span></span>|<span data-ttu-id="cad3e-164">False</span><span class="sxs-lookup"><span data-stu-id="cad3e-164">false</span></span>|<span data-ttu-id="cad3e-165">false</span><span class="sxs-lookup"><span data-stu-id="cad3e-165">false</span></span>|<span data-ttu-id="cad3e-166">true</span><span class="sxs-lookup"><span data-stu-id="cad3e-166">true</span></span>|  
|<span data-ttu-id="cad3e-167">true</span><span class="sxs-lookup"><span data-stu-id="cad3e-167">true</span></span>|<span data-ttu-id="cad3e-168">null</span><span class="sxs-lookup"><span data-stu-id="cad3e-168">null</span></span>|<span data-ttu-id="cad3e-169">null</span><span class="sxs-lookup"><span data-stu-id="cad3e-169">null</span></span>|<span data-ttu-id="cad3e-170">true</span><span class="sxs-lookup"><span data-stu-id="cad3e-170">true</span></span>|  
|<span data-ttu-id="cad3e-171">False</span><span class="sxs-lookup"><span data-stu-id="cad3e-171">false</span></span>|<span data-ttu-id="cad3e-172">true</span><span class="sxs-lookup"><span data-stu-id="cad3e-172">true</span></span>|<span data-ttu-id="cad3e-173">False</span><span class="sxs-lookup"><span data-stu-id="cad3e-173">false</span></span>|<span data-ttu-id="cad3e-174">true</span><span class="sxs-lookup"><span data-stu-id="cad3e-174">true</span></span>|  
|<span data-ttu-id="cad3e-175">False</span><span class="sxs-lookup"><span data-stu-id="cad3e-175">false</span></span>|<span data-ttu-id="cad3e-176">False</span><span class="sxs-lookup"><span data-stu-id="cad3e-176">false</span></span>|<span data-ttu-id="cad3e-177">False</span><span class="sxs-lookup"><span data-stu-id="cad3e-177">false</span></span>|<span data-ttu-id="cad3e-178">False</span><span class="sxs-lookup"><span data-stu-id="cad3e-178">false</span></span>|  
|<span data-ttu-id="cad3e-179">False</span><span class="sxs-lookup"><span data-stu-id="cad3e-179">false</span></span>|<span data-ttu-id="cad3e-180">null</span><span class="sxs-lookup"><span data-stu-id="cad3e-180">null</span></span>|<span data-ttu-id="cad3e-181">False</span><span class="sxs-lookup"><span data-stu-id="cad3e-181">false</span></span>|<span data-ttu-id="cad3e-182">null</span><span class="sxs-lookup"><span data-stu-id="cad3e-182">null</span></span>|  
|<span data-ttu-id="cad3e-183">null</span><span class="sxs-lookup"><span data-stu-id="cad3e-183">null</span></span>|<span data-ttu-id="cad3e-184">true</span><span class="sxs-lookup"><span data-stu-id="cad3e-184">true</span></span>|<span data-ttu-id="cad3e-185">null</span><span class="sxs-lookup"><span data-stu-id="cad3e-185">null</span></span>|<span data-ttu-id="cad3e-186">true</span><span class="sxs-lookup"><span data-stu-id="cad3e-186">true</span></span>|  
|<span data-ttu-id="cad3e-187">null</span><span class="sxs-lookup"><span data-stu-id="cad3e-187">null</span></span>|<span data-ttu-id="cad3e-188">False</span><span class="sxs-lookup"><span data-stu-id="cad3e-188">false</span></span>|<span data-ttu-id="cad3e-189">False</span><span class="sxs-lookup"><span data-stu-id="cad3e-189">false</span></span>|<span data-ttu-id="cad3e-190">null</span><span class="sxs-lookup"><span data-stu-id="cad3e-190">null</span></span>|  
|<span data-ttu-id="cad3e-191">null</span><span class="sxs-lookup"><span data-stu-id="cad3e-191">null</span></span>|<span data-ttu-id="cad3e-192">null</span><span class="sxs-lookup"><span data-stu-id="cad3e-192">null</span></span>|<span data-ttu-id="cad3e-193">null</span><span class="sxs-lookup"><span data-stu-id="cad3e-193">null</span></span>|<span data-ttu-id="cad3e-194">null</span><span class="sxs-lookup"><span data-stu-id="cad3e-194">null</span></span>|  

<span data-ttu-id="cad3e-195">那些運算子的行為和具有可為 Null 實值類型之一般運算子的行為並不相同。</span><span class="sxs-lookup"><span data-stu-id="cad3e-195">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="cad3e-196">一般而言，已針對某個實值類型之運算元定義的運算子，也可以搭配相對應可為 Null 實值類型的運算元使用。</span><span class="sxs-lookup"><span data-stu-id="cad3e-196">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="cad3e-197">這種運算子會在其任何一個運算元為 `null` 的情況下產生 `null`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-197">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="cad3e-198">不過，就算其中一個運算元是 `null`，`&` 和 `|` 運算子仍可以產生非 Null。</span><span class="sxs-lookup"><span data-stu-id="cad3e-198">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="cad3e-199">如需具備可為 Null 實值類型之運算子行為的詳細資訊，請參閱[使用可為 Null 的類型](../../programming-guide/nullable-types/using-nullable-types.md)一文中的[運算子](../../programming-guide/nullable-types/using-nullable-types.md#operators)一節。</span><span class="sxs-lookup"><span data-stu-id="cad3e-199">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="cad3e-200">您也可以使用 `!` 和 `^` 運算子搭配 `bool?` 運算元，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="cad3e-200">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="cad3e-201">條件邏輯運算子 `&&` 和 `||` 不支援 `bool?` 運算元。</span><span class="sxs-lookup"><span data-stu-id="cad3e-201">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="cad3e-202">複合指派</span><span class="sxs-lookup"><span data-stu-id="cad3e-202">Compound assignment</span></span>

<span data-ttu-id="cad3e-203">若是二元運算子 `op`，表單的複合指派運算式</span><span class="sxs-lookup"><span data-stu-id="cad3e-203">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="cad3e-204">相當於</span><span class="sxs-lookup"><span data-stu-id="cad3e-204">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="cad3e-205">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="cad3e-205">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="cad3e-206">`&`、`|` 和 `^` 運算子支援複合指派，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="cad3e-206">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="cad3e-207">條件邏輯運算子 `&&` 和 `||` 不支援複合指派。</span><span class="sxs-lookup"><span data-stu-id="cad3e-207">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="cad3e-208">運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="cad3e-208">Operator precedence</span></span>

<span data-ttu-id="cad3e-209">下列清單會依優先順序將邏輯運算子排序 (從最高到最低)：</span><span class="sxs-lookup"><span data-stu-id="cad3e-209">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="cad3e-210">邏輯否定運算子 `!`</span><span class="sxs-lookup"><span data-stu-id="cad3e-210">Logical negation operator `!`</span></span>
- <span data-ttu-id="cad3e-211">邏輯 AND 運算子 `&`</span><span class="sxs-lookup"><span data-stu-id="cad3e-211">Logical AND operator `&`</span></span>
- <span data-ttu-id="cad3e-212">邏輯互斥 OR 運算子 `^`</span><span class="sxs-lookup"><span data-stu-id="cad3e-212">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="cad3e-213">邏輯 OR 運算子 `|`</span><span class="sxs-lookup"><span data-stu-id="cad3e-213">Logical OR operator `|`</span></span>
- <span data-ttu-id="cad3e-214">條件邏輯 AND 運算子 `&&`</span><span class="sxs-lookup"><span data-stu-id="cad3e-214">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="cad3e-215">條件邏輯 OR 運算子 `||`</span><span class="sxs-lookup"><span data-stu-id="cad3e-215">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="cad3e-216">使用括號 `()` 來變更由運算子優先順序所強制執行的評估順序：</span><span class="sxs-lookup"><span data-stu-id="cad3e-216">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Precedence)]

<span data-ttu-id="cad3e-217">如需按優先順序層級排序的 C# 運算子完整清單，請參閱 [C# 運算子](index.md)。</span><span class="sxs-lookup"><span data-stu-id="cad3e-217">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="cad3e-218">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="cad3e-218">Operator overloadability</span></span>

<span data-ttu-id="cad3e-219">使用者定義類型可以[多載](../keywords/operator.md) `!`、`&`、`|` 及 `^` 運算子。</span><span class="sxs-lookup"><span data-stu-id="cad3e-219">A user-defined type can [overload](../keywords/operator.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="cad3e-220">當二元運算子多載時，對應的複合指派運算子也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="cad3e-220">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="cad3e-221">使用者定義型別無法明確地多載複合指派運算子。</span><span class="sxs-lookup"><span data-stu-id="cad3e-221">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="cad3e-222">使用者定義類型無法多載條件邏輯運算子 `&&` 和 `||`。</span><span class="sxs-lookup"><span data-stu-id="cad3e-222">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="cad3e-223">不過，若使用者定義類型以某種方式多載 [True 和 False 運算子](true-false-operators.md)以及 `&` 或 `|` 運算子，就可以針對該類型的運算元個別評估 `&&` 或 `||` 作業。</span><span class="sxs-lookup"><span data-stu-id="cad3e-223">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="cad3e-224">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="cad3e-224">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cad3e-225">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="cad3e-225">C# language specification</span></span>

<span data-ttu-id="cad3e-226">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="cad3e-226">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="cad3e-227">邏輯否定運算子</span><span class="sxs-lookup"><span data-stu-id="cad3e-227">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="cad3e-228">邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="cad3e-228">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="cad3e-229">條件邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="cad3e-229">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="cad3e-230">複合指派</span><span class="sxs-lookup"><span data-stu-id="cad3e-230">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="cad3e-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cad3e-231">See also</span></span>

- [<span data-ttu-id="cad3e-232">C# 參考</span><span class="sxs-lookup"><span data-stu-id="cad3e-232">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cad3e-233">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cad3e-233">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cad3e-234">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="cad3e-234">C# Operators</span></span>](index.md)
- [<span data-ttu-id="cad3e-235">位元與移位運算子</span><span class="sxs-lookup"><span data-stu-id="cad3e-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
