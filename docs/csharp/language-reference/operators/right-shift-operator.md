---
title: '>> 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 809cd2cab29d3378892ea224cf846e9d0909b073
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219720"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3d331-102">>> 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3d331-102">>> operator (C# Reference)</span></span>

<span data-ttu-id="3d331-103">右移運算子 (`>>`) 會向其第一個運算元右移第二個運算元所定義的位元數。</span><span class="sxs-lookup"><span data-stu-id="3d331-103">The right-shift operator `>>` shifts its first operand right by the number of bits defined by its second operand.</span></span> <span data-ttu-id="3d331-104">所有整數型別都支援 `>>` 運算子。</span><span class="sxs-lookup"><span data-stu-id="3d331-104">All integer types support the `>>` operator.</span></span> <span data-ttu-id="3d331-105">不過，第二個運算元的類型必須是 [int](../keywords/int.md) 或對 `int` 進行[預先定義隱含數值轉換](../keywords/implicit-numeric-conversions-table.md)的類型。</span><span class="sxs-lookup"><span data-stu-id="3d331-105">However, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="3d331-106">右移作業會捨棄低位位元。</span><span class="sxs-lookup"><span data-stu-id="3d331-106">The right-shift operation discards the low-order bits.</span></span> <span data-ttu-id="3d331-107">會根據第一個運算元的類型來設定高位空位元位置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3d331-107">The high-order empty bit positions are set based on the type of the first operand as follows:</span></span>

- <span data-ttu-id="3d331-108">若第一個運算元的型別為 [int](../keywords/int.md) 或 [long](../keywords/long.md)，則右移運算元會執行**算術**位移：第一個運算元之最高有效位元 (正負號位元) 的值會傳播到高為空位元位置。</span><span class="sxs-lookup"><span data-stu-id="3d331-108">If the first operand is of type [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift operator performs an **arithmetic** shift: the value of the most significant bit (the sign bit) of the first operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="3d331-109">也就是說，若第一個運算元不是負值且在為負值時被設定為一，則高位空位元位置會被設定為零。</span><span class="sxs-lookup"><span data-stu-id="3d331-109">That is, the high-order empty bit positions are set to zero if the first operand is non-negative and set to one if it's negative.</span></span>

- <span data-ttu-id="3d331-110">若第一個運算元的型別為 [uint](../keywords/uint.md) 或 [ulong](../keywords/ulong.md)，則右移運算子會執行**邏輯**位移：高位空位元位置一律會被設定為零。</span><span class="sxs-lookup"><span data-stu-id="3d331-110">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift operator performs a **logical** shift: the high-order empty bit positions are always set to zero.</span></span>

<span data-ttu-id="3d331-111">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="3d331-111">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[right shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShift)]

## <a name="shift-count"></a><span data-ttu-id="3d331-112">位移計數</span><span class="sxs-lookup"><span data-stu-id="3d331-112">Shift count</span></span>

<span data-ttu-id="3d331-113">針對運算式 `x >> count`，實際位移計數相依於 `x` 的型別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3d331-113">For the expression `x >> count`, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="3d331-114">若 `x` 的型別為 [int](../keywords/int.md) 或 [uint](../keywords/uint.md)，則位移計數是由第二個運算元的低位*五個*位元所給定。</span><span class="sxs-lookup"><span data-stu-id="3d331-114">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is given by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="3d331-115">也就是說，位移計數是從 `count & 0x1F` (或 `count & 0b_1_1111`) 所計算。</span><span class="sxs-lookup"><span data-stu-id="3d331-115">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="3d331-116">若 `x` 的型別為 [long](../keywords/long.md) 或 [ulong](../keywords/ulong.md)，則位移計數是由第二個運算元的低位*六個*位元所給定。</span><span class="sxs-lookup"><span data-stu-id="3d331-116">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is given by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="3d331-117">也就是說，位移計數是從 `count & 0x3F` (或 `count & 0b_11_1111`) 所計算。</span><span class="sxs-lookup"><span data-stu-id="3d331-117">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="3d331-118">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="3d331-118">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftByLargeCount)]

## <a name="remarks"></a><span data-ttu-id="3d331-119">備註</span><span class="sxs-lookup"><span data-stu-id="3d331-119">Remarks</span></span>

<span data-ttu-id="3d331-120">位移作業一律不會導致溢位並產生[已選取與未選取](../keywords/checked-and-unchecked.md)內容的相同結果。</span><span class="sxs-lookup"><span data-stu-id="3d331-120">Shift operations never cause overflows and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="3d331-121">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="3d331-121">Operator overloadability</span></span>

<span data-ttu-id="3d331-122">使用者定義型別可以[多載](../keywords/operator.md) `>>` 運算子。</span><span class="sxs-lookup"><span data-stu-id="3d331-122">User-defined types can [overload](../keywords/operator.md) the `>>` operator.</span></span> <span data-ttu-id="3d331-123">若使用者定義型別 `T` 會多載 `>>` 運算子，則第一個運算元的型別必須是 `T`，且第二個運算元的型別必須是 `int`。</span><span class="sxs-lookup"><span data-stu-id="3d331-123">If a user-defined type `T` overloads the `>>` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span> <span data-ttu-id="3d331-124">多載 `>>` 運算子時，[右移指派運算子](right-shift-assignment-operator.md) `>>=`也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="3d331-124">When the `>>` operator is overloaded, the [right-shift assignment operator](right-shift-assignment-operator.md) `>>=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3d331-125">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3d331-125">C# language specification</span></span>

<span data-ttu-id="3d331-126">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[位移運算子](~/_csharplang/spec/expressions.md#shift-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="3d331-126">For more information, see the [Shift operators](~/_csharplang/spec/expressions.md#shift-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d331-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d331-127">See also</span></span>

- [<span data-ttu-id="3d331-128">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3d331-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3d331-129">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3d331-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3d331-130">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="3d331-130">C# operators</span></span>](index.md)
- [<span data-ttu-id="3d331-131"><< 運算子</span><span class="sxs-lookup"><span data-stu-id="3d331-131"><< operator</span></span>](left-shift-operator.md)