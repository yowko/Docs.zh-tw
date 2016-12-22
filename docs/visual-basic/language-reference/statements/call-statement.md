---
title: "Call Statement (Visual Basic) | Microsoft Docs"
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
  - "vb.Call"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedures, Call statement"
  - "Call statement"
  - "procedures, calling"
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Call Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

將控制項轉換至 `Function`、`Sub` 或動態連結程式庫 \(DLL\) 程序。  
  
## 語法  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## 組件  
 `procedureName`  
 必要項。  要呼叫的程序名稱。  
  
 `argumentList`  
 選擇項。  變數或運算式的清單，表示在呼叫程序時傳遞至程序中的引數。  以逗號 \( , \) 分隔多個引數。  如果包含 `argumentList`，則必須以括號括住它。  
  
## 備註  
 您可以使用`Call`關鍵字，當您呼叫程序。  大部分的程序呼叫，便不需要使用這個關鍵字。  
  
 您通常會使用`Call`關鍵字的識別項無法啟動的被呼叫的運算式時。  使用非`Call`建議您不要為其他用途的關鍵字。  
  
 如果程序傳回值，`Call` 陳述式便會捨棄它。  
  
## 範例  
 下列程式碼會顯示兩個範例， `Call`關鍵字是為了呼叫程序。  在這兩個範例中，被呼叫的運算式並不會啟動的識別項。  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## 請參閱  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)