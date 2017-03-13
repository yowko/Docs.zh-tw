---
title: "How to: Call a Procedure That Returns a Value (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedure calls, returning values"
  - "Visual Basic code, procedures"
  - "procedures, calling"
  - "procedures, returning a value"
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Call a Procedure That Returns a Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

`Function` 程序會將值傳回給呼叫程式碼。  您可以藉由將其名稱和引數包括在指派陳述式的右邊或在運算式中，來加以呼叫。  
  
### 若要呼叫運算式內的 Function 程序  
  
1.  以使用變數的相同方式，使用 `Function` 程序名稱。  運算式中能使用變數或常數的任何位置，都可以使用 `Function` 程序呼叫。  
  
2.  遵循有括號的程序名稱，封入引數清單。  如果未提供引數，您也可以選擇省略括號。  但是，使用括號會讓您的程式碼更容易閱讀。  
  
3.  在引數清單中，將引數置於括號內並以逗號分隔。  請確定依 `Function` 程序定義對應參數的順序來提供引數。  
  
     此外，也可以依名稱來傳遞一或多個引數。  如需詳細資訊，請參閱[Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)。  
  
4.  程序的傳回值會參與運算式，方式與變數或常數參與運算式的方式相同。  
  
### 若要在指派陳述式中呼叫 Function 程序  
  
1.  請在指派陳述式的等號 \(`=`\) 後使用 `Function` 程序名稱。  
  
2.  遵循有括號的程序名稱，封入引數清單。  如果未提供引數，您也可以選擇省略括號。  但是，使用括號會讓您的程式碼更容易閱讀。  
  
3.  在引數清單中，將引數置於括號內並以逗號分隔。  請確定依 `Function` 程序定義對應參數的順序來提供引數 \(除非依名稱傳遞這些參數\)。  
  
4.  程序的傳回值會儲存在指派陳述式左邊的變數或屬性中。  
  
## 範例  
 下列範例會呼叫 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A>，來擷取作業系統環境變數的值。  第一行會呼叫運算式內部的 `Environ`，第二行則會在指派陳述式中呼叫它。  `Environ` 採取變數名稱做為其獨有引數。  它會將變數值傳回至呼叫程式碼中。  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## 請參閱  
 [函式程序](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [How to: Create a Procedure that Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure-that-returns-a-value.md)   
 [How to: Return a Value from a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-return-a-value-from-a-procedure.md)   
 [How to: Call a Procedure that Does Not Return a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-does-not-return-a-value.md)