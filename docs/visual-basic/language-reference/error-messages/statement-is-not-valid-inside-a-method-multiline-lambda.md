---
title: "Statement is not valid inside a method/multiline lambda | Microsoft Docs"
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
  - "vbc30024"
  - "bc30024"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30024"
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Statement is not valid inside a method/multiline lambda
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Sub`、`Function`、屬性 `Get` 或屬性  `Set` 程序中的陳述式無效。  某些陳述式可放在模組或類別層級。  其他像是 `Option Strict`，則必須放在命名空間層級並置於所有宣告之前。  
  
 **錯誤 ID：**BC30024  
  
### 若要更正這個錯誤  
  
-   移除程序中的陳述式。  
  
## 請參閱  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)   
 [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)