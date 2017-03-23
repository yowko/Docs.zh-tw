---
title: "Events of shared WithEvents variables cannot be handled by non-shared methods | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30594"
  - "vbc30594"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30594"
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Events of shared WithEvents variables cannot be handled by non-shared methods
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

使用 `Shared` 修飾詞來宣告的變數就是共用變數，  一個 Shared 變數只能識別一個儲存位置。  使用 `WithEvents` 修飾詞宣告的變數就會判斷提示 \(Assert\) 變數所屬型別要處理變數引發的一組事件。  將值指派給變數時，`WithEvents` 宣告建立的屬性會移除任何現有事件處理常式，同時透過 `Add` 方法加入新的事件處理常式。  
  
 **錯誤 ID**︰BC30594  
  
### 若要更正這個錯誤  
  
-   將事件處理常式宣告為 `Shared`。  
  
## 請參閱  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)   
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)