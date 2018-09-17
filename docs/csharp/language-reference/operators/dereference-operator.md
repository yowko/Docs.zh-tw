---
title: -&gt; 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: fb95e508ce1339868723bcc3178851e8c1355c1f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45609514"
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="2ab5b-102">-&gt; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2ab5b-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="2ab5b-103">`->` 運算子結合了指標取值和成員存取。</span><span class="sxs-lookup"><span data-stu-id="2ab5b-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ab5b-104">備註</span><span class="sxs-lookup"><span data-stu-id="2ab5b-104">Remarks</span></span>  
 <span data-ttu-id="2ab5b-105">以下格式的運算式：</span><span class="sxs-lookup"><span data-stu-id="2ab5b-105">An expression of the form,</span></span>  
  
```csharp  
x->y  
```  
  
 <span data-ttu-id="2ab5b-106">(其中 `x` 是類型 `T*` 的指標，而 `y` 是 `T` 的成員) 相當於：</span><span class="sxs-lookup"><span data-stu-id="2ab5b-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```csharp  
(*x).y  
```  
  
 <span data-ttu-id="2ab5b-107">`->` 運算子只能用於標記為 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2ab5b-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="2ab5b-108">無法多載 `->` 運算子。</span><span class="sxs-lookup"><span data-stu-id="2ab5b-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ab5b-109">範例</span><span class="sxs-lookup"><span data-stu-id="2ab5b-109">Example</span></span>  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2ab5b-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="2ab5b-110">See Also</span></span>

- [<span data-ttu-id="2ab5b-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="2ab5b-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2ab5b-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2ab5b-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2ab5b-113">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="2ab5b-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
