---
title: "Identifier is too long | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30033"
  - "vbc30033"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30033"
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Identifier is too long
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

每個程式設計項目的名稱或識別項，都不能超過 1023 個字元的限制。  此外，完整名稱不可超過 1023 個字元。  這表示整個識別項字串 \(`<namespace>.<...>.<namespace>.<class>.<element>`\) 的長度不可超過 1023 個字元，包括成員存取運算子 \(`.`\) 字元在內。  
  
 **錯誤 ID：**BC30033  
  
### 若要更正這個錯誤  
  
-   減少識別項的長度。  
  
## 請參閱  
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)