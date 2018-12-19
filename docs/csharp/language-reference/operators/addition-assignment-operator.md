---
title: += 運算子 - C# 參考
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: 5d48f2fe53a9bb6f781f8d35f1e0983bcaa30f88
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240927"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="975c0-102">+= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="975c0-102">+= Operator (C# Reference)</span></span>

<span data-ttu-id="975c0-103">加法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="975c0-103">The addition assignment operator.</span></span>

<span data-ttu-id="975c0-104">使用 `+=` 運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="975c0-104">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="975c0-105">相當於</span><span class="sxs-lookup"><span data-stu-id="975c0-105">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="975c0-106">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="975c0-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="975c0-107">針對數值型別，[加法運算子](addition-operator.md) `+` 會計算其運算元的和。</span><span class="sxs-lookup"><span data-stu-id="975c0-107">For numeric types, the [addition operator](addition-operator.md) `+` computes the sum of its operands.</span></span> <span data-ttu-id="975c0-108">如果其中一或兩個運算元的型別為 [string](../keywords/string.md)，則它會串連其運算元的字串表示。</span><span class="sxs-lookup"><span data-stu-id="975c0-108">If one or both operands is of type [string](../keywords/string.md), it concatenates the string representations of its operands.</span></span> <span data-ttu-id="975c0-109">針對委派型別，`+` 運算子會傳回為其運算元組合的新委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="975c0-109">For delegate types, the `+` operator returns a new delegate instance that is combination of its operands.</span></span>

<span data-ttu-id="975c0-110">當您訂閱[事件](../keywords/event.md)時，您也會使用 `+=` 來指定事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="975c0-110">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="975c0-111">如需詳細資訊，請參閱[＜How to：訂閱及取消訂閱事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="975c0-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

<span data-ttu-id="975c0-112">下列範例示範 `+=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="975c0-112">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]

## <a name="operator-overloadability"></a><span data-ttu-id="975c0-113">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="975c0-113">Operator overloadability</span></span>

<span data-ttu-id="975c0-114">如果使用者定義的型別將[加法運算子](addition-operator.md) `+` [多載](../keywords/operator.md)，則加法指派運算子 `+=` 會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="975c0-114">If a user-defined type [overloads](../keywords/operator.md) the [addition operator](addition-operator.md) `+`, the addition assignment operator `+=` is implicitly overloaded.</span></span> <span data-ttu-id="975c0-115">使用者定義型別無法明確地多載其他指派運算子。</span><span class="sxs-lookup"><span data-stu-id="975c0-115">A user-defined type cannot explicitly overload the addition assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="975c0-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="975c0-116">C# language specification</span></span>

<span data-ttu-id="975c0-117">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[複合指派](~/_csharplang/spec/expressions.md#compound-assignment)及[事件指派](~/_csharplang/spec/expressions.md#event-assignment)章節。</span><span class="sxs-lookup"><span data-stu-id="975c0-117">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) and [Event assignment](~/_csharplang/spec/expressions.md#event-assignment) sections of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="975c0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="975c0-118">See also</span></span>

- [<span data-ttu-id="975c0-119">C# 參考</span><span class="sxs-lookup"><span data-stu-id="975c0-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="975c0-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="975c0-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="975c0-121">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="975c0-121">C# Operators</span></span>](index.md)
- [<span data-ttu-id="975c0-122">事件</span><span class="sxs-lookup"><span data-stu-id="975c0-122">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="975c0-123">委派</span><span class="sxs-lookup"><span data-stu-id="975c0-123">Delegates</span></span>](../../programming-guide/delegates/index.md)
