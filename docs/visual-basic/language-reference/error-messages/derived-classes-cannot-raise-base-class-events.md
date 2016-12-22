---
title: "Derived classes cannot raise base class events | Microsoft Docs"
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
  - "vbc30029"
  - "bc30029"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30029"
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Derived classes cannot raise base class events
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

只有從宣告事件的宣告空間才能引發該事件。  因此，類別不能從其他類別 \(即使是衍生它的類別\) 引發事件。  
  
 **錯誤 ID**：BC30029  
  
### 若要更正這個錯誤  
  
-   移動 `Event` 陳述式或 `RaiseEvent` 陳述式，以便讓他們在相同的類別之中。  
  
## 請參閱  
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md)