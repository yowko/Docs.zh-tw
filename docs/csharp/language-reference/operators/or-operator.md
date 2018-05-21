---
title: '| 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 7b62af53f0d8b7cba29f4496887717f1726eabf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="23088-102">| 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="23088-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="23088-103">整數型別和 `bool` 會預先定義二元 `|` 運算子。</span><span class="sxs-lookup"><span data-stu-id="23088-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="23088-104">對於整數型別，`|` 會計算其運算元的位元 OR。</span><span class="sxs-lookup"><span data-stu-id="23088-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="23088-105">對於 `bool` 運算元，`|` 會計算其運算元的邏輯 OR；亦即，如果且唯有當其兩個運算元都是 `false` 時，結果會是 `false`。</span><span class="sxs-lookup"><span data-stu-id="23088-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23088-106">備註</span><span class="sxs-lookup"><span data-stu-id="23088-106">Remarks</span></span>  
 <span data-ttu-id="23088-107">使用者定義型別可以多載 `|` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="23088-107">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23088-108">範例</span><span class="sxs-lookup"><span data-stu-id="23088-108">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="23088-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="23088-109">See Also</span></span>  
 [<span data-ttu-id="23088-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="23088-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="23088-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="23088-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="23088-112">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="23088-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
