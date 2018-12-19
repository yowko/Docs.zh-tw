---
title: '&amp;&amp; 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 82442f50275f21e0a0748951dc50628a8d7e11bb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243572"
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="c443e-102">&amp;&amp; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c443e-102">&amp;&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="c443e-103">條件式邏輯 AND 運算子 `&&`，也稱為「捷徑運算」邏輯 AND 運算子，會計算其 [bool](../keywords/bool.md) 運算元的邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="c443e-103">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="c443e-104">若 `x` 及 `y` 皆求出 `true`，那麼 `x && y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="c443e-104">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="c443e-105">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c443e-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="c443e-106">若第一個運算元的值為 `false`，就不會求第二個運算元的值，而運算結果會是 `false`。</span><span class="sxs-lookup"><span data-stu-id="c443e-106">If the first operand evaluates to `false`, the second operand is not evaluated and the result of operation is `false`.</span></span> <span data-ttu-id="c443e-107">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="c443e-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#And)]

<span data-ttu-id="c443e-108">[邏輯 AND 運算子](and-operator.md) `&`也會計算其 `bool` 運算元的邏輯 AND，但一律會求兩個運算元的值。</span><span class="sxs-lookup"><span data-stu-id="c443e-108">The [logical AND operator](and-operator.md) `&` also computes the logical AND of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="c443e-109">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="c443e-109">Operator overloadability</span></span>

<span data-ttu-id="c443e-110">使用者定義型別無法多載條件式邏輯 AND 運算子。</span><span class="sxs-lookup"><span data-stu-id="c443e-110">A user-defined type cannot overload the conditional logical AND operator.</span></span> <span data-ttu-id="c443e-111">不過，若使用者定義型別以某種方式多載[邏輯 AND](and-operator.md) 及 [true 和 false 運算子](../keywords/true-false-operators.md)，就可以針對該型別的運算元評估 `&&` 運算。</span><span class="sxs-lookup"><span data-stu-id="c443e-111">However, if a user-defined type overloads the [logical AND](and-operator.md) and [true and false operators](../keywords/true-false-operators.md) in a certain way, the `&&` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="c443e-112">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="c443e-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c443e-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c443e-113">C# language specification</span></span>

<span data-ttu-id="c443e-114">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[條件式邏輯運算子](~/_csharplang/spec/expressions.md#conditional-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="c443e-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c443e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c443e-115">See also</span></span>

- [<span data-ttu-id="c443e-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c443e-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c443e-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c443e-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c443e-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="c443e-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="c443e-119">|| 運算子</span><span class="sxs-lookup"><span data-stu-id="c443e-119">|| operator</span></span>](conditional-or-operator.md)
- [<span data-ttu-id="c443e-120">\! 運算子</span><span class="sxs-lookup"><span data-stu-id="c443e-120">! operator</span></span>](logical-negation-operator.md)
- [<span data-ttu-id="c443e-121">& 運算子</span><span class="sxs-lookup"><span data-stu-id="c443e-121">& operator</span></span>](and-operator.md)
