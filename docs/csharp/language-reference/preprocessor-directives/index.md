---
title: "C# 前置處理器指示詞"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.preprocessor
dev_langs:
- CSharp
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 91bb2daefbc677fad8a3dd93b37aac996234d48c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="75e06-102">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="75e06-102">C# Preprocessor Directives</span></span>
<span data-ttu-id="75e06-103">本節包含下列 C# 前置處理器指示詞的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="75e06-103">This section contains information about the following C# preprocessor directives.</span></span>  
  
 [<span data-ttu-id="75e06-104">#if</span><span class="sxs-lookup"><span data-stu-id="75e06-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)  
  
 [<span data-ttu-id="75e06-105">#else</span><span class="sxs-lookup"><span data-stu-id="75e06-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)  
  
 [<span data-ttu-id="75e06-106">#elif</span><span class="sxs-lookup"><span data-stu-id="75e06-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)  
  
 [<span data-ttu-id="75e06-107">#endif</span><span class="sxs-lookup"><span data-stu-id="75e06-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)  
  
 [<span data-ttu-id="75e06-108">#define</span><span class="sxs-lookup"><span data-stu-id="75e06-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)  
  
 [<span data-ttu-id="75e06-109">#undef</span><span class="sxs-lookup"><span data-stu-id="75e06-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
  
 [<span data-ttu-id="75e06-110">#warning</span><span class="sxs-lookup"><span data-stu-id="75e06-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)  
  
 [<span data-ttu-id="75e06-111">#error</span><span class="sxs-lookup"><span data-stu-id="75e06-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)  
  
 [<span data-ttu-id="75e06-112">#line</span><span class="sxs-lookup"><span data-stu-id="75e06-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)  
  
 [<span data-ttu-id="75e06-113">#region</span><span class="sxs-lookup"><span data-stu-id="75e06-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)  
  
 [<span data-ttu-id="75e06-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="75e06-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)  
  
 [<span data-ttu-id="75e06-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="75e06-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)  
  
 [<span data-ttu-id="75e06-116">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="75e06-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="75e06-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="75e06-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
 <span data-ttu-id="75e06-118">如需詳細資訊和範例，請參閱個別主題。</span><span class="sxs-lookup"><span data-stu-id="75e06-118">See the individual topics for more information and examples.</span></span>  
  
 <span data-ttu-id="75e06-119">雖然編譯器沒有個別的前置處理器，但處理本節中所述的指示詞時會像是有一個前置處理器一樣。</span><span class="sxs-lookup"><span data-stu-id="75e06-119">Although the compiler does not have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="75e06-120">這些指示詞可用於協助條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="75e06-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="75e06-121">不同於 C 和 C++ 指示詞，您無法使用這些指示詞來建立巨集。</span><span class="sxs-lookup"><span data-stu-id="75e06-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>  
  
 <span data-ttu-id="75e06-122">每個前置處理器指示詞都必須是該行中的唯一指令。</span><span class="sxs-lookup"><span data-stu-id="75e06-122">A preprocessor directive must be the only instruction on a line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75e06-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75e06-123">See Also</span></span>  
 <span data-ttu-id="75e06-124">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="75e06-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 [<span data-ttu-id="75e06-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="75e06-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

