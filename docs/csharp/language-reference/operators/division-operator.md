---
title: / 運算子 - C# 參考
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 45bcd64b60e7d13f389064faefeda815ea1f32c9
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286529"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8960d-102">/ 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8960d-102">/ Operator (C# Reference)</span></span>

<span data-ttu-id="8960d-103">除法運算子 `/` 會將它的第一個運算元除以第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="8960d-103">The division operator `/` divides its first operand by its second operand.</span></span> <span data-ttu-id="8960d-104">所有數值類型皆支援除法運算子。</span><span class="sxs-lookup"><span data-stu-id="8960d-104">All numeric types support the division operator.</span></span>

## <a name="integer-division"></a><span data-ttu-id="8960d-105">整數除數</span><span class="sxs-lookup"><span data-stu-id="8960d-105">Integer division</span></span>

<span data-ttu-id="8960d-106">針對整數型別的運算元，`/` 運算子的結果會是整數型別，且等於兩個運算元捨入為零的商：</span><span class="sxs-lookup"><span data-stu-id="8960d-106">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#Integer)]

<span data-ttu-id="8960d-107">若要以浮點數的形式取得兩個運算元的商，請使用 `float`、`double` 或 `decimal` 型別：</span><span class="sxs-lookup"><span data-stu-id="8960d-107">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#IntegerAsFloatingPoint)]

## <a name="floating-point-division"></a><span data-ttu-id="8960d-108">浮點除數</span><span class="sxs-lookup"><span data-stu-id="8960d-108">Floating-point division</span></span>

<span data-ttu-id="8960d-109">針對 `float`、`double` 和 `decimal` 型別，`/` 運算子的結果會是兩個運算元的商：</span><span class="sxs-lookup"><span data-stu-id="8960d-109">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#FloatingPoint)]

<span data-ttu-id="8960d-110">如果其中一個運算元是 `decimal`，則另一個運算元便不可以是 `float` 或 `double`，因為 `float` 或 `double` 都無法隱含轉換為 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="8960d-110">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="8960d-111">您必須明確地將 `float` 或 `double` 運算元轉換為 `decimal` 型別。</span><span class="sxs-lookup"><span data-stu-id="8960d-111">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="8960d-112">如需在數值型別之間進行隱含轉換的詳細資訊，請參閱[隱含數值轉換表](../keywords/implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="8960d-112">For more information about implicit conversions between numeric types, see [Implicit numeric conversions table](../keywords/implicit-numeric-conversions-table.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="8960d-113">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="8960d-113">Operator overloadability</span></span>

<span data-ttu-id="8960d-114">使用者定義型別可以[多載](../keywords/operator.md) `/` 運算子。</span><span class="sxs-lookup"><span data-stu-id="8960d-114">User-defined types can [overload](../keywords/operator.md) the `/` operator.</span></span> <span data-ttu-id="8960d-115">多載 `/` 運算子時，[除法指派運算子](division-assignment-operator.md) `/=` 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="8960d-115">When the `/` operator is overloaded, the [division assignment operator](division-assignment-operator.md) `/=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8960d-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="8960d-116">C# language specification</span></span>

<span data-ttu-id="8960d-117">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[除法運算子](~/_csharplang/spec/expressions.md#division-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="8960d-117">For more information, see the [Division operator](~/_csharplang/spec/expressions.md#division-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8960d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8960d-118">See also</span></span>

- [<span data-ttu-id="8960d-119">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8960d-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8960d-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8960d-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8960d-121">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="8960d-121">C# Operators</span></span>](index.md)
- [<span data-ttu-id="8960d-122">% 運算子</span><span class="sxs-lookup"><span data-stu-id="8960d-122">% Operator</span></span>](remainder-operator.md)
