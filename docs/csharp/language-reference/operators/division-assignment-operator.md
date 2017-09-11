---
title: "/= 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5e105bf11f5413d77d62be4177ed22ba420312c3
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="19c2f-102">/= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="19c2f-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="19c2f-103">除法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="19c2f-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19c2f-104">備註</span><span class="sxs-lookup"><span data-stu-id="19c2f-104">Remarks</span></span>  
 <span data-ttu-id="19c2f-105">使用 `/=` 指派運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="19c2f-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```  
x /= y  
```  
  
 <span data-ttu-id="19c2f-106">相當於</span><span class="sxs-lookup"><span data-stu-id="19c2f-106">is equivalent to</span></span>  
  
```  
x = x / y  
```  
  
 <span data-ttu-id="19c2f-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="19c2f-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="19c2f-108">會針對要執行除法的數值類型，預先定義 [/ 運算子](../../../csharp/language-reference/operators/division-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="19c2f-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="19c2f-109">無法直接多載 `/=` 運算子，但使用者定義型別可以多載 [/ 運算子](../../../csharp/language-reference/operators/division-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="19c2f-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="19c2f-110">在所有複合指派運算子上，多載二元運算子會隱含地多載對等的複合指派。</span><span class="sxs-lookup"><span data-stu-id="19c2f-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19c2f-111">範例</span><span class="sxs-lookup"><span data-stu-id="19c2f-111">Example</span></span>  
 <span data-ttu-id="19c2f-112">[!code-cs[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="19c2f-112">[!code-cs[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19c2f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19c2f-113">See Also</span></span>  
 <span data-ttu-id="19c2f-114">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="19c2f-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="19c2f-115">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="19c2f-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="19c2f-116">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="19c2f-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

