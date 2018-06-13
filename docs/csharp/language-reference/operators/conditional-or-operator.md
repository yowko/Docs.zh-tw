---
title: '|| 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: d22e57d097edb0fe52b604e9c6431e167c410f0b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171802"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0341d-102">|| 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="0341d-102">|| Operator (C# Reference)</span></span>
<span data-ttu-id="0341d-103">條件式 OR 運算子 (`||`) 會執行其 `bool` 運算元的邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="0341d-103">The conditional-OR operator (`||`) performs a logical-OR of its `bool` operands.</span></span> <span data-ttu-id="0341d-104">如果第一個運算元評估值為 `true`，就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="0341d-104">If the first operand evaluates to `true`, the second operand isn't evaluated.</span></span> <span data-ttu-id="0341d-105">如果第一個運算元評估值為 `false`，第二個運算子會判斷整個 OR 運算式是評估為`true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="0341d-105">If the first operand evaluates to `false`, the second operator determines whether the OR expression as a whole evaluates to `true` or `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0341d-106">備註</span><span class="sxs-lookup"><span data-stu-id="0341d-106">Remarks</span></span>  
 <span data-ttu-id="0341d-107">作業</span><span class="sxs-lookup"><span data-stu-id="0341d-107">The operation</span></span>  
  
```csharp  
x || y  
```  
  
 <span data-ttu-id="0341d-108">對應至作業</span><span class="sxs-lookup"><span data-stu-id="0341d-108">corresponds to the operation</span></span>  
  
```csharp  
x | y  
```  
  
 <span data-ttu-id="0341d-109">差異在於，如果 `x` 是 `true`，則不會評估 `y`，因為不論 `y` 的值為何，OR 運算都是 `true`。</span><span class="sxs-lookup"><span data-stu-id="0341d-109">except that if `x` is `true`, `y` is not evaluated because the OR operation is `true` regardless of the value of `y`.</span></span> <span data-ttu-id="0341d-110">這個概念稱為「最少運算」求值。</span><span class="sxs-lookup"><span data-stu-id="0341d-110">This concept is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="0341d-111">無法多載條件式 OR 運算子，但規則邏輯運算子與 [true](../../../csharp/language-reference/keywords/true.md) 和 [false](../../../csharp/language-reference/keywords/false.md) 運算子的多載具有某些限制，也會視為條件式邏輯運算子的多載。</span><span class="sxs-lookup"><span data-stu-id="0341d-111">The conditional-OR operator cannot be overloaded, but overloads of the regular logical operators and the [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) operators are, with certain restrictions, also considered to be overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0341d-112">範例</span><span class="sxs-lookup"><span data-stu-id="0341d-112">Example</span></span>  
 <span data-ttu-id="0341d-113">在下列範例中，使用 `||` 的運算式只會評估第一個運算元。</span><span class="sxs-lookup"><span data-stu-id="0341d-113">In the following examples, the expression that uses `||` evaluates only the first operand.</span></span> <span data-ttu-id="0341d-114">使用 `|` 的運算式則評估這兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="0341d-114">The expression that uses `|` evaluates both operands.</span></span> <span data-ttu-id="0341d-115">在第二個範例中，如果評估這兩個運算元，就會發生執行階段例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0341d-115">In the second example, a run-time exception occurs if both operands are evaluated.</span></span>  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0341d-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="0341d-116">See Also</span></span>  
 [<span data-ttu-id="0341d-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0341d-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0341d-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0341d-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0341d-119">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="0341d-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
