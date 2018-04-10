---
title: '|| 運算子 (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b95fd162c9a89789e1970b32473c8acf16ba5cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="42d2a-102">|| 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="42d2a-102">|| Operator (C# Reference)</span></span>
<span data-ttu-id="42d2a-103">條件式 OR 運算子 (`||`) 會執行其 `bool` 運算元的邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="42d2a-103">The conditional-OR operator (`||`) performs a logical-OR of its `bool` operands.</span></span> <span data-ttu-id="42d2a-104">如果第一個運算元評估值為 `true`，就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="42d2a-104">If the first operand evaluates to `true`, the second operand isn't evaluated.</span></span> <span data-ttu-id="42d2a-105">如果第一個運算元評估值為 `false`，第二個運算子會判斷整個 OR 運算式是評估為`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="42d2a-105">If the first operand evaluates to `false`, the second operator determines whether the OR expression as a whole evaluates to `true` or `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42d2a-106">備註</span><span class="sxs-lookup"><span data-stu-id="42d2a-106">Remarks</span></span>  
 <span data-ttu-id="42d2a-107">作業</span><span class="sxs-lookup"><span data-stu-id="42d2a-107">The operation</span></span>  
  
```  
x || y  
```  
  
 <span data-ttu-id="42d2a-108">對應至作業</span><span class="sxs-lookup"><span data-stu-id="42d2a-108">corresponds to the operation</span></span>  
  
```  
x | y  
```  
  
 <span data-ttu-id="42d2a-109">差異在於，如果 `x` 是 `true`，則不會評估 `y`，因為不論 `y` 的值為何，OR 運算都是 `true`。</span><span class="sxs-lookup"><span data-stu-id="42d2a-109">except that if `x` is `true`, `y` is not evaluated because the OR operation is `true` regardless of the value of `y`.</span></span> <span data-ttu-id="42d2a-110">這個概念稱為「最少運算」求值。</span><span class="sxs-lookup"><span data-stu-id="42d2a-110">This concept is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="42d2a-111">無法多載條件式 OR 運算子，但規則邏輯運算子與 [true](../../../csharp/language-reference/keywords/true.md) 和 [false](../../../csharp/language-reference/keywords/false.md) 運算子的多載具有某些限制，也會視為條件式邏輯運算子的多載。</span><span class="sxs-lookup"><span data-stu-id="42d2a-111">The conditional-OR operator cannot be overloaded, but overloads of the regular logical operators and the [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) operators are, with certain restrictions, also considered to be overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42d2a-112">範例</span><span class="sxs-lookup"><span data-stu-id="42d2a-112">Example</span></span>  
 <span data-ttu-id="42d2a-113">在下列範例中，使用 `||` 的運算式只會評估第一個運算元。</span><span class="sxs-lookup"><span data-stu-id="42d2a-113">In the following examples, the expression that uses `||` evaluates only the first operand.</span></span> <span data-ttu-id="42d2a-114">使用 `|` 的運算式則評估這兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="42d2a-114">The expression that uses `|` evaluates both operands.</span></span> <span data-ttu-id="42d2a-115">在第二個範例中，如果評估這兩個運算元，就會發生執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42d2a-115">In the second example, a run-time exception occurs if both operands are evaluated.</span></span>  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="42d2a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42d2a-116">See Also</span></span>  
 [<span data-ttu-id="42d2a-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="42d2a-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="42d2a-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="42d2a-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="42d2a-119">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="42d2a-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
