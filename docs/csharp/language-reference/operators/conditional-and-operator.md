---
title: '&amp;&amp; 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 459b791fde3e4d3940dbd3d916f940e81f365da6
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999726"
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="3924f-102">&amp;&amp; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3924f-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="3924f-103">條件式 AND 運算子 (`&&`) 會執行其 `bool` 運算元的邏輯 AND，但只有在必要時才會評估其第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="3924f-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3924f-104">備註</span><span class="sxs-lookup"><span data-stu-id="3924f-104">Remarks</span></span>  
 <span data-ttu-id="3924f-105">作業</span><span class="sxs-lookup"><span data-stu-id="3924f-105">The operation</span></span>  
  
```csharp  
x && y  
```  
  
 <span data-ttu-id="3924f-106">對應至作業</span><span class="sxs-lookup"><span data-stu-id="3924f-106">corresponds to the operation</span></span>  
  
```csharp  
x & y  
```  
  
 <span data-ttu-id="3924f-107">差異在於，如果 `x` 是 `false`，則不會評估 `y`因為不論 `y` 的值為何，AND 運算的結果都是 `false`。</span><span class="sxs-lookup"><span data-stu-id="3924f-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="3924f-108">這稱為「最少運算」求值。</span><span class="sxs-lookup"><span data-stu-id="3924f-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="3924f-109">無法多載條件式 AND 運算子，但規則邏輯運算子 [true](../../../csharp/language-reference/keywords/true.md) 和 [false](../../../csharp/language-reference/keywords/false.md) 的多載會具有某些限制，也會視為條件式邏輯運算子的多載。</span><span class="sxs-lookup"><span data-stu-id="3924f-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3924f-110">範例</span><span class="sxs-lookup"><span data-stu-id="3924f-110">Example</span></span>  
 <span data-ttu-id="3924f-111">在下列範例中，第二個 `if` 陳述式中的條件式運算式只會評估第一個運算元，因為運算元會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="3924f-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3924f-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3924f-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3924f-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="3924f-113">See Also</span></span>

- [<span data-ttu-id="3924f-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3924f-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="3924f-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3924f-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3924f-116">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="3924f-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
