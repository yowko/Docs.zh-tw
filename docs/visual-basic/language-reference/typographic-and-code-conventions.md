---
title: "Typographic and Code Conventions (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "coding conventions, Visual Basic"
  - "best practices, coding conventions"
  - "conventions, Visual Basic coding"
  - "typographic conventions"
  - "document conventions"
  - "conventions, documentation"
  - "Visual Basic code, conventions"
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Typographic and Code Conventions (Visual Basic)
[!INCLUDE[vs2017banner](../../visual-basic/includes/vs2017banner.md)]

Visual Basic 文件使用下列的印刷樣式與程式碼慣例。  
  
## 印刷樣式慣例  
  
|範例|描述|  
|--------|--------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|如範例所示，語言特有的關鍵字和執行階段成員都有第一個字母大寫並已格式化。|  
|SmallProject, ButtonCollection|如範例所示，要求您輸入的單字和片語已格式化。|  
|[Module Statement](../../visual-basic/language-reference/statements/module-statement.md)|如範例所示，您可以按一下以移至其他說明頁的連結已格式化。|  
|*object*, *variableName*, `argumentList`|如範例所示，您提供資訊的預留位置已格式化。|  
|\[ Shadows \], \[ *expressionList* \]|在語法中，選擇性項目是放在方括號內。|  
|{ `Public` &#124; `Friend` &#124; `Private` }|在語法中，當您必須在兩個以上的項目做選擇時，這些項目是放在大括號內，並以分隔號分隔。<br /><br /> 您只能選取其中一個項目。|  
|\[ `Protected` &#124; `Friend` \]|在語法中，當您可以選取兩個以上的項目時，這些項目是放在方括號內，並以分隔號分隔。<br /><br /> 您可以選取這些項目中的任何組合，或不選擇任何項目。|  
|\[{ `ByVal` &#124; `ByRef` }\]|在語法中，當您只能選取一個項目，但也可以完全忽略這些項目時，這些項目會放在方括號內，前後圍繞著大括號並以分隔號分隔。|  
|*memberName* 1、*memberName*2、*memberName*3|如範例所示，註標 \(Subscript\) 會區分相同預留位置的多個執行個體。|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|在語法中，省略號 \(...\) 是用來表示省略號之前還有很多個該種類的項目。<br /><br /> 在程式碼中，為能清楚表示，省略號代表省略的程式碼。|  
|ESC、ENTER|鍵盤上的按鍵名稱和按鍵組合以全字大寫顯示。|  
|ALT\+F1|當按鍵名稱之間出現加號 \(\+\) 時，您必須按住一個按鍵，同時按下其他按鍵。  例如，ALT\+F1 表示按住 ALT 鍵的同時，按下 F1 鍵。|  
  
## 程式碼慣例  
  
|範例|描述|  
|--------|--------|  
|`sampleString = "Hello, world!"`|如範例所示，程式碼範例以固定字幅 \(Fixed\-Pitch\) 的字型顯示並已格式化。|  
|上述陳述式會將 `sampleString` 的值設定為 "Hello, world\!"。|如範例所示，說明文字中的程式碼項目以固定字幅的字型顯示。|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|所有格符號 \('\) 或 REM 關鍵字後方可加入程式碼註解。|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|在程式碼行尾空格後加上底線 \( \_\) 表示陳述式延續到下一行。|  
  
## 請參閱  
 [Visual Basic Language Reference](../../visual-basic/language-reference/index.md)   
 [關鍵字](../../visual-basic/language-reference/keywords/index.md)   
 [Visual Basic Runtime Library Members](../../visual-basic/language-reference/runtime-library-members.md)   
 [Visual Basic Naming Conventions](../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [如何：在程式碼中中斷和合併陳述式](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)   
 [Comments in Code](../../visual-basic/programming-guide/program-structure/comments-in-code.md)