---
title: 'C # 運算子和運算式-c # 參考'
description: '瞭解 c # 運算子和運算式、運算子優先順序和運算子的關聯性'
ms.date: 08/04/2020
f1_keywords:
- cs.operators
helpviewer_keywords:
- operators [C#]
- operator precedence [C#]
- operator associativity [C#]
- expressions [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 9ada39a2144e5565a76a25df0f83424710ad939f
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916810"
---
# <a name="c-operators-and-expressions-c-reference"></a><span data-ttu-id="13f3b-103">C # 運算子和運算式 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="13f3b-103">C# operators and expressions (C# reference)</span></span>

<span data-ttu-id="13f3b-104">C # 提供一些運算子。</span><span class="sxs-lookup"><span data-stu-id="13f3b-104">C# provides a number of operators.</span></span> <span data-ttu-id="13f3b-105">[內建類型](../builtin-types/built-in-types.md)支援其中許多，而且可讓您使用這些類型的值來執行基本作業。</span><span class="sxs-lookup"><span data-stu-id="13f3b-105">Many of them are supported by the [built-in types](../builtin-types/built-in-types.md) and allow you to perform basic operations with values of those types.</span></span> <span data-ttu-id="13f3b-106">這些運算子包含下列群組：</span><span class="sxs-lookup"><span data-stu-id="13f3b-106">Those operators include the following groups:</span></span>

- <span data-ttu-id="13f3b-107">使用數值運算元執行算數運算的[算術運算子](arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="13f3b-107">[Arithmetic operators](arithmetic-operators.md) that perform arithmetic operations with numeric operands</span></span>
- <span data-ttu-id="13f3b-108">比較數值運算元的[比較運算子](comparison-operators.md)</span><span class="sxs-lookup"><span data-stu-id="13f3b-108">[Comparison operators](comparison-operators.md) that compare numeric operands</span></span>
- <span data-ttu-id="13f3b-109">使用運算元執行邏輯運算的[布林邏輯運算子](boolean-logical-operators.md) [`bool`](../builtin-types/bool.md)</span><span class="sxs-lookup"><span data-stu-id="13f3b-109">[Boolean logical operators](boolean-logical-operators.md) that perform logical operations with [`bool`](../builtin-types/bool.md) operands</span></span>
- <span data-ttu-id="13f3b-110">使用整數類型的運算元來執行位 or 移位運算的[位 and 移位運算子](bitwise-and-shift-operators.md)</span><span class="sxs-lookup"><span data-stu-id="13f3b-110">[Bitwise and shift operators](bitwise-and-shift-operators.md) that perform bitwise or shift operations with operands of the integral types</span></span>
- <span data-ttu-id="13f3b-111">檢查其運算元是否相等的[等號比較運算子](equality-operators.md)</span><span class="sxs-lookup"><span data-stu-id="13f3b-111">[Equality operators](equality-operators.md) that check if their operands are equal or not</span></span>

<span data-ttu-id="13f3b-112">一般來說，您可以多[載這些運算子，也就](operator-overloading.md)是指定使用者定義型別之運算元的運算子行為。</span><span class="sxs-lookup"><span data-stu-id="13f3b-112">Typically, you can [overload](operator-overloading.md) those operators, that is, specify the operator behavior for the operands of a user-defined type.</span></span>

<span data-ttu-id="13f3b-113">最簡單的 c # 運算式是常值 (例如，[整數](../builtin-types/integral-numeric-types.md#integer-literals)和[實數](../builtin-types/floating-point-numeric-types.md#real-literals)) 和變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="13f3b-113">The simplest C# expressions are literals (for example, [integer](../builtin-types/integral-numeric-types.md#integer-literals) and [real](../builtin-types/floating-point-numeric-types.md#real-literals) numbers) and names of variables.</span></span> <span data-ttu-id="13f3b-114">您可以使用運算子將它們結合成複雜的運算式。</span><span class="sxs-lookup"><span data-stu-id="13f3b-114">You can combine them into complex expressions by using operators.</span></span> <span data-ttu-id="13f3b-115">運算子[優先順序](#operator-precedence)和[關聯](#operator-associativity)性決定運算式中作業的執行順序。</span><span class="sxs-lookup"><span data-stu-id="13f3b-115">Operator [precedence](#operator-precedence) and [associativity](#operator-associativity) determine the order in which the operations in an expression are performed.</span></span> <span data-ttu-id="13f3b-116">您可以使用括弧來變更由運算子優先順序和關聯性強制執行的評估順序。</span><span class="sxs-lookup"><span data-stu-id="13f3b-116">You can use parentheses to change the order of evaluation imposed by operator precedence and associativity.</span></span>

<span data-ttu-id="13f3b-117">在下列程式碼中，運算式的範例位於指派的右手邊：</span><span class="sxs-lookup"><span data-stu-id="13f3b-117">In the following code, examples of expressions are at the right-hand side of assignments:</span></span>

[!code-csharp[expression examples](snippets/shared/Overview.cs#Expressions)]

<span data-ttu-id="13f3b-118">通常，運算式會產生結果，而且可以包含在另一個運算式中。</span><span class="sxs-lookup"><span data-stu-id="13f3b-118">Typically, an expression produces a result and can be included in another expression.</span></span> <span data-ttu-id="13f3b-119">[`void`](../builtin-types/void.md)方法呼叫是不會產生結果之運算式的範例。</span><span class="sxs-lookup"><span data-stu-id="13f3b-119">A [`void`](../builtin-types/void.md) method call is an example of an expression that doesn't produce a result.</span></span> <span data-ttu-id="13f3b-120">它只能當做[語句](../../programming-guide/statements-expressions-operators/statements.md)使用，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="13f3b-120">It can be used only as a [statement](../../programming-guide/statements-expressions-operators/statements.md), as the following example shows:</span></span>

```csharp
Console.WriteLine("Hello, world!");
```

<span data-ttu-id="13f3b-121">以下是 c # 提供的其他運算式類型：</span><span class="sxs-lookup"><span data-stu-id="13f3b-121">Here are some other kinds of expressions that C# provides:</span></span>

- <span data-ttu-id="13f3b-122">[插補字串運算式](../tokens/interpolated.md)，提供方便的語法來建立格式化的字串：</span><span class="sxs-lookup"><span data-stu-id="13f3b-122">[Interpolated string expressions](../tokens/interpolated.md) that provide convenient syntax to create formatted strings:</span></span>

  [!code-csharp-interactive[interpolated string](snippets/shared/Overview.cs#InterpolatedString)]

- <span data-ttu-id="13f3b-123">可讓您建立匿名函數的[Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)：</span><span class="sxs-lookup"><span data-stu-id="13f3b-123">[Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) that allow you to create anonymous functions:</span></span>

  [!code-csharp-interactive[lambda expression](snippets/shared/Overview.cs#Lambda)]

- <span data-ttu-id="13f3b-124">[查詢運算式](../keywords/query-keywords.md)可讓您直接在 c # 中使用查詢功能：</span><span class="sxs-lookup"><span data-stu-id="13f3b-124">[Query expressions](../keywords/query-keywords.md) that allow you to use query capabilities directly in C#:</span></span>

  [!code-csharp-interactive[query expression](snippets/shared/Overview.cs#Query)]

<span data-ttu-id="13f3b-125">您可以使用[運算式主體定義](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)來提供方法、函式、屬性、索引子或完成項的簡潔定義。</span><span class="sxs-lookup"><span data-stu-id="13f3b-125">You can use an [expression body definition](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to provide a concise definition for a method, constructor, property, indexer, or finalizer.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="13f3b-126">運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="13f3b-126">Operator precedence</span></span>

<span data-ttu-id="13f3b-127">在具有多個運算子的運算式中，具有較高優先順序的運算子會在優先順序較低的運算子之前進行評估。</span><span class="sxs-lookup"><span data-stu-id="13f3b-127">In an expression with multiple operators, the operators with higher precedence are evaluated before the operators with lower precedence.</span></span> <span data-ttu-id="13f3b-128">在下列範例中，因為乘法的優先順序高於加法，所以會先執行乘法：</span><span class="sxs-lookup"><span data-stu-id="13f3b-128">In the following example, the multiplication is performed first because it has higher precedence than addition:</span></span>

```csharp-interactive
var a = 2 + 2 * 2;
Console.WriteLine(a); //  output: 6
```

<span data-ttu-id="13f3b-129">使用括弧變更由運算子優先順序強制執行的評估順序：</span><span class="sxs-lookup"><span data-stu-id="13f3b-129">Use parentheses to change the order of evaluation imposed by operator precedence:</span></span>

```csharp-interactive
var a = (2 + 2) * 2;
Console.WriteLine(a); //  output: 8
```

<span data-ttu-id="13f3b-130">下表列出 C# 運算子，從最高優先順序開始到最低優先順序。</span><span class="sxs-lookup"><span data-stu-id="13f3b-130">The following table lists the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="13f3b-131">每個資料列中的運算子都具有相同的優先順序。</span><span class="sxs-lookup"><span data-stu-id="13f3b-131">The operators within each row have the same precedence.</span></span>

| <span data-ttu-id="13f3b-132">操作員</span><span class="sxs-lookup"><span data-stu-id="13f3b-132">Operators</span></span> | <span data-ttu-id="13f3b-133">類別或名稱</span><span class="sxs-lookup"><span data-stu-id="13f3b-133">Category or name</span></span> |
| --------- | ---------------- |
| <span data-ttu-id="13f3b-134">[x-y](member-access-operators.md#member-access-expression-)、 [f (x) ](member-access-operators.md#invocation-expression-)、 [&#91;i&#93;](member-access-operators.md#indexer-operator-)、 [`x?.y`](member-access-operators.md#null-conditional-operators--and-) 、 [`x?[y]`](member-access-operators.md#null-conditional-operators--and-) 、 [x + +](arithmetic-operators.md#increment-operator-)、 [x--](arithmetic-operators.md#decrement-operator---)、 [x！](null-forgiving.md)、 [new](new-operator.md)、 [typeof](type-testing-and-cast.md#typeof-operator)、 [checked](../keywords/checked.md)、 [unchecked](../keywords/unchecked.md)、 [default](default.md)、 [nameof](nameof.md)、 [delegate](delegate-operator.md)、 [sizeof](sizeof.md)、 [stackalloc](stackalloc.md)、 [x->y](pointer-related-operators.md#pointer-member-access-operator--)</span><span class="sxs-lookup"><span data-stu-id="13f3b-134">[x.y](member-access-operators.md#member-access-expression-), [f(x)](member-access-operators.md#invocation-expression-), [a&#91;i&#93;](member-access-operators.md#indexer-operator-), [`x?.y`](member-access-operators.md#null-conditional-operators--and-), [`x?[y]`](member-access-operators.md#null-conditional-operators--and-), [x++](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---), [x!](null-forgiving.md), [new](new-operator.md), [typeof](type-testing-and-cast.md#typeof-operator), [checked](../keywords/checked.md), [unchecked](../keywords/unchecked.md), [default](default.md), [nameof](nameof.md), [delegate](delegate-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [x->y](pointer-related-operators.md#pointer-member-access-operator--)</span></span> | <span data-ttu-id="13f3b-135">主要</span><span class="sxs-lookup"><span data-stu-id="13f3b-135">Primary</span></span> |
| <span data-ttu-id="13f3b-136">[+ x](arithmetic-operators.md#unary-plus-and-minus-operators)， [-x](arithmetic-operators.md#unary-plus-and-minus-operators)， [ \! x](boolean-logical-operators.md#logical-negation-operator-)， [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-)， [+ + x](arithmetic-operators.md#increment-operator-)， [--x](arithmetic-operators.md#decrement-operator---)， [^ x](member-access-operators.md#index-from-end-operator-)， [ (T) x](type-testing-and-cast.md#cast-expression)， [await](await.md)， [&x](pointer-related-operators.md#address-of-operator-)， [\* x](pointer-related-operators.md#pointer-indirection-operator-)， [true 和 false](true-false-operators.md)</span><span class="sxs-lookup"><span data-stu-id="13f3b-136">[+x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [\!x](boolean-logical-operators.md#logical-negation-operator-), [~x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++x](arithmetic-operators.md#increment-operator-), [--x](arithmetic-operators.md#decrement-operator---), [^x](member-access-operators.md#index-from-end-operator-), [(T)x](type-testing-and-cast.md#cast-expression), [await](await.md), [&x](pointer-related-operators.md#address-of-operator-), [\*x](pointer-related-operators.md#pointer-indirection-operator-), [true and false](true-false-operators.md)</span></span> | <span data-ttu-id="13f3b-137">一元 (Unary)</span><span class="sxs-lookup"><span data-stu-id="13f3b-137">Unary</span></span> |
| [<span data-ttu-id="13f3b-138">x.。y</span><span class="sxs-lookup"><span data-stu-id="13f3b-138">x..y</span></span>](member-access-operators.md#range-operator-) | <span data-ttu-id="13f3b-139">範圍</span><span class="sxs-lookup"><span data-stu-id="13f3b-139">Range</span></span> |
| [<span data-ttu-id="13f3b-140">switch</span><span class="sxs-lookup"><span data-stu-id="13f3b-140">switch</span></span>](switch-expression.md) | <span data-ttu-id="13f3b-141">`switch` 運算式</span><span class="sxs-lookup"><span data-stu-id="13f3b-141">`switch` expression</span></span> |
| <span data-ttu-id="13f3b-142">[x \* y](arithmetic-operators.md#multiplication-operator-)、[x / y](arithmetic-operators.md#division-operator-)、[x % y](arithmetic-operators.md#remainder-operator-)</span><span class="sxs-lookup"><span data-stu-id="13f3b-142">[x \* y](arithmetic-operators.md#multiplication-operator-), [x / y](arithmetic-operators.md#division-operator-), [x % y](arithmetic-operators.md#remainder-operator-)</span></span> | <span data-ttu-id="13f3b-143">乘法</span><span class="sxs-lookup"><span data-stu-id="13f3b-143">Multiplicative</span></span>|
| <span data-ttu-id="13f3b-144">[x + y](arithmetic-operators.md#addition-operator-)、[x – y](arithmetic-operators.md#subtraction-operator--)</span><span class="sxs-lookup"><span data-stu-id="13f3b-144">[x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--)</span></span> | <span data-ttu-id="13f3b-145">加法</span><span class="sxs-lookup"><span data-stu-id="13f3b-145">Additive</span></span> |
| <span data-ttu-id="13f3b-146">[x \<\<  y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-)</span><span class="sxs-lookup"><span data-stu-id="13f3b-146">[x \<\<  y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-)</span></span> | <span data-ttu-id="13f3b-147">Shift</span><span class="sxs-lookup"><span data-stu-id="13f3b-147">Shift</span></span> |
| <span data-ttu-id="13f3b-148">[x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-)， [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x > = y](comparison-operators.md#greater-than-or-equal-operator-)，[是](type-testing-and-cast.md#is-operator)， [as](type-testing-and-cast.md#as-operator)</span><span class="sxs-lookup"><span data-stu-id="13f3b-148">[x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x >= y](comparison-operators.md#greater-than-or-equal-operator-), [is](type-testing-and-cast.md#is-operator), [as](type-testing-and-cast.md#as-operator)</span></span> | <span data-ttu-id="13f3b-149">關聯性和型別測試</span><span class="sxs-lookup"><span data-stu-id="13f3b-149">Relational and type-testing</span></span> |
| <span data-ttu-id="13f3b-150">[x = = y](equality-operators.md#equality-operator-)， [x！ = y](equality-operators.md#inequality-operator-)</span><span class="sxs-lookup"><span data-stu-id="13f3b-150">[x == y](equality-operators.md#equality-operator-), [x != y](equality-operators.md#inequality-operator-)</span></span> | <span data-ttu-id="13f3b-151">等式</span><span class="sxs-lookup"><span data-stu-id="13f3b-151">Equality</span></span> |
| `x & y` | <span data-ttu-id="13f3b-152">[布林值邏輯 AND](boolean-logical-operators.md#logical-and-operator-) 或[位元邏輯 AND](bitwise-and-shift-operators.md#logical-and-operator-)</span><span class="sxs-lookup"><span data-stu-id="13f3b-152">[Boolean logical AND](boolean-logical-operators.md#logical-and-operator-) or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-)</span></span> |
| `x ^ y` | <span data-ttu-id="13f3b-153">[布林值邏輯 XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) 或[位元邏輯 XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="13f3b-153">[Boolean logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-)</span></span> |
| <code>x &#124; y</code> | <span data-ttu-id="13f3b-154">[布林值邏輯 OR](boolean-logical-operators.md#logical-or-operator-) 或[位元邏輯 OR](bitwise-and-shift-operators.md#logical-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="13f3b-154">[Boolean logical OR](boolean-logical-operators.md#logical-or-operator-) or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-)</span></span> |
| [<span data-ttu-id="13f3b-155">x && y</span><span class="sxs-lookup"><span data-stu-id="13f3b-155">x && y</span></span>](boolean-logical-operators.md#conditional-logical-and-operator-) | <span data-ttu-id="13f3b-156">條件式 AND</span><span class="sxs-lookup"><span data-stu-id="13f3b-156">Conditional AND</span></span> |
| [<span data-ttu-id="13f3b-157">x &#124;&#124; y</span><span class="sxs-lookup"><span data-stu-id="13f3b-157">x &#124;&#124; y</span></span>](boolean-logical-operators.md#conditional-logical-or-operator-) | <span data-ttu-id="13f3b-158">條件式 OR</span><span class="sxs-lookup"><span data-stu-id="13f3b-158">Conditional OR</span></span> |
| [<span data-ttu-id="13f3b-159">x ?? y</span><span class="sxs-lookup"><span data-stu-id="13f3b-159">x ?? y</span></span>](null-coalescing-operator.md) | <span data-ttu-id="13f3b-160">Null 聯合運算子</span><span class="sxs-lookup"><span data-stu-id="13f3b-160">Null-coalescing operator</span></span> |
| [<span data-ttu-id="13f3b-161">c ? t : f</span><span class="sxs-lookup"><span data-stu-id="13f3b-161">c ? t : f</span></span>](conditional-operator.md) | <span data-ttu-id="13f3b-162">條件運算子</span><span class="sxs-lookup"><span data-stu-id="13f3b-162">Conditional operator</span></span> |
| <span data-ttu-id="13f3b-163">[x = y](assignment-operator.md)， [x + = y](arithmetic-operators.md#compound-assignment)， [x-= y](arithmetic-operators.md#compound-assignment)， [x \* = y](arithmetic-operators.md#compound-assignment)， [x/= y](arithmetic-operators.md#compound-assignment)， [x% = y](arithmetic-operators.md#compound-assignment)， [x &= y](boolean-logical-operators.md#compound-assignment)， [x &#124;= y](boolean-logical-operators.md#compound-assignment)，x [^ =](boolean-logical-operators.md#compound-assignment)y，x [ <<= y](bitwise-and-shift-operators.md#compound-assignment)， [x >>= y](bitwise-and-shift-operators.md#compound-assignment)， [x？？= y](null-coalescing-operator.md)，[=>](lambda-operator.md)</span><span class="sxs-lookup"><span data-stu-id="13f3b-163">[x = y](assignment-operator.md), [x += y](arithmetic-operators.md#compound-assignment), [x -= y](arithmetic-operators.md#compound-assignment), [x \*= y](arithmetic-operators.md#compound-assignment), [x /= y](arithmetic-operators.md#compound-assignment), [x %= y](arithmetic-operators.md#compound-assignment), [x &= y](boolean-logical-operators.md#compound-assignment), [x &#124;= y](boolean-logical-operators.md#compound-assignment), [x ^= y](boolean-logical-operators.md#compound-assignment), [x <<= y](bitwise-and-shift-operators.md#compound-assignment), [x >>= y](bitwise-and-shift-operators.md#compound-assignment), [x ??= y](null-coalescing-operator.md), [=>](lambda-operator.md)</span></span> | <span data-ttu-id="13f3b-164">指派和 Lambda 宣告</span><span class="sxs-lookup"><span data-stu-id="13f3b-164">Assignment and lambda declaration</span></span> |

## <a name="operator-associativity"></a><span data-ttu-id="13f3b-165">運算子關聯性</span><span class="sxs-lookup"><span data-stu-id="13f3b-165">Operator associativity</span></span>

<span data-ttu-id="13f3b-166">當運算子具有相同的優先順序時，運算子的關聯性會決定作業的執行順序：</span><span class="sxs-lookup"><span data-stu-id="13f3b-166">When operators have the same precedence, associativity of the operators determines the order in which the operations are performed:</span></span>

- <span data-ttu-id="13f3b-167">*左關聯*運算子會依序從左至右進行評估。</span><span class="sxs-lookup"><span data-stu-id="13f3b-167">*Left-associative* operators are evaluated in order from left to right.</span></span> <span data-ttu-id="13f3b-168">除了[指派運算子](assignment-operator.md)和[null 聯合運算子](null-coalescing-operator.md)以外，所有二元運算子都是靠左關聯。</span><span class="sxs-lookup"><span data-stu-id="13f3b-168">Except for the [assignment operators](assignment-operator.md) and the [null-coalescing operators](null-coalescing-operator.md), all binary operators are left-associative.</span></span> <span data-ttu-id="13f3b-169">例如，`a + b - c` 會判斷值為 `(a + b) - c`。</span><span class="sxs-lookup"><span data-stu-id="13f3b-169">For example, `a + b - c` is evaluated as `(a + b) - c`.</span></span>
- <span data-ttu-id="13f3b-170">*右向關聯*運算子會依序從右至左進行評估。</span><span class="sxs-lookup"><span data-stu-id="13f3b-170">*Right-associative* operators are evaluated in order from right to left.</span></span> <span data-ttu-id="13f3b-171">指派運算子、null 聯合運算子和[條件運算子 `?:` ](conditional-operator.md)是右向關聯。</span><span class="sxs-lookup"><span data-stu-id="13f3b-171">The assignment operators, the null-coalescing operators, and the [conditional operator `?:`](conditional-operator.md) are right-associative.</span></span> <span data-ttu-id="13f3b-172">例如，`x = y = z` 會判斷值為 `x = (y = z)`。</span><span class="sxs-lookup"><span data-stu-id="13f3b-172">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="13f3b-173">使用括弧來變更由運算子關聯性強制執行的評估順序：</span><span class="sxs-lookup"><span data-stu-id="13f3b-173">Use parentheses to change the order of evaluation imposed by operator associativity:</span></span>

```csharp-interactive
int a = 13 / 5 / 2;
int b = 13 / (5 / 2);
Console.WriteLine($"a = {a}, b = {b}");  // output: a = 1, b = 6
```

## <a name="operand-evaluation"></a><span data-ttu-id="13f3b-174">運算元評估</span><span class="sxs-lookup"><span data-stu-id="13f3b-174">Operand evaluation</span></span>

<span data-ttu-id="13f3b-175">與運算子優先順序和關聯性無關，運算式中的運算元會由左至右評估。</span><span class="sxs-lookup"><span data-stu-id="13f3b-175">Unrelated to operator precedence and associativity, operands in an expression are evaluated from left to right.</span></span> <span data-ttu-id="13f3b-176">下列範例示範了運算子和運算元的評估順序：</span><span class="sxs-lookup"><span data-stu-id="13f3b-176">The following examples demonstrate the order in which operators and operands are evaluated:</span></span>

| <span data-ttu-id="13f3b-177">運算是</span><span class="sxs-lookup"><span data-stu-id="13f3b-177">Expression</span></span> | <span data-ttu-id="13f3b-178">評估順序</span><span class="sxs-lookup"><span data-stu-id="13f3b-178">Order of evaluation</span></span> |
| ---------- | ------------------- |
|`a + b`|<span data-ttu-id="13f3b-179">a，b，+</span><span class="sxs-lookup"><span data-stu-id="13f3b-179">a, b, +</span></span>|
|`a + b * c`|<span data-ttu-id="13f3b-180">a，b，c，\*，+</span><span class="sxs-lookup"><span data-stu-id="13f3b-180">a, b, c, \*, +</span></span>|
|`a / b + c * d`|<span data-ttu-id="13f3b-181">a，b，/，c，d，\*，+</span><span class="sxs-lookup"><span data-stu-id="13f3b-181">a, b, /, c, d, \*, +</span></span>|
|`a / (b + c) * d`|<span data-ttu-id="13f3b-182">a，b，c，+，/，d，\*</span><span class="sxs-lookup"><span data-stu-id="13f3b-182">a, b, c, +, /, d, \*</span></span>|

<span data-ttu-id="13f3b-183">通常會評估所有運算子運算元。</span><span class="sxs-lookup"><span data-stu-id="13f3b-183">Typically, all operator operands are evaluated.</span></span> <span data-ttu-id="13f3b-184">不過，有些運算子會有條件地評估運算元。</span><span class="sxs-lookup"><span data-stu-id="13f3b-184">However, some operators evaluate operands conditionally.</span></span> <span data-ttu-id="13f3b-185">也就是說，這類運算子最左邊運算元的值會定義 (還是應該評估其他運算元) 。</span><span class="sxs-lookup"><span data-stu-id="13f3b-185">That is, the value of the leftmost operand of such an operator defines if (or which) other operands should be evaluated.</span></span> <span data-ttu-id="13f3b-186">這些運算子是條件式邏輯[AND (`&&`) ](boolean-logical-operators.md#conditional-logical-and-operator-)和[或 (`||`) ](boolean-logical-operators.md#conditional-logical-or-operator-)運算子、 [null 聯合運算子 `??` 和 `??=` ](null-coalescing-operator.md)、 [null 條件運算子 `?.` 和 `?[]` ](member-access-operators.md#null-conditional-operators--and-)和[條件運算子 `?:` ](conditional-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="13f3b-186">These operators are the conditional logical [AND (`&&`)](boolean-logical-operators.md#conditional-logical-and-operator-) and [OR (`||`)](boolean-logical-operators.md#conditional-logical-or-operator-) operators, the [null-coalescing operators `??` and `??=`](null-coalescing-operator.md), the [null-conditional operators `?.` and `?[]`](member-access-operators.md#null-conditional-operators--and-), and the [conditional operator `?:`](conditional-operator.md).</span></span> <span data-ttu-id="13f3b-187">如需詳細資訊，請參閱每個運算子的說明。</span><span class="sxs-lookup"><span data-stu-id="13f3b-187">For more information, see the description of each operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="13f3b-188">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="13f3b-188">C# language specification</span></span>

<span data-ttu-id="13f3b-189">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="13f3b-189">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="13f3b-190">運算式</span><span class="sxs-lookup"><span data-stu-id="13f3b-190">Expressions</span></span>](~/_csharplang/spec/expressions.md)
- [<span data-ttu-id="13f3b-191">運算子</span><span class="sxs-lookup"><span data-stu-id="13f3b-191">Operators</span></span>](~/_csharplang/spec/expressions.md#operators)

## <a name="see-also"></a><span data-ttu-id="13f3b-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13f3b-192">See also</span></span>

- [<span data-ttu-id="13f3b-193">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="13f3b-193">C# reference</span></span>](../index.md)
- [<span data-ttu-id="13f3b-194">運算子多載</span><span class="sxs-lookup"><span data-stu-id="13f3b-194">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="13f3b-195">運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="13f3b-195">Expression trees</span></span>](../../programming-guide/concepts/expression-trees/index.md)
