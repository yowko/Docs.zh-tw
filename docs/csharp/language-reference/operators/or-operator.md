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
ms.openlocfilehash: d95fe29aa7ffab9938e8edc57999445268fe41a8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085701"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="02d24-102">| 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="02d24-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="02d24-103">整數型別和 `bool` 會預先定義二元 `|` 運算子。</span><span class="sxs-lookup"><span data-stu-id="02d24-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="02d24-104">對於整數型別，`|` 會計算其運算元的位元 OR。</span><span class="sxs-lookup"><span data-stu-id="02d24-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="02d24-105">對於 `bool` 運算元，`|` 會計算其運算元的邏輯 OR；亦即，如果且唯有當其兩個運算元都是 `false` 時，結果會是 `false`。</span><span class="sxs-lookup"><span data-stu-id="02d24-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02d24-106">備註</span><span class="sxs-lookup"><span data-stu-id="02d24-106">Remarks</span></span>  
 <span data-ttu-id="02d24-107">二元 `|` 運算子會評估兩個運算元，不論第一個運算元的值為何，其與 [條件式-OR 運算子]     (conditional-or-operator.md) `||` 不同。</span><span class="sxs-lookup"><span data-stu-id="02d24-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator]     (conditional-or-operator.md) `||`.</span></span>
 
 <span data-ttu-id="02d24-108">使用者定義型別可以多載 `|` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="02d24-108">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02d24-109">範例</span><span class="sxs-lookup"><span data-stu-id="02d24-109">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="02d24-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="02d24-110">See Also</span></span>

- [<span data-ttu-id="02d24-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="02d24-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="02d24-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="02d24-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="02d24-113">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="02d24-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
