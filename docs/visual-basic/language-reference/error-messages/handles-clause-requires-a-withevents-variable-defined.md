---
title: "Handles clause requires a WithEvents variable defined in the containing type or one of its base types | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30506"
  - "bc30506"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30506"
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Handles clause requires a WithEvents variable defined in the containing type or one of its base types
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

您未在 `Handles` 子句中提供 `WithEvents` 變數。  在程序宣告結尾的 `Handles` 關鍵字，會讓它處理使用 `WithEvents` 關鍵字宣告的物件變數引發的事件。  
  
 **錯誤 ID**︰BC30506  
  
### 若要更正這個錯誤  
  
-   提供需要的 `WithEvents` 變數。  
  
## 請參閱  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)