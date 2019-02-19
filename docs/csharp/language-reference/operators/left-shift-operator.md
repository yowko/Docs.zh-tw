---
title: << 運算子 - C# 參考
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: deea2d0f720ba7f096e65c67378586bc88f24673
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219431"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3d833-102">\<\< 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3d833-102">\<\< operator (C# Reference)</span></span>

<span data-ttu-id="3d833-103">左移運算子 (`<<`) 會向其第一個運算元左移第二個運算元所定義的位元數。</span><span class="sxs-lookup"><span data-stu-id="3d833-103">The left-shift operator `<<` shifts its first operand left by the number of bits defined by its second operand.</span></span> <span data-ttu-id="3d833-104">所有整數型別都支援 `<<` 運算子。</span><span class="sxs-lookup"><span data-stu-id="3d833-104">All integer types support the `<<` operator.</span></span> <span data-ttu-id="3d833-105">不過，第二個運算元的類型必須是 [int](../keywords/int.md) 或對 `int` 進行[預先定義隱含數值轉換](../keywords/implicit-numeric-conversions-table.md)的類型。</span><span class="sxs-lookup"><span data-stu-id="3d833-105">However, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="3d833-106">位於結果型別範圍以外的高位位元會被捨棄，而且低位空位元位置會被設定為零，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="3d833-106">The high-order bits that are outside the range of the result type are discarded, and the low-order empty bit positions are set to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShift)]

## <a name="shift-count"></a><span data-ttu-id="3d833-107">位移計數</span><span class="sxs-lookup"><span data-stu-id="3d833-107">Shift count</span></span>

<span data-ttu-id="3d833-108">針對運算式 `x << count`，實際位移計數相依於 `x` 的型別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3d833-108">For the expression `x << count`, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="3d833-109">若 `x` 的型別為 [int](../keywords/int.md) 或 [uint](../keywords/uint.md)，則位移計數是由第二個運算元的低位*五個*位元所給定。</span><span class="sxs-lookup"><span data-stu-id="3d833-109">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is given by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="3d833-110">也就是說，位移計數是從 `count & 0x1F` (或 `count & 0b_1_1111`) 所計算。</span><span class="sxs-lookup"><span data-stu-id="3d833-110">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="3d833-111">若 `x` 的型別為 [long](../keywords/long.md) 或 [ulong](../keywords/ulong.md)，則位移計數是由第二個運算元的低位*六個*位元所給定。</span><span class="sxs-lookup"><span data-stu-id="3d833-111">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is given by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="3d833-112">也就是說，位移計數是從 `count & 0x3F` (或 `count & 0b_11_1111`) 所計算。</span><span class="sxs-lookup"><span data-stu-id="3d833-112">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="3d833-113">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="3d833-113">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftByLargeCount)]

## <a name="remarks"></a><span data-ttu-id="3d833-114">備註</span><span class="sxs-lookup"><span data-stu-id="3d833-114">Remarks</span></span>

<span data-ttu-id="3d833-115">位移作業一律不會導致溢位並產生[已選取與未選取](../keywords/checked-and-unchecked.md)內容的相同結果。</span><span class="sxs-lookup"><span data-stu-id="3d833-115">Shift operations never cause overflows and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="3d833-116">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="3d833-116">Operator overloadability</span></span>

<span data-ttu-id="3d833-117">使用者定義型別可以[多載](../keywords/operator.md) `<<` 運算子。</span><span class="sxs-lookup"><span data-stu-id="3d833-117">User-defined types can [overload](../keywords/operator.md) the `<<` operator.</span></span> <span data-ttu-id="3d833-118">若使用者定義型別 `T` 會多載 `<<` 運算子，則第一個運算元的型別必須是 `T`，且第二個運算元的型別必須是 `int`。</span><span class="sxs-lookup"><span data-stu-id="3d833-118">If a user-defined type `T` overloads the `<<` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span> <span data-ttu-id="3d833-119">多載 `<<` 運算子時，[左移指派運算子](left-shift-assignment-operator.md) `<<=`也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="3d833-119">When the `<<` operator is overloaded, the [left-shift assignment operator](left-shift-assignment-operator.md) `<<=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3d833-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3d833-120">C# language specification</span></span>

<span data-ttu-id="3d833-121">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[位移運算子](~/_csharplang/spec/expressions.md#shift-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="3d833-121">For more information, see the [Shift operators](~/_csharplang/spec/expressions.md#shift-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d833-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d833-122">See also</span></span>

- [<span data-ttu-id="3d833-123">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3d833-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3d833-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3d833-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3d833-125">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="3d833-125">C# Operators</span></span>](index.md)
- [<span data-ttu-id="3d833-126">>> 運算子</span><span class="sxs-lookup"><span data-stu-id="3d833-126">>> operator</span></span>](right-shift-operator.md)
