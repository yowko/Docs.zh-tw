---
title: "&amp;&amp; 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&&_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 18
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
ms.openlocfilehash: 1da61947cbc85e5b3045513e99e013d1e4fae4b3
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="39a0b-102">&amp;&amp; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="39a0b-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="39a0b-103">條件式 AND 運算子 (`&&`) 會執行其 `bool` 運算元的邏輯 AND，但只會評估其第二個運算元 (必要的話)。</span><span class="sxs-lookup"><span data-stu-id="39a0b-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39a0b-104">備註</span><span class="sxs-lookup"><span data-stu-id="39a0b-104">Remarks</span></span>  
 <span data-ttu-id="39a0b-105">作業</span><span class="sxs-lookup"><span data-stu-id="39a0b-105">The operation</span></span>  
  
```  
x && y  
```  
  
 <span data-ttu-id="39a0b-106">對應至作業</span><span class="sxs-lookup"><span data-stu-id="39a0b-106">corresponds to the operation</span></span>  
  
```  
x & y  
```  
  
 <span data-ttu-id="39a0b-107">差異在於，如果 `x` 是 `false`，則不會評估 `y`因為不論 `y` 的值為何，AND 運算的結果都是 `false`。</span><span class="sxs-lookup"><span data-stu-id="39a0b-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="39a0b-108">這稱為「最少運算」求值。</span><span class="sxs-lookup"><span data-stu-id="39a0b-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="39a0b-109">無法多載條件式 AND 運算子，但規則邏輯運算子 [true](../../../csharp/language-reference/keywords/true.md) 和 [false](../../../csharp/language-reference/keywords/false.md) 的多載會具有某些限制，也會視為條件式邏輯運算子的多載。</span><span class="sxs-lookup"><span data-stu-id="39a0b-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39a0b-110">範例</span><span class="sxs-lookup"><span data-stu-id="39a0b-110">Example</span></span>  
 <span data-ttu-id="39a0b-111">在下列範例中，第二個 `if` 陳述式中的條件式運算式只會評估第一個運算元，因為運算元會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="39a0b-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 <span data-ttu-id="39a0b-112">[!code-cs[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="39a0b-112">[!code-cs[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="39a0b-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="39a0b-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="39a0b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39a0b-114">See Also</span></span>  
 <span data-ttu-id="39a0b-115">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="39a0b-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="39a0b-116">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="39a0b-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="39a0b-117">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="39a0b-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

