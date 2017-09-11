---
title: "() 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ()_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: 22
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
ms.openlocfilehash: 1b0a683880f0791ee69ea5971756d104323b4303
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="3999c-102">() 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3999c-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="3999c-103">除了用來指定運算式中運算的順序，括號也可用來執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="3999c-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="3999c-104">指定轉換或型別轉換。</span><span class="sxs-lookup"><span data-stu-id="3999c-104">Specify casts, or type conversions.</span></span>  
  
     <span data-ttu-id="3999c-105">[!code-cs[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3999c-105">[!code-cs[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]</span></span>  
  
2.  <span data-ttu-id="3999c-106">叫用方法或委派。</span><span class="sxs-lookup"><span data-stu-id="3999c-106">Invoke methods or delegates.</span></span>  
  
     <span data-ttu-id="3999c-107">[!code-cs[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="3999c-107">[!code-cs[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3999c-108">備註</span><span class="sxs-lookup"><span data-stu-id="3999c-108">Remarks</span></span>  
 <span data-ttu-id="3999c-109">轉換會明確叫用轉換運算子，將某個類型轉換為另一個類型；若沒有定義這類轉換運算子，轉換就會失敗。</span><span class="sxs-lookup"><span data-stu-id="3999c-109">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="3999c-110">若要定義轉換運算子，請參閱 [explicit](../../../csharp/language-reference/keywords/explicit.md) 和 [implicit](../../../csharp/language-reference/keywords/implicit.md)。</span><span class="sxs-lookup"><span data-stu-id="3999c-110">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="3999c-111">`()` 運算子無法多載。</span><span class="sxs-lookup"><span data-stu-id="3999c-111">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="3999c-112">如需詳細資訊，請參閱[轉換和型別轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="3999c-112">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="3999c-113">cast 運算式可能會導致語法模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="3999c-113">A cast expression could lead to ambiguous syntax.</span></span> <span data-ttu-id="3999c-114">例如，運算式 `(x)–y` 可以解譯成 cast 運算式 (由 –y 至 x 類型的轉換)，或是結合括號運算式的加法運算式 (該括號運算式會計算 x – y 的值)。</span><span class="sxs-lookup"><span data-stu-id="3999c-114">For example, the expression `(x)–y` could be either interpreted as a cast expression (a cast of –y to type x) or as an additive expression combined with a parenthesized expression, which computes the value x – y.</span></span>  
  
 <span data-ttu-id="3999c-115">如需方法引動過程的詳細資訊，請參閱[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="3999c-115">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3999c-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3999c-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3999c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3999c-117">See Also</span></span>  
 <span data-ttu-id="3999c-118">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="3999c-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="3999c-119">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3999c-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="3999c-120">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="3999c-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

