---
title: "指示詞 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8219f17f1b8093b4d02b370c7b008101923b1873
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="directives-visual-basic"></a>指示詞 (Visual Basic)
本節中的主題記錄 Visual Basic 原始程式碼編譯器指示詞。  
  
## <a name="in-this-section"></a>本章節內容  
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
