---
title: '&amp;= 運算子 (C# 參考)'
ms.date: 10/29/2018
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 8ce27c999cf21a9059ba23ee3c86b8fa024c7341
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "50980605"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="59e95-102">&amp;= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="59e95-102">&amp;= Operator (C# Reference)</span></span>

<span data-ttu-id="59e95-103">AND 指派運算子。</span><span class="sxs-lookup"><span data-stu-id="59e95-103">The AND assignment operator.</span></span>

<span data-ttu-id="59e95-104">使用 `&=` 運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="59e95-104">An expression using the `&=` operator, such as</span></span>

```csharp
x &= y
```

<span data-ttu-id="59e95-105">相當於</span><span class="sxs-lookup"><span data-stu-id="59e95-105">is equivalent to</span></span>

```csharp
x = x & y
```

<span data-ttu-id="59e95-106">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="59e95-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="59e95-107">若為整數運算元，[`&` 運算子](and-operator.md)會計算其運算元的位元邏輯 AND；若為 [bool](../keywords/bool.md) 運算元，則會計算其運算元的邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="59e95-107">For integer operands, the [`&` operator](and-operator.md) computes the bitwise logical AND of its operands; for [bool](../keywords/bool.md) operands, it computes the logical AND of its operands.</span></span>

<span data-ttu-id="59e95-108">下列範例示範 `&=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="59e95-108">The following example demonstrates the usage of the `&=` operator:</span></span>

[!code-csharp-interactive[AND assignment example](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#AndAssignmentExample)]

## <a name="operator-overloadability"></a><span data-ttu-id="59e95-109">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="59e95-109">Operator overloadability</span></span>

<span data-ttu-id="59e95-110">若使用者定義型別[多載](../keywords/operator.md) [`&` 運算子](and-operator.md)，AND 指派運算子 `&=` 會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="59e95-110">If a user-defined type [overloads](../keywords/operator.md) the [`&` operator](and-operator.md), the AND assignment operator `&=` is implicitly overloaded.</span></span> <span data-ttu-id="59e95-111">使用者定義型別無法明確地多載 AND 指派運算子。</span><span class="sxs-lookup"><span data-stu-id="59e95-111">A user-defined type cannot explicitly overload the AND assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="59e95-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="59e95-112">C# language specification</span></span>

<span data-ttu-id="59e95-113">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[複合指派](~/_csharplang/spec/expressions.md#compound-assignment)章節。</span><span class="sxs-lookup"><span data-stu-id="59e95-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59e95-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59e95-114">See also</span></span>

- [<span data-ttu-id="59e95-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="59e95-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="59e95-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="59e95-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="59e95-117">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="59e95-117">C# Operators</span></span>](index.md)
