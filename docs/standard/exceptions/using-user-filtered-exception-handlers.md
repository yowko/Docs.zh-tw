---
title: "使用使用者篩選的例外狀況處理常式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "例外狀況, 使用者篩選"
  - "使用者篩選的例外狀況"
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# 使用使用者篩選的例外狀況處理常式
目前，Visual Basic 支援使用者篩選的例外狀況。  使用者篩選的例外處理常式根據您對例外狀況定義的需求，攔截並處理例外狀況。  這些處理常式會使用 **Catch** 陳述式配合 **When** 關鍵字。  
  
 這個技術在特定例外狀況物件對應至多個錯誤時很有用處。  在這個情形中，物件基本上具有屬性，包含與錯誤相關聯的特定錯誤碼。  您可以在運算式中使用錯誤碼屬性，只選取您想要在那個 **Catch** 子句中處理的特定錯誤。  
  
 下列 Visual Basic 範例說明 **Catch\/When** 陳述式。  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 使用者篩選的子句的運算式並不以任何方式來限制。  如果例外狀況在使用者篩選運算式執行時發生，便會捨棄該例外狀況，並將篩選運算式視為已經評估成 false。  在此情形下，Common Language Runtime 會繼續搜尋目前例外狀況的處理常式。  
  
## 組合特定例外狀況和使用者篩選的子句  
 Catch 陳述式可以包含特定例外狀況和使用者篩選的子句兩者。  執行階段首先會測試特定例外狀況。  如果特定例外狀況成功，執行階段即執行使用者篩選條件。  泛用篩選條件可以包含宣告於類別篩選條件中的變數的參考。  注意，兩個篩選子句的順序不能相反。  
  
 下列 Visual Basic 範例示範 **Catch** 陳述式中的特定例外狀況 `ClassLoadException`，以及使用 **When** 關鍵字的使用者篩選子句。  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  
  
## 請參閱  
 [如何：使用 Try\/Catch 區塊攔截例外狀況](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [如何：使用 Catch 區塊中的特定例外狀況](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)   
 [例外狀況的最佳作法](../../../docs/standard/exceptions/best-practices-for-exceptions.md)   
 [例外狀況處理基礎觀念](../../../docs/standard/exceptions/exception-handling-fundamentals.md)