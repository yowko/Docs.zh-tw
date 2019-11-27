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
# <a name="directives-visual-basic"></a>指示詞 (Visual Basic)

本節中的主題記錄 Visual Basic 原始程式碼編譯器指示詞。  
  
## <a name="in-this-section"></a>本節內容  

 [#Const](../../../visual-basic/language-reference/directives/const-directive.md)指示詞--定義編譯器常數  
  
 [#ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md)指示詞--表示來源行與來源外部文字之間的對應  
  
 [#If .。。Then ... #Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)指示詞--編譯選取的程式碼區塊  
  
 [#Region](../../../visual-basic/language-reference/directives/region-directive.md)指示詞--在 Visual Studio 編輯器中折迭和隱藏程式碼區段  
  
 **#Disable，#Enable** --停用和啟用程式碼區域的特定警告。  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 您也可以停用和啟用警告程式碼的逗號分隔清單。  
  
## <a name="related-sections"></a>相關章節  

 [Visual Basic 語言參考](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)
