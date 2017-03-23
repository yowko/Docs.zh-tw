---
title: "Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30941"
  - "vbc30941"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30941"
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

結構定義並未包含任何非共用變數或非共用的非自訂事件。  
  
 每個結構所擁有的變數或事件，必須是套用至個別的特定執行個體 \(即非共用的\)，而非一併套用至全部執行個體 \([Shared](../../../visual-basic/language-reference/modifiers/shared.md)\)。  非共用的常數、屬性和程序並未能符合這項規定。  此外，如果沒有非共用變數而只有一個非共用事件，則該事件不可以是 `Custom` 事件。  
  
 **錯誤 ID**：BC30941  
  
### 若要更正這個錯誤  
  
-   請至少定義一個不是 `Shared` 的變數或事件。  如果只有定義一個事件，該事件必須為非自訂而且也是非共用的。  
  
## 請參閱  
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [How to: Declare a Structure](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)