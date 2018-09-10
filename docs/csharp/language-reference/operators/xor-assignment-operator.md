---
title: ^= 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: d6546f23ffb6dee792339a7e3863bf58ae668d58
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857228"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="91d46-102">^= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="91d46-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="91d46-103">互斥 OR 指派運算子。</span><span class="sxs-lookup"><span data-stu-id="91d46-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91d46-104">備註</span><span class="sxs-lookup"><span data-stu-id="91d46-104">Remarks</span></span>  
 <span data-ttu-id="91d46-105">以下格式的運算式</span><span class="sxs-lookup"><span data-stu-id="91d46-105">An expression of the form</span></span>  
  
```csharp  
x ^= y  
```  
  
 <span data-ttu-id="91d46-106">評估為</span><span class="sxs-lookup"><span data-stu-id="91d46-106">is evaluated as</span></span>  
  
```csharp  
x = x ^ y  
```  
  
 <span data-ttu-id="91d46-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="91d46-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="91d46-108">[^ 運算子](../../../csharp/language-reference/operators/xor-operator.md)會在整數運算元上執行位元互斥 OR 運算，以及在 [bool](../../../csharp/language-reference/keywords/bool.md) 運算元上執行邏輯互斥 OR。</span><span class="sxs-lookup"><span data-stu-id="91d46-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="91d46-109">無法直接多載 ^= 運算子，但使用者定義型別可以多載 [^ 運算子](../../../csharp/language-reference/operators/xor-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="91d46-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="91d46-110">範例</span><span class="sxs-lookup"><span data-stu-id="91d46-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="91d46-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="91d46-111">See Also</span></span>

- [<span data-ttu-id="91d46-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="91d46-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="91d46-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="91d46-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="91d46-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="91d46-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
