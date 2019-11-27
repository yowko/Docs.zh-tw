---
title: 指示詞
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: d76e10ad5ce8ad3accdc84f97146e0816048d8f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343810"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="86d78-102">指示詞 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86d78-102">Directives (Visual Basic)</span></span>

<span data-ttu-id="86d78-103">本節中的主題記錄 Visual Basic 原始程式碼編譯器指示詞。</span><span class="sxs-lookup"><span data-stu-id="86d78-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86d78-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="86d78-104">In This Section</span></span>  

 <span data-ttu-id="86d78-105">[#Const](../../../visual-basic/language-reference/directives/const-directive.md)指示詞--定義編譯器常數</span><span class="sxs-lookup"><span data-stu-id="86d78-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="86d78-106">[#ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md)指示詞--表示來源行與來源外部文字之間的對應</span><span class="sxs-lookup"><span data-stu-id="86d78-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="86d78-107">[#If .。。Then ... #Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)指示詞--編譯選取的程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="86d78-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="86d78-108">[#Region](../../../visual-basic/language-reference/directives/region-directive.md)指示詞--在 Visual Studio 編輯器中折迭和隱藏程式碼區段</span><span class="sxs-lookup"><span data-stu-id="86d78-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="86d78-109">**#Disable，#Enable** --停用和啟用程式碼區域的特定警告。</span><span class="sxs-lookup"><span data-stu-id="86d78-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="86d78-110">您也可以停用和啟用警告程式碼的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="86d78-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="86d78-111">相關章節</span><span class="sxs-lookup"><span data-stu-id="86d78-111">Related Sections</span></span>  

 [<span data-ttu-id="86d78-112">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="86d78-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="86d78-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86d78-113">Visual Basic</span></span>](../../../visual-basic/index.md)
