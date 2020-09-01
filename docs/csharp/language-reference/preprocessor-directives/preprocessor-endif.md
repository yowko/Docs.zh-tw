---
description: '#endif - C# 參考'
title: '#endif - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 8068a6e437145178fd5c88763c86692a8700c349
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138159"
---
# <a name="endif-c-reference"></a><span data-ttu-id="2543f-103">#endif (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2543f-103">#endif (C# Reference)</span></span>
<span data-ttu-id="2543f-104">`#endif` 指定條件指示詞的結尾，而其開始於 [#if](./preprocessor-if.md) 指示詞。</span><span class="sxs-lookup"><span data-stu-id="2543f-104">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="2543f-105">例如，</span><span class="sxs-lookup"><span data-stu-id="2543f-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="2543f-106">備註</span><span class="sxs-lookup"><span data-stu-id="2543f-106">Remarks</span></span>  
 <span data-ttu-id="2543f-107">以 `#if` 指示詞開頭的條件指示詞必須明確地以 `#endif` 指示詞終止。</span><span class="sxs-lookup"><span data-stu-id="2543f-107">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="2543f-108">如需如何使用 `#endif` 的範例，請參閱 [#if](./preprocessor-if.md)。</span><span class="sxs-lookup"><span data-stu-id="2543f-108">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2543f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2543f-109">See also</span></span>

- [<span data-ttu-id="2543f-110">C # 參考</span><span class="sxs-lookup"><span data-stu-id="2543f-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2543f-111">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2543f-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2543f-112">C # 預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="2543f-112">C# Preprocessor Directives</span></span>](./index.md)
