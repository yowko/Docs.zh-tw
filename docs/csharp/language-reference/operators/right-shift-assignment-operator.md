---
title: '>>= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 51914bb5e9ebffd5d868528b5a8d3072a956cea6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220909"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9156e-102">>>= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="9156e-102">>>= operator (C# Reference)</span></span>

<span data-ttu-id="9156e-103">右移指派運算子。</span><span class="sxs-lookup"><span data-stu-id="9156e-103">The right-shift assignment operator.</span></span>

<span data-ttu-id="9156e-104">使用 `>>=` 運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="9156e-104">An expression using the `>>=` operator, such as</span></span>

```csharp
x >>= y
```

<span data-ttu-id="9156e-105">相當於</span><span class="sxs-lookup"><span data-stu-id="9156e-105">is equivalent to</span></span>

```csharp
x = x >> y
```

<span data-ttu-id="9156e-106">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="9156e-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="9156e-107">[`>>` 運算子](right-shift-operator.md)會向其第一個運算元右移第二個運算元所定義的位元數。</span><span class="sxs-lookup"><span data-stu-id="9156e-107">The [`>>` operator](right-shift-operator.md) shifts its first operand right by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="9156e-108">下列範例示範 `>>=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="9156e-108">The following example demonstrates the usage of the `>>=` operator:</span></span>

[!code-csharp-interactive[right shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="9156e-109">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="9156e-109">Operator overloadability</span></span>

<span data-ttu-id="9156e-110">若使用者定義型別[多載](../keywords/operator.md) [`>>` 運算子](right-shift-operator.md)，右移指派運算子 `>>=` 會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="9156e-110">If a user-defined type [overloads](../keywords/operator.md) the [`>>` operator](right-shift-operator.md), the right-shift assignment operator `>>=` is implicitly overloaded.</span></span> <span data-ttu-id="9156e-111">使用者定義型別無法明確地多載右移指派運算子。</span><span class="sxs-lookup"><span data-stu-id="9156e-111">A user-defined type cannot explicitly overload the right-shift assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9156e-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9156e-112">C# language specification</span></span>

<span data-ttu-id="9156e-113">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[複合指派](~/_csharplang/spec/expressions.md#compound-assignment)章節。</span><span class="sxs-lookup"><span data-stu-id="9156e-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9156e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9156e-114">See also</span></span>

- [<span data-ttu-id="9156e-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="9156e-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9156e-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9156e-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9156e-117">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="9156e-117">C# operators</span></span>](index.md)