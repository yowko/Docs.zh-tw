---
title: "Walkthrough: Validating That Passwords Are Complex (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "String data type, validation"
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Walkthrough: Validating That Passwords Are Complex (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

這個方法會檢查是否一些強式密碼性質，並以檢查密碼失敗的相關資訊更新字串參數。  
  
 密碼可以用在安全的系統，以便授權使用者。  然而，密碼必須難以讓未授權使用者猜出。  攻擊者可以使用「*字典攻擊*」\(Dictionary Attack\) 程式，這個程式會逐一查看字典 \(或多個不同語言的字典\) 中的所有字組，並測試是否有任何字組可做為使用者的密碼。  如 "Yankees" 或 "Mustang" 之類的弱式密碼，很快就會被猜出。  如 "?You'L1N3vaFiNdMeyeP@sSWerd\!" 之類的強式密碼，則非常不可能被猜出。  密碼保護的系統應該確定使用者選擇強式密碼。  
  
 強式密碼是很複雜的 \(包含大寫、小寫、數字和特殊字元的混用\)，而且不是單字。  以下範例會驗證複雜性。  
  
## 範例  
  
### 程式碼  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## 編譯程式碼  
 傳遞包含該密碼的字串，呼叫這個方法。  
  
 這個範例需要：  
  
-   對 <xref:System.Text.RegularExpressions> 命名空間成員的存取權。  如果您的程式碼中未完整限定成員名稱，請加入 `Imports` 陳述式。  如需詳細資訊，請參閱 [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## 安全性  
 如果您要跨網路移動密碼，則您需要使用安全方法傳送資料。  如需詳細資訊，請參閱 [ASP.NET Web Application Security](../Topic/ASP.NET%20Web%20Application%20Security.md)。  
  
 您可以加入其他複雜性檢查，改善 `ValidatePassword` 函式的精確性：  
  
-   對照使用者名稱、使用者識別項和應用程式定義的字典，比較密碼和子字串。  此外，當執行比較時，將看起來類似的字元視為對等字元。  例如，將字母 "l" 和 "e" 視為與數字 "1" 和 "3" 對等。  
  
-   如果只有一個大寫字元，請確定它不是密碼的第一個字元。  
  
-   確定密碼的最後兩個字元是字母字元。  
  
-   不允許密碼的所有符號，都是從鍵盤第一列輸入的。  
  
## 請參閱  
 <xref:System.Text.RegularExpressions.Regex>   
 [ASP.NET Web Application Security](../Topic/ASP.NET%20Web%20Application%20Security.md)