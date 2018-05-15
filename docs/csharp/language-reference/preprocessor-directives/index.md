---
title: C# 前置處理器指示詞
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: 63a7bdb6d36794e0380ca84443926338fe926e4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="7b664-102">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="7b664-102">C# preprocessor directives</span></span>
<span data-ttu-id="7b664-103">本節包含下列 C# 前置處理器指示詞的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="7b664-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="7b664-104">#if</span><span class="sxs-lookup"><span data-stu-id="7b664-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
- [<span data-ttu-id="7b664-105">#else</span><span class="sxs-lookup"><span data-stu-id="7b664-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)
- [<span data-ttu-id="7b664-106">#elif</span><span class="sxs-lookup"><span data-stu-id="7b664-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)
- [<span data-ttu-id="7b664-107">#endif</span><span class="sxs-lookup"><span data-stu-id="7b664-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)
- [<span data-ttu-id="7b664-108">#define</span><span class="sxs-lookup"><span data-stu-id="7b664-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)
- [<span data-ttu-id="7b664-109">#undef</span><span class="sxs-lookup"><span data-stu-id="7b664-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="7b664-110">#warning</span><span class="sxs-lookup"><span data-stu-id="7b664-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)
- [<span data-ttu-id="7b664-111">#error</span><span class="sxs-lookup"><span data-stu-id="7b664-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)
- [<span data-ttu-id="7b664-112">#line</span><span class="sxs-lookup"><span data-stu-id="7b664-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)
- [<span data-ttu-id="7b664-113">#region</span><span class="sxs-lookup"><span data-stu-id="7b664-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)
- [<span data-ttu-id="7b664-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="7b664-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)
- [<span data-ttu-id="7b664-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="7b664-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)
- [<span data-ttu-id="7b664-116">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="7b664-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="7b664-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="7b664-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

<span data-ttu-id="7b664-118">如需詳細資訊和範例，請參閱個別主題。</span><span class="sxs-lookup"><span data-stu-id="7b664-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="7b664-119">雖然編譯器沒有另外的前置處理器，但處理本節中所述的指示詞時，會像是有前置處理器一樣。</span><span class="sxs-lookup"><span data-stu-id="7b664-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="7b664-120">這些指示詞可用於協助條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="7b664-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="7b664-121">不同於 C 和 C++ 指示詞，您無法使用這些指示詞來建立巨集。</span><span class="sxs-lookup"><span data-stu-id="7b664-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="7b664-122">每個前置處理器指示詞都必須是該行中的唯一指令。</span><span class="sxs-lookup"><span data-stu-id="7b664-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b664-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b664-123">See also</span></span>
 [<span data-ttu-id="7b664-124">C# 參考</span><span class="sxs-lookup"><span data-stu-id="7b664-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7b664-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7b664-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
