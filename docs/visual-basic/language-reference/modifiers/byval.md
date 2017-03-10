---
title: "ByVal (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ByVal"
  - "ByVal"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ByVal keyword, contexts"
  - "ByVal keyword"
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# ByVal (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定一種傳遞引數的方式，如果使用這種方式，呼叫的程序或屬性 \(Property\) 便無法變更呼叫程式碼中引數所含的變數值。  
  
## 備註  
 `ByVal` 修飾詞可用於以下內容中：  
  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 範例  
 下列範例示範如何使用 `ByVal` 參數傳遞機制以及參考型別引數。  在範例中，引數 `c1` 是 `Class1` 類別的執行個體。  `ByVal` 可避免程序中的程式碼變更參考引數 `c1` 的基礎值，但無法保護 `c1` 的可存取欄位和屬性。  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/visualbasic/byval_1.vb)]  
  
## 請參閱  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)   
 [Passing Arguments by Value and by Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)