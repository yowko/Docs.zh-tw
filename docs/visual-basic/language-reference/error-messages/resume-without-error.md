---
title: "Resume without error | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID20"
dev_langs: 
  - "VB"
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Resume without error
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`Resume` 陳述式出現在錯誤處理程式碼外部，或者即使沒有錯誤但程式碼仍然跳至錯誤處理常式中。  
  
### 若要更正這個錯誤  
  
1.  請將 `Resume` 陳述式移動至錯誤處理常式，或者直接刪除。  
  
2.  跳躍標籤不能跨程序發生，因此請搜尋可識別錯誤處理常式的標籤程序。  如果您找到重複並指定為 `GoTo` 陳述式 \(而不是 `On Error GoTo` 陳述式\) 的目標標籤，請變更列標籤以符合其原本的目標。  
  
## 請參閱  
 [Resume Statement](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)