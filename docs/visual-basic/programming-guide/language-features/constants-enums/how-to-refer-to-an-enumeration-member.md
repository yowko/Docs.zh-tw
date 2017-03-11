---
title: "How to: Refer to an Enumeration Member (Visual Basic) | Microsoft Docs"
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
  - "enumerations [Visual Basic], referring to"
  - "values, associating constant values with names"
  - "enumeration members"
  - "constants, enumerated"
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Refer to an Enumeration Member (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

列舉型別 \(Enumeration\) 提供使用相關常數組和建立常數值與名稱間關聯的便利方法。  例如，您可以宣告列舉來當做一組與每週日期關聯的整數常數，接著在程式碼中使用日期的名稱而不是它們的整數值。  
  
 您可以搭配使用 `Imports` 陳述式，就無須指定完整的名稱。  如需詳細資訊，請參閱[Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。  
  
### 若要參考列舉型別成員  
  
-   在成員名稱前面加上列舉型別。  例如，下面的範例會將 `FirstDayOfWeek` 列舉型別的 `Saturday` 成員指派給變數 `DayValue`。  
  
     [!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#19)]  
  
## 請參閱  
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)