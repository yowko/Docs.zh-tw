---
title: "&#39;Class&#39; statement must end with a matching &#39;End Class&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30481"
  - "bc30481"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30481"
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &#39;Class&#39; statement must end with a matching &#39;End Class&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`Class` 是用來啟始 `Class` 區塊；因此它只能出現在區塊的開頭，而且後面有相對應的 `End Class` 陳述式來結束區塊。  您可能有多餘的 `Class` 陳述式，或者您不是以 `End Class` 結束 `Class` 區塊。  
  
 **錯誤 ID︰**BC30481  
  
### 若要更正這個錯誤  
  
-   找出並移除多餘的 `Class` 陳述式。  
  
-   使用對應的 `End Class` 結束 `Class` 區塊。  
  
## 請參閱  
 [End \<keyword\> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)