---
title: "- 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: -_CSharpKeyword
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 315d8cf47cc0819e124c1c08546ede580918f328
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-c-reference"></a><span data-ttu-id="74e53-102">- 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="74e53-102">- Operator (C# Reference)</span></span>
<span data-ttu-id="74e53-103">`-` 運算子可以作為一元或二元運算子。</span><span class="sxs-lookup"><span data-stu-id="74e53-103">The `-` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74e53-104">備註</span><span class="sxs-lookup"><span data-stu-id="74e53-104">Remarks</span></span>  
 <span data-ttu-id="74e53-105">會預先定義所有數字類型的一元 `-` 運算子。</span><span class="sxs-lookup"><span data-stu-id="74e53-105">Unary `-` operators are predefined for all numeric types.</span></span> <span data-ttu-id="74e53-106">對數值類型執行一元 `-` 運算的結果就是運算元的負數值。</span><span class="sxs-lookup"><span data-stu-id="74e53-106">The result of a unary `-` operation on a numeric type is the numeric negation of the operand.</span></span>  
  
 <span data-ttu-id="74e53-107">針對所有數值和列舉類型預先定義二元 `-` 運算子，以將第一個運算元減去第一個運算元。</span><span class="sxs-lookup"><span data-stu-id="74e53-107">Binary `-` operators are predefined for all numeric and enumeration types to subtract the second operand from the first.</span></span>  
  
 <span data-ttu-id="74e53-108">委派類型也會提供可執行委派移除的二元 `-` 運算子。</span><span class="sxs-lookup"><span data-stu-id="74e53-108">Delegate types also provide a binary `-` operator, which performs delegate removal.</span></span>  
  
 <span data-ttu-id="74e53-109">使用者定義型別可以多載一元 `-` 和二元 `-` 運算子。</span><span class="sxs-lookup"><span data-stu-id="74e53-109">User-defined types can overload the unary `-` and binary `-` operators.</span></span> <span data-ttu-id="74e53-110">如需詳細資訊，請參閱 [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md)。</span><span class="sxs-lookup"><span data-stu-id="74e53-110">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="74e53-111">範例</span><span class="sxs-lookup"><span data-stu-id="74e53-111">Example</span></span>  
 [!code-csharp[csRefOperators#40](../../../csharp/language-reference/operators/codesnippet/CSharp/subtraction-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="74e53-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74e53-112">See Also</span></span>  
 [<span data-ttu-id="74e53-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="74e53-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="74e53-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="74e53-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="74e53-115">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="74e53-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
