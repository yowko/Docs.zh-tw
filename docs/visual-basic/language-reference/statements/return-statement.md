---
title: "Return Statement (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Return"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Return statement, syntax"
  - "control flow, returning control to expressions"
  - "Return statement"
  - "expressions [Visual Basic], returning control to"
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Return Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

將控制傳回至呼叫 `Function`、`Sub`、`Get`、`Set` 或 `Operator` 程序的程式碼。  
  
## 語法  
  
```  
Return  
-or-  
Return expression  
```  
  
## 組件  
 `expression`  
 在 `Function`、`Get` 或 `Operator` 程序中為必要項。  運算式，表示傳回給呼叫程式碼的值。  
  
## 備註  
 在 `Sub` 或 `Set` 程序中，`Return` 陳述式相當於 `Exit Sub` 或 `Exit Property` 陳述式，而且不得提供 `expression`。  
  
 在 `Function`、`Get` 或 `Operator` 程序中，`Return` 陳述式必須包含 `expression`，而且 `expression` 必須評估為可轉換成程序之傳回型別的資料型別。  在 `Function` 或 `Get` 程序中還會有其他的替代方案，也就是將運算式指派給程序名稱做為傳回值，再執行 `Exit Function` 或 `Exit Property` 陳述式。  在 `Operator` 程序中，您必須使用 `Return` `expression`。  
  
 您可以在同一個程序中視需要納入多個 `Return` 陳述式。  
  
> [!NOTE]
>  在 `Try` 或 `Catch` 區塊中出現 `Return` 陳述式之後，且在執行此 `Return` 陳述式之前，會執行 `Finally` 區塊的程式碼。  A `Return`陳述式不能包含在`Finally`區塊。  
  
## 範例  
 當程序不必執行其他工作時，下列範例會多次使用 `Return` 陳述式以返回至呼叫程式碼。  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## 請參閱  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)   
 [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)   
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)