---
title: "-&gt; 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c5918f56257feb29d2624ba29b8cebaaa4f4ebe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="93692-102">-&gt; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="93692-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="93692-103">`->` 運算子結合了指標取值和成員存取。</span><span class="sxs-lookup"><span data-stu-id="93692-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93692-104">備註</span><span class="sxs-lookup"><span data-stu-id="93692-104">Remarks</span></span>  
 <span data-ttu-id="93692-105">以下格式的運算式：</span><span class="sxs-lookup"><span data-stu-id="93692-105">An expression of the form,</span></span>  
  
```  
x->y  
```  
  
 <span data-ttu-id="93692-106">(其中 `x` 是類型 `T*` 的指標，而 `y` 是 `T` 的成員) 相當於：</span><span class="sxs-lookup"><span data-stu-id="93692-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```  
(*x).y  
```  
  
 <span data-ttu-id="93692-107">`->` 運算子只能用於標記為 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="93692-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="93692-108">`->` 運算子無法多載。</span><span class="sxs-lookup"><span data-stu-id="93692-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93692-109">範例</span><span class="sxs-lookup"><span data-stu-id="93692-109">Example</span></span>  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="93692-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93692-110">See Also</span></span>  
 [<span data-ttu-id="93692-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="93692-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="93692-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="93692-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="93692-113">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="93692-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
