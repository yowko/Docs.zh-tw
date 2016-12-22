---
title: "&#39;#ElseIf&#39; must be preceded by a matching &#39;#If&#39; or &#39;#ElseIf&#39; | Microsoft Docs"
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
  - "vbc30014"
  - "bc30014"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30014"
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ElseIf&#39; must be preceded by a matching &#39;#If&#39; or &#39;#ElseIf&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#ElseIf` 是一個條件式編譯指示詞。  `#ElseIf` 子句的前面必須搭配相對應的 `#If` 或 `#ElseIf` 子句。  
  
 **錯誤 ID︰**BC30014  
  
### 若要更正這個錯誤  
  
1.  檢查前面的 `#If`  或 `#ElseIf` 是否未由中間條件式編譯區塊或位置不正確的 `#End If` 從此 `#ElseIf` 分隔。  
  
2.  如果 `#ElseIf` 的前面是 `#Else` 指示詞，請移除 `#Else` 或將它變更為 `#ElseIf`。  
  
3.  如果一切已就緒，請將 `#If` 指示詞加入條件式編譯區塊的開頭。  
  
## 請參閱  
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)