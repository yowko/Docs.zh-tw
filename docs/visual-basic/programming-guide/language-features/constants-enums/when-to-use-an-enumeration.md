---
title: "When to Use an Enumeration (Visual Basic) | Microsoft Docs"
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
  - "enumerations [Visual Basic]"
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# When to Use an Enumeration (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

列舉型別則能夠讓您輕鬆使用一組相關的常數。  列舉型別或 `Enum` 是一組值的符號名稱。  列舉型別可視為是資料型別，您可以用來建立多組常數以便與變數和屬性搭配使用。  
  
## 何時使用列舉型別  
 當程序接受一組限定的變數時，請考慮使用列舉型別。  列舉型別可使程式碼更清楚、更容易讀取，特別是使用有意義的名稱時。  
  
 使用列舉型別的好處包括：  
  
-   減少因調換或輸錯數字造成的錯誤。  
  
-   將來更容易變更值。  
  
-   使程式碼更容易讀取，即不容易產生錯誤。  
  
-   確保向前相容性 \(Forward Compatibility\)。  若使用列舉型別，一旦將來有人變更對應到成員名稱的值，程式碼失敗的可能性會較低。  
  
## 命名列舉型別  
 請使用列舉型別成員的命名規範。  當 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 遇到列舉型別成員名稱時，如果其他參考的型別程式庫內含相同名稱，可能會擲回例外狀況。  請使用唯一前置詞，以便識別應用程式或元件的值。  
  
 當參考列舉型別的成員時，您必須使用列舉型別名稱或使用 `Imports` 陳述式限定成員名稱。  如需詳細資訊，請參閱[Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。  
  
## 預先定義的列舉型別  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會提供數個預先定義的列舉型別 \(如 `FirstDayOfWeek` 和 `MsgBoxResul`\)，幫助您撰寫程式碼。  如需這些型別的清單，請參閱[Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)。  
  
## 請參閱  
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)