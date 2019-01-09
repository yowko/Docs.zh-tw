---
title: == 運算子 - C# 參考
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: 6d86348eefc87e847267f262141ff49e5d51faae
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655955"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ed64e-102">== 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ed64e-102">== Operator (C# Reference)</span></span>

<span data-ttu-id="ed64e-103">等號比較運算子 `==` 會在其運算元相等時傳回 `true`，否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="ed64e-103">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

## <a name="value-types-equality"></a><span data-ttu-id="ed64e-104">實值型別相等</span><span class="sxs-lookup"><span data-stu-id="ed64e-104">Value types equality</span></span>

<span data-ttu-id="ed64e-105">若他們的值相等時，[內建實值型別](../keywords/value-types-table.md)的運算元就會相等：</span><span class="sxs-lookup"><span data-stu-id="ed64e-105">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="ed64e-106">對於關係運算子 `==`、`>`、`<`、`>=` 及 `<=`，若所有運算元皆為數字 (<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>) 時，運算的結果就會是 `false`。</span><span class="sxs-lookup"><span data-stu-id="ed64e-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="ed64e-107">這代表 `NaN` 的值皆不會大於、小於或等於任何其他 `double` (或 `float`) 的值。</span><span class="sxs-lookup"><span data-stu-id="ed64e-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="ed64e-108">如需詳細資訊和範例，請參閱 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 參考文章。</span><span class="sxs-lookup"><span data-stu-id="ed64e-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="ed64e-109">若基礎整數型別的對應值相等時，相同[列舉](../keywords/enum.md)類型的兩個運算元就會相等。</span><span class="sxs-lookup"><span data-stu-id="ed64e-109">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="ed64e-110">根據預設，`==` 運算子不會定義為使用者定義 [struct](../keywords/struct.md) 類型。</span><span class="sxs-lookup"><span data-stu-id="ed64e-110">By default, the `==` operator is not defined for a user-defined [struct](../keywords/struct.md) type.</span></span> <span data-ttu-id="ed64e-111">使用者定義型別可以[多載](#operator-overloadability) `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="ed64e-111">A user-defined type can [overload](#operator-overloadability) the `==` operator.</span></span>

<span data-ttu-id="ed64e-112">從 C# 7.3 說起，`==` 及 [`!=`](not-equal-operator.md) 運算子是由 C# [tuples](../../tuples.md) 所支援。</span><span class="sxs-lookup"><span data-stu-id="ed64e-112">Beginning with C# 7.3, the `==` and [`!=`](not-equal-operator.md) operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="ed64e-113">如需詳細資訊，請參閱 [C# Tuple 類型](../../tuples.md)一文中的[相等與 Tuple](../../tuples.md#equality-and-tuples)一節。</span><span class="sxs-lookup"><span data-stu-id="ed64e-113">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

## <a name="string-equality"></a><span data-ttu-id="ed64e-114">字串相等</span><span class="sxs-lookup"><span data-stu-id="ed64e-114">String equality</span></span>

<span data-ttu-id="ed64e-115">當兩個 [string](../keywords/string.md) 運算元皆為 `null`，或兩個 string 執行個體的長度相同且在各字元位置擁有完全相同的字元，兩者就會相等：</span><span class="sxs-lookup"><span data-stu-id="ed64e-115">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

<span data-ttu-id="ed64e-116">其為區分大小寫的序數比較。</span><span class="sxs-lookup"><span data-stu-id="ed64e-116">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="ed64e-117">如需如何比較字串的詳細資訊，請參閱[如何在 C# 中比較字串](../../how-to/compare-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="ed64e-117">For more information about how to compare strings, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

## <a name="reference-types-equality"></a><span data-ttu-id="ed64e-118">參考型別相等</span><span class="sxs-lookup"><span data-stu-id="ed64e-118">Reference types equality</span></span>

<span data-ttu-id="ed64e-119">當兩個不是 `string` 參考型別的運算元參考相同的物件時，兩者就會相等：</span><span class="sxs-lookup"><span data-stu-id="ed64e-119">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

<span data-ttu-id="ed64e-120">此範例顯示出使用者定義參考型別會支援 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="ed64e-120">The example shows that the `==` operator is supported by user-defined reference types.</span></span> <span data-ttu-id="ed64e-121">不過，使用者定義參考型別可以多載 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="ed64e-121">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="ed64e-122">若參考型別多載 `==` 運算子，請使用 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 方法檢查兩個該類型的參考是否參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="ed64e-122">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ed64e-123">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="ed64e-123">Operator overloadability</span></span>

<span data-ttu-id="ed64e-124">使用者定義型別可以[多載](../keywords/operator.md) `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="ed64e-124">User-defined types can [overload](../keywords/operator.md) the `==` operator.</span></span> <span data-ttu-id="ed64e-125">若類型多載等號比較運算子 `==`，其必須也多載[不等比較運算子](not-equal-operator.md) `!=`。</span><span class="sxs-lookup"><span data-stu-id="ed64e-125">If a type overloads the equality operator `==`, it must also overload the [inequality operator](not-equal-operator.md) `!=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ed64e-126">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ed64e-126">C# language specification</span></span>

<span data-ttu-id="ed64e-127">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="ed64e-127">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed64e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed64e-128">See also</span></span>

- [<span data-ttu-id="ed64e-129">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ed64e-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ed64e-130">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ed64e-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ed64e-131">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="ed64e-131">C# Operators</span></span>](index.md)
- [<span data-ttu-id="ed64e-132">相等比較</span><span class="sxs-lookup"><span data-stu-id="ed64e-132">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
