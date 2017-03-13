---
title: "How to: Iterate Through An Enumeration in Visual Basic | Microsoft Docs"
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
  - "arrays [Visual Basic], iterating"
  - "enumerations [Visual Basic], iterating"
  - "ListBox control [Windows Forms], populating from an enumeration"
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How to: Iterate Through An Enumeration in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

列舉型別提供使用相關常數組和建立常數值與名稱間關聯的便利方法。  若要逐一查看列舉型別 \(Enumeration\)，您可使用 <xref:System.Enum.GetValues%2A> 方法將該列舉型別移至陣列中。  您也可以使用 `For...Each` 陳述式、使用 <xref:System.Enum.GetNames%2A> 或 <xref:System.Enum.GetValues%2A> 方法擷取字串或數值，來逐一查看列舉型別。  
  
### 若要逐一查看列舉型別  
  
-   首先宣告一陣列，然後使用 <xref:System.Enum.GetValues%2A> 方法將列舉型別轉換為該陣列，接著您就可以如同其他任何變數一般來傳遞陣列。  下列範例會顯示逐一查看列舉型別時，列舉型別 <xref:Microsoft.VisualBasic.FirstDayOfWeek> 的每個成員。  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## 請參閱  
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)