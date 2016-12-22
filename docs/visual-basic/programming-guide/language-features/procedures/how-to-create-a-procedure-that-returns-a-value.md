---
title: "How to: Create a Procedure that Returns a Value (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "procedures, returning a value"
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create a Procedure that Returns a Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

使用 `Function` 程序，將值傳回給呼叫程式碼。  
  
### 若要建立傳回值的程序  
  
1.  在任何其他程序之外，使用後面緊接 `End Function` 陳述式 \(Statement\) 的 `Function` 陳述式。  
  
2.  在 `Function` 陳述式中，於 `Function` 關鍵字後面緊接著程序名稱，然後是用括號括住的參數清單。  
  
3.  在括號後面緊接著 `As` 子句，以指定傳回值的資料型別。  
  
4.  將程序的程式碼陳述式放在 `Function` 與 `End Function` 陳述式之間。  
  
5.  使用 `Return` 陳述式，將值傳回給呼叫程式碼。  
  
     下列 `Function` 程序會在已知其他兩邊值的情況下，計算直角三角形的最長邊 \(也稱為斜邊\)。  
  
     [!CODE [VbVbcnProcedures#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#1)]  
  
     下列範例顯示  `hypotenuse` 的典型呼叫。  
  
     [!CODE [VbVbcnProcedures#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#6)]  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [How to: Return a Value from a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-return-a-value-from-a-procedure.md)   
 [How to: Call a Procedure That Returns a Value](../Topic/How%20to:%20Call%20a%20Procedure%20That%20Returns%20a%20Value%20\(Visual%20Basic\).md)