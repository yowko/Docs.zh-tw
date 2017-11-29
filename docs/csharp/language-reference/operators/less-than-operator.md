---
title: "&lt; 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76d53d4c943c886f6b8c8a68e2b8bb12bc9a9d6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="71d41-102">&lt; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="71d41-102">&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="71d41-103">如果第一個運算元小於第二個運算元，則所有數值和列舉類型都會定義「小於」關係運算子 (`<`) 以傳回 `true`否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="71d41-103">All numeric and enumeration types define a "less than" relational operator (`<`) that returns `true` if the first operand is less than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71d41-104">備註</span><span class="sxs-lookup"><span data-stu-id="71d41-104">Remarks</span></span>  
 <span data-ttu-id="71d41-105">使用者定義型別可以多載 `<` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="71d41-105">User-defined types can overload the `<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="71d41-106">如果多載 `<`，也必須多載 [>](../../../csharp/language-reference/operators/greater-than-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="71d41-106">If `<` is overloaded, [>](../../../csharp/language-reference/operators/greater-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="71d41-107">二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="71d41-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71d41-108">範例</span><span class="sxs-lookup"><span data-stu-id="71d41-108">Example</span></span>  
 [!code-csharp[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="71d41-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71d41-109">See Also</span></span>  
 [<span data-ttu-id="71d41-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="71d41-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="71d41-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="71d41-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="71d41-112">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="71d41-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
