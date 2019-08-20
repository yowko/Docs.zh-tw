---
title: C# 前置處理器指示詞
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: f63ba3e0bd89a88ad04b14c2f359a8cde65e8f12
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608594"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="505de-102">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="505de-102">C# preprocessor directives</span></span>
<span data-ttu-id="505de-103">本節包含下列 C# 前置處理器指示詞的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="505de-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="505de-104">#if</span><span class="sxs-lookup"><span data-stu-id="505de-104">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="505de-105">#else</span><span class="sxs-lookup"><span data-stu-id="505de-105">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="505de-106">#elif</span><span class="sxs-lookup"><span data-stu-id="505de-106">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="505de-107">#endif</span><span class="sxs-lookup"><span data-stu-id="505de-107">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="505de-108">#define</span><span class="sxs-lookup"><span data-stu-id="505de-108">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="505de-109">#undef</span><span class="sxs-lookup"><span data-stu-id="505de-109">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="505de-110">#warning</span><span class="sxs-lookup"><span data-stu-id="505de-110">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="505de-111">#error</span><span class="sxs-lookup"><span data-stu-id="505de-111">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="505de-112">#line</span><span class="sxs-lookup"><span data-stu-id="505de-112">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="505de-113">#region</span><span class="sxs-lookup"><span data-stu-id="505de-113">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="505de-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="505de-114">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="505de-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="505de-115">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="505de-116">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="505de-116">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="505de-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="505de-117">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="505de-118">如需詳細資訊和範例，請參閱個別主題。</span><span class="sxs-lookup"><span data-stu-id="505de-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="505de-119">雖然編譯器沒有另外的前置處理器，但處理本節中所述的指示詞時，會像是有前置處理器一樣。</span><span class="sxs-lookup"><span data-stu-id="505de-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="505de-120">這些指示詞可用於協助條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="505de-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="505de-121">不同於 C 和 C++ 指示詞，您無法使用這些指示詞來建立巨集。</span><span class="sxs-lookup"><span data-stu-id="505de-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="505de-122">每個前置處理器指示詞都必須是該行中的唯一指令。</span><span class="sxs-lookup"><span data-stu-id="505de-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="505de-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="505de-123">See also</span></span>

- [<span data-ttu-id="505de-124">C# 參考</span><span class="sxs-lookup"><span data-stu-id="505de-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="505de-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="505de-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
