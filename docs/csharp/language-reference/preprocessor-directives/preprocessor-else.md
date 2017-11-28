---
title: "#<a name=\"else-c-reference\"></a>else (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#else'
helpviewer_keywords: '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c3468d35a6e45c06f46fe8671708ce01a3cc7b65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="else-c-reference"></a><span data-ttu-id="92201-102">#else (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="92201-102">#else (C# Reference)</span></span>
<span data-ttu-id="92201-103">`#else` 可讓您建立複合條件指示詞，如此，如果前面的 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 或 (選擇性) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) 指示詞中沒有運算式為 `true`，則編譯器會評估 `#else` 與後續 `#endif` 之間的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="92201-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or (optional) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) directives to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92201-104">備註</span><span class="sxs-lookup"><span data-stu-id="92201-104">Remarks</span></span>  
 <span data-ttu-id="92201-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) 必須是 `#else` 後面的下一個前置處理器指示詞。</span><span class="sxs-lookup"><span data-stu-id="92201-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="92201-106">如需如何使用 `#else` 的範例，請參閱 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)。</span><span class="sxs-lookup"><span data-stu-id="92201-106">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92201-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92201-107">See Also</span></span>  
 [<span data-ttu-id="92201-108">C# 參考</span><span class="sxs-lookup"><span data-stu-id="92201-108">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="92201-109">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="92201-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="92201-110">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="92201-110">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
