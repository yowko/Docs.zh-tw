---
title: "How to: Declare a Property with Mixed Access Levels (Visual Basic) | Microsoft Docs"
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
  - "access levels, properties"
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "mixed access levels"
  - "Visual Basic code, properties"
  - "properties [Visual Basic], access levels"
  - "Property statement, declaring mixed access levels"
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Declare a Property with Mixed Access Levels (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

若要屬性上的 `Get` 和 `Set` 程序擁有不同的存取層級，可在 `Property` 陳述式 \(Statement\) 中使用更寬鬆的層級，並且在 `Get` 或 `Set` 陳述式中使用更嚴格的層級。  若要程式碼的某個部分只能取得屬性值，而要其他部分能夠變更值，請在屬性上使用混合存取層級。  
  
 如需存取層級的詳細資訊，請參閱 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
### 若要宣告具有混合存取層級的屬性  
  
1.  以一般方式宣告屬性，然後於 `Property` 陳述式中指定較不嚴格的存取層級 \(例如 `Public`\)。  
  
2.  宣告 `Get` 或 `Set` 程序以指定更嚴格的存取層級 \(例如 `Friend`\)。  
  
3.  請勿在其他屬性程序上指定存取層級。  它會假設使用 `Property` 陳述式中宣告的存取層級。  您可以限制僅能存取其中一個屬性程序。  
  
     [!code-vb[VbVbcnProcedures#10](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-declare-a-propert_1.vb)]  
  
     在前述範例中，`Get` 程序擁有與屬性本身相同的 `Protected` 存取權限，`Set` 程序則擁有 `Private` 存取權限。  `salary` 值可供衍生自 `employee` 的類別 \(Class\) 讀取，但這個類別只能由 `employee` 類別進行設定。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)