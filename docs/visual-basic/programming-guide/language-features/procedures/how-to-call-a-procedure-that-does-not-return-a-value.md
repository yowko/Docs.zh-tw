---
title: "How to: Call a Procedure that Does Not Return a Value (Visual Basic) | Microsoft Docs"
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
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# How to: Call a Procedure that Does Not Return a Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

`Sub` 程序不會傳回值給呼叫程式碼。  您可以利用獨立的呼叫陳述式，明確地呼叫它。  您無法在運算式中只以其名稱來呼叫它。  
  
### 若要呼叫 Sub 程序  
  
1.  指定 `Sub` 程序的名稱。  
  
2.  遵循有括號的程序名稱，封入引數清單。  如果未提供引數，您也可以選擇省略括號。  但是，使用括號會讓您的程式碼更容易閱讀。  
  
3.  在引數清單中，將引數置於括號內並以逗號分隔。  請務必以 `Sub` 程序定義對應參數的順序來提供引數。  
  
     下列範例會呼叫 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 函式，以啟動應用程式視窗。  <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 採取視窗標題做為其獨有引數。  它不會傳回值給呼叫程式碼。  若記事本處理序並未執行，這個範例就會產生 <xref:System.ArgumentException>。  `Shell` 程序會假設應用程式是在指定的路徑中。  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>   
 <xref:System.ArgumentException>   
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [How to: Create a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure.md)   
 [How to: Call a Procedure That Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-returns-a-value.md)   
 [How to: Call an Event Handler in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-event-handler.md)