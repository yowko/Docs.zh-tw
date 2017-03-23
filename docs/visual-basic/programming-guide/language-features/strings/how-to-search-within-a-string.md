---
title: "How to: Search Within a String (Visual Basic) | Microsoft Docs"
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
  - "strings [Visual Basic], finding"
  - "strings [Visual Basic], searching"
  - "examples [Visual Basic], strings"
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Search Within a String (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

這個範例在 <xref:System.String> 物件上呼叫 <xref:System.String.IndexOf%2A> 方法，報告第一個出現的子字串索引。  
  
## 範例  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   指定 <xref:System> 命名空間的 `Imports` 陳述式。  如需詳細資訊，請參閱 [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## 穩固程式設計  
 <xref:System.String.IndexOf%2A> 方法會報告子字串之第一個相符項目的第一個字元的位置。  索引是以 0 起始，這表示字串的第一個字元之索引為 0。  
  
 如果 <xref:System.String.IndexOf%2A> 找不到子字串，則會傳回 \-1。  
  
 <xref:System.String.IndexOf%2A> 方法區分大小寫，並使用目前的文化特性。  
  
 如需最佳化錯誤控制項，您會想將字串搜尋封入 [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) 語法結構的 `Try` 區塊中。  
  
## 請參閱  
 <xref:System.String.IndexOf%2A>   
 [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)   
 [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md)