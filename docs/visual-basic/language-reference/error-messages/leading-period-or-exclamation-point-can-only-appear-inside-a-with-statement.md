---
title: "Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30157"
  - "bc30157"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30157"
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Leading &#39;.&#39; or &#39;!&#39; can only appear inside a &#39;With&#39; statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

產生一個不在 `With` 區塊內的句號 \(.\) 或驚嘆號 \(\!\)，且在左邊沒有運算式。  成員存取 \(`.`\) 和字典成員存取 \(`!`\) 需要一個運算式來指定含有成員的項目。  這必須立刻出現在存取子的左邊，或是做為含有成員存取之 `With` 區塊的目標。  
  
 **錯誤 ID：**BC30157  
  
### 若要更正這個錯誤  
  
1.  確定是否正確地格式化 `With` 區塊。  
  
2.  如果沒有 `With` 區塊，在評估為含有成員之已定義項目的存取子左邊，加上一個運算式。  
  
## 請參閱  
 [Special Characters in Code](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)   
 [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)