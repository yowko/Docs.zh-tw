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
ms.openlocfilehash: de621b26334bbc9679ba7e48a9d5a0cbaec67eab
ms.sourcegitcommit: d21bee9dbd32b9540ad30f9d0e2e874227040be3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59427314"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="26d48-103">布林值邏輯運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="26d48-103">Boolean logical operators (C# Reference)</span></span>

<span data-ttu-id="26d48-104">下列運算子會搭配 [bool](../keywords/bool.md) 運算元執行邏輯作業：</span><span class="sxs-lookup"><span data-stu-id="26d48-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="26d48-105">一元 [`!` (邏輯否定)](#logical-negation-operator-) 運算子。</span><span class="sxs-lookup"><span data-stu-id="26d48-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="26d48-106">二元 [`&` (邏輯 AND)](#logical-and-operator-)、[`|` (邏輯 OR)](#logical-or-operator-) 及 [`^` (邏輯互斥 OR)](#logical-exclusive-or-operator-) 運算子。</span><span class="sxs-lookup"><span data-stu-id="26d48-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="26d48-107">那些運算子一律會評估兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="26d48-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="26d48-108">二元 [`&&` (條件邏輯 AND)](#conditional-logical-and-operator-) 及 [`||` (條件邏輯 OR)](#conditional-logical-or-operator-) 運算子。</span><span class="sxs-lookup"><span data-stu-id="26d48-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="26d48-109">那些運算子只會在必要時才評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="26d48-109">Those operators evaluate the second operand only if it's necessary.</span></span>

<span data-ttu-id="26d48-110">針對[整數](../keywords/integral-types-table.md)類型的運算元，`&`、`|` 及 `^` 運算子都會執行位元邏輯作業。</span><span class="sxs-lookup"><span data-stu-id="26d48-110">For the operands of [integral](../keywords/integral-types-table.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="26d48-111">邏輯否定運算子 !</span><span class="sxs-lookup"><span data-stu-id="26d48-111">Logical negation operator !</span></span>

<span data-ttu-id="26d48-112">`!` 運算子會計算其運算元的邏輯否定。</span><span class="sxs-lookup"><span data-stu-id="26d48-112">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="26d48-113">也就是說，它會在運算元評估為 `false` 時產生 `true`，並在運算元評估為 `true` 時產生 `false`：</span><span class="sxs-lookup"><span data-stu-id="26d48-113">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Negation)]

## <a name="logical-and-operator-amp"></a><span data-ttu-id="26d48-114">邏輯 AND 運算子 &amp;</span><span class="sxs-lookup"><span data-stu-id="26d48-114">Logical AND operator &amp;</span></span>

<span data-ttu-id="26d48-115">`&` 運算子會計算其運算元的邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="26d48-115">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="26d48-116">若 `x` 及 `y` 皆求出 `true`，那麼 `x & y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="26d48-116">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="26d48-117">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="26d48-117">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="26d48-118">即使第一個運算元的值為 `false`，`&` 運算子仍會求這兩個運算元的值，所以不論第二個運算元的值為何，其結果必定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="26d48-118">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span>

<span data-ttu-id="26d48-119">在下列範例中，`&` 運算子的第二個運算元是方法呼叫；無論第一個運算元的值為何，系統都會執行該呼叫：</span><span class="sxs-lookup"><span data-stu-id="26d48-119">In the following example, the second operand of the `&` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#And)]

<span data-ttu-id="26d48-120">[條件邏輯 AND 運算子](#conditional-logical-and-operator-) `&&` 也會計算其運算元的邏輯 AND，但如果第一個運算元的值評估為 `false`，系統便不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="26d48-120">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="26d48-121">針對整數類型的運算元，`&` 運算子會計算其運算元的[位元邏輯 AND](and-operator.md#integer-logical-bitwise-and-operator)。</span><span class="sxs-lookup"><span data-stu-id="26d48-121">For the operands of integral types, the `&` operator computes [bitwise logical AND](and-operator.md#integer-logical-bitwise-and-operator) of its operands.</span></span> <span data-ttu-id="26d48-122">一元的 `&` 運算子是 [address-of 運算子](and-operator.md#unary-address-of-operator)。</span><span class="sxs-lookup"><span data-stu-id="26d48-122">The unary `&` operator is the [address-of operator](and-operator.md#unary-address-of-operator).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="26d48-123">邏輯互斥 OR 運算子 ^</span><span class="sxs-lookup"><span data-stu-id="26d48-123">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="26d48-124">`^` 運算子會計算其運算元的邏輯互斥 OR，其也稱為邏輯 XOR。</span><span class="sxs-lookup"><span data-stu-id="26d48-124">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="26d48-125">如果 `x` 評估為 `true` 且 `y` 評估為 `false`，或是 `x` 評估為 `false` 且 `y` 評估為 `true` 時，`x ^ y` 的結果將會為 `true`。</span><span class="sxs-lookup"><span data-stu-id="26d48-125">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="26d48-126">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="26d48-126">Otherwise, the result is `false`.</span></span> <span data-ttu-id="26d48-127">也就是說，針對 `bool` 運算元，`^` 運算子的計算結果會與[不等比較運算子](equality-operators.md#inequality-operator-) `!=` 相同。</span><span class="sxs-lookup"><span data-stu-id="26d48-127">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Xor)]

<span data-ttu-id="26d48-128">針對整數類型的運算元，`^` 運算子會計算其運算元的[位元邏輯互斥 OR](xor-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="26d48-128">For the operands of integral types, the `^` operator computes [bitwise logical exclusive OR](xor-operator.md) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="26d48-129">邏輯 OR 運算子 |</span><span class="sxs-lookup"><span data-stu-id="26d48-129">Logical OR operator |</span></span>

<span data-ttu-id="26d48-130">`|` 運算子會計算其運算元的邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="26d48-130">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="26d48-131">若 `x` 或 `y` 其中一項的值為 `true`，`x | y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="26d48-131">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="26d48-132">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="26d48-132">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="26d48-133">即使第一個運算元的值為 `true`，`|` 運算子仍會求這兩個運算元的值，所以不論第二個運算元的值為何，其結果必定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="26d48-133">The `|` operator evaluates both operands even if the first operand evaluates to `true`, so that the result must be `true` regardless of the value of the second operand.</span></span>

<span data-ttu-id="26d48-134">在下列範例中，`|` 運算子的第二個運算元是方法呼叫；無論第一個運算元的值為何，系統都會執行該呼叫：</span><span class="sxs-lookup"><span data-stu-id="26d48-134">In the following example, the second operand of the `|` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Or)]

<span data-ttu-id="26d48-135">[條件邏輯 OR 運算子](#conditional-logical-or-operator-) `||` 也會計算其運算元的邏輯 OR，但如果第一個運算元的值評估為 `true`，系統便不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="26d48-135">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the second operand if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="26d48-136">針對整數類型的運算元，`|` 運算子會計算其運算元的[位元邏輯 OR](or-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="26d48-136">For the operands of integral types, the `|` operator computes [bitwise logical OR](or-operator.md) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><span data-ttu-id="26d48-137">條件邏輯 AND 運算子 &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="26d48-137">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="26d48-138">條件邏輯 AND 運算子 `&&`，也稱為「捷徑運算」邏輯 AND 運算子，會計算其運算元的邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="26d48-138">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="26d48-139">若 `x` 及 `y` 皆求出 `true`，那麼 `x && y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="26d48-139">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="26d48-140">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="26d48-140">Otherwise, the result is `false`.</span></span> <span data-ttu-id="26d48-141">如果第一個運算元評估值為 `false`，就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="26d48-141">If the first operand evaluates to `false`, the second operand is not evaluated.</span></span>

<span data-ttu-id="26d48-142">在下列範例中，`&&` 運算子的第二個運算元是方法呼叫；如果第一個運算元的值評估為 `false`，系統便不會執行該呼叫：</span><span class="sxs-lookup"><span data-stu-id="26d48-142">In the following example, the second operand of the `&&` operator is a method call, which isn't performed if the first operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="26d48-143">[邏輯 AND 運算子](#logical-and-operator-) `&` 也會計算其運算元的邏輯 AND，但一律會求兩個運算元的值。</span><span class="sxs-lookup"><span data-stu-id="26d48-143">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="26d48-144">條件邏輯 OR 運算子 ||</span><span class="sxs-lookup"><span data-stu-id="26d48-144">Conditional logical OR operator ||</span></span>

<span data-ttu-id="26d48-145">條件邏輯 OR 運算子 `||`，也稱為「捷徑運算」邏輯 OR 運算子，會計算其運算元的邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="26d48-145">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="26d48-146">若 `x` 或 `y` 其中一項的值為 `true`，`x || y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="26d48-146">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="26d48-147">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="26d48-147">Otherwise, the result is `false`.</span></span> <span data-ttu-id="26d48-148">如果第一個運算元評估值為 `true`，就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="26d48-148">If the first operand evaluates to `true`, the second operand is not evaluated.</span></span>

<span data-ttu-id="26d48-149">在下列範例中，`||` 運算子的第二個運算元是方法呼叫；如果第一個運算元的值評估為 `true`，系統便不會執行該呼叫：</span><span class="sxs-lookup"><span data-stu-id="26d48-149">In the following example, the second operand of the `||` operator is a method call, which isn't performed if the first operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="26d48-150">[邏輯 OR 運算子](#logical-or-operator-) `|` 也會計算其運算元的邏輯 OR，但一律會求兩個運算元的值。</span><span class="sxs-lookup"><span data-stu-id="26d48-150">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="26d48-151">可為 Null 的布林值邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="26d48-151">Nullable Boolean logical operators</span></span>

<span data-ttu-id="26d48-152">針對 `bool?` 運算元，`&` 和 `|` 運算子支援三值邏輯。</span><span class="sxs-lookup"><span data-stu-id="26d48-152">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="26d48-153">這些運算子的語意是由下列表格定義的：</span><span class="sxs-lookup"><span data-stu-id="26d48-153">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="26d48-154">x</span><span class="sxs-lookup"><span data-stu-id="26d48-154">x</span></span>|<span data-ttu-id="26d48-155">y</span><span class="sxs-lookup"><span data-stu-id="26d48-155">y</span></span>|<span data-ttu-id="26d48-156">x&y</span><span class="sxs-lookup"><span data-stu-id="26d48-156">x&y</span></span>|<span data-ttu-id="26d48-157">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="26d48-157">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="26d48-158">true</span><span class="sxs-lookup"><span data-stu-id="26d48-158">true</span></span>|<span data-ttu-id="26d48-159">true</span><span class="sxs-lookup"><span data-stu-id="26d48-159">true</span></span>|<span data-ttu-id="26d48-160">true</span><span class="sxs-lookup"><span data-stu-id="26d48-160">true</span></span>|<span data-ttu-id="26d48-161">true</span><span class="sxs-lookup"><span data-stu-id="26d48-161">true</span></span>|  
|<span data-ttu-id="26d48-162">true</span><span class="sxs-lookup"><span data-stu-id="26d48-162">true</span></span>|<span data-ttu-id="26d48-163">False</span><span class="sxs-lookup"><span data-stu-id="26d48-163">false</span></span>|<span data-ttu-id="26d48-164">false</span><span class="sxs-lookup"><span data-stu-id="26d48-164">false</span></span>|<span data-ttu-id="26d48-165">true</span><span class="sxs-lookup"><span data-stu-id="26d48-165">true</span></span>|  
|<span data-ttu-id="26d48-166">true</span><span class="sxs-lookup"><span data-stu-id="26d48-166">true</span></span>|<span data-ttu-id="26d48-167">null</span><span class="sxs-lookup"><span data-stu-id="26d48-167">null</span></span>|<span data-ttu-id="26d48-168">null</span><span class="sxs-lookup"><span data-stu-id="26d48-168">null</span></span>|<span data-ttu-id="26d48-169">true</span><span class="sxs-lookup"><span data-stu-id="26d48-169">true</span></span>|  
|<span data-ttu-id="26d48-170">False</span><span class="sxs-lookup"><span data-stu-id="26d48-170">false</span></span>|<span data-ttu-id="26d48-171">true</span><span class="sxs-lookup"><span data-stu-id="26d48-171">true</span></span>|<span data-ttu-id="26d48-172">False</span><span class="sxs-lookup"><span data-stu-id="26d48-172">false</span></span>|<span data-ttu-id="26d48-173">true</span><span class="sxs-lookup"><span data-stu-id="26d48-173">true</span></span>|  
|<span data-ttu-id="26d48-174">False</span><span class="sxs-lookup"><span data-stu-id="26d48-174">false</span></span>|<span data-ttu-id="26d48-175">False</span><span class="sxs-lookup"><span data-stu-id="26d48-175">false</span></span>|<span data-ttu-id="26d48-176">False</span><span class="sxs-lookup"><span data-stu-id="26d48-176">false</span></span>|<span data-ttu-id="26d48-177">False</span><span class="sxs-lookup"><span data-stu-id="26d48-177">false</span></span>|  
|<span data-ttu-id="26d48-178">False</span><span class="sxs-lookup"><span data-stu-id="26d48-178">false</span></span>|<span data-ttu-id="26d48-179">null</span><span class="sxs-lookup"><span data-stu-id="26d48-179">null</span></span>|<span data-ttu-id="26d48-180">False</span><span class="sxs-lookup"><span data-stu-id="26d48-180">false</span></span>|<span data-ttu-id="26d48-181">null</span><span class="sxs-lookup"><span data-stu-id="26d48-181">null</span></span>|  
|<span data-ttu-id="26d48-182">null</span><span class="sxs-lookup"><span data-stu-id="26d48-182">null</span></span>|<span data-ttu-id="26d48-183">true</span><span class="sxs-lookup"><span data-stu-id="26d48-183">true</span></span>|<span data-ttu-id="26d48-184">null</span><span class="sxs-lookup"><span data-stu-id="26d48-184">null</span></span>|<span data-ttu-id="26d48-185">true</span><span class="sxs-lookup"><span data-stu-id="26d48-185">true</span></span>|  
|<span data-ttu-id="26d48-186">null</span><span class="sxs-lookup"><span data-stu-id="26d48-186">null</span></span>|<span data-ttu-id="26d48-187">False</span><span class="sxs-lookup"><span data-stu-id="26d48-187">false</span></span>|<span data-ttu-id="26d48-188">False</span><span class="sxs-lookup"><span data-stu-id="26d48-188">false</span></span>|<span data-ttu-id="26d48-189">null</span><span class="sxs-lookup"><span data-stu-id="26d48-189">null</span></span>|  
|<span data-ttu-id="26d48-190">null</span><span class="sxs-lookup"><span data-stu-id="26d48-190">null</span></span>|<span data-ttu-id="26d48-191">null</span><span class="sxs-lookup"><span data-stu-id="26d48-191">null</span></span>|<span data-ttu-id="26d48-192">null</span><span class="sxs-lookup"><span data-stu-id="26d48-192">null</span></span>|<span data-ttu-id="26d48-193">null</span><span class="sxs-lookup"><span data-stu-id="26d48-193">null</span></span>|  

<span data-ttu-id="26d48-194">那些運算子的行為和具有可為 Null 實值類型之一般運算子的行為並不相同。</span><span class="sxs-lookup"><span data-stu-id="26d48-194">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="26d48-195">一般而言，已針對某個實值類型之運算元定義的運算子，也可以搭配相對應可為 Null 實值類型的運算元使用。</span><span class="sxs-lookup"><span data-stu-id="26d48-195">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="26d48-196">這種運算子會在其任何一個運算元為 `null` 的情況下產生 `null`。</span><span class="sxs-lookup"><span data-stu-id="26d48-196">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="26d48-197">不過，就算其中一個運算元是 `null`，`&` 和 `|` 運算子仍可以產生非 Null。</span><span class="sxs-lookup"><span data-stu-id="26d48-197">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="26d48-198">如需具備可為 Null 實值類型之運算子行為的詳細資訊，請參閱[使用可為 Null 的類型](../../programming-guide/nullable-types/using-nullable-types.md)一文中的[運算子](../../programming-guide/nullable-types/using-nullable-types.md#operators)一節。</span><span class="sxs-lookup"><span data-stu-id="26d48-198">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="26d48-199">您也可以使用 `!` 和 `^` 運算子搭配 `bool?` 運算元，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="26d48-199">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="26d48-200">條件邏輯運算子 `&&` 和 `||` 不支援 `bool?` 運算元。</span><span class="sxs-lookup"><span data-stu-id="26d48-200">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="26d48-201">複合指派</span><span class="sxs-lookup"><span data-stu-id="26d48-201">Compound assignment</span></span>

<span data-ttu-id="26d48-202">若是二元運算子 `op`，表單的複合指派運算式</span><span class="sxs-lookup"><span data-stu-id="26d48-202">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="26d48-203">相當於</span><span class="sxs-lookup"><span data-stu-id="26d48-203">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="26d48-204">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="26d48-204">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="26d48-205">`&`、`|` 和 `^` 運算子支援複合指派，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="26d48-205">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="26d48-206">條件邏輯運算子 `&&` 和 `||` 不支援複合指派。</span><span class="sxs-lookup"><span data-stu-id="26d48-206">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="26d48-207">運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="26d48-207">Operator precedence</span></span>

<span data-ttu-id="26d48-208">下列清單會依優先順序將邏輯運算子排序 (從最高到最低)：</span><span class="sxs-lookup"><span data-stu-id="26d48-208">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="26d48-209">邏輯否定運算子</span><span class="sxs-lookup"><span data-stu-id="26d48-209">Logical negation operator</span></span> `!`
- <span data-ttu-id="26d48-210">邏輯 AND 運算子</span><span class="sxs-lookup"><span data-stu-id="26d48-210">Logical AND operator</span></span> `&`
- <span data-ttu-id="26d48-211">邏輯互斥 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="26d48-211">Logical exclusive OR operator</span></span> `^`
- <span data-ttu-id="26d48-212">邏輯 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="26d48-212">Logical OR operator</span></span> `|`
- <span data-ttu-id="26d48-213">條件邏輯 AND 運算子</span><span class="sxs-lookup"><span data-stu-id="26d48-213">Conditional logical AND operator</span></span> `&&`
- <span data-ttu-id="26d48-214">條件邏輯 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="26d48-214">Conditional logical OR operator</span></span> `||`

<span data-ttu-id="26d48-215">使用括號 `()` 來變更由運算子優先順序所強制執行的評估順序：</span><span class="sxs-lookup"><span data-stu-id="26d48-215">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Precedence)]

<span data-ttu-id="26d48-216">如需按優先順序層級排序的 C# 運算子完整清單，請參閱 [C# 運算子](index.md)。</span><span class="sxs-lookup"><span data-stu-id="26d48-216">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="26d48-217">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="26d48-217">Operator overloadability</span></span>

<span data-ttu-id="26d48-218">使用者定義類型可以[多載](../keywords/operator.md) `!`、`&`、`|` 及 `^` 運算子。</span><span class="sxs-lookup"><span data-stu-id="26d48-218">A user-defined type can [overload](../keywords/operator.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="26d48-219">當二元運算子多載時，對應的複合指派運算子也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="26d48-219">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="26d48-220">使用者定義型別無法明確地多載複合指派運算子。</span><span class="sxs-lookup"><span data-stu-id="26d48-220">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="26d48-221">使用者定義類型無法多載條件邏輯運算子 `&&` 和 `||`。</span><span class="sxs-lookup"><span data-stu-id="26d48-221">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="26d48-222">不過，若使用者定義類型以某種方式多載 [True 和 False 運算子](../keywords/true-false-operators.md)以及 `&` 或 `|` 運算子，就可以針對該類型的運算元個別評估 `&&` 或 `||` 作業。</span><span class="sxs-lookup"><span data-stu-id="26d48-222">However, if a user-defined type overloads the [true and false operators](../keywords/true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="26d48-223">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="26d48-223">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="26d48-224">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="26d48-224">C# language specification</span></span>

<span data-ttu-id="26d48-225">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="26d48-225">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="26d48-226">邏輯否定運算子</span><span class="sxs-lookup"><span data-stu-id="26d48-226">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="26d48-227">邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="26d48-227">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="26d48-228">條件邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="26d48-228">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)

## <a name="see-also"></a><span data-ttu-id="26d48-229">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26d48-229">See also</span></span>

- [<span data-ttu-id="26d48-230">C# 參考</span><span class="sxs-lookup"><span data-stu-id="26d48-230">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="26d48-231">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="26d48-231">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="26d48-232">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="26d48-232">C# Operators</span></span>](index.md)
