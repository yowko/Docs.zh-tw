---
title: "How to: Validate Strings That Represent Dates or Times (Visual Basic) | Microsoft Docs"
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
  - "strings [Visual Basic], validating"
  - "String data type, validation"
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Validate Strings That Represent Dates or Times (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

下列程式碼範例會設定 `Boolean` 值，指出代表日期或時間的字串是否有效。  
  
## 範例  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/visualbasic/how-to-validate-strings-_1.vb)]  
  
## 編譯程式碼  
 以想要驗證的日期和時間，分別取代 `("01/01/03")` 和 `"9:30 PM"`。  您可以使用另一個硬式編碼的字串、`String` 變數或會傳回字串的方法 \(例如，`InputBox`\)，取代上述字串。  
  
## 穩固程式設計  
 請先使用此方法驗證字串，再嘗試將 `String` 轉換為 `DateTime` 變數。  先檢查日期或時間，可以避免在執行階段產生例外狀況。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>   
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>   
 [Validating Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)