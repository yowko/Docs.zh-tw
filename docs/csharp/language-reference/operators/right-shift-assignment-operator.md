---
title: '&gt;&gt;= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: aebc92ffb007db7b4950313874ebc2bf3c40615f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239442"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="cbd5a-102">&gt;&gt;= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="cbd5a-102">&gt;&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="cbd5a-103">右移指派運算子。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-103">The right-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbd5a-104">備註</span><span class="sxs-lookup"><span data-stu-id="cbd5a-104">Remarks</span></span>  
 <span data-ttu-id="cbd5a-105">以下格式的運算式</span><span class="sxs-lookup"><span data-stu-id="cbd5a-105">An expression of the form</span></span>  
  
```csharp  
x >>= y  
```  
  
 <span data-ttu-id="cbd5a-106">評估為</span><span class="sxs-lookup"><span data-stu-id="cbd5a-106">is evaluated as</span></span>  
  
```csharp  
x = x >> y  
```  
  
 <span data-ttu-id="cbd5a-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="cbd5a-108">[>> 運算子](../../../csharp/language-reference/operators/right-shift-operator.md)會將 `x` 右移 `y` 所指定的數量。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-108">The [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>  
  
 <span data-ttu-id="cbd5a-109">無法直接多載 >>= 運算子，但使用者定義型別可以多載 [>> 運算子](../../../csharp/language-reference/operators/right-shift-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbd5a-110">範例</span><span class="sxs-lookup"><span data-stu-id="cbd5a-110">Example</span></span>  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cbd5a-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="cbd5a-111">See Also</span></span>

- [<span data-ttu-id="cbd5a-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="cbd5a-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="cbd5a-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cbd5a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="cbd5a-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="cbd5a-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
