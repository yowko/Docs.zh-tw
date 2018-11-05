---
title: += 運算子 (C# 參考)
ms.date: 10/22/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ee335e3e2e7d352d4e26b802bad2b08a05c666ab
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192027"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4535d-102">+= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4535d-102">+= Operator (C# Reference)</span></span>

<span data-ttu-id="4535d-103">加法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="4535d-103">The addition assignment operator.</span></span>

<span data-ttu-id="4535d-104">使用 `+=` 運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="4535d-104">An expression using the `+=` operator, such as</span></span>  

```csharp
x += y
```  

<span data-ttu-id="4535d-105">相當於</span><span class="sxs-lookup"><span data-stu-id="4535d-105">is equivalent to</span></span>  

```csharp
x = x + y
```  

<span data-ttu-id="4535d-106">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="4535d-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="4535d-107">針對數值型別，[加法運算子](addition-operator.md) `+` 會計算其運算元的和。</span><span class="sxs-lookup"><span data-stu-id="4535d-107">For numeric types, the [addition operator](addition-operator.md) `+` computes the sum of its operands.</span></span> <span data-ttu-id="4535d-108">如果其中一或兩個運算元的型別為 [string](../keywords/string.md)，則它會串連其運算元的字串表示。</span><span class="sxs-lookup"><span data-stu-id="4535d-108">If one or both operands is of type [string](../keywords/string.md), it concatenates the string representations of its operands.</span></span> <span data-ttu-id="4535d-109">針對委派型別，`+` 運算子會傳回為其運算元組合的新委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="4535d-109">For delegate types, the `+` operator returns a new delegate instance that is combination of its operands.</span></span>

<span data-ttu-id="4535d-110">如果使用者定義的型別將[加法運算子](addition-operator.md) `+` [多載](../keywords/operator.md)，則加法指派運算子 `+=` 會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="4535d-110">If a user-defined type [overloads](../keywords/operator.md) the [addition operator](addition-operator.md) `+`, the addition assignment operator `+=` is implicitly overloaded.</span></span>

<span data-ttu-id="4535d-111">當您訂閱[事件](../keywords/event.md)時，您也會使用 `+=` 來指定事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="4535d-111">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="4535d-112">如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="4535d-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

<span data-ttu-id="4535d-113">下列範例示範 `+=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="4535d-113">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]
  
## <a name="see-also"></a><span data-ttu-id="4535d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4535d-114">See also</span></span>

- [<span data-ttu-id="4535d-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4535d-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4535d-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4535d-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4535d-117">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="4535d-117">C# Operators</span></span>](index.md)
- [<span data-ttu-id="4535d-118">事件</span><span class="sxs-lookup"><span data-stu-id="4535d-118">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="4535d-119">委派</span><span class="sxs-lookup"><span data-stu-id="4535d-119">Delegates</span></span>](../../programming-guide/delegates/index.md)
