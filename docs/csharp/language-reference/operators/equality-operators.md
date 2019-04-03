---
title: 等號比較運算子 - C# 參考
ms.date: 03/28/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 98b96f5b4c6d6ea70687a97c849e89573c67c37e
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545887"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="17d3b-102">等號比較運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="17d3b-102">Equality operators (C# Reference)</span></span>

<span data-ttu-id="17d3b-103">[`==` (相等)](#equality-operator-) 和 [`!=` (不等)](#inequality-operator-) 運算子可檢查其運算元是否相等。</span><span class="sxs-lookup"><span data-stu-id="17d3b-103">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="17d3b-104">等號比較運算子 ==</span><span class="sxs-lookup"><span data-stu-id="17d3b-104">Equality operator ==</span></span>

<span data-ttu-id="17d3b-105">等號比較運算子 `==` 會在其運算元相等時傳回 `true`，否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="17d3b-105">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="17d3b-106">實值型別相等</span><span class="sxs-lookup"><span data-stu-id="17d3b-106">Value types equality</span></span>

<span data-ttu-id="17d3b-107">若他們的值相等時，[內建實值型別](../keywords/value-types-table.md)的運算元就會相等：</span><span class="sxs-lookup"><span data-stu-id="17d3b-107">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="17d3b-108">對於相等和關係運算子 `==`、`>`、`<`、`>=` 及 `<=`，若任何一個運算元不是數字 (<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>)，運算的結果就會是 `false`。</span><span class="sxs-lookup"><span data-stu-id="17d3b-108">For equality and relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="17d3b-109">這代表 `NaN` 的值皆不會大於、小於或等於任何其他 `double` (或 `float`) 的值，包括 `NaN`。</span><span class="sxs-lookup"><span data-stu-id="17d3b-109">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="17d3b-110">如需詳細資訊和範例，請參閱 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 參考文章。</span><span class="sxs-lookup"><span data-stu-id="17d3b-110">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="17d3b-111">若基礎整數型別的對應值相等時，相同[列舉](../keywords/enum.md)類型的兩個運算元就會相等。</span><span class="sxs-lookup"><span data-stu-id="17d3b-111">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="17d3b-112">使用者定義[結構](../keywords/struct.md)型別預設不支援 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="17d3b-112">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="17d3b-113">若要支援 `==` 運算子，使用者定義結構必須[多載](#operator-overloadability)它。</span><span class="sxs-lookup"><span data-stu-id="17d3b-113">To support the `==` operator, a user-defined struct must [overload](#operator-overloadability) it.</span></span>

<span data-ttu-id="17d3b-114">從 C# 7.3 開始，`==` 及 `!=` 運算子是由 C# [tuples](../../tuples.md) 所支援。</span><span class="sxs-lookup"><span data-stu-id="17d3b-114">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="17d3b-115">如需詳細資訊，請參閱 [C# Tuple 類型](../../tuples.md)一文中的[相等與 Tuple](../../tuples.md#equality-and-tuples)一節。</span><span class="sxs-lookup"><span data-stu-id="17d3b-115">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="string-equality"></a><span data-ttu-id="17d3b-116">字串相等</span><span class="sxs-lookup"><span data-stu-id="17d3b-116">String equality</span></span>

<span data-ttu-id="17d3b-117">當兩個 [string](../keywords/string.md) 運算元皆為 `null`，或兩個 string 執行個體的長度相同且在各字元位置擁有完全相同的字元，兩者就會相等：</span><span class="sxs-lookup"><span data-stu-id="17d3b-117">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

<span data-ttu-id="17d3b-118">其為區分大小寫的序數比較。</span><span class="sxs-lookup"><span data-stu-id="17d3b-118">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="17d3b-119">如需有關字串比較的詳細資訊，請參閱[如何在 C# 中比較字串](../../how-to/compare-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="17d3b-119">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="17d3b-120">參考型別相等</span><span class="sxs-lookup"><span data-stu-id="17d3b-120">Reference types equality</span></span>

<span data-ttu-id="17d3b-121">當兩個不是 `string` 參考型別的運算元參考相同的物件時，兩者就會相等：</span><span class="sxs-lookup"><span data-stu-id="17d3b-121">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

<span data-ttu-id="17d3b-122">如範例所示，使用者定義參考型別預設支援 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="17d3b-122">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="17d3b-123">不過，使用者定義參考型別可以多載 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="17d3b-123">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="17d3b-124">若參考型別多載 `==` 運算子，請使用 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 方法檢查兩個該類型的參考是否參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="17d3b-124">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="inequality-operator-"></a><span data-ttu-id="17d3b-125">不等比較運算子 !=</span><span class="sxs-lookup"><span data-stu-id="17d3b-125">Inequality operator !=</span></span>

<span data-ttu-id="17d3b-126">不等比較運算子 `!=` 會在其運算元不相等時傳回 `true`，否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="17d3b-126">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="17d3b-127">對於[內建類型](../keywords/built-in-types-table.md)的運算元，運算式 `x != y` 會產生與運算式 `!(x == y)` 相同的結果。</span><span class="sxs-lookup"><span data-stu-id="17d3b-127">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="17d3b-128">如需有關型別等號的詳細資訊，請參閱[等號比較運算子](#equality-operator-)一節。</span><span class="sxs-lookup"><span data-stu-id="17d3b-128">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="17d3b-129">下列範例示範 `!=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="17d3b-129">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="17d3b-130">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="17d3b-130">Operator overloadability</span></span>

<span data-ttu-id="17d3b-131">使用者定義型別可以[多載](../keywords/operator.md) `==` 和 `!=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="17d3b-131">User-defined types can [overload](../keywords/operator.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="17d3b-132">如果某個型別多載這兩個運算子之一，它也必須多載另一個運算子。</span><span class="sxs-lookup"><span data-stu-id="17d3b-132">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="17d3b-133">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="17d3b-133">C# language specification</span></span>

<span data-ttu-id="17d3b-134">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="17d3b-134">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17d3b-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17d3b-135">See also</span></span>

- [<span data-ttu-id="17d3b-136">C# 參考</span><span class="sxs-lookup"><span data-stu-id="17d3b-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="17d3b-137">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="17d3b-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="17d3b-138">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="17d3b-138">C# Operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="17d3b-139">相等比較</span><span class="sxs-lookup"><span data-stu-id="17d3b-139">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
