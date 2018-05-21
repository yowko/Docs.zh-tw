---
title: '!= 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: e409e2a80886fd5f7f4cdbeaa9b4e3325f8a967b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f63d8-102">!= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f63d8-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="f63d8-103">不等比較運算子 (`!=`) 會在其運算元相等時傳回 false，否則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="f63d8-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="f63d8-104">所有類型 (包括字串和物件) 已預先定義不等比較運算子。</span><span class="sxs-lookup"><span data-stu-id="f63d8-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="f63d8-105">使用者定義型別可以多載 `!=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="f63d8-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f63d8-106">備註</span><span class="sxs-lookup"><span data-stu-id="f63d8-106">Remarks</span></span>  
 <span data-ttu-id="f63d8-107">對於預先定義的實值型別，不等比較運算子 (`!=`) 在其運算元的值不同時傳回 true；否則傳回 false。</span><span class="sxs-lookup"><span data-stu-id="f63d8-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="f63d8-108">對於 `string` 以外的參考型別，若 `!=` 的兩個運算元參考不同物件，則會傳回 true。</span><span class="sxs-lookup"><span data-stu-id="f63d8-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="f63d8-109">對於 `string` 類型，`!=` 會比較字串的值。</span><span class="sxs-lookup"><span data-stu-id="f63d8-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="f63d8-110">使用者定義的實值型別可以多載 `!=` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="f63d8-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="f63d8-111">使用者定義的參考型別也可以，不過 `!=` 對預先定義和使用者定義之參考型別的預設運作方式會如上所述。</span><span class="sxs-lookup"><span data-stu-id="f63d8-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="f63d8-112">如果多載 `!=`，也必須多載 [==](../../../csharp/language-reference/operators/equality-comparison-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="f63d8-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="f63d8-113">整數類資料類型上的作業通常允許用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="f63d8-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f63d8-114">範例</span><span class="sxs-lookup"><span data-stu-id="f63d8-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f63d8-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="f63d8-115">See Also</span></span>  
 [<span data-ttu-id="f63d8-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f63d8-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f63d8-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f63d8-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f63d8-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="f63d8-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
