---
title: '*= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 70461f79e714e44354fe4137e5360769fa048d3e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967382"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c7bb8-102">\*= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c7bb8-102">\*= Operator (C# Reference)</span></span>

<span data-ttu-id="c7bb8-103">乘法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="c7bb8-103">The multiplication assignment operator.</span></span>

<span data-ttu-id="c7bb8-104">使用 `*=` 運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="c7bb8-104">An expression using the `*=` operator, such as</span></span>

```csharp
x *= y
```

<span data-ttu-id="c7bb8-105">相當於</span><span class="sxs-lookup"><span data-stu-id="c7bb8-105">is equivalent to</span></span>

```csharp
x = x * y
```

<span data-ttu-id="c7bb8-106">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="c7bb8-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="c7bb8-107">針對數值類型，[\* 運算子](multiplication-operator.md)會計算其運算元的乘積。</span><span class="sxs-lookup"><span data-stu-id="c7bb8-107">For numeric types, the [\* operator](multiplication-operator.md) computes the product of its operands.</span></span>

<span data-ttu-id="c7bb8-108">下列範例示範 `*=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="c7bb8-108">The following example demonstrates the usage of the `*=` operator:</span></span>

[!code-csharp-interactive[multiply and assign](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#MultiplyAndAssign)]

## <a name="operator-overloadability"></a><span data-ttu-id="c7bb8-109">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="c7bb8-109">Operator overloadability</span></span>

<span data-ttu-id="c7bb8-110">如果使用者定義類型將[乘法運算子](multiplication-operator.md) `*` [多載](../keywords/operator.md)，則乘法指派運算子 `*=` 會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="c7bb8-110">If a user-defined type [overloads](../keywords/operator.md) the [multiplication operator](multiplication-operator.md) `*`, the multiplication assignment operator `*=` is implicitly overloaded.</span></span> <span data-ttu-id="c7bb8-111">使用者定義類型無法明確地多載乘法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="c7bb8-111">A user-defined type cannot explicitly overload the multiplication assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c7bb8-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c7bb8-112">C# language specification</span></span>

<span data-ttu-id="c7bb8-113">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[複合指派](~/_csharplang/spec/expressions.md#compound-assignment)章節。</span><span class="sxs-lookup"><span data-stu-id="c7bb8-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7bb8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7bb8-114">See also</span></span>

- [<span data-ttu-id="c7bb8-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c7bb8-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c7bb8-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c7bb8-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c7bb8-117">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="c7bb8-117">C# Operators</span></span>](index.md)
