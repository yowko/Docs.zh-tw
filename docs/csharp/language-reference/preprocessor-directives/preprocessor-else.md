---
title: '#else - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: 967ef38687b739ef3bea3f8923ab26bba0b6cea9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712555"
---
# <a name="else-c-reference"></a><span data-ttu-id="6e41b-102">#else (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6e41b-102">#else (C# Reference)</span></span>
<span data-ttu-id="6e41b-103">`#else` 可讓您建立複合條件指示詞，如此，如果前面的 [#if](./preprocessor-if.md) 或 (選擇性) [#elif](./preprocessor-elif.md) 指示詞中沒有運算式評估為 `true`，則編譯器會評估 `#else` 與後續 `#endif` 之間的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="6e41b-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e41b-104">備註</span><span class="sxs-lookup"><span data-stu-id="6e41b-104">Remarks</span></span>  
 <span data-ttu-id="6e41b-105">[#endif](./preprocessor-endif.md) 必須是 `#else` 後面的下一個前置處理器指示詞。</span><span class="sxs-lookup"><span data-stu-id="6e41b-105">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="6e41b-106">如需如何使用 `#else` 的範例，請參閱 [#if](./preprocessor-if.md)。</span><span class="sxs-lookup"><span data-stu-id="6e41b-106">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e41b-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e41b-107">See also</span></span>

- [<span data-ttu-id="6e41b-108">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6e41b-108">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6e41b-109">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6e41b-109">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6e41b-110">C# 預處理器指令</span><span class="sxs-lookup"><span data-stu-id="6e41b-110">C# Preprocessor Directives</span></span>](./index.md)
