---
title: "How to: Create a String from An Array of Char Values (Visual Basic) | Microsoft Docs"
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
  - "examples [Visual Basic], arrays"
  - "examples [Visual Basic], Char data type"
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create a String from An Array of Char Values (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

這個範例使用個別字元來建立字串 "abcd"。  
  
## 範例  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## 編譯程式碼  
 這個方法沒有任何特殊的需求。  
  
 語法 `"a"c` \(其中單一 `c` 緊跟著以引號括住的單一字元\) 是用來建立字元常值 \(Character Literal\)。  
  
## 穩固程式設計  
 字串中的 null 字元 \(相當於 `Chr(0)`\) 會在使用字串時造成無法預期的結果。  null 字元包含在字串中，但是在某些情況下不會顯示接在 null 字元後的字元。  
  
## 請參閱  
 <xref:System.String>   
 [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [資料類型](../../../../visual-basic/reference/command-line-compiler/index.md)