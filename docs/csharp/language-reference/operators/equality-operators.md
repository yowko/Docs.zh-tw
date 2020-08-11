---
title: 等號比較運算子 - C# 參考
description: 深入了解 C# 等號比較運算子與 C# 型別等號。
ms.date: 06/26/2019
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
ms.openlocfilehash: 33215e2440b14fb888a6f0df5c220c891ebed0e2
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063090"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="e706a-103">等號比較運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e706a-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="e706a-104">[ `==` (相等的) ](#equality-operator-)和[ `!=` (不相等) ](#inequality-operator-)運算子會檢查其運算元是否相等。</span><span class="sxs-lookup"><span data-stu-id="e706a-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="e706a-105">等號比較運算子 ==</span><span class="sxs-lookup"><span data-stu-id="e706a-105">Equality operator ==</span></span>

<span data-ttu-id="e706a-106">等號比較運算子 `==` 會在其運算元相等時傳回 `true`，否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="e706a-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="e706a-107">實值型別相等</span><span class="sxs-lookup"><span data-stu-id="e706a-107">Value types equality</span></span>

<span data-ttu-id="e706a-108">若他們的值相等時，[內建實值型別](../builtin-types/value-types.md#built-in-value-types)的運算元就會相等：</span><span class="sxs-lookup"><span data-stu-id="e706a-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](snippets/shared/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="e706a-109">對於、、、 `==` [ `<` `>` `<=` 和 `>=` ](comparison-operators.md)運算子而言，如果任何運算元不是 (<xref:System.Double.NaN?displayProperty=nameWithType> 或) 的數位，作業 <xref:System.Single.NaN?displayProperty=nameWithType> 的結果會是 `false` 。</span><span class="sxs-lookup"><span data-stu-id="e706a-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="e706a-110">這代表 `NaN` 的值皆不會大於、小於或等於任何其他 `double` (或 `float`) 的值，包括 `NaN`。</span><span class="sxs-lookup"><span data-stu-id="e706a-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="e706a-111">如需詳細資訊和範例，請參閱 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 參考文章。</span><span class="sxs-lookup"><span data-stu-id="e706a-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="e706a-112">若基礎整數型別的對應值相等時，相同[列舉](../builtin-types/enum.md)類型的兩個運算元就會相等。</span><span class="sxs-lookup"><span data-stu-id="e706a-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="e706a-113">使用者定義[結構](../builtin-types/struct.md)型別預設不支援 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="e706a-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="e706a-114">若要支援 `==` 運算子，使用者定義結構必須[多載](operator-overloading.md)它。</span><span class="sxs-lookup"><span data-stu-id="e706a-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="e706a-115">從 C# 7.3 說起，`==` 及 `!=` 運算子是由 C# [tuples](../builtin-types/value-tuples.md) 所支援。</span><span class="sxs-lookup"><span data-stu-id="e706a-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="e706a-116">如需詳細資訊，請參閱「[元組類型](../builtin-types/value-tuples.md)」一文的「[元組相等](../builtin-types/value-tuples.md#tuple-equality)」一節。</span><span class="sxs-lookup"><span data-stu-id="e706a-116">For more information, see the [Tuple equality](../builtin-types/value-tuples.md#tuple-equality) section of the [Tuple types](../builtin-types/value-tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="e706a-117">參考型別相等</span><span class="sxs-lookup"><span data-stu-id="e706a-117">Reference types equality</span></span>

<span data-ttu-id="e706a-118">根據預設，當兩個參考型別的運算元參考相同物件時，兩者就相等：</span><span class="sxs-lookup"><span data-stu-id="e706a-118">By default, two reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](snippets/shared/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="e706a-119">如範例所示，使用者定義參考型別預設支援 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="e706a-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="e706a-120">不過，參考型別可以多載 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="e706a-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="e706a-121">若參考型別多載 `==` 運算子，請使用 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 方法檢查兩個該類型的參考是否參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="e706a-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="string-equality"></a><span data-ttu-id="e706a-122">字串相等</span><span class="sxs-lookup"><span data-stu-id="e706a-122">String equality</span></span>

<span data-ttu-id="e706a-123">當兩個 [string](../builtin-types/reference-types.md#the-string-type) 運算元皆為 `null`，或兩個 string 執行個體的長度相同且在各字元位置擁有完全相同的字元，兩者就會相等：</span><span class="sxs-lookup"><span data-stu-id="e706a-123">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](snippets/shared/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="e706a-124">這是區分大小寫的序數比較。</span><span class="sxs-lookup"><span data-stu-id="e706a-124">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="e706a-125">如需有關字串比較的詳細資訊，請參閱[如何在 C# 中比較字串](../../how-to/compare-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="e706a-125">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="e706a-126">委派等號</span><span class="sxs-lookup"><span data-stu-id="e706a-126">Delegate equality</span></span>

<span data-ttu-id="e706a-127">相同執行階段型別的兩個[委派](../../programming-guide/delegates/index.md)運算元都是 `null` 或其引動過程清單長度相同且每個位置都有相等的項目時，那兩個運算元相等：</span><span class="sxs-lookup"><span data-stu-id="e706a-127">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](snippets/shared/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="e706a-128">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[委派相等運算子](~/_csharplang/spec/expressions.md#delegate-equality-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="e706a-128">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="e706a-129">從語意相同之 [lambda 運算式](lambda-expressions.md)之評估產生的委派不相等，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e706a-129">Delegates that are produced from evaluation of semantically identical [lambda expressions](lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](snippets/shared/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="e706a-130">不等比較運算子 !=</span><span class="sxs-lookup"><span data-stu-id="e706a-130">Inequality operator !=</span></span>

<span data-ttu-id="e706a-131">不等比較運算子 `!=` 會在其運算元不相等時傳回 `true`，否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="e706a-131">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="e706a-132">對於[內建類型](../builtin-types/built-in-types.md)的運算元，運算式 `x != y` 會產生與運算式 `!(x == y)` 相同的結果。</span><span class="sxs-lookup"><span data-stu-id="e706a-132">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="e706a-133">如需有關型別等號的詳細資訊，請參閱[等號比較運算子](#equality-operator-)一節。</span><span class="sxs-lookup"><span data-stu-id="e706a-133">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="e706a-134">下列範例示範 `!=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="e706a-134">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](snippets/shared/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="e706a-135">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="e706a-135">Operator overloadability</span></span>

<span data-ttu-id="e706a-136">使用者定義類型可以[多載](operator-overloading.md)`==` 和 `!=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="e706a-136">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="e706a-137">如果型別多載兩個運算子的其中一個，它也必須多載另一個。</span><span class="sxs-lookup"><span data-stu-id="e706a-137">If a type overloads one of the two operators, it must also overload the other one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e706a-138">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e706a-138">C# language specification</span></span>

<span data-ttu-id="e706a-139">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="e706a-139">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e706a-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e706a-140">See also</span></span>

- [<span data-ttu-id="e706a-141">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="e706a-141">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e706a-142">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="e706a-142">C# operators and expressions</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e706a-143">相等比較</span><span class="sxs-lookup"><span data-stu-id="e706a-143">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="e706a-144">比較運算子</span><span class="sxs-lookup"><span data-stu-id="e706a-144">Comparison operators</span></span>](comparison-operators.md)
