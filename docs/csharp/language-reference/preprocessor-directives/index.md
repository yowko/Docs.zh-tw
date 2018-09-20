---
title: C# 前置處理器指示詞
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: 1c0a97cabce347be0bc9367f3d090a1fc699db19
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46480447"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="db118-102">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="db118-102">C# preprocessor directives</span></span>
<span data-ttu-id="db118-103">本節包含下列 C# 前置處理器指示詞的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="db118-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="db118-104">#if</span><span class="sxs-lookup"><span data-stu-id="db118-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
- [<span data-ttu-id="db118-105">#else</span><span class="sxs-lookup"><span data-stu-id="db118-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)
- [<span data-ttu-id="db118-106">#elif</span><span class="sxs-lookup"><span data-stu-id="db118-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)
- [<span data-ttu-id="db118-107">#endif</span><span class="sxs-lookup"><span data-stu-id="db118-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)
- [<span data-ttu-id="db118-108">#define</span><span class="sxs-lookup"><span data-stu-id="db118-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)
- [<span data-ttu-id="db118-109">#undef</span><span class="sxs-lookup"><span data-stu-id="db118-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="db118-110">#warning</span><span class="sxs-lookup"><span data-stu-id="db118-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)
- [<span data-ttu-id="db118-111">#error</span><span class="sxs-lookup"><span data-stu-id="db118-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)
- [<span data-ttu-id="db118-112">#line</span><span class="sxs-lookup"><span data-stu-id="db118-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)
- [<span data-ttu-id="db118-113">#region</span><span class="sxs-lookup"><span data-stu-id="db118-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)
- [<span data-ttu-id="db118-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="db118-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)
- [<span data-ttu-id="db118-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="db118-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)
- [<span data-ttu-id="db118-116">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="db118-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="db118-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="db118-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

<span data-ttu-id="db118-118">如需詳細資訊和範例，請參閱個別主題。</span><span class="sxs-lookup"><span data-stu-id="db118-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="db118-119">雖然編譯器沒有另外的前置處理器，但處理本節中所述的指示詞時，會像是有前置處理器一樣。</span><span class="sxs-lookup"><span data-stu-id="db118-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="db118-120">這些指示詞可用於協助條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="db118-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="db118-121">不同於 C 和 C++ 指示詞，您無法使用這些指示詞來建立巨集。</span><span class="sxs-lookup"><span data-stu-id="db118-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="db118-122">每個前置處理器指示詞都必須是該行中的唯一指令。</span><span class="sxs-lookup"><span data-stu-id="db118-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="db118-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db118-123">See also</span></span>

- [<span data-ttu-id="db118-124">C# 參考</span><span class="sxs-lookup"><span data-stu-id="db118-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="db118-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="db118-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
