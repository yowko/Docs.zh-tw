---
title: '&lt; 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
ms.openlocfilehash: bb0f590bb547c4e632bd14c773f095435c8986f0
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655942"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="93681-102">&lt; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="93681-102">&lt; Operator (C# Reference)</span></span>

<span data-ttu-id="93681-103">若「小於」關係運算子的第一個運算元小於其第二個運算元，其 `<` 會傳回 `true`，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="93681-103">The "less than" relational operator `<` returns `true` if its first operand is less than its second operand, `false` otherwise.</span></span> <span data-ttu-id="93681-104">所有數值及列舉類型都支援 `<` 運算子。</span><span class="sxs-lookup"><span data-stu-id="93681-104">All numeric and enumeration types support the `<` operator.</span></span> <span data-ttu-id="93681-105">相同[列舉](../keywords/enum.md)類型的運算元會比較基礎整數型別的對應值。</span><span class="sxs-lookup"><span data-stu-id="93681-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="93681-106">對於關係運算子 `==`、`>`、`<`、`>=` 及 `<=`，若所有運算元皆為數字 (<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>) 時，運算的結果就會是 `false`。</span><span class="sxs-lookup"><span data-stu-id="93681-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="93681-107">這代表 `NaN` 的值皆不會大於、小於或等於任何其他 `double` (或 `float`) 的值。</span><span class="sxs-lookup"><span data-stu-id="93681-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="93681-108">如需詳細資訊和範例，請參閱 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 參考文章。</span><span class="sxs-lookup"><span data-stu-id="93681-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="93681-109">下列範例示範 `<` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="93681-109">The following example demonstrates the usage of the `<` operator:</span></span>

[!code-csharp-interactive[less than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Less)]

## <a name="operator-overloadability"></a><span data-ttu-id="93681-110">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="93681-110">Operator overloadability</span></span>

<span data-ttu-id="93681-111">使用者定義型別可以[多載](../keywords/operator.md) `<` 運算子。</span><span class="sxs-lookup"><span data-stu-id="93681-111">User-defined types can [overload](../keywords/operator.md) the `<` operator.</span></span> <span data-ttu-id="93681-112">若類型多載「小於」運算子 `<`，其也必須多載[「大於」運算子](greater-than-operator.md) `>`。</span><span class="sxs-lookup"><span data-stu-id="93681-112">If a type overloads the "less than" operator `<`, it must also overload the ["greater than" operator](greater-than-operator.md) `>`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="93681-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="93681-113">C# language specification</span></span>

<span data-ttu-id="93681-114">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="93681-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="93681-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93681-115">See also</span></span>

- [<span data-ttu-id="93681-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="93681-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="93681-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="93681-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="93681-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="93681-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="93681-119"><= 運算子</span><span class="sxs-lookup"><span data-stu-id="93681-119"><= Operator</span></span>](less-than-equal-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
