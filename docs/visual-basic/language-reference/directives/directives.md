---
title: 指示詞 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="directives-visual-basic"></a>指示詞 (Visual Basic)
本節中的主題記錄 Visual Basic 原始程式碼編譯器指示詞。  
  
## <a name="in-this-section"></a>本節內容  
 [#Const 指示詞](../../../visual-basic/language-reference/directives/const-directive.md)-定義編譯器常數  
  
 [#ExternalSource 指示詞](../../../visual-basic/language-reference/directives/externalsource-directive.md)-指出原始程式行和來源外部文字之間的對應  
  
 [#If......#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)-編譯選取的程式碼區塊  
  
 [#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md)--摺疊和隱藏在 Visual Studio 編輯器中的程式碼區段  
  
 **#Disable、 #Enable** --停用和啟用程式碼區域的特定警告。  
  
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
