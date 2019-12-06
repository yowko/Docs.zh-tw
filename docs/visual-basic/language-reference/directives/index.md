---
title: 指示詞
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: b5e857198351b30c0d7a38dce1a9e6d1209b5258
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838139"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="c8cdc-102">指示詞 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cdc-102">Directives (Visual Basic)</span></span>

<span data-ttu-id="c8cdc-103">本節中的主題記錄 Visual Basic 原始程式碼編譯器指示詞。</span><span class="sxs-lookup"><span data-stu-id="c8cdc-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8cdc-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="c8cdc-104">In This Section</span></span>  

 <span data-ttu-id="c8cdc-105">[#Const](../../../visual-basic/language-reference/directives/const-directive.md)指示詞--定義編譯器常數</span><span class="sxs-lookup"><span data-stu-id="c8cdc-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="c8cdc-106">[#ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md)指示詞--表示來源行與來源外部文字之間的對應</span><span class="sxs-lookup"><span data-stu-id="c8cdc-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="c8cdc-107">[#If .。。Then ... #Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)指示詞--編譯選取的程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="c8cdc-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="c8cdc-108">[#Region](../../../visual-basic/language-reference/directives/region-directive.md)指示詞--在 Visual Studio 編輯器中折迭和隱藏程式碼區段</span><span class="sxs-lookup"><span data-stu-id="c8cdc-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="c8cdc-109">**#Disable，#Enable** --停用和啟用程式碼區域的特定警告。</span><span class="sxs-lookup"><span data-stu-id="c8cdc-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="c8cdc-110">您也可以停用和啟用警告程式碼的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="c8cdc-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c8cdc-111">相關章節</span><span class="sxs-lookup"><span data-stu-id="c8cdc-111">Related Sections</span></span>  

 [<span data-ttu-id="c8cdc-112">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="c8cdc-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  