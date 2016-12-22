---
title: "&#39;Module&#39; statements can occur only at file or namespace level | Microsoft Docs"
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
  - "bc30617"
  - "vbc30617"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30617"
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Module&#39; statements can occur only at file or namespace level
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Module` 陳述式必須出現在原始程式檔 \(Source File\) 的最前面，緊接在 `Option` 和 `Imports` 陳述式、全域屬性 \(Property\) 和命名空間 \(Namespace\) 宣告之後，但是要在其他所有宣告之前。  
  
 **錯誤 ID︰**BC30617  
  
### 若要更正這個錯誤  
  
-   請將 `Module` 陳述式移至命名空間宣告或原始程式檔的最前面。  
  
## 請參閱  
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)