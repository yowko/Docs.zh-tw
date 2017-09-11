---
title: "?: 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 794ff53fe471ef23163503f59599b528df127e2e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="4c817-102">?: 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4c817-102">?: Operator (C# Reference)</span></span>
<span data-ttu-id="4c817-103">條件運算子 (`?:`) 是根據布林運算式的值傳回兩個值的其中一個。</span><span class="sxs-lookup"><span data-stu-id="4c817-103">The conditional operator (`?:`) returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="4c817-104">以下是條件運算子的語法。</span><span class="sxs-lookup"><span data-stu-id="4c817-104">Following is the syntax for the conditional operator.</span></span>  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a><span data-ttu-id="4c817-105">備註</span><span class="sxs-lookup"><span data-stu-id="4c817-105">Remarks</span></span>  
 <span data-ttu-id="4c817-106">`condition` 必須判斷值為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="4c817-106">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="4c817-107">如果 `condition` 為 `true`，則會評估 `first_expression` 並產生結果。</span><span class="sxs-lookup"><span data-stu-id="4c817-107">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="4c817-108">如果 `condition` 為 `false`，則會評估 `second_expression` 並產生結果。</span><span class="sxs-lookup"><span data-stu-id="4c817-108">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="4c817-109">只會評估兩個運算式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="4c817-109">Only one of the two expressions is evaluated.</span></span>  
  
 <span data-ttu-id="4c817-110">`first_expression` 和 `second_expression` 必須屬於相同類型，否則必須從其中一種類型隱含轉換為另一種類型。</span><span class="sxs-lookup"><span data-stu-id="4c817-110">Either the type of `first_expression` and `second_expression` must be the same, or an implicit conversion must exist from one type to the other.</span></span>  
  
 <span data-ttu-id="4c817-111">你可以使用條件運算子更精確地表示可能需要 `if-else` 建構的計算。</span><span class="sxs-lookup"><span data-stu-id="4c817-111">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="4c817-112">例如，下列程式碼會先使用 `if` 陳述式，再使用條件運算子將整數分類為正數或負數。</span><span class="sxs-lookup"><span data-stu-id="4c817-112">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>  
  
```  
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 <span data-ttu-id="4c817-113">條件運算子是右向關聯。</span><span class="sxs-lookup"><span data-stu-id="4c817-113">The conditional operator is right-associative.</span></span> <span data-ttu-id="4c817-114">運算式 `a ? b : c ? d : e` 會判斷值為 `a ? b : (c ? d : e)`，而不是 `(a ? b : c) ? d : e`。</span><span class="sxs-lookup"><span data-stu-id="4c817-114">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
 <span data-ttu-id="4c817-115">條件運算子不能多載。</span><span class="sxs-lookup"><span data-stu-id="4c817-115">The conditional operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c817-116">範例</span><span class="sxs-lookup"><span data-stu-id="4c817-116">Example</span></span>  
 <span data-ttu-id="4c817-117">[!code-cs[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c817-117">[!code-cs[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c817-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c817-118">See Also</span></span>  
 <span data-ttu-id="4c817-119">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4c817-119">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4c817-120">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4c817-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4c817-121">[C# 運算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="4c817-121">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="4c817-122">[if-else](../../../csharp/language-reference/keywords/if-else.md) </span><span class="sxs-lookup"><span data-stu-id="4c817-122">[if-else](../../../csharp/language-reference/keywords/if-else.md) </span></span>  
 <span data-ttu-id="4c817-123">[?. 和 ? 運算子](../../../csharp/language-reference/operators/null-conditional-operators.md) </span><span class="sxs-lookup"><span data-stu-id="4c817-123">[?. and ?Operators](../../../csharp/language-reference/operators/null-conditional-operators.md) </span></span>  
 [<span data-ttu-id="4c817-124">??運算子</span><span class="sxs-lookup"><span data-stu-id="4c817-124">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)

