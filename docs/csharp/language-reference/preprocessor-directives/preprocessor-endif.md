---
title: '#endif (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: a652c1226f8f0c624ec8ebf0e665a4aa77ddf6f0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43420810"
---
# <a name="endif-c-reference"></a><span data-ttu-id="cb6b9-102">#endif (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="cb6b9-102">#endif (C# Reference)</span></span>
<span data-ttu-id="cb6b9-103">`#endif` 指定條件指示詞的結尾，而其開始於 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 指示詞。</span><span class="sxs-lookup"><span data-stu-id="cb6b9-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="cb6b9-104">例如，套用至物件的</span><span class="sxs-lookup"><span data-stu-id="cb6b9-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="cb6b9-105">備註</span><span class="sxs-lookup"><span data-stu-id="cb6b9-105">Remarks</span></span>  
 <span data-ttu-id="cb6b9-106">以 `#if` 指示詞開頭的條件指示詞必須明確地以 `#endif` 指示詞終止。</span><span class="sxs-lookup"><span data-stu-id="cb6b9-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="cb6b9-107">如需如何使用 `#endif` 的範例，請參閱 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)。</span><span class="sxs-lookup"><span data-stu-id="cb6b9-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb6b9-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="cb6b9-108">See Also</span></span>

- [<span data-ttu-id="cb6b9-109">C# 參考</span><span class="sxs-lookup"><span data-stu-id="cb6b9-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="cb6b9-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cb6b9-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="cb6b9-111">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="cb6b9-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
