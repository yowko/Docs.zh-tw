---
title: "() 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d62e6c93dcc69c892d4ca96ace3806cb1c8d989
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="73423-102">() 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="73423-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="73423-103">除了用來指定運算式中運算的順序，括號也可用來執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="73423-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="73423-104">指定轉換或型別轉換。</span><span class="sxs-lookup"><span data-stu-id="73423-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="73423-105">叫用方法或委派。</span><span class="sxs-lookup"><span data-stu-id="73423-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="73423-106">備註</span><span class="sxs-lookup"><span data-stu-id="73423-106">Remarks</span></span>  
 <span data-ttu-id="73423-107">轉換會明確叫用轉換運算子，將某個類型轉換為另一個類型；若沒有定義這類轉換運算子，轉換就會失敗。</span><span class="sxs-lookup"><span data-stu-id="73423-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="73423-108">若要定義轉換運算子，請參閱 [explicit](../../../csharp/language-reference/keywords/explicit.md) 和 [implicit](../../../csharp/language-reference/keywords/implicit.md)。</span><span class="sxs-lookup"><span data-stu-id="73423-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="73423-109">`()` 運算子無法多載。</span><span class="sxs-lookup"><span data-stu-id="73423-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="73423-110">如需詳細資訊，請參閱[轉換和型別轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="73423-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="73423-111">cast 運算式可能會導致語法模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="73423-111">A cast expression could lead to ambiguous syntax.</span></span> <span data-ttu-id="73423-112">例如，運算式 `(x)–y` 可以解譯成 cast 運算式 (由 –y 至 x 類型的轉換)，或是結合括號運算式的加法運算式 (該括號運算式會計算 x – y 的值)。</span><span class="sxs-lookup"><span data-stu-id="73423-112">For example, the expression `(x)–y` could be either interpreted as a cast expression (a cast of –y to type x) or as an additive expression combined with a parenthesized expression, which computes the value x – y.</span></span>  
  
 <span data-ttu-id="73423-113">如需方法引動過程的詳細資訊，請參閱[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="73423-113">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="73423-114">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="73423-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73423-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73423-115">See Also</span></span>  
 [<span data-ttu-id="73423-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="73423-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="73423-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="73423-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="73423-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="73423-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
