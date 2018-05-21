---
title: '&gt; 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
ms.openlocfilehash: 1589c5e785b33db6106a0ef0a58202e771db9fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="5b811-102">&gt; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5b811-102">&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="5b811-103">如果第一個運算元大於第二個運算元，則所有數值和列舉類型都會定義「大於」關係運算子 (`>`) 以傳回 `true`，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="5b811-103">All numeric and enumeration types define a "greater than" relational operator (`>`) that returns `true` if the first operand is greater than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b811-104">備註</span><span class="sxs-lookup"><span data-stu-id="5b811-104">Remarks</span></span>  
 <span data-ttu-id="5b811-105">使用者定義型別可以多載 `>` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="5b811-105">User-defined types can overload the `>` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="5b811-106">如果多載 `>`，也必須多載 [<](../../../csharp/language-reference/operators/less-than-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="5b811-106">If `>` is overloaded, [<](../../../csharp/language-reference/operators/less-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="5b811-107">二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="5b811-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b811-108">範例</span><span class="sxs-lookup"><span data-stu-id="5b811-108">Example</span></span>  
 [!code-csharp[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5b811-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="5b811-109">See Also</span></span>  
 [<span data-ttu-id="5b811-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="5b811-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5b811-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5b811-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5b811-112">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="5b811-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="5b811-113">explicit</span><span class="sxs-lookup"><span data-stu-id="5b811-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
