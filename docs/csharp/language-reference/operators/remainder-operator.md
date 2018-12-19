---
title: '% 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 09/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: a5c12b6683e35cc1ec2d40446dd0ed068c3d2552
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236475"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e41b7-102">% 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e41b7-102">% Operator (C# Reference)</span></span>

<span data-ttu-id="e41b7-103">餘數運算子 `%` 會計算其第一個運算元除以第二個運算元之後的餘數。</span><span class="sxs-lookup"><span data-stu-id="e41b7-103">The remainder operator `%` computes the remainder after dividing its first operand by its second operand.</span></span>

<span data-ttu-id="e41b7-104">使用者定義型別可以[多載](../keywords/operator.md) `%` 運算子。</span><span class="sxs-lookup"><span data-stu-id="e41b7-104">User-defined types can [overload](../keywords/operator.md) the `%` operator.</span></span> <span data-ttu-id="e41b7-105">當 `%` 多載時，[餘數指派運算子](remainder-assignment-operator.md) `%=`也會隱含多載。</span><span class="sxs-lookup"><span data-stu-id="e41b7-105">When the `%` is overloaded, the [remainder assignment operator](remainder-assignment-operator.md) `%=` is also implicitly overloaded.</span></span>

<span data-ttu-id="e41b7-106">所有數值類型皆支援餘數運算子。</span><span class="sxs-lookup"><span data-stu-id="e41b7-106">All numeric types support the remainder operator.</span></span>

## <a name="integer-remainder"></a><span data-ttu-id="e41b7-107">整數餘數</span><span class="sxs-lookup"><span data-stu-id="e41b7-107">Integer remainder</span></span>
  
<span data-ttu-id="e41b7-108">對整數運算元來說，`a % b` 的結果是 `a - (a / b) * b` 所產生的值。</span><span class="sxs-lookup"><span data-stu-id="e41b7-108">For the integer operands, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="e41b7-109">非零餘數的正負號與第一個運算元的正負號相同，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e41b7-109">The sign of the non-zero remainder is the same as that of the first operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#1)]

## <a name="floating-point-remainder"></a><span data-ttu-id="e41b7-110">浮點數餘數</span><span class="sxs-lookup"><span data-stu-id="e41b7-110">Floating-point remainder</span></span>

<span data-ttu-id="e41b7-111">對於 [float](../keywords/float.md) 和 [double](../keywords/double.md) 運算元，有限 `x` 和 `y`的 `x % y` 結果是 `z` 值，像是</span><span class="sxs-lookup"><span data-stu-id="e41b7-111">For the [float](../keywords/float.md) and [double](../keywords/double.md) operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="e41b7-112">若 `z` 不是零，其正負號與 `x` 的正負號相同；</span><span class="sxs-lookup"><span data-stu-id="e41b7-112">the sign of `z`, if non-zero, is the same as the sign of `x`;</span></span>
- <span data-ttu-id="e41b7-113">`z` 的絕對值是由 `|x| - n * |y|` 產生的值，其中 `n` 為最大可能整數，小於或等於 `|x| / |y|`，而 `|x|`和 `|y|`則分別是 `x` 和 `y` 的絕對值。</span><span class="sxs-lookup"><span data-stu-id="e41b7-113">the absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

<span data-ttu-id="e41b7-114">如需在非有限運算元情況中 `%` 運算子的行為，請參閱 [C# 語言規格](../language-specification/index.md)的[餘數運算子](~/_csharplang/spec/expressions.md#remainder-operator)小節。</span><span class="sxs-lookup"><span data-stu-id="e41b7-114">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e41b7-115">這項計算餘數的方法和用於整數運算元的方法類似，但不同於 IEEE 754。</span><span class="sxs-lookup"><span data-stu-id="e41b7-115">This method of computing the remainder is analogous to that used for integer operands, but differs from the IEEE 754.</span></span> <span data-ttu-id="e41b7-116">如需符合 IEEE 754 的餘數運算，請使用 <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="e41b7-116">If you need the remainder operation that complies with the IEEE 754, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="e41b7-117">下列範例示範 `float` 和 `double` 運算元的餘數運算子行為：</span><span class="sxs-lookup"><span data-stu-id="e41b7-117">The following example demonstrates the behavior of the remainder operator for `float` and `double` operands:</span></span>

[!code-csharp-interactive[float and double remainder](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#2)]

<span data-ttu-id="e41b7-118">請注意與浮點數類型有關的四捨五入錯誤。</span><span class="sxs-lookup"><span data-stu-id="e41b7-118">Note the round-off errors that can be associated with the floating-point types.</span></span>

<span data-ttu-id="e41b7-119">針對 [decimal](../keywords/decimal.md) 運算元，餘數運算子 `%` 等於 <xref:System.Decimal?displayProperty=nameWithType> 類型的[餘數運算子](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>)。</span><span class="sxs-lookup"><span data-stu-id="e41b7-119">For the [decimal](../keywords/decimal.md) operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

## <a name="see-also"></a><span data-ttu-id="e41b7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e41b7-120">See also</span></span>

- [<span data-ttu-id="e41b7-121">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e41b7-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e41b7-122">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e41b7-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e41b7-123">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="e41b7-123">C# Operators</span></span>](index.md)
- <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>
- <xref:System.Math.DivRem%2A?displayProperty=nameWithType>
