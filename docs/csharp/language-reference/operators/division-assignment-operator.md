---
title: /= 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: 8fff048cc441181aa3f0e3c0c638d501aaf9de3f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526304"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="65fad-102">/= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="65fad-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="65fad-103">除法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="65fad-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65fad-104">備註</span><span class="sxs-lookup"><span data-stu-id="65fad-104">Remarks</span></span>  
 <span data-ttu-id="65fad-105">使用 `/=` 指派運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="65fad-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```csharp  
x /= y  
```  
  
 <span data-ttu-id="65fad-106">相當於</span><span class="sxs-lookup"><span data-stu-id="65fad-106">is equivalent to</span></span>  
  
```csharp  
x = x / y  
```  
  
 <span data-ttu-id="65fad-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="65fad-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="65fad-108">會針對要執行除法的數值類型，預先定義 [/ 運算子](../../../csharp/language-reference/operators/division-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="65fad-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="65fad-109">無法直接多載 `/=` 運算子，但使用者定義型別可以多載 [/ 運算子](../../../csharp/language-reference/operators/division-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="65fad-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="65fad-110">在所有複合指派運算子上，多載二元運算子會隱含地多載對等的複合指派。</span><span class="sxs-lookup"><span data-stu-id="65fad-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65fad-111">範例</span><span class="sxs-lookup"><span data-stu-id="65fad-111">Example</span></span>  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="65fad-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="65fad-112">See Also</span></span>

- [<span data-ttu-id="65fad-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="65fad-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="65fad-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="65fad-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="65fad-115">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="65fad-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
