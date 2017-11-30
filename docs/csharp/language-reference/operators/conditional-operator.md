---
title: "?: 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9abfe4ca6be29b54edd591b503069c15e02c3532
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="56d2b-102">?: 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="56d2b-102">?: Operator (C# Reference)</span></span>
<span data-ttu-id="56d2b-103">條件運算子 (`?:`) 是根據布林運算式的值傳回兩個值的其中一個。</span><span class="sxs-lookup"><span data-stu-id="56d2b-103">The conditional operator (`?:`) returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="56d2b-104">以下是條件運算子的語法。</span><span class="sxs-lookup"><span data-stu-id="56d2b-104">Following is the syntax for the conditional operator.</span></span>  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a><span data-ttu-id="56d2b-105">備註</span><span class="sxs-lookup"><span data-stu-id="56d2b-105">Remarks</span></span>  
 <span data-ttu-id="56d2b-106">`condition` 必須判斷值為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="56d2b-106">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="56d2b-107">如果 `condition` 為 `true`，則會評估 `first_expression` 並產生結果。</span><span class="sxs-lookup"><span data-stu-id="56d2b-107">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="56d2b-108">如果 `condition` 為 `false`，則會評估 `second_expression` 並產生結果。</span><span class="sxs-lookup"><span data-stu-id="56d2b-108">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="56d2b-109">只會評估兩個運算式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="56d2b-109">Only one of the two expressions is evaluated.</span></span>  
  
 <span data-ttu-id="56d2b-110">`first_expression` 和 `second_expression` 必須屬於相同類型，否則必須從其中一種類型隱含轉換為另一種類型。</span><span class="sxs-lookup"><span data-stu-id="56d2b-110">Either the type of `first_expression` and `second_expression` must be the same, or an implicit conversion must exist from one type to the other.</span></span>  
  
 <span data-ttu-id="56d2b-111">你可以使用條件運算子更精確地表示可能需要 `if-else` 建構的計算。</span><span class="sxs-lookup"><span data-stu-id="56d2b-111">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="56d2b-112">例如，下列程式碼會先使用 `if` 陳述式，再使用條件運算子將整數分類為正數或負數。</span><span class="sxs-lookup"><span data-stu-id="56d2b-112">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="56d2b-113">條件運算子是右向關聯。</span><span class="sxs-lookup"><span data-stu-id="56d2b-113">The conditional operator is right-associative.</span></span> <span data-ttu-id="56d2b-114">運算式 `a ? b : c ? d : e` 會判斷值為 `a ? b : (c ? d : e)`，而不是 `(a ? b : c) ? d : e`。</span><span class="sxs-lookup"><span data-stu-id="56d2b-114">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
 <span data-ttu-id="56d2b-115">條件運算子不能多載。</span><span class="sxs-lookup"><span data-stu-id="56d2b-115">The conditional operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56d2b-116">範例</span><span class="sxs-lookup"><span data-stu-id="56d2b-116">Example</span></span>  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="56d2b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56d2b-117">See Also</span></span>  
 [<span data-ttu-id="56d2b-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="56d2b-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="56d2b-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="56d2b-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="56d2b-120">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="56d2b-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="56d2b-121">if-else</span><span class="sxs-lookup"><span data-stu-id="56d2b-121">if-else</span></span>](../../../csharp/language-reference/keywords/if-else.md)  
 [<span data-ttu-id="56d2b-122">?.和嗎？運算子</span><span class="sxs-lookup"><span data-stu-id="56d2b-122">?. and ?Operators</span></span>](../../../csharp/language-reference/operators/null-conditional-operators.md)  
 [<span data-ttu-id="56d2b-123">??運算子</span><span class="sxs-lookup"><span data-stu-id="56d2b-123">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)
