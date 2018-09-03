---
title: '&amp;= 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: f3a6fe20ca89a90b5a64118d73fb39e9a364d1e9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406731"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="6d40b-102">&amp;= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6d40b-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="6d40b-103">AND 指派運算子。</span><span class="sxs-lookup"><span data-stu-id="6d40b-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d40b-104">備註</span><span class="sxs-lookup"><span data-stu-id="6d40b-104">Remarks</span></span>  
 <span data-ttu-id="6d40b-105">使用 `&=` 指派運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="6d40b-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```csharp  
x &= y  
```  
  
 <span data-ttu-id="6d40b-106">相當於</span><span class="sxs-lookup"><span data-stu-id="6d40b-106">is equivalent to</span></span>  
  
```csharp  
x = x & y  
```  
  
 <span data-ttu-id="6d40b-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="6d40b-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="6d40b-108">[& 運算子](../../../csharp/language-reference/operators/and-operator.md)在整數運算元上執行位元邏輯 AND 運算，在 `bool` 運算元上執行邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="6d40b-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="6d40b-109">無法直接多載 `&=` 運算子，但使用者定義型別可以多載二進位 [& 運算子](../../../csharp/language-reference/operators/and-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="6d40b-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d40b-110">範例</span><span class="sxs-lookup"><span data-stu-id="6d40b-110">Example</span></span>  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6d40b-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="6d40b-111">See Also</span></span>

- [<span data-ttu-id="6d40b-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6d40b-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="6d40b-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6d40b-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6d40b-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="6d40b-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
