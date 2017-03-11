---
title: "How to: Put a Value in a Property (Visual Basic) | Microsoft Docs"
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
  - "property values"
  - "Visual Basic code, procedures"
  - "values, properties"
  - "Visual Basic code, properties"
  - "properties [Visual Basic], values"
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Put a Value in a Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

藉由在指派陳述式 \(Assignment Statement\) 的左邊放置屬性名稱，即可將值置入屬性。  
  
 屬性的 `Set` 程序可儲存值，但您並未依名稱明確呼叫它。  使用此屬性的方式與使用變數相同。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會呼叫屬性的程序。  
  
### 若要將值存入屬性  
  
1.  請在指派陳述式的左邊使用屬性名稱。  
  
     下列範例會將 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] `TimeOfDay` 屬性值設定為 noon，隱含呼叫其 `Set` 程序。  
  
     [!code-vb[VbVbcnProcedures#11](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-put-a-value-in-a-_1.vb)]  
  
2.  如果屬性有引數，請在屬性名稱之後緊接著括號，將引數清單括起來。  如果未提供引數，您也可以選擇省略括號。  
  
3.  在引數清單中，將引數置於括號內並以逗號分隔。  請確定您是以屬性定義所對應參數的相同順序來提供引數。  
  
4.  指派陳述式右邊所產生的值會存入屬性中。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)