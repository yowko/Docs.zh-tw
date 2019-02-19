---
title: <<= 運算子 - C# 參考
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: d2105fbee4ddfe1b2cb3325d82b0f2f8c5559297
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219445"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="278d0-102">\<\<= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="278d0-102">\<\<= operator (C# Reference)</span></span>

<span data-ttu-id="278d0-103">左移指派運算子。</span><span class="sxs-lookup"><span data-stu-id="278d0-103">The left-shift assignment operator.</span></span>

<span data-ttu-id="278d0-104">使用 `<<=` 運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="278d0-104">An expression using the `<<=` operator, such as</span></span>

```csharp
x <<= y
```

<span data-ttu-id="278d0-105">相當於</span><span class="sxs-lookup"><span data-stu-id="278d0-105">is equivalent to</span></span>

```csharp
x = x << y
```

<span data-ttu-id="278d0-106">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="278d0-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="278d0-107">[`<<` 運算子](left-shift-operator.md)會向其第一個運算元左移第二個運算元所定義的位元數。</span><span class="sxs-lookup"><span data-stu-id="278d0-107">The [`<<` operator](left-shift-operator.md) shifts its first operand left by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="278d0-108">下列範例示範 `<<=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="278d0-108">The following example demonstrates the usage of the `<<=` operator:</span></span>

[!code-csharp-interactive[left shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="278d0-109">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="278d0-109">Operator overloadability</span></span>

<span data-ttu-id="278d0-110">若使用者定義型別[多載](../keywords/operator.md) [`<<` 運算子](left-shift-operator.md)，左移指派運算子 `<<=` 會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="278d0-110">If a user-defined type [overloads](../keywords/operator.md) the [`<<` operator](left-shift-operator.md), the left-shift assignment operator `<<=` is implicitly overloaded.</span></span> <span data-ttu-id="278d0-111">使用者定義型別無法明確地多載左移指派運算子。</span><span class="sxs-lookup"><span data-stu-id="278d0-111">A user-defined type cannot explicitly overload the left-shift assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="278d0-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="278d0-112">C# language specification</span></span>

<span data-ttu-id="278d0-113">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[複合指派](~/_csharplang/spec/expressions.md#compound-assignment)章節。</span><span class="sxs-lookup"><span data-stu-id="278d0-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="278d0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="278d0-114">See also</span></span>

- [<span data-ttu-id="278d0-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="278d0-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="278d0-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="278d0-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="278d0-117">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="278d0-117">C# Operators</span></span>](index.md)
