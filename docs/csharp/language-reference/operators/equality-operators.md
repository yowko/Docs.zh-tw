---
title: 等號比較運算子 - C# 參考
description: 深入了解 C# 等號比較運算子。
ms.date: 03/28/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: b4d3f3c0c6195fef22a33c47ad0b8c498f512f6a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753483"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="82f27-103">等號比較運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="82f27-103">Equality operators (C# Reference)</span></span>

<span data-ttu-id="82f27-104">[`==` (相等)](#equality-operator-) 和 [`!=` (不等)](#inequality-operator-) 運算子可檢查其運算元是否相等。</span><span class="sxs-lookup"><span data-stu-id="82f27-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="82f27-105">等號比較運算子 ==</span><span class="sxs-lookup"><span data-stu-id="82f27-105">Equality operator ==</span></span>

<span data-ttu-id="82f27-106">等號比較運算子 `==` 會在其運算元相等時傳回 `true`，否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="82f27-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="82f27-107">實值型別相等</span><span class="sxs-lookup"><span data-stu-id="82f27-107">Value types equality</span></span>

<span data-ttu-id="82f27-108">若他們的值相等時，[內建實值型別](../keywords/value-types-table.md)的運算元就會相等：</span><span class="sxs-lookup"><span data-stu-id="82f27-108">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="82f27-109">針對 `==`、[`<`、`>`、`<=` 和 `>=`](comparison-operators.md) 運算子，如果任何運算元不是數字 (<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>)，則作業的結果是 `false`。</span><span class="sxs-lookup"><span data-stu-id="82f27-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="82f27-110">這代表 `NaN` 的值皆不會大於、小於或等於任何其他 `double` (或 `float`) 的值，包括 `NaN`。</span><span class="sxs-lookup"><span data-stu-id="82f27-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="82f27-111">如需詳細資訊和範例，請參閱 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 參考文章。</span><span class="sxs-lookup"><span data-stu-id="82f27-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="82f27-112">若基礎整數型別的對應值相等時，相同[列舉](../keywords/enum.md)類型的兩個運算元就會相等。</span><span class="sxs-lookup"><span data-stu-id="82f27-112">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="82f27-113">使用者定義[結構](../keywords/struct.md)型別預設不支援 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="82f27-113">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="82f27-114">若要支援 `==` 運算子，使用者定義結構必須[多載](#operator-overloadability)它。</span><span class="sxs-lookup"><span data-stu-id="82f27-114">To support the `==` operator, a user-defined struct must [overload](#operator-overloadability) it.</span></span>

<span data-ttu-id="82f27-115">從 C# 7.3 開始，`==` 及 `!=` 運算子是由 C# [tuples](../../tuples.md) 所支援。</span><span class="sxs-lookup"><span data-stu-id="82f27-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="82f27-116">如需詳細資訊，請參閱 [C# Tuple 類型](../../tuples.md)一文中的[相等與 Tuple](../../tuples.md#equality-and-tuples)一節。</span><span class="sxs-lookup"><span data-stu-id="82f27-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="string-equality"></a><span data-ttu-id="82f27-117">字串相等</span><span class="sxs-lookup"><span data-stu-id="82f27-117">String equality</span></span>

<span data-ttu-id="82f27-118">當兩個 [string](../keywords/string.md) 運算元皆為 `null`，或兩個 string 執行個體的長度相同且在各字元位置擁有完全相同的字元，兩者就會相等：</span><span class="sxs-lookup"><span data-stu-id="82f27-118">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

<span data-ttu-id="82f27-119">其為區分大小寫的序數比較。</span><span class="sxs-lookup"><span data-stu-id="82f27-119">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="82f27-120">如需有關字串比較的詳細資訊，請參閱[如何在 C# 中比較字串](../../how-to/compare-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="82f27-120">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="82f27-121">參考型別相等</span><span class="sxs-lookup"><span data-stu-id="82f27-121">Reference types equality</span></span>

<span data-ttu-id="82f27-122">當兩個不是 `string` 參考型別的運算元參考相同的物件時，兩者就會相等：</span><span class="sxs-lookup"><span data-stu-id="82f27-122">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

<span data-ttu-id="82f27-123">如範例所示，使用者定義參考型別預設支援 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="82f27-123">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="82f27-124">不過，使用者定義參考型別可以多載 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="82f27-124">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="82f27-125">若參考型別多載 `==` 運算子，請使用 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 方法檢查兩個該類型的參考是否參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="82f27-125">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="inequality-operator-"></a><span data-ttu-id="82f27-126">不等比較運算子 !=</span><span class="sxs-lookup"><span data-stu-id="82f27-126">Inequality operator !=</span></span>

<span data-ttu-id="82f27-127">不等比較運算子 `!=` 會在其運算元不相等時傳回 `true`，否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="82f27-127">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="82f27-128">對於[內建類型](../keywords/built-in-types-table.md)的運算元，運算式 `x != y` 會產生與運算式 `!(x == y)` 相同的結果。</span><span class="sxs-lookup"><span data-stu-id="82f27-128">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="82f27-129">如需有關型別等號的詳細資訊，請參閱[等號比較運算子](#equality-operator-)一節。</span><span class="sxs-lookup"><span data-stu-id="82f27-129">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="82f27-130">下列範例示範 `!=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="82f27-130">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="82f27-131">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="82f27-131">Operator overloadability</span></span>

<span data-ttu-id="82f27-132">使用者定義類型可以[多載](../keywords/operator.md) `==` 和 `!=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="82f27-132">A user-defined type can [overload](../keywords/operator.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="82f27-133">如果某個型別多載這兩個運算子之一，它也必須多載另一個運算子。</span><span class="sxs-lookup"><span data-stu-id="82f27-133">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="82f27-134">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="82f27-134">C# language specification</span></span>

<span data-ttu-id="82f27-135">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="82f27-135">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="82f27-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82f27-136">See also</span></span>

- [<span data-ttu-id="82f27-137">C# 參考</span><span class="sxs-lookup"><span data-stu-id="82f27-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="82f27-138">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="82f27-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="82f27-139">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="82f27-139">C# Operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="82f27-140">相等比較</span><span class="sxs-lookup"><span data-stu-id="82f27-140">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="82f27-141">比較運算子</span><span class="sxs-lookup"><span data-stu-id="82f27-141">Comparison operators</span></span>](comparison-operators.md)
