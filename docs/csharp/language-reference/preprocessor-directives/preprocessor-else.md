---
title: '#else (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: 662d19f38ce1f3a7a04c9abe27c1f217e3d848f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="else-c-reference"></a><span data-ttu-id="3c6e2-102">#else (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3c6e2-102">#else (C# Reference)</span></span>
<span data-ttu-id="3c6e2-103">`#else` 可讓您建立複合條件指示詞，如此，如果前面的 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 或 (選擇性) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) 指示詞中沒有運算式為 `true`，則編譯器會評估 `#else` 與後續 `#endif` 之間的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="3c6e2-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or (optional) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) directives to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c6e2-104">備註</span><span class="sxs-lookup"><span data-stu-id="3c6e2-104">Remarks</span></span>  
 <span data-ttu-id="3c6e2-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) 必須是 `#else` 後面的下一個前置處理器指示詞。</span><span class="sxs-lookup"><span data-stu-id="3c6e2-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="3c6e2-106">如需如何使用 `#else` 的範例，請參閱 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)。</span><span class="sxs-lookup"><span data-stu-id="3c6e2-106">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c6e2-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c6e2-107">See Also</span></span>  
 [<span data-ttu-id="3c6e2-108">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3c6e2-108">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3c6e2-109">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3c6e2-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3c6e2-110">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="3c6e2-110">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
