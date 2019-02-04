---
title: '> 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
ms.openlocfilehash: 3b036c491d9663bf4ab0971d84a0a8d58d902ee6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287205"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="89d31-102">> 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="89d31-102">> Operator (C# Reference)</span></span>

<span data-ttu-id="89d31-103">若「大於」關係運算子的第一個運算元大於其第二個運算元，其 `>` 會傳回 `true`，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="89d31-103">The "greater than" relational operator `>` returns `true` if its first operand is greater than its second operand, `false` otherwise.</span></span> <span data-ttu-id="89d31-104">所有數值及列舉類型都支援 `>` 運算子。</span><span class="sxs-lookup"><span data-stu-id="89d31-104">All numeric and enumeration types support the `>` operator.</span></span> <span data-ttu-id="89d31-105">相同[列舉](../keywords/enum.md)類型的運算元會比較基礎整數型別的對應值。</span><span class="sxs-lookup"><span data-stu-id="89d31-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="89d31-106">對於關係運算子 `==`、`>`、`<`、`>=` 及 `<=`，若所有運算元皆為數字 (<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>) 時，運算的結果就會是 `false`。</span><span class="sxs-lookup"><span data-stu-id="89d31-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="89d31-107">這代表 `NaN` 的值皆不會大於、小於或等於任何其他 `double` (或 `float`) 的值。</span><span class="sxs-lookup"><span data-stu-id="89d31-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="89d31-108">如需詳細資訊和範例，請參閱 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 參考文章。</span><span class="sxs-lookup"><span data-stu-id="89d31-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="89d31-109">下列範例示範 `>` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="89d31-109">The following example demonstrates the usage of the `>` operator:</span></span>

[!code-csharp-interactive[greater than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Greater)]

## <a name="operator-overloadability"></a><span data-ttu-id="89d31-110">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="89d31-110">Operator overloadability</span></span>

<span data-ttu-id="89d31-111">使用者定義型別可以[多載](../keywords/operator.md) `>` 運算子。</span><span class="sxs-lookup"><span data-stu-id="89d31-111">User-defined types can [overload](../keywords/operator.md) the `>` operator.</span></span> <span data-ttu-id="89d31-112">若類型多載「大於」運算子 `>`，其也必須多載[「小於」運算子](less-than-operator.md) `<`。</span><span class="sxs-lookup"><span data-stu-id="89d31-112">If a type overloads the "greater than" operator `>`, it must also overload the ["less than" operator](less-than-operator.md) `<`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="89d31-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="89d31-113">C# language specification</span></span>

<span data-ttu-id="89d31-114">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="89d31-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="89d31-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89d31-115">See also</span></span>

- [<span data-ttu-id="89d31-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="89d31-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="89d31-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="89d31-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="89d31-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="89d31-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="89d31-119">>= 運算子</span><span class="sxs-lookup"><span data-stu-id="89d31-119">>= Operator</span></span>](greater-than-equal-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
