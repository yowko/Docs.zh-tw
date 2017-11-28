---
title: "+= 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 91286b3c6b9a7239bcd5d5bac0ef08bfd7fa8345
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8e5c5-102">+= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8e5c5-102">+= Operator (C# Reference)</span></span>
<span data-ttu-id="8e5c5-103">加法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="8e5c5-103">The addition assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e5c5-104">備註</span><span class="sxs-lookup"><span data-stu-id="8e5c5-104">Remarks</span></span>  
 <span data-ttu-id="8e5c5-105">使用 `+=` 指派運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="8e5c5-105">An expression using the `+=` assignment operator, such as</span></span>  
  
```  
x += y  
```  
  
 <span data-ttu-id="8e5c5-106">相當於</span><span class="sxs-lookup"><span data-stu-id="8e5c5-106">is equivalent to</span></span>  
  
```  
x = x + y  
```  
  
 <span data-ttu-id="8e5c5-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="8e5c5-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="8e5c5-108">[+ 運算子](../../../csharp/language-reference/operators/addition-operator.md)的意義隨 `x` 和 `y` 的類型而定 (加上數值運算元、字串運算元串連等等)。</span><span class="sxs-lookup"><span data-stu-id="8e5c5-108">The meaning of the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) depends on the types of `x` and `y` (addition for numeric operands, concatenation for string operands, and so forth).</span></span>  
  
 <span data-ttu-id="8e5c5-109">無法直接多載 `+=` 運算子，但使用者定義型別可以多載 [+ 運算子](../../../csharp/language-reference/operators/addition-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="8e5c5-109">The `+=` operator cannot be overloaded directly, but user-defined types can overload the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="8e5c5-110">`+=` 運算子也可以用來指定回應事件所呼叫的方法，這類方法稱之為事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8e5c5-110">The `+=` operator is also used to specify a method that will be called in response to an event; such methods are called event handlers.</span></span> <span data-ttu-id="8e5c5-111">在此內容中使用 `+=` 運算子，稱之為「訂閱事件」。</span><span class="sxs-lookup"><span data-stu-id="8e5c5-111">The use of the `+=` operator in this context is referred to as *subscribing to an event*.</span></span> <span data-ttu-id="8e5c5-112">如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="8e5c5-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span> <span data-ttu-id="8e5c5-113">和[委派](../../../csharp/programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="8e5c5-113">and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e5c5-114">範例</span><span class="sxs-lookup"><span data-stu-id="8e5c5-114">Example</span></span>  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8e5c5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e5c5-115">See Also</span></span>  
 [<span data-ttu-id="8e5c5-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8e5c5-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8e5c5-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8e5c5-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8e5c5-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="8e5c5-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
