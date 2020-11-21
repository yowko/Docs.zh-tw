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
ms.openlocfilehash: 1269522b2687b76292f7b796a4ffc8095f23442e
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099057"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="8a68f-103">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="8a68f-103">C# preprocessor directives</span></span>

<span data-ttu-id="8a68f-104">本節包含下列 C# 前置處理器指示詞的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="8a68f-104">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="8a68f-105">#if</span><span class="sxs-lookup"><span data-stu-id="8a68f-105">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="8a68f-106">#else</span><span class="sxs-lookup"><span data-stu-id="8a68f-106">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="8a68f-107">#elif</span><span class="sxs-lookup"><span data-stu-id="8a68f-107">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="8a68f-108">#endif</span><span class="sxs-lookup"><span data-stu-id="8a68f-108">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="8a68f-109">#define</span><span class="sxs-lookup"><span data-stu-id="8a68f-109">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="8a68f-110">#undef</span><span class="sxs-lookup"><span data-stu-id="8a68f-110">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="8a68f-111">#warning</span><span class="sxs-lookup"><span data-stu-id="8a68f-111">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="8a68f-112">#error</span><span class="sxs-lookup"><span data-stu-id="8a68f-112">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="8a68f-113">#line</span><span class="sxs-lookup"><span data-stu-id="8a68f-113">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="8a68f-114">#nullable</span><span class="sxs-lookup"><span data-stu-id="8a68f-114">#nullable</span></span>](./preprocessor-nullable.md)
- [<span data-ttu-id="8a68f-115">#region</span><span class="sxs-lookup"><span data-stu-id="8a68f-115">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="8a68f-116">#endregion</span><span class="sxs-lookup"><span data-stu-id="8a68f-116">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="8a68f-117">#pragma</span><span class="sxs-lookup"><span data-stu-id="8a68f-117">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="8a68f-118">#pragma 警告</span><span class="sxs-lookup"><span data-stu-id="8a68f-118">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="8a68f-119">#pragma 總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="8a68f-119">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="8a68f-120">如需詳細資訊和範例，請參閱個別主題。</span><span class="sxs-lookup"><span data-stu-id="8a68f-120">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="8a68f-121">雖然編譯器沒有另外的前置處理器，但處理本節中所述的指示詞時，會像是有前置處理器一樣。</span><span class="sxs-lookup"><span data-stu-id="8a68f-121">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="8a68f-122">這些指示詞可用於協助條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="8a68f-122">They are used to help in conditional compilation.</span></span> <span data-ttu-id="8a68f-123">不同於 C 和 C++ 指示詞，您無法使用這些指示詞來建立巨集。</span><span class="sxs-lookup"><span data-stu-id="8a68f-123">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="8a68f-124">每個前置處理器指示詞都必須是該行中的唯一指令。</span><span class="sxs-lookup"><span data-stu-id="8a68f-124">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a68f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a68f-125">See also</span></span>

- [<span data-ttu-id="8a68f-126">C # 參考</span><span class="sxs-lookup"><span data-stu-id="8a68f-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8a68f-127">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8a68f-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
