---
title: "REM Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.'"
  - "vb.Rem"
  - "Rem"
  - "'"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "REM statement"
  - "comments, Visual Basic code"
  - "code comments, Visual Basic"
  - "Visual Basic code, comments"
  - "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# REM Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

用來在程式的原始程式碼中包含闡明註解。  
  
## 語法  
  
```  
REM comment  
' comment  
```  
  
## 組件  
 `comment`  
 選擇項。  可包含任何註解文字。  還有之間需要`REM`關鍵字和`comment`。  
  
## 備註  
 您可以單獨在一行中放置 `REM` 陳述式，或將其放置在另一個陳述式之後。  `REM` 陳述式必須是行中的最後一個陳述式。  若是在另一個陳述式之後，`REM` 就必須以空格來和該陳述式分隔。  
  
 您也可以使用單引號 \(`'`\) 來分隔，而不用 `REM`。  不論註解是與另一陳述式位於同一行中 \(接在該陳述式之後\)，或單獨位於一行，都可使用這種方式。  
  
> [!NOTE]
>  您無法使用行接續 \(Line\-Continuation\) 序列 \(`_`\) 來繼續 `REM` 陳述式。  註解開始後，編譯器並不會檢查字元是否有具特別意義。  如需多行註解，請在每行上使用其他 `REM` 陳述式或註解符號 \(`'`\)。  
  
## 範例  
 下列範例會說明 `REM` 陳述式，此陳述式用於在程式中包含闡明註解。  同時顯示另一種使用單引號字元 \(`'`\) 而不用 `REM` 的方式。  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/rem-statement_1.vb)]  
  
## 請參閱  
 [Comments in Code](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)   
 [如何：在程式碼中中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)