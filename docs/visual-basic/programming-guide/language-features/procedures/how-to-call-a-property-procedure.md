---
title: "How to: Call a Property Procedure (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "Visual Basic code, properties"
  - "procedures, calling"
  - "properties [Visual Basic], property procedures"
  - "procedure calls, property procedures"
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Call a Property Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以藉由儲存屬性值或擷取其值來呼叫屬性程序，  您可以利用存取變數的方式來存取屬性。  
  
 屬性的 `Set` 程序可儲存值，且其 `Get` 程序可擷取值。  然而，您不會依名稱明確地呼叫這些程序。  您可以使用指派陳述式或運算式來使用屬性，如同儲存或擷取變數值一般。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會呼叫屬性的程序。  
  
### 若要呼叫屬性的 Get 程序  
  
1.  請在運算式中使用屬性名稱，使用方式與使用變數名稱相同。  只要可以使用變數或常數的地方，都可以使用屬性。  
  
     \-或\-  
  
     請在指派陳述式的等號 \(`=`\) 後使用屬性名稱。  
  
     下列範例會讀取 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> 屬性的值，隱含地呼叫其 `Get` 程序。  
  
     [!code-vb[VbVbalrDateProperties#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/VbVbalrDateProperties/Module1.vb#4)]  
  
2.  如果屬性有引數，請在屬性名稱之後緊接著括號，將引數清單括起來。  如果未提供引數，您也可以選擇省略括號。  
  
3.  在引數清單中，將引數置於括號內並以逗號分隔。  請確定您是以屬性定義所對應參數的相同順序來提供引數。  
  
 屬性值會如同變數或常數加入運算式，或是儲存於指派陳述式左邊的變數或屬性中。  
  
### 若要呼叫屬性的 Set 程序  
  
1.  請在指派陳述式的左邊使用屬性名稱。  
  
     下列範例會設定 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> 屬性的值，隱含呼叫 `Set` 程序。  
  
     [!code-vb[VbVbcnProcedures#11](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-call-a-property-p_2.vb)]  
  
2.  如果屬性有引數，請在屬性名稱之後緊接著括號，將引數清單括起來。  如果未提供引數，您也可以選擇省略括號。  
  
3.  在引數清單中，將引數置於括號內並以逗號分隔。  請確定您是以屬性定義所對應參數的相同順序來提供引數。  
  
 指派陳述式右邊所產生的值會存入屬性中。  
  
## 請參閱  
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)   
 [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)   
 [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)