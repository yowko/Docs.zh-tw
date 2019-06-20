---
title: 指示詞 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268202"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="c6d0e-102">指示詞 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6d0e-102">Directives (Visual Basic)</span></span>
<span data-ttu-id="c6d0e-103">本節中的主題記錄 Visual Basic 原始程式碼編譯器指示詞。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6d0e-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="c6d0e-104">In This Section</span></span>  
 <span data-ttu-id="c6d0e-105">[#Const 指示詞](../../../visual-basic/language-reference/directives/const-directive.md)-定義編譯器常數</span><span class="sxs-lookup"><span data-stu-id="c6d0e-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="c6d0e-106">[#ExternalSource 指示詞](../../../visual-basic/language-reference/directives/externalsource-directive.md)-表示原始程式行和來源外部文字之間的對應</span><span class="sxs-lookup"><span data-stu-id="c6d0e-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="c6d0e-107">[#If......#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)-編譯選取的程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="c6d0e-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="c6d0e-108">[#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md)--摺疊和隱藏的 Visual Studio 編輯器中的程式碼區段</span><span class="sxs-lookup"><span data-stu-id="c6d0e-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="c6d0e-109">**#Disable、 #Enable** --停用和啟用程式碼區域的特定警告。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="c6d0e-110">您也可以停用和啟用警告程式碼的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c6d0e-111">相關章節</span><span class="sxs-lookup"><span data-stu-id="c6d0e-111">Related Sections</span></span>  
 [<span data-ttu-id="c6d0e-112">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="c6d0e-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="c6d0e-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6d0e-113">Visual Basic</span></span>](../../../visual-basic/index.md)
