---
title: '| 運算子 (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 374adc30e6937a68d67bfae152f2546c854b829b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4739e-102">| 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4739e-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="4739e-103">整數型別和 `bool` 會預先定義二元 `|` 運算子。</span><span class="sxs-lookup"><span data-stu-id="4739e-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="4739e-104">對於整數型別，`|` 會計算其運算元的位元 OR。</span><span class="sxs-lookup"><span data-stu-id="4739e-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="4739e-105">對於 `bool` 運算元，`|` 會計算其運算元的邏輯 OR；亦即，如果且唯有當其兩個運算元都是 `false` 時，結果會是 `false`。</span><span class="sxs-lookup"><span data-stu-id="4739e-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4739e-106">備註</span><span class="sxs-lookup"><span data-stu-id="4739e-106">Remarks</span></span>  
 <span data-ttu-id="4739e-107">使用者定義型別可以多載 `|` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="4739e-107">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4739e-108">範例</span><span class="sxs-lookup"><span data-stu-id="4739e-108">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4739e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4739e-109">See Also</span></span>  
 [<span data-ttu-id="4739e-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4739e-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4739e-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4739e-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4739e-112">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="4739e-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
