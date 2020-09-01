---
description: C# 前置處理器指示詞
title: C# 前置處理器指示詞
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: a7ffca8b39f1bd9f05193bccbb6d90e67fa262c9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132361"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="328aa-103">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="328aa-103">C# preprocessor directives</span></span>
<span data-ttu-id="328aa-104">本節包含下列 C# 前置處理器指示詞的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="328aa-104">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="328aa-105">#if</span><span class="sxs-lookup"><span data-stu-id="328aa-105">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="328aa-106">#else</span><span class="sxs-lookup"><span data-stu-id="328aa-106">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="328aa-107">#elif</span><span class="sxs-lookup"><span data-stu-id="328aa-107">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="328aa-108">#endif</span><span class="sxs-lookup"><span data-stu-id="328aa-108">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="328aa-109">#define</span><span class="sxs-lookup"><span data-stu-id="328aa-109">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="328aa-110">#undef</span><span class="sxs-lookup"><span data-stu-id="328aa-110">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="328aa-111">#warning</span><span class="sxs-lookup"><span data-stu-id="328aa-111">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="328aa-112">#error</span><span class="sxs-lookup"><span data-stu-id="328aa-112">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="328aa-113">#line</span><span class="sxs-lookup"><span data-stu-id="328aa-113">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="328aa-114">#region</span><span class="sxs-lookup"><span data-stu-id="328aa-114">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="328aa-115">#endregion</span><span class="sxs-lookup"><span data-stu-id="328aa-115">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="328aa-116">#pragma</span><span class="sxs-lookup"><span data-stu-id="328aa-116">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="328aa-117">#pragma 警告</span><span class="sxs-lookup"><span data-stu-id="328aa-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="328aa-118">#pragma 總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="328aa-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="328aa-119">如需詳細資訊和範例，請參閱個別主題。</span><span class="sxs-lookup"><span data-stu-id="328aa-119">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="328aa-120">雖然編譯器沒有另外的前置處理器，但處理本節中所述的指示詞時，會像是有前置處理器一樣。</span><span class="sxs-lookup"><span data-stu-id="328aa-120">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="328aa-121">這些指示詞可用於協助條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="328aa-121">They are used to help in conditional compilation.</span></span> <span data-ttu-id="328aa-122">不同於 C 和 C++ 指示詞，您無法使用這些指示詞來建立巨集。</span><span class="sxs-lookup"><span data-stu-id="328aa-122">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="328aa-123">每個前置處理器指示詞都必須是該行中的唯一指令。</span><span class="sxs-lookup"><span data-stu-id="328aa-123">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="328aa-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="328aa-124">See also</span></span>

- [<span data-ttu-id="328aa-125">C # 參考</span><span class="sxs-lookup"><span data-stu-id="328aa-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="328aa-126">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="328aa-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
