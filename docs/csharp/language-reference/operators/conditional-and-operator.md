---
title: '&amp;&amp; 運算子 (C# 參考)'
ms.date: 11/06/2018
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: d0e6d9a5aedc7dc87393e3dea070bf442b3268dc
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "43529231"
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="0d2f3-102">&amp;&amp; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="0d2f3-102">&amp;&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="0d2f3-103">條件式邏輯 AND 運算子 `&&`，也稱為「捷徑運算」邏輯 AND 運算子，會計算其 [bool](../keywords/bool.md) 運算元的邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="0d2f3-103">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="0d2f3-104">若 `x` 及 `y` 皆求出 `true`，那麼 `x && y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="0d2f3-104">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="0d2f3-105">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="0d2f3-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="0d2f3-106">若第一個運算元的值為 `false`，就不會求第二個運算元的值，而運算結果會是 `false`。</span><span class="sxs-lookup"><span data-stu-id="0d2f3-106">If the first operand evaluates to `false`, the second operand is not evaluated and the result of operation is `false`.</span></span> <span data-ttu-id="0d2f3-107">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="0d2f3-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#And)]

<span data-ttu-id="0d2f3-108">[邏輯 AND 運算子](and-operator.md) `&`也會計算其 `bool` 運算元的邏輯 AND，但一律會求兩個運算元的值。</span><span class="sxs-lookup"><span data-stu-id="0d2f3-108">The [logical AND operator](and-operator.md) `&` also computes the logical AND of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="0d2f3-109">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="0d2f3-109">Operator overloadability</span></span>

<span data-ttu-id="0d2f3-110">使用者定義型別無法多載條件式邏輯 AND 運算子。</span><span class="sxs-lookup"><span data-stu-id="0d2f3-110">A user-defined type cannot overload the conditional logical AND operator.</span></span> <span data-ttu-id="0d2f3-111">不過，若使用者定義型別以某種方式多載[邏輯 AND](and-operator.md)、[true](../keywords/true-operator.md) 和 [false](../keywords/false-operator.md) 運算子，就可以為該類型運算元求 `&&` 運算的值。</span><span class="sxs-lookup"><span data-stu-id="0d2f3-111">However, if a user-defined type overloads the [logical AND](and-operator.md), [true](../keywords/true-operator.md), and [false](../keywords/false-operator.md) operators in a certain way, the `&&` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="0d2f3-112">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="0d2f3-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0d2f3-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="0d2f3-113">C# language specification</span></span>

<span data-ttu-id="0d2f3-114">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[條件式邏輯運算子](~/_csharplang/spec/expressions.md#conditional-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="0d2f3-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d2f3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d2f3-115">See also</span></span>

- [<span data-ttu-id="0d2f3-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0d2f3-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0d2f3-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0d2f3-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0d2f3-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="0d2f3-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="0d2f3-119">|| 運算子</span><span class="sxs-lookup"><span data-stu-id="0d2f3-119">|| operator</span></span>](conditional-or-operator.md)
- [<span data-ttu-id="0d2f3-120">\! 運算子</span><span class="sxs-lookup"><span data-stu-id="0d2f3-120">! operator</span></span>](logical-negation-operator.md)
- [<span data-ttu-id="0d2f3-121">& 運算子</span><span class="sxs-lookup"><span data-stu-id="0d2f3-121">& operator</span></span>](and-operator.md)
