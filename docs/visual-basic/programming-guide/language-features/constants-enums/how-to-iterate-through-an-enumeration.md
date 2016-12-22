---
title: "How to: Iterate Through An Enumeration in Visual Basic | Microsoft Docs"
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
  - "arrays [Visual Basic], iterating"
  - "enumerations [Visual Basic], iterating"
  - "ListBox control [Windows Forms], populating from an enumeration"
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Iterate Through An Enumeration in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

列舉型別提供使用相關常數組和建立常數值與名稱間關聯的便利方法。  若要逐一查看列舉型別 \(Enumeration\)，您可使用 <xref:System.Enum.GetValues%2A> 方法將該列舉型別移至陣列中。  您也可以使用 `For...Each` 陳述式、使用 <xref:System.Enum.GetNames%2A> 或 <xref:System.Enum.GetValues%2A> 方法擷取字串或數值，來逐一查看列舉型別。  
  
### 若要逐一查看列舉型別  
  
-   首先宣告一陣列，然後使用 <xref:System.Enum.GetValues%2A> 方法將列舉型別轉換為該陣列，接著您就可以如同其他任何變數一般來傳遞陣列。  下列範例會顯示逐一查看列舉型別時，列舉型別 <xref:Microsoft.VisualBasic.FirstDayOfWeek> 的每個成員。  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## 請參閱  
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [How to: Determine the String Associated with an Enumeration Value](../Topic/How%20to:%20Determine%20the%20String%20Associated%20with%20an%20Enumeration%20Value%20\(Visual%20Basic\).md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)