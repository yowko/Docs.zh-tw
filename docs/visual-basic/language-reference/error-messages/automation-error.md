---
title: "Automation error | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID440"
dev_langs: 
  - "VB"
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Automation error
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

執行方法，或取得或設定物件變數的屬性時發生錯誤。  錯誤由建立物件的應用程式所回報。  
  
### 更正這個錯誤  
  
1.  檢查 `Err` 物件的屬性，判斷錯誤的來源和本質。  
  
2.  在存取陳述式之前使用 `On Error Resume Next` 陳述式，然後在存取陳述式之後立即檢查錯誤。  
  
## 請參閱  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [告訴我們](/visual-studio/ide/talk-to-us)