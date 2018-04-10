---
title: '!= 運算子 (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b69d0b12734e690f0ba0209ccbbc7627ff92fe8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="58754-102">!= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="58754-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="58754-103">不等比較運算子 (`!=`) 會在其運算元相等時傳回 false，否則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="58754-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="58754-104">所有類型 (包括字串和物件) 已預先定義不等比較運算子。</span><span class="sxs-lookup"><span data-stu-id="58754-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="58754-105">使用者定義型別可以多載 `!=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="58754-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58754-106">備註</span><span class="sxs-lookup"><span data-stu-id="58754-106">Remarks</span></span>  
 <span data-ttu-id="58754-107">對於預先定義的實值型別，不等比較運算子 (`!=`) 在其運算元的值不同時傳回 true；否則傳回 false。</span><span class="sxs-lookup"><span data-stu-id="58754-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="58754-108">對於 `string` 以外的參考型別，若 `!=` 的兩個運算元參考不同物件，則會傳回 true。</span><span class="sxs-lookup"><span data-stu-id="58754-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="58754-109">對於 `string` 類型，`!=` 會比較字串的值。</span><span class="sxs-lookup"><span data-stu-id="58754-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="58754-110">使用者定義的實值型別可以多載 `!=` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="58754-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="58754-111">使用者定義的參考型別也可以，不過 `!=` 對預先定義和使用者定義之參考型別的預設運作方式會如上所述。</span><span class="sxs-lookup"><span data-stu-id="58754-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="58754-112">如果多載 `!=`，也必須多載 [==](../../../csharp/language-reference/operators/equality-comparison-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="58754-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="58754-113">整數類資料類型上的作業通常允許用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="58754-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58754-114">範例</span><span class="sxs-lookup"><span data-stu-id="58754-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="58754-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58754-115">See Also</span></span>  
 [<span data-ttu-id="58754-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="58754-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="58754-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="58754-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="58754-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="58754-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
