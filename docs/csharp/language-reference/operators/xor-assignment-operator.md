---
title: "^= 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ^=_CSharpKeyword
helpviewer_keywords: ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d4de06dbfd269dc5e0f2cc5003e8981068220a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4e899-102">^= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4e899-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="4e899-103">互斥 OR 指派運算子。</span><span class="sxs-lookup"><span data-stu-id="4e899-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e899-104">備註</span><span class="sxs-lookup"><span data-stu-id="4e899-104">Remarks</span></span>  
 <span data-ttu-id="4e899-105">以下格式的運算式</span><span class="sxs-lookup"><span data-stu-id="4e899-105">An expression of the form</span></span>  
  
```  
x ^= y  
```  
  
 <span data-ttu-id="4e899-106">評估為</span><span class="sxs-lookup"><span data-stu-id="4e899-106">is evaluated as</span></span>  
  
```  
x = x ^ y  
```  
  
 <span data-ttu-id="4e899-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="4e899-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="4e899-108">[^ 運算子](../../../csharp/language-reference/operators/xor-operator.md)會在整數運算元上執行位元互斥 OR 運算，以及在 [bool](../../../csharp/language-reference/keywords/bool.md) 運算元上執行邏輯互斥 OR。</span><span class="sxs-lookup"><span data-stu-id="4e899-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="4e899-109">無法直接多載 ^= 運算子，但使用者定義型別可以多載 [^ 運算子](../../../csharp/language-reference/operators/xor-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="4e899-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e899-110">範例</span><span class="sxs-lookup"><span data-stu-id="4e899-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4e899-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e899-111">See Also</span></span>  
 [<span data-ttu-id="4e899-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4e899-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4e899-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4e899-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4e899-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="4e899-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
