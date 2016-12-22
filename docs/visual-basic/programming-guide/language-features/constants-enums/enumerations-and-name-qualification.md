---
title: "Enumerations and Name Qualification (Visual Basic) | Microsoft Docs"
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
  - "declarations, enumerations"
  - "Imports statement, namespace declarations"
  - "declaring namespaces, enumerations"
  - "name collisions"
  - "ambiguous names, enumerations"
  - "enumerations [Visual Basic], name qualification"
  - "names, avoiding conflicts"
  - "namespaces, declaring"
  - "naming conflicts, enumerations"
  - "naming conflicts, qualifying names"
  - "declaring enumerations"
  - "references, enumeration members"
  - "naming conventions, naming conflicts"
  - "declarations, namespaces"
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Enumerations and Name Qualification (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

通常當您參考列舉型別的成員時，必須使用列舉型別名稱來限定成員名稱。  例如，要參考 `Days` 列舉型別的 `Sunday` 成員時，您將會使用下列語法：  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## 使用匯入陳述式  
 您可以將 `Imports` 陳述式加入至程式碼中的命名空間 \(Namespace\) 宣告區段，這樣就可避免使用完整名稱，如下列範例所示：  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 `Imports` 陳述式會從參考專案和組件匯入命名空間名稱，以及在同一專案中，從出現這個陳述式的模組匯入命名空間名稱。  加入這個陳述式後，您便可以參考列舉成員而不需限定，如下列範例所示：  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 您可透過在列舉型別中組織關聯的常數集，以在不同的內文中使用相同的常數名稱。  例如，您可以在 `Days` 和 `WorkDays` 列舉型別中使用名稱相同的星期名稱常數。  如果您對列舉型別使用 `Imports` 陳述式，則必須小心地避免模稜兩可的參考。  參考下列範例：  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 假設 `Monday` 同時是 `Days` 和 `Workdays` 列舉型別的成員，則這段程式碼會產生編譯器錯誤。  若要在參考個別常數時避免模稜兩可的參考，請使用常數的列舉來限定常數名稱。  下列程式碼參考 `Days` 和 `WorkDays` 列舉型別中的 `Saturday` 常數。  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## 請參閱  
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [How to: Determine the String Associated with an Enumeration Value](../Topic/How%20to:%20Determine%20the%20String%20Associated%20with%20an%20Enumeration%20Value%20\(Visual%20Basic\).md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)