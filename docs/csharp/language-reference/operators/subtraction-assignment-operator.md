---
title: -= 運算子 (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 443f0d717288a491838d23eaa63218150bd346d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-c-reference"></a><span data-ttu-id="28ce4-102">-= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="28ce4-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="28ce4-103">減法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="28ce4-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28ce4-104">備註</span><span class="sxs-lookup"><span data-stu-id="28ce4-104">Remarks</span></span>  
 <span data-ttu-id="28ce4-105">使用 `-=` 指派運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="28ce4-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```  
x -= y  
```  
  
 <span data-ttu-id="28ce4-106">相當於</span><span class="sxs-lookup"><span data-stu-id="28ce4-106">is equivalent to</span></span>  
  
```  
x = x - y  
```  
  
 <span data-ttu-id="28ce4-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="28ce4-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="28ce4-108">[- 運算子](../../../csharp/language-reference/operators/subtraction-operator.md) 的意義取決於 `x` 和 `y` 的類型 (數字運算元表示減法、委派運算元表示委派移除等等)。</span><span class="sxs-lookup"><span data-stu-id="28ce4-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="28ce4-109">無法直接多載 `-=` 運算子，但使用者定義型別可以多載 [- 運算子](../../../csharp/language-reference/operators/subtraction-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="28ce4-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="28ce4-110">-= 運算子也會用於 C# 中，以取消事件的訂閱。</span><span class="sxs-lookup"><span data-stu-id="28ce4-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="28ce4-111">如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="28ce4-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="28ce4-112">範例</span><span class="sxs-lookup"><span data-stu-id="28ce4-112">Example</span></span>  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="28ce4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28ce4-113">See Also</span></span>  
 [<span data-ttu-id="28ce4-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="28ce4-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="28ce4-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="28ce4-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="28ce4-116">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="28ce4-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
