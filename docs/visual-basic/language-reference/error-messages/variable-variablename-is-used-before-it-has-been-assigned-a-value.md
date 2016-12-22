---
title: "Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42104"
  - "BC42104"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42104"
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

變數 '\<variablename\>' 已在指派值之前使用。而且會在執行階段產生 null 參考例外狀況。  
  
 應用程式在程式碼中至少有一個可能的路徑，可以在指派任何值給變數之前先讀取該變數。  
  
 如果從未指派變數的值，則變數會保留資料型別的預設值。  若是參考資料型別，預設值為 [Nothing](../../../visual-basic/language-reference/nothing.md)。  讀取具有 `Nothing` 值的參考變數會在某些情況下造成 <xref:System.NullReferenceException>。  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID**︰BC42104  
  
### 若要更正這個錯誤  
  
-   檢查控制項流程邏輯，並確定變數具有有效值，再將控制項傳遞至讀取它的任何一個陳述式。  
  
-   保證變數一定會具備有效值的一個方法，是將變數初始化為宣告的一部分。  請參閱 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) 中的＜初始設定＞一節。  
  
## 請參閱  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [為變數進行疑難排解](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)