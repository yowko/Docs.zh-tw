---
title: /= 運算子 - C# 參考
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: ed4dd6c0c944b77543aae4de8d51534b4df4f4ef
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286516"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="900b2-102">/= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="900b2-102">/= Operator (C# Reference)</span></span>

<span data-ttu-id="900b2-103">除法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="900b2-103">The division assignment operator.</span></span>

<span data-ttu-id="900b2-104">使用 `/=` 運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="900b2-104">An expression using the `/=` operator, such as</span></span>

```csharp
x /= y
```

<span data-ttu-id="900b2-105">相當於</span><span class="sxs-lookup"><span data-stu-id="900b2-105">is equivalent to</span></span>

```csharp
x = x / y
```

<span data-ttu-id="900b2-106">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="900b2-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="900b2-107">[除法運算子](division-operator.md) `/` 會將它的第一個運算元除以第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="900b2-107">The [division operator](division-operator.md) `/` divides its first operand by its second operand.</span></span> <span data-ttu-id="900b2-108">所有數值型別都支援。</span><span class="sxs-lookup"><span data-stu-id="900b2-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="900b2-109">下列範例示範 `/=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="900b2-109">The following example demonstrates the usage of the `/=` operator:</span></span>

[!code-csharp-interactive[divide and assign](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#DivisionAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="900b2-110">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="900b2-110">Operator overloadability</span></span>

<span data-ttu-id="900b2-111">如果使用者定義的型別將[除法運算子](division-operator.md) `/` [多載](../keywords/operator.md)，則除法指派運算子 `/=` 會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="900b2-111">If a user-defined type [overloads](../keywords/operator.md) the [division operator](division-operator.md) `/`, the division assignment operator `/=` is implicitly overloaded.</span></span> <span data-ttu-id="900b2-112">使用者定義型別無法明確地多載除法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="900b2-112">A user-defined type cannot explicitly overload the division assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="900b2-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="900b2-113">C# language specification</span></span>

<span data-ttu-id="900b2-114">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[複合指派](~/_csharplang/spec/expressions.md#compound-assignment)章節。</span><span class="sxs-lookup"><span data-stu-id="900b2-114">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="900b2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="900b2-115">See also</span></span>

- [<span data-ttu-id="900b2-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="900b2-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="900b2-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="900b2-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="900b2-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="900b2-118">C# Operators</span></span>](index.md)
