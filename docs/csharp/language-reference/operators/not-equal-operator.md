---
title: '!= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 939b5664dba4345e62a43fb2f8d4d5379659d6aa
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610173"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9874a-102">!= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="9874a-102">!= Operator (C# Reference)</span></span>

<span data-ttu-id="9874a-103">不等比較運算子 `!=` 會在其運算元不相等時傳回 `true`，否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="9874a-103">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="9874a-104">對於[內建類型](../keywords/built-in-types-table.md)的運算元，運算式 `x != y` 會產生與運算式 `!(x == y)` 相同的結果。</span><span class="sxs-lookup"><span data-stu-id="9874a-104">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="9874a-105">如需詳細資訊，請參閱 [== 運算子](equality-comparison-operator.md)一文。</span><span class="sxs-lookup"><span data-stu-id="9874a-105">For more information, see the [== Operator](equality-comparison-operator.md) article.</span></span>

<span data-ttu-id="9874a-106">下列範例示範 `!=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="9874a-106">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="9874a-107">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="9874a-107">Operator overloadability</span></span>

<span data-ttu-id="9874a-108">使用者定義型別可以[多載](../keywords/operator.md) `!=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="9874a-108">User-defined types can [overload](../keywords/operator.md) the `!=` operator.</span></span> <span data-ttu-id="9874a-109">若類型多載不等比較運算子 `!=`，其必須也多載[等號比較運算子](equality-comparison-operator.md) `==`。</span><span class="sxs-lookup"><span data-stu-id="9874a-109">If a type overloads the inequality operator `!=`, it must also overload the [equality operator](equality-comparison-operator.md) `==`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9874a-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9874a-110">C# language specification</span></span>

<span data-ttu-id="9874a-111">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="9874a-111">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9874a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9874a-112">See also</span></span>

- [<span data-ttu-id="9874a-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="9874a-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9874a-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9874a-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9874a-115">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="9874a-115">C# Operators</span></span>](index.md)
- [<span data-ttu-id="9874a-116">相等比較</span><span class="sxs-lookup"><span data-stu-id="9874a-116">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
