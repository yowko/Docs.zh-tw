---
title: "&amp;= 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bea90651faaafe7b754ce1cf16bddbab997d5f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="04178-102">&amp;= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="04178-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="04178-103">AND 指派運算子。</span><span class="sxs-lookup"><span data-stu-id="04178-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04178-104">備註</span><span class="sxs-lookup"><span data-stu-id="04178-104">Remarks</span></span>  
 <span data-ttu-id="04178-105">使用 `&=` 指派運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="04178-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```  
x &= y  
```  
  
 <span data-ttu-id="04178-106">相當於</span><span class="sxs-lookup"><span data-stu-id="04178-106">is equivalent to</span></span>  
  
```  
x = x & y  
```  
  
 <span data-ttu-id="04178-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="04178-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="04178-108">[& 運算子](../../../csharp/language-reference/operators/and-operator.md)在整數運算元上執行位元邏輯 AND 運算，在 `bool` 運算元上執行邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="04178-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="04178-109">無法直接多載 `&=` 運算子，但使用者定義型別可以多載二進位 [& 運算子](../../../csharp/language-reference/operators/and-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="04178-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04178-110">範例</span><span class="sxs-lookup"><span data-stu-id="04178-110">Example</span></span>  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="04178-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04178-111">See Also</span></span>  
 [<span data-ttu-id="04178-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="04178-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="04178-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="04178-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="04178-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="04178-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
