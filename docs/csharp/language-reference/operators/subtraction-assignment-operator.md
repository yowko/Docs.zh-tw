---
title: "-= 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- -=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d7f26ae1fce54eb0d03a314a83ce523baeb3f348
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="--operator-c-reference"></a><span data-ttu-id="f85c3-102">-= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f85c3-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="f85c3-103">減法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="f85c3-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f85c3-104">備註</span><span class="sxs-lookup"><span data-stu-id="f85c3-104">Remarks</span></span>  
 <span data-ttu-id="f85c3-105">使用 `-=` 指派運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="f85c3-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```  
x -= y  
```  
  
 <span data-ttu-id="f85c3-106">相當於</span><span class="sxs-lookup"><span data-stu-id="f85c3-106">is equivalent to</span></span>  
  
```  
x = x - y  
```  
  
 <span data-ttu-id="f85c3-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="f85c3-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f85c3-108">[- 運算子](../../../csharp/language-reference/operators/subtraction-operator.md) 的意義取決於 `x` 和 `y` 的類型 (數字運算元表示減法、委派運算元表示委派移除等等)。</span><span class="sxs-lookup"><span data-stu-id="f85c3-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="f85c3-109">無法直接多載 `-=` 運算子，但使用者定義型別可以多載 [- 運算子](../../../csharp/language-reference/operators/subtraction-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="f85c3-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="f85c3-110">-= 運算子也會用於 C# 中，以取消事件的訂閱。</span><span class="sxs-lookup"><span data-stu-id="f85c3-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="f85c3-111">如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="f85c3-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f85c3-112">範例</span><span class="sxs-lookup"><span data-stu-id="f85c3-112">Example</span></span>  
 <span data-ttu-id="f85c3-113">[!code-cs[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f85c3-113">[!code-cs[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f85c3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f85c3-114">See Also</span></span>  
 <span data-ttu-id="f85c3-115">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f85c3-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f85c3-116">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f85c3-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="f85c3-117">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="f85c3-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

