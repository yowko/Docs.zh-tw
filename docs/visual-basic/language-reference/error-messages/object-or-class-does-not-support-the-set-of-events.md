---
title: "Object or class does not support the set of events | Microsoft Docs"
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
  - "vbrID459"
dev_langs: 
  - "VB"
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Object or class does not support the set of events
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您嘗試以某一元件使用 `WithEvents` 變數，而該元件無法做為指定事件的設定之事件的來源。  例如，您希望接收某一物件的事件，然後建立另一個物件來 `Implements` 第一個物件。  您或許認為可以從實作的物件接收到事件，但並不是一定會這樣。  `Implements` 只會為方法和屬性實作介面。  私用的`UserControls` 不支援 `WithEvents`，因為在執行階段時並沒有引發 `ObjectEvent` 所需的型別資訊可供使用。  
  
### 若要更正這個錯誤  
  
1.  您不可為非事件來源的元件接收事件。  
  
## 請參閱  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)   
 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)