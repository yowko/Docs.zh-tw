---
title: "Statement cannot end a block outside of a line &#39;If&#39; statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc32005"
  - "bc32005"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32005"
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Statement cannot end a block outside of a line &#39;If&#39; statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

單行的 `If` 陳述式包含數個用冒號 \(:\) 分隔的陳述式，其中一個是該行 `If` 之外的控制區塊所使用的 `End` 陳述式。  單行的 `If` 陳述式不使用 `End If` 陳述式。  
  
 **錯誤 ID︰**BC32005  
  
### 若要更正這個錯誤  
  
-   請將單行的 `If` 陳述式移至包含 `End If` 陳述式的控制區塊之外。  
  
## 請參閱  
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)