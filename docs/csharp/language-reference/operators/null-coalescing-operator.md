---
title: ?? 運算子 - C# 參考
ms.custom: seodec18
ms.date: 06/07/2019
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 8ca97261b348b7813ab179abbc1f2c5f535966a1
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816017"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="be744-103">??</span><span class="sxs-lookup"><span data-stu-id="be744-103">??</span></span> <span data-ttu-id="be744-104">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="be744-104">operator (C# Reference)</span></span>

<span data-ttu-id="be744-105">如果 Null 聯合運算子 `??` 不是 `null`，會傳回其左方運算元的值；否則它會評估右方運算元，並傳回其結果。</span><span class="sxs-lookup"><span data-stu-id="be744-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="be744-106">如果左方運算元評估為非 Null，`??` 運算子不會評估其右方運算元。</span><span class="sxs-lookup"><span data-stu-id="be744-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="be744-107">Null 聯合運算子是右向關聯運算子，亦即，以下形式的運算式</span><span class="sxs-lookup"><span data-stu-id="be744-107">The null-coalescing operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ?? b ?? c
```

<span data-ttu-id="be744-108">評估為</span><span class="sxs-lookup"><span data-stu-id="be744-108">is evaluated as</span></span>

```csharp
a ?? (b ?? c)
```

<span data-ttu-id="be744-109">`??` 運算子在下列案例中很有用：</span><span class="sxs-lookup"><span data-stu-id="be744-109">The `??` operator can be useful in the following scenarios:</span></span>

- <span data-ttu-id="be744-110">在使用 [Null 聯合運算子 ?. 和 ?[]](member-access-operators.md#null-conditional-operators--and-) 的運算式中，您可以使用 Null 聯合運算子在 Null 條件運算的結果為 `null` 的運算式中，提供用於評估的替代運算式：</span><span class="sxs-lookup"><span data-stu-id="be744-110">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="be744-111">當您使用[可為 Null 的實值型別](../../programming-guide/nullable-types/index.md)，而且需要提供基礎實值型別的值時，請使用 Null 聯合運算子，在可為 Null 的實值型別為 `null` 時，指定要提供的值：</span><span class="sxs-lookup"><span data-stu-id="be744-111">When you work with [nullable value types](../../programming-guide/nullable-types/index.md) and need to provide a value of an underlying value type, use the null-coalescing operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="be744-112">如果可為 Null 型別的值為 `null` 時要使用的值為基礎實值型別的預設值，請使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="be744-112">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="be744-113">從 C# 7.0 開始，您可以使用 [`throw` 運算式](../keywords/throw.md#the-throw-expression)作為 Null 聯合運算子的右方運算元，讓引數檢查程式碼更簡潔：</span><span class="sxs-lookup"><span data-stu-id="be744-113">Starting with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the null-coalescing operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="be744-114">上述範例中也會示範如何使用[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)定義屬性。</span><span class="sxs-lookup"><span data-stu-id="be744-114">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="be744-115">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="be744-115">Operator overloadability</span></span>

<span data-ttu-id="be744-116">無法多載 Null 聯合運算子。</span><span class="sxs-lookup"><span data-stu-id="be744-116">The null-coalescing operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="be744-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="be744-117">C# language specification</span></span>

<span data-ttu-id="be744-118">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [Null 聯合運算子](~/_csharplang/spec/expressions.md#the-null-coalescing-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="be744-118">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="be744-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be744-119">See also</span></span>

- [<span data-ttu-id="be744-120">C# 參考</span><span class="sxs-lookup"><span data-stu-id="be744-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="be744-121">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="be744-121">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="be744-122">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="be744-122">C# operators</span></span>](index.md)
- <span data-ttu-id="be744-123">[?. 和 ?[] 運算子](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="be744-123">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="be744-124">?: 運算子</span><span class="sxs-lookup"><span data-stu-id="be744-124">?: operator</span></span>](conditional-operator.md)
