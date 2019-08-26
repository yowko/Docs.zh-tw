---
title: '#endif - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 74205c836b4eeb2d8b17b907bb13708f3225df08
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608576"
---
# <a name="endif-c-reference"></a><span data-ttu-id="419e1-102">#endif (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="419e1-102">#endif (C# Reference)</span></span>
<span data-ttu-id="419e1-103">`#endif` 指定條件指示詞的結尾，而其開始於 [#if](./preprocessor-if.md) 指示詞。</span><span class="sxs-lookup"><span data-stu-id="419e1-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="419e1-104">例如，套用至物件的</span><span class="sxs-lookup"><span data-stu-id="419e1-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="419e1-105">備註</span><span class="sxs-lookup"><span data-stu-id="419e1-105">Remarks</span></span>  
 <span data-ttu-id="419e1-106">以 `#if` 指示詞開頭的條件指示詞必須明確地以 `#endif` 指示詞終止。</span><span class="sxs-lookup"><span data-stu-id="419e1-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="419e1-107">如需如何使用 `#endif` 的範例，請參閱 [#if](./preprocessor-if.md)。</span><span class="sxs-lookup"><span data-stu-id="419e1-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="419e1-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="419e1-108">See also</span></span>

- [<span data-ttu-id="419e1-109">C# 參考</span><span class="sxs-lookup"><span data-stu-id="419e1-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="419e1-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="419e1-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="419e1-111">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="419e1-111">C# Preprocessor Directives</span></span>](./index.md)
