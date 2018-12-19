---
title: '&lt;= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
ms.openlocfilehash: 950ba3fc02e015f2574d123d1fd9adc116aae045
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243448"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="2ddbd-102">&lt;= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2ddbd-102">&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="2ddbd-103">如果第一個運算元小於或等於第二個運算元，則所有數值和列舉類型都會定義「小於或等於」關係運算子 (`<=`) 以傳回 `true`否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="2ddbd-103">All numeric and enumeration types define a "less than or equal" relational operator (`<=`) that returns `true` if the first operand is less than or equal to the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ddbd-104">備註</span><span class="sxs-lookup"><span data-stu-id="2ddbd-104">Remarks</span></span>  
 <span data-ttu-id="2ddbd-105">使用者定義型別可以多載 `<=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="2ddbd-105">User-defined types can overload the `<=` operator.</span></span> <span data-ttu-id="2ddbd-106">如需詳細資訊，請參閱[運算子](../../../csharp/language-reference/keywords/operator.md)。</span><span class="sxs-lookup"><span data-stu-id="2ddbd-106">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="2ddbd-107">如果多載 `<=`，也必須多載 [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="2ddbd-107">If `<=` is overloaded, [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="2ddbd-108">整數類資料類型上的作業通常允許用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="2ddbd-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ddbd-109">範例</span><span class="sxs-lookup"><span data-stu-id="2ddbd-109">Example</span></span>  
 [!code-csharp[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2ddbd-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="2ddbd-110">See Also</span></span>

- [<span data-ttu-id="2ddbd-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="2ddbd-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2ddbd-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2ddbd-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2ddbd-113">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="2ddbd-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="2ddbd-114">explicit</span><span class="sxs-lookup"><span data-stu-id="2ddbd-114">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
