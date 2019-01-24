---
title: '|| 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: 079c021eb68ece097c7f644416f1e9469a82dcea
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415425"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="02aba-102">|| 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="02aba-102">|| Operator (C# Reference)</span></span>

<span data-ttu-id="02aba-103">條件式邏輯 OR 運算子 `||`，也稱為「捷徑運算」邏輯 OR 運算子，會計算其 [bool](../keywords/bool.md) 運算元的邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="02aba-103">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="02aba-104">若 `x` 或 `y` 其中一項的值為 `true`，`x || y` 的結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="02aba-104">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="02aba-105">否則，結果為 `false`。</span><span class="sxs-lookup"><span data-stu-id="02aba-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="02aba-106">若第一個運算元的值為 `true`，就不會求第二個運算元的值，而運算結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="02aba-106">If the first operand evaluates to `true`, the second operand is not evaluated and the result of operation is `true`.</span></span> <span data-ttu-id="02aba-107">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="02aba-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#Or)]

<span data-ttu-id="02aba-108">[邏輯 OR 運算子](or-operator.md) `|` 也會計算其 `bool` 運算元的邏輯 OR，但一律會求兩個運算元的值。</span><span class="sxs-lookup"><span data-stu-id="02aba-108">The [logical OR operator](or-operator.md) `|` also computes the logical OR of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="02aba-109">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="02aba-109">Operator overloadability</span></span>

<span data-ttu-id="02aba-110">使用者定義型別無法多載條件式邏輯 OR 運算子。</span><span class="sxs-lookup"><span data-stu-id="02aba-110">A user-defined type cannot overload the conditional logical OR operator.</span></span> <span data-ttu-id="02aba-111">不過，若使用者定義型別以某種方式多載[邏輯 OR](or-operator.md) 及 [true 和 false 運算子](../keywords/true-false-operators.md)，就可以針對該類型的運算元評估 `||` 運算。</span><span class="sxs-lookup"><span data-stu-id="02aba-111">However, if a user-defined type overloads the [logical OR](or-operator.md) and [true and false operators](../keywords/true-false-operators.md) in a certain way, the `||` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="02aba-112">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[使用者定義條件式邏輯運算子](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="02aba-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="02aba-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="02aba-113">C# language specification</span></span>

<span data-ttu-id="02aba-114">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[條件式邏輯運算子](~/_csharplang/spec/expressions.md#conditional-logical-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="02aba-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="02aba-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02aba-115">See also</span></span>

- [<span data-ttu-id="02aba-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="02aba-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="02aba-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="02aba-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="02aba-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="02aba-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="02aba-119">&& 運算子</span><span class="sxs-lookup"><span data-stu-id="02aba-119">&& operator</span></span>](conditional-and-operator.md)
- [<span data-ttu-id="02aba-120">\! 運算子</span><span class="sxs-lookup"><span data-stu-id="02aba-120">\! operator</span></span>](logical-negation-operator.md)
- [<span data-ttu-id="02aba-121">| 運算子</span><span class="sxs-lookup"><span data-stu-id="02aba-121">| operator</span></span>](or-operator.md)
