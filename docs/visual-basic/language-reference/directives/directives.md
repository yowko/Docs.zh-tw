---
title: "Directives (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "directives, Visual Basic compiler"
  - "Visual Basic code, directives"
  - "directives"
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Directives (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

本節中的主題記錄 Visual Basic 原始程式碼編譯器指示詞。  
  
## 在本節中  
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) \-\- 定義編譯器常數  
  
 [\#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) \-\- 指出原始程式行和來源外部文字之間的對應  
  
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) \-\- 編譯選取的程式碼區塊  
  
 [\#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) \-\- 在 Visual Studio 編輯器中摺疊和隱藏程式碼區段  
  
 **\#Disable, \#Enable** \-\- 停用和啟用程式碼區域的特定警告。  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
  
```  
  
 您也可以停用和啟用警告程式碼的逗號分隔清單。  
  
## 相關章節  
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)