---
title: 指示詞
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: b5fcf3cb8801bc99dd2096c28cc41ebefeb34592
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409994"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="b4892-102">指示詞 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4892-102">Directives (Visual Basic)</span></span>

<span data-ttu-id="b4892-103">本節中的主題記錄 Visual Basic 原始程式碼編譯器指示詞。</span><span class="sxs-lookup"><span data-stu-id="b4892-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4892-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="b4892-104">In This Section</span></span>  

 <span data-ttu-id="b4892-105">[#Const](const-directive.md)指示詞--定義編譯器常數</span><span class="sxs-lookup"><span data-stu-id="b4892-105">[#Const Directive](const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="b4892-106">[#ExternalSource](externalsource-directive.md)指示詞--表示來源行與來源外部文字之間的對應</span><span class="sxs-lookup"><span data-stu-id="b4892-106">[#ExternalSource Directive](externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="b4892-107">[#If .。。Then ... #Else](if-then-else-directives.md)指示詞--編譯選取的程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="b4892-107">[#If...Then...#Else Directives](if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="b4892-108">[#Region](region-directive.md)指示詞--在 Visual Studio 編輯器中折迭和隱藏程式碼區段</span><span class="sxs-lookup"><span data-stu-id="b4892-108">[#Region Directive](region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="b4892-109">**#Disable，#Enable** --停用和啟用程式碼區域的特定警告。</span><span class="sxs-lookup"><span data-stu-id="b4892-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="b4892-110">您也可以停用和啟用警告程式碼的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="b4892-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b4892-111">相關章節</span><span class="sxs-lookup"><span data-stu-id="b4892-111">Related Sections</span></span>  

 [<span data-ttu-id="b4892-112">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="b4892-112">Visual Basic Language Reference</span></span>](../index.md)  
  