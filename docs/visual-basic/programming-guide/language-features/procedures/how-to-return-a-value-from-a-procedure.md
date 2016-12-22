---
title: "How to: Return a Value from a Procedure (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, procedures"
  - "procedures, returning from"
  - "procedures, returning a value"
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Return a Value from a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`Function` 程序透過執行  `Return` 陳述式或遇到 `Exit Function` 或 `End Function` 陳述式，即會傳回值給呼叫程式碼。  
  
### 若要使用 Return 陳述式傳回值  
  
1.  將 `Return` 陳述式放在已完成程序工作的點。  
  
2.  在 `Return` 關鍵字後面緊接的運算式可產生想要傳回給呼叫程式碼的值。  
  
3.  在相同程序中可有一個以上的 `Return` 陳述式。  
  
     下列 `Function` 程序會計算直角三角形的最長邊 \(也稱為斜邊\)，並將它傳回給呼叫程式碼。  
  
     [!CODE [VbVbcnProcedures#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#1)]  
  
     下列範例示範 `hypotenuse` 的典型呼叫，其可儲存傳回的值。  
  
     [!CODE [VbVbcnProcedures#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#6)]  
  
### 若要使用 Exit Function 或 End Function 傳回值  
  
1.  至少在 `Function` 程序的一個位置中，將值指派給程序的名稱。  
  
2.  當您執行 `Exit Function` 或 `End Function` 陳述式時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會傳回最近指派給程序名稱的值。  
  
3.  在相同程序中可有一個以上的 `Exit Function` 陳述式，且可在相同程序中混合 `Return` 和 `Exit Function` 陳述式。  
  
4.  在 `Function` 程序中只可有一個 `End Function` 陳述式。  
  
     如需詳細資訊和範例，請參閱 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) 中「傳回值」的部分。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md)   
 [How to: Create a Procedure that Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure-that-returns-a-value.md)   
 [How to: Call a Procedure That Returns a Value](../Topic/How%20to:%20Call%20a%20Procedure%20That%20Returns%20a%20Value%20\(Visual%20Basic\).md)