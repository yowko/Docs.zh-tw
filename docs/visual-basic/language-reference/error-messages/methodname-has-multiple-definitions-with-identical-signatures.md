---
title: "&#39;&lt;methodname&gt;&#39; has multiple definitions with identical signatures | Microsoft Docs"
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
  - "vbc30269"
  - "bc30269"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30269"
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;methodname&gt;&#39; has multiple definitions with identical signatures
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Function` 或 `Sub` 程序宣告使用和前一個宣告相同的程序名稱與引數清單。  可能的原因是嘗試多載原始程序。  多載程序必須具有不同的引數清單。  
  
 **錯誤 ID**︰BC30269  
  
### 若要更正這個錯誤  
  
-   變更程序名稱或引數清單，或是移除重複的宣告。  
  
## 請參閱  
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Considerations in Overloading Procedures](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)