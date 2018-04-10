---
title: '|= 運算子 (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aac4fd6016b65daa15da4bd3a414f385edce7c22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9c0d2-102">|= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="9c0d2-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="9c0d2-103">OR 指派運算子。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c0d2-104">備註</span><span class="sxs-lookup"><span data-stu-id="9c0d2-104">Remarks</span></span>  
 <span data-ttu-id="9c0d2-105">使用 `|=` 指派運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="9c0d2-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```  
x |= y  
```  
  
 <span data-ttu-id="9c0d2-106">相當於</span><span class="sxs-lookup"><span data-stu-id="9c0d2-106">is equivalent to</span></span>  
  
```  
x = x | y  
```  
  
 <span data-ttu-id="9c0d2-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="9c0d2-108">[&#124; 運算子](../../../csharp/language-reference/operators/or-operator.md) 在整數運算元上執行位元邏輯 OR 運算，在 bool 運算元上執行邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="9c0d2-109">無法直接多載 `|=` 運算子，但使用者定義型別可以多載 [&#124; 運算子](../../../csharp/language-reference/operators/or-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="9c0d2-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c0d2-110">範例</span><span class="sxs-lookup"><span data-stu-id="9c0d2-110">Example</span></span>  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9c0d2-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c0d2-111">See Also</span></span>  
 [<span data-ttu-id="9c0d2-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="9c0d2-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9c0d2-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9c0d2-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9c0d2-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="9c0d2-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
