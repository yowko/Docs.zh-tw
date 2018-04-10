---
title: '% 運算子 (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- modulus operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cea4aa03424e93f3ec144126d73c63931a737b54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="456f0-102">% 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="456f0-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="456f0-103">`%` 運算子會計算其第一個運算元除以第二個運算元之後的餘數。</span><span class="sxs-lookup"><span data-stu-id="456f0-103">The `%` operator computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="456f0-104">所有數值類型都有預先定義的餘數運算子。</span><span class="sxs-lookup"><span data-stu-id="456f0-104">All numeric types have predefined remainder operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="456f0-105">備註</span><span class="sxs-lookup"><span data-stu-id="456f0-105">Remarks</span></span>  
 <span data-ttu-id="456f0-106">使用者定義型別可以多載 `%` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="456f0-106">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="456f0-107">二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="456f0-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="456f0-108">範例</span><span class="sxs-lookup"><span data-stu-id="456f0-108">Example</span></span>  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="456f0-109">註解</span><span class="sxs-lookup"><span data-stu-id="456f0-109">Comments</span></span>  
 <span data-ttu-id="456f0-110">請注意與 double 類型建立關聯的四捨五入錯誤。</span><span class="sxs-lookup"><span data-stu-id="456f0-110">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="456f0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="456f0-111">See Also</span></span>  
 [<span data-ttu-id="456f0-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="456f0-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="456f0-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="456f0-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="456f0-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="456f0-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
