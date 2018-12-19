---
title: '&lt; 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
ms.openlocfilehash: 3cc125471eee7bf0002e9844c2a1cdc05e8d4a03
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241218"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="a1314-102">&lt; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a1314-102">&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="a1314-103">如果第一個運算元小於第二個運算元，則所有數值和列舉類型都會定義「小於」關係運算子 (`<`) 以傳回 `true`否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="a1314-103">All numeric and enumeration types define a "less than" relational operator (`<`) that returns `true` if the first operand is less than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1314-104">備註</span><span class="sxs-lookup"><span data-stu-id="a1314-104">Remarks</span></span>  
 <span data-ttu-id="a1314-105">使用者定義型別可以多載 `<` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="a1314-105">User-defined types can overload the `<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="a1314-106">如果多載 `<`，也必須多載 [>](../../../csharp/language-reference/operators/greater-than-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="a1314-106">If `<` is overloaded, [>](../../../csharp/language-reference/operators/greater-than-operator.md) must also be overloaded.</span></span>
  
## <a name="example"></a><span data-ttu-id="a1314-107">範例</span><span class="sxs-lookup"><span data-stu-id="a1314-107">Example</span></span>  
 [!code-csharp[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a1314-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="a1314-108">See Also</span></span>

- [<span data-ttu-id="a1314-109">C# 參考</span><span class="sxs-lookup"><span data-stu-id="a1314-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a1314-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a1314-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a1314-111">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="a1314-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
