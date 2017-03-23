---
title: "Declaration expected | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30188"
  - "bc30188"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30188"
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Declaration expected
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

在程序之外出現一個像是指派或迴圈陳述式的非宣告式陳述式。  程序以外只容許宣告。  
  
 相反地，程式項目並沒有使用像是 `Dim` 或 `Const` 的宣告關鍵字來宣告。  
  
 **錯誤 ID：**BC30188  
  
### 若要更正這個錯誤  
  
-   將非宣告式項目移到程序的主體之中。  
  
-   使用適當的宣告關鍵字做為宣告的開頭。  
  
-   確定宣告關鍵字的拼字是否正確。  
  
## 請參閱  
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)