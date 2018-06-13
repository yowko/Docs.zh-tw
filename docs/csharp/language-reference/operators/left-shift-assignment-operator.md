---
title: '&lt;&lt;= 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: e5f3886670baa34b0360501ee15280b93fac36bc
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171789"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="4f752-102">&lt;&lt;= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4f752-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="4f752-103">左移指派運算子。</span><span class="sxs-lookup"><span data-stu-id="4f752-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f752-104">備註</span><span class="sxs-lookup"><span data-stu-id="4f752-104">Remarks</span></span>  
 <span data-ttu-id="4f752-105">以下格式的運算式</span><span class="sxs-lookup"><span data-stu-id="4f752-105">An expression of the form</span></span>  
  
```csharp  
x <<= y  
```  
  
 <span data-ttu-id="4f752-106">評估為</span><span class="sxs-lookup"><span data-stu-id="4f752-106">is evaluated as</span></span>  
  
```csharp  
x = x << y  
```  
  
 <span data-ttu-id="4f752-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="4f752-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="4f752-108">[<< 運算子](../../../csharp/language-reference/operators/left-shift-operator.md)會將 `x` 左移 `y` 所指定的位元數。</span><span class="sxs-lookup"><span data-stu-id="4f752-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="4f752-109">無法直接多載 `<<=` 運算子，但使用者定義型別可以多載 [<< 運算子](../../../csharp/language-reference/operators/left-shift-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="4f752-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f752-110">範例</span><span class="sxs-lookup"><span data-stu-id="4f752-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4f752-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="4f752-111">See Also</span></span>  
 [<span data-ttu-id="4f752-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4f752-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4f752-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4f752-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4f752-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="4f752-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
