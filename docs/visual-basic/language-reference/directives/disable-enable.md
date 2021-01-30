---
title: Enable 和 Disable 指示詞
ms.date: 01/28/2021
helpviewer_keywords:
- directives, enable
- directives, disable
- disable directive
ms.openlocfilehash: 3104b25c903465f3a650304f477b25a74591c8ba
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217224"
---
# <a name="disable-and-enable-directives-visual-basic"></a><span data-ttu-id="87575-102">#Disable 和 #Enable 指示詞 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="87575-102">#Disable and #Enable directives (Visual Basic)</span></span>

<span data-ttu-id="87575-103">和指示詞 `#Disable` `#Enable` 是 Visual Basic 的原始程式碼編譯器指示詞。</span><span class="sxs-lookup"><span data-stu-id="87575-103">The `#Disable` and `#Enable` directives are Visual Basic source code compiler directives.</span></span> <span data-ttu-id="87575-104">它們可用來停用和重新啟用程式碼區域的特定警告。</span><span class="sxs-lookup"><span data-stu-id="87575-104">They are used to disable and re-enable specific warnings for regions of code.</span></span>

```vb
' Suppress warning about no awaits in this method.
#Disable Warning BC42356
    Async Function TestAsync() As Task
        Console.WriteLine("testing")
    End Function
#Enable Warning BC42356
```

<span data-ttu-id="87575-105">您也可以停用並啟用以逗號分隔的警告代碼清單。</span><span class="sxs-lookup"><span data-stu-id="87575-105">You can also disable and enable a comma-separated list of warning codes.</span></span>

## <a name="see-also"></a><span data-ttu-id="87575-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87575-106">See also</span></span>

- [<span data-ttu-id="87575-107">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="87575-107">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="87575-108">如何隱藏程式碼分析警告</span><span class="sxs-lookup"><span data-stu-id="87575-108">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
