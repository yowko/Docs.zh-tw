---
title: '*= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: f8604cdadeda14a5761bc923bd966186fd258a6d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245346"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a7adc-102">\*= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a7adc-102">\*= Operator (C# Reference)</span></span>
<span data-ttu-id="a7adc-103">二進位乘法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="a7adc-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7adc-104">備註</span><span class="sxs-lookup"><span data-stu-id="a7adc-104">Remarks</span></span>  
 <span data-ttu-id="a7adc-105">使用 `*=` 指派運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="a7adc-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```csharp  
x *= y  
```  
  
 <span data-ttu-id="a7adc-106">相當於</span><span class="sxs-lookup"><span data-stu-id="a7adc-106">is equivalent to</span></span>  
  
```csharp  
x = x * y  
```  
  
 <span data-ttu-id="a7adc-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="a7adc-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="a7adc-108">對於對要執行乘法的數值類型，已預先定義 [\* 運算子](../../../csharp/language-reference/operators/multiplication-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="a7adc-108">The [\* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="a7adc-109">無法直接多載 `*=` 運算子，但使用者定義型別可以多載 [\* 運算子](../../../csharp/language-reference/operators/multiplication-operator.md) (請參閱[運算子](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="a7adc-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [\* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7adc-110">範例</span><span class="sxs-lookup"><span data-stu-id="a7adc-110">Example</span></span>  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a7adc-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="a7adc-111">See Also</span></span>

- [<span data-ttu-id="a7adc-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="a7adc-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a7adc-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a7adc-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a7adc-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="a7adc-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
