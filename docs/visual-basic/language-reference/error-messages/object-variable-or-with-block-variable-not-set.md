---
title: "Object variable or With block variable not set | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID91"
dev_langs: 
  - "VB"
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# Object variable or With block variable not set
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

參考的變數無效。  若要建立物件變數，必須宣告該物件變數，然後使用 `Set` 陳述式為物件變數指定有效的參考。  同樣地，`With...End With` 區塊必須藉由執行 `With` 陳述式進入點 \(Entry Point\) 進行初始化。  
  
### 若要更正這個錯誤  
  
1.  請確定物件變數參考有效的物件，而且指定或重新指定物件的參考。  
  
2.  請確定您未使用設定為 `Nothing` 的物件變數。  
  
3.  請確定在 \[`Add References`\] 對話方塊中，已選取描述物件所在的物件程式庫。  
  
4.  請確定您的 `With` 區塊已經藉由執行 `With` 陳述式進入點進行初始化。  
  
## 請參閱  
 [Object Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)