---
title: '|= 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: fe56005ce94656b5e8a075cddfb91dc0da096cf7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44194503"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6aed2-102">|= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6aed2-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="6aed2-103">OR 指派運算子。</span><span class="sxs-lookup"><span data-stu-id="6aed2-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6aed2-104">備註</span><span class="sxs-lookup"><span data-stu-id="6aed2-104">Remarks</span></span>  
 <span data-ttu-id="6aed2-105">使用 `|=` 指派運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="6aed2-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```csharp  
x |= y  
```  
  
 <span data-ttu-id="6aed2-106">相當於</span><span class="sxs-lookup"><span data-stu-id="6aed2-106">is equivalent to</span></span>  
  
```csharp  
x = x | y  
```  
  
 <span data-ttu-id="6aed2-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="6aed2-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="6aed2-108">[&#124; 運算子](../../../csharp/language-reference/operators/or-operator.md) 在整數運算元上執行位元邏輯 OR 運算，在 bool 運算元上執行邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="6aed2-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="6aed2-109">無法直接多載 `|=` 運算子，但使用者定義型別可以多載 [&#124; 運算子](../../../csharp/language-reference/operators/or-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="6aed2-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6aed2-110">範例</span><span class="sxs-lookup"><span data-stu-id="6aed2-110">Example</span></span>  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6aed2-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="6aed2-111">See Also</span></span>

- [<span data-ttu-id="6aed2-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6aed2-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="6aed2-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6aed2-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6aed2-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="6aed2-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
